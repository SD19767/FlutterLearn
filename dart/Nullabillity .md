## **Null Overview**

- Swift: 變數形態須為 Optional ，才可將變數指向 nil 。

```swift
var a = nil // ❌ 'nil' requires a contextual type
var b: Int? = nil
```

- Dart: 變數可指向 null，不給予值時為 null 。

```dart
var a; // null
var b = null; // null
int? c; // null
```

- The non-nullable type is a subtype of its nullable form. For example, String is a subtype of String? since String? can be a String.
- For any nullable variable in Dart, if you don’t initialize it with a value, it’ll be given the default value of `null`.

## Handling Nullable Types

### Type Promotion

- The **Dart analyzer** is the tool that tells you what the compile-time errors and warnings are. It’s smart enough to tell in a wide range of situations if a nullable variable is guaranteed to contain a non-null value or not.

Take the last example, but this time assign `name` a string literal:

```dart
String? name;
name = 'Ray';
print(name.length);
```

### Flow Analysis

- Type promotion works for more than just the trivial example above. Dart uses sophisticated **flow analysis** to check every possible route the code could take. As long as none of the routes come up with the possibility of `null`, it’s promotion time!

Take the following slightly less trivial example:

```dart
bool isPositive(int? anInteger) {
  if (anInteger == null) {
    return false;
  }
  return !anInteger.isNegative;
}
```

### Null-Aware Operators

- **`??`**: If-null operator. (同 Swift)
- **`??=`**: Null-aware assignment operator.
- **`?.`**: Null-aware access operator. (同 Swift)
- **`?.`**: Null-aware method invocation operator. (同 Swift)
- **`!`**: Null assertion operator. (同 Swift)
- **`?..`**: Null-aware cascade operator.
- **`?[]`**: Null-aware index operator.
- **`...?`**: Null-aware spread operator.

### If-Null Operator (`??`)

```dart
String? message;
final text = message ?? 'Error';
```

```dart
String text;
if (message == null) {
  text = 'Error';
} else {
  text = message;
}
```

### Null-Aware Assignment Operator (`??=`)

```dart
fontSize = fontSize ?? 20.0;
```

```dart
fontSize ??= 20.0;
```

### Null-Aware Access Operator (`?.`)

```dart
int? age;
print(age?.isNegative);
```

### Null-Aware Method Invocation Operator (`?.`)

```dart
print(age?.toDouble());
```

### Null Assertion Operator (`!`)

```dart
String nonNullableString = myNullableString!;
```

Here’s an example to see the assertion operator at work. In your project, add the following function that returns a nullable Boolean:

```dart
bool? isBeautiful(String? item) {
  if (item == 'flower') {
    return true;
  } else if (item == 'garbage') {
    return false;
  }
  return null;
}
```

```dart
bool flowerIsBeautiful = isBeautiful('flower')!;
```

```dart
bool flowerIsBeautiful = isBeautiful('flower') as bool;
```

Here’s an alternative that won’t ever crash the app:

```dart
bool flowerIsBeautiful = isBeautiful('flower') ?? true;
```

### Null-Aware Cascade Operator (`?..`)

```dart
class User {
  String? name;
  int? id;
}
```

```dart
User user = User()
  ..name = 'Ray'
  ..id = 42;
```

```dart
User? user;
```

```dart
user
  ?..name = 'Ray'
  ..id = 42;
```

You only need to use `?..` for the first item in the chain. If `user` is `null`, then the chain will be **short-circuited**, or terminated, without calling the other items in the cascade chain.

This is similar for the null-aware access operator (`?.`) as well. Look at this example:

```dart
String? lengthString = user?.name?.length.toString();
```

### The Late Keyword

Sometimes you want to use a non-nullable type, but you can’t initialize it in any of the ways you learned above.

Here’s an example:

```dart
class User {
  User(this.name);

  final String name;
  final int _secretNumber = _calculateSecret();

  int _calculateSecret() {
    return name.length + 42;
  }
}
```

```
The instance member '_calculateSecret' can't be accessed in an initializer.
```

```dart
late final int _secretNumber = _calculateSecret();
```

- Using `late` means that Dart doesn’t initialize the variable right away. It only initializes it when you access it the first time. This is also known as **lazy initialization**. It’s like procrastination for variables.

It’s also common to use `late` to initialize a field variable in the constructor body. Here’s an alternate version of the example above:

```dart
class User {
  User(this.name) {
    _secretNumber = _calculateSecret();
  }
  late final int _secretNumber;
  // ...
}

```

Initializing a final variable in the constructor body wouldn’t have been allowed if it weren’t marked as `late`.

### Dangers of Being Late

The example above was for initializing a final variable, but you can also use `late` with non-final variables. You have to be careful with this, though:

```dart
class User {
  late String name;
}

```

- Dart doesn’t complain at you, because using `late` means that you’re promising Dart that you’ll initialize the field before it’s ever used. This moves checking from compile-time to runtime.

Now add the following code to `main` and run it:

```dart
final user = User();
print(user.name);
```

```
LateInitializationError: Field 'name' has not been initialized.
```

### Benefits of Being Lazy

- There are times when it might take some heavy calculations to initialize a variable. If you never end up using the variable, then all that initialization work was a waste. Since *lazy*initialization is never done until you actually use the variable, though, this kind of work will never be wasted.
- Top-level and static variables have always been lazy in Dart. As you learned above, the `late` keyword makes other variables lazy, too. That means even if your variable is nullable, you can still use `late` to get the benefit of making it lazy.

Here’s what that would look like:

```dart
class SomeClass {
  late String? value = doHeavyCalculation();
  String? doHeavyCalculation() {
    // do heavy calculation
  }
}
```

## Key Points

- Null means “no value.”
- A common cause of errors for programming languages in general comes from not properly handling `null`.
- Dart 2.12 introduced sound null safety to the language.
- Sound null safety distinguishes nullable and non-nullable types.
- A non-nullable type is guaranteed to never be `null`.
- Null-aware operators help developers to gracefully handle `null`.

```
??    if-null operator
??=   null-aware assignment operator
?.    null-aware access operator
?.    null-aware method invocation operator
!     null assertion operator
?..   null-aware cascade operator
?[]   null-aware index operator
...?  null-aware spread operator

```

- The `late` keyword allows you to delay initializing a field in a class.
- Using `late` also makes initialization lazy, so a variable’s value won’t be calculated until you access the variable for the first time.
- `late` and `!` opt out of sound null safety, so use them sparingly.
