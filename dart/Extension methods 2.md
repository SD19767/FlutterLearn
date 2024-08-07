<p><a target="_blank" href="https://app.eraser.io/workspace/zewzQ0Ar2zO1ES5CPi3E" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

延伸方法（Extension Methods）在 Dart 中是一種強大的工具，可以用來為現有的類別添加新的功能，而不需要修改原始的類別定義。這些新功能包括方法、getter、setter、運算子、靜態欄位和靜態輔助方法。以下是對這些功能的更詳細說明：

### 方法
延伸方法允許你為現有類別添加新的實例方法。這些方法可以像類別中的其他方法一樣被調用。

```dart
extension StringParsing on String {
  int parseInt() {
    return int.parse(this);
  }

  double parseDouble() {
    return double.parse(this);
  }
}
```
### Getter 和 Setter
延伸方法可以添加新的 getter 和 setter，使你可以為現有類別添加新的屬性訪問器。

```dart
extension StringExtension on String {
  bool get isNumeric => double.tryParse(this) != null;

  set firstChar(String char) {
    if (char.length == 1) {
      this[0] = char;
    }
  }
}
```
### 運算子
延伸方法還可以添加新的運算子，以擴展現有類別的運算行為。

```dart
extension PointExtension on Point {
  Point operator +(Point other) {
    return Point(this.x + other.x, this.y + other.y);
  }
}
```
### 靜態欄位和靜態輔助方法
延伸方法還可以包含靜態欄位和靜態輔助方法。這些靜態成員只能通過延伸方法的名稱來訪問，類似於類別的靜態成員。

```dart
extension MathUtils on num {
  static const double pi = 3.141592653589793;

  static double degreesToRadians(double degrees) {
    return degrees * (pi / 180.0);
  }
}
```
在延伸方法的宣告之外存取靜態成員，可以像類變數和方法一樣，通過宣告名稱來調用它們。例如：

```dart
void main() {
  print(MathUtils.pi); // 輸出: 3.141592653589793
  print(MathUtils.degreesToRadians(180)); // 輸出: 3.141592653589793
}
```
### 使用範例
這是一個包含各種成員的延伸方法的綜合範例：

```dart
extension AdvancedString on String {
  // 實例方法
  bool get isPalindrome {
    var reversed = this.split('').reversed.join('');
    return this == reversed;
  }

  // Getter
  String get firstChar => this.isNotEmpty ? this[0] : '';

  // Setter
  set firstChar(String char) {
    if (this.isNotEmpty && char.length == 1) {
      this.replaceRange(0, 1, char);
    }
  }

  // 運算子
  String operator *(int times) {
    return List.filled(times, this).join('');
  }

  // 靜態成員
  static const String vowels = 'aeiou';

  static bool isVowel(String char) {
    return vowels.contains(char.toLowerCase());
  }
}

void main() {
  var str = 'level';
  print(str.isPalindrome); // 輸出: true
  print(str.firstChar); // 輸出: l
  str.firstChar = 'L';
  print(str); // 輸出: Level
  print(str * 3); // 輸出: LevelLevelLevel
  print(AdvancedString.vowels); // 輸出: aeiou
  print(AdvancedString.isVowel('e')); // 輸出: true
}
```
這些功能展示了延伸方法的強大，使得你可以在不改變原始類別的情況下，靈活地添加和使用新的方法和屬性。

## Implementing extension methods 實作延伸方法 
Use the following syntax to create an extension:

```
extension <extension name>? on <type> { // <extension-name> 是可選的
  (<member definition>)* // 可以提供一個或多個 <member definition>。
}
```
例如，這是如何在 `String` 類上實作一個延伸方法：

```
extension NumberParsing on String {
  int parseInt() {
    return int.parse(this);
  }

  double parseDouble() {
    return double.parse(this);
  }
}
```
**Extension methods **的成員可以是方法、getter、setter 或運算子。延伸方法也可以有靜態欄位和靜態輔助方法。要在延伸方法宣告之外存取靜態成員，可以像類變數和方法一樣通過宣告名稱來調用它們。

### Unnamed extensions  未命名的延伸方法
宣告**Extension methods **時，可以省略名稱。未命名的延伸方法僅在它們宣告的庫中可見。由於它們沒有名稱，無法顯式地應用以解決 API 衝突。

dart

```
extension on String {
  bool get isBlank => trim().isEmpty;
}
```
你只能在**Extension methods **宣告內部調用未命名延伸方法的靜態成員。

## Implementing generic extensions 實作泛型延伸方法
**Extension methods **可以具有泛型類型參數。例如，這是一段擴展內建 `List<T>` 類型的程式碼，其中包含一個 getter、一個運算子和一個方法：

dart

```
extension MyFancyList<T> on List<T> {
  int get doubleLength => length * 2;
  List<T> operator -() => reversed.toList();
  List<List<T>> split(int at) => [sublist(0, at), sublist(at)];
}
```
類型 `T` 是根據呼叫方法的清單的靜態類型來綁定的。



<!--- Eraser file: https://app.eraser.io/workspace/zewzQ0Ar2zO1ES5CPi3E --->