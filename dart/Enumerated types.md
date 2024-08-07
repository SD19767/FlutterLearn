<p><a target="_blank" href="https://app.eraser.io/workspace/l4LnAwjnWJmnhDED126X" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

## Declaring simple enums
[﻿#](https://dart.dev/language/enums#declaring-simple-enums) 

To declare a simple enumerated type, use the `enum` keyword and list the values you want to be enumerated:

```
enum Color { red, green, blue }
```
## Declaring enhanced enums
[﻿#](https://dart.dev/language/enums#declaring-enhanced-enums) 

Dart also allows enum declarations to declare classes with fields, methods, and const constructors which are limited to a fixed number of known constant instances.

To declare an enhanced enum, follow a syntax similar to normal [﻿classes](https://dart.dev/language/classes), but with a few extra requirements:

- Instance variables must be `final` , including those added by [﻿mixins](https://dart.dev/language/mixins) .
- All [﻿generative constructors](https://dart.dev/language/constructors#constant-constructors)  must be constant.
- [﻿Factory constructors](https://dart.dev/language/constructors#factory-constructors)  can only return one of the fixed, known enum instances.
- No other class can be extended as [﻿Enum](https://api.dart.dev/stable/dart-core/Enum-class.html)  is automatically extended.
- There cannot be overrides for `index` , `hashCode` , the equality operator `==` .
- A member named `values`  cannot be declared in an enum, as it would conflict with the automatically generated static `values`  getter.
- All instances of the enum must be declared in the beginning of the declaration, and there must be at least one instance declared.
Instance methods in an enhanced enum can use `this` to reference the current enum value.

Here is an example that declares an enhanced enum with multiple instances, instance variables, getters, and an implemented interface:

```
enum Vehicle implements Comparable<Vehicle> {
  car(tires: 4, passengers: 5, carbonPerKilometer: 400),
  bus(tires: 6, passengers: 50, carbonPerKilometer: 800),
  bicycle(tires: 2, passengers: 1, carbonPerKilometer: 0);

  const Vehicle({
    required this.tires,
    required this.passengers,
    required this.carbonPerKilometer,
  });

  final int tires;
  final int passengers;
  final int carbonPerKilometer;

  int get carbonFootprint => (carbonPerKilometer / passengers).round();

  bool get isTwoWheeled => this == Vehicle.bicycle;

  @override
  int compareTo(Vehicle other) => carbonFootprint - other.carbonFootprint;
}
```
## Using enums
[﻿#](https://dart.dev/language/enums#using-enums) 

Access the enumerated values like any other [﻿static variable](https://dart.dev/language/classes#class-variables-and-methods):

```
final favoriteColor = Color.blue;
if (favoriteColor == Color.blue) {
  print('Your favorite color is blue!');
}
```
```
assert(Color.red.index == 0);
assert(Color.green.index == 1);
assert(Color.blue.index == 2);
```
```
var aColor = Color.blue;

switch (aColor) {
  case Color.red:
    print('Red as roses!');
  case Color.green:
    print('Green as grass!');
  default: // Without this, you see a WARNING.
    print(aColor); // 'Color.blue'
}
```
```
print(Color.blue.name); // 'blue'
```
```
print(Vehicle.car.carbonFootprint);
```
![Screenshot 2024-08-07 at 10.24.54 PM.png](/.eraser/l4LnAwjnWJmnhDED126X___VX62QT0iRNNAjvNzl3utFBVzgTD3___a2XiB57_FhT5Kf181b4-t.png "Screenshot 2024-08-07 at 10.24.54 PM.png")







<!--- Eraser file: https://app.eraser.io/workspace/l4LnAwjnWJmnhDED126X --->