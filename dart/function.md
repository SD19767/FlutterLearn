以下是 Dart 和 Swift 在函數部分的不同之處，並附上中文補充說明：

### 基本函數定義

**Dart:**

```dart
String compliment(int number) {
  return '$number is a very nice number.';
}
```

**Swift:**

```swift
func compliment(number: Int) -> String {
  return "\(number) is a very nice number."
}
```

**不同點**：Dart 使用的是 `String` 和 `int` 來定義返回類型和參數類型，而 Swift 使用的是 `String` 和 `Int`，並且 Swift 的函數定義語法不同，使用 `func` 關鍵字，並且參數名稱和類型放在冒號前後。

### 主函數

**Dart:**

```dart
void main() {
  const input = 12;
  final output = compliment(input);
  print(output);
}
```

**Swift:**

Swift 沒有直接等同於 Dart 的 `main` 函數。通常在 Swift 中，我們會在應用程序的入口點（如 ViewController 或 AppDelegate 中）調用函數。

**不同點**：Dart 有一個明確的 `main` 函數作為程序入口，而 Swift 沒有這樣的要求，入口點由應用程序結構決定。

### 可選參數

**Dart:**

```dart
String fullName(String first, String last, [String? title]) {
  if (title != null) {
    return '$title $first $last';
  } else {
    return '$first $last';
  }
}
```

**Swift:**

```swift
func fullName(first: String, last: String, title: String? = nil) -> String {
  if let title = title {
    return "\(title) \(first) \(last)"
  } else {
    return "\(first) \(last)"
  }
}
```

**不同點**：Dart 使用方括號 `[]` 來表示可選參數，並且需要顯示地檢查 `null`。Swift 則使用默認參數值，並且可選類型以問號 `?` 表示，使用 `if let` 解包。

### 命名參數

**Dart:**

```dart
bool withinTolerance(int value, {int min = 0, int max = 10}) {
  return min <= value && value <= max;
}
```

**Swift:**

```swift
func withinTolerance(value: Int, min: Int = 0, max: Int = 10) -> Bool {
  return min <= value && value <= max
}
```

**不同點**：Dart 使用大括號 `{}` 來表示命名參數，並在函數調用時使用參數名稱。Swift 的命名參數是函數定義中的一部分，默認情況下所有參數都是命名參數。

### 箭頭函數

**Dart:**

```dart
int add(int a, int b) => a + b;
```

**Swift:**

Swift 中沒有直接的箭頭函數語法，但可以使用閉包來達到類似的效果：

```swift
let add: (Int, Int) -> Int = { $0 + $1 }
```

**不同點**：Dart 支持使用 `=>` 來簡化單行函數的定義，而 Swift 使用閉包語法來達到相同效果。

### 必需的命名參數

**Dart:**

```dart
bool withinTolerance({
  required int value,
  int min = 0,
  int max = 10,
}) {
  return min <= value && value <= max;
}
```

**Swift:**

在 Swift 中，所有參數默認都是必需的，除非給出默認值。因此，不需要 `required` 關鍵字：

```swift
func withinTolerance(value: Int, min: Int = 0, max: Int = 10) -> Bool {
  return min <= value && value <= max
}
```

**不同點**：Dart 使用 `required` 關鍵字來標識必需的命名參數，而 Swift 中默認所有參數都是必需的，除非提供了默認值，因此不需要額外的關鍵字。

這些是 Dart 和 Swift 在函數方面的主要不同之處。