# Class

class 是一個物件的藍圖，透過實例化做成一個物件。

## Constructors

如果不定義，會有預設的 Default constructors.

### constructors

可以使用 this 的語法糖

```dart
class Point {
  // Initializer list of variables and values
  double x = 2.0;
  double y = 2.0;

  // Generative constructor with initializing formal parameters:
  Point(this.x, this.y);
}
```

### Named constructors

自訂名稱的初始化器

```dart
const double xOrigin = 0;
const double yOrigin = 0;

class Point {
  final double x;
  final double y;

  // Sets the x and y instance variables
  // before the constructor body runs.
  Point(this.x, this.y);

  // Named constructor
  Point.origin()
      : x = xOrigin,
        y = yOrigin;
}
```

### Constant constructors

如果值是常量的話，可以定義常數初始化器

```dart
class ImmutablePoint {
  static const ImmutablePoint origin = ImmutablePoint(0, 0);

  final double x, y;

  const ImmutablePoint(this.x, this.y);
}
```


### Redirecting constructors

建構函式可能會重定向到同一類中的另一個建構函式。 重定向建構函式有一個空主體。 建構函式使用這個，而不是冒號（:）後面的類名。

```dart
class Point {
  double x, y;

  // The main constructor for this class.
  Point(this.x, this.y);

  // Delegates to the main constructor.
  Point.alongXAxis(double x) : this(x, 0);
}
```


### Factory constructors


當遇到以下兩種情況之一時，可以使用 `factory`  關鍵字來實現構造函數：

1. **構造函數不一定每次都創建新實例** ：

* **從緩存中返回現有實例** ：工廠構造函數可以根據某些條件返回已經存在的實例，而不是每次都創建新實例。例如，當我們希望實現單例模式（singleton pattern）時，可以使用工廠構造函數。
* **返回子類的新實例** ：工廠構造函數還可以返回一個子類的新實例，而不一定是當前類的實例。

1. **在構造實例之前需要執行複雜的操作** ：

* **參數檢查或處理** ：在構造實例之前需要對參數進行檢查或進行其他處理，這些操作不能在初始化列表中完成時，可以使用工廠構造函數。

```dart
class Logger {
  final String name;
  bool mute = false;

  // _cache is library-private, thanks to
  // the _ in front of its name.
  static final Map<String, Logger> _cache = <String, Logger>{};

  factory Logger(String name) {
    return _cache.putIfAbsent(name, () => Logger._internal(name));
  }

  factory Logger.fromJson(Map<String, Object> json) {
    return Logger(json['name'].toString());
  }

  Logger._internal(this.name);

  void log(String msg) {
    if (!mute) print(msg);
  }
}
```
