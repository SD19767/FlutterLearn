### Types & OperationsWritten

## Dart 中的數據類型

在 Dart 中，**類型** 是一種告訴編譯器你打算如何使用某些數據的方法。到目前為止，你已經看到了以下類型：

- `int`
- `double`
- `num`
- `dynamic`
- `String`

Dart 只有雙精度 double，沒有浮點數 float.

像 `int`、`double` 和 `num` 這樣的類型是 `Object` 類型的子類，或者說是**子類型**。`Object` 定義了一些核心操作，例如測試相等性和描述自身。Dart 中的每個非空類型都是 `Object` 的子類型，作為子類型，它們共享 `Object` 的基本功能。

### 創建常量變數

以上述方式聲明變數會使它們變為可變的。如果你想讓它們變為不可變的，但仍保持類型註釋，可以在前面加上 `const` 或 `final`。

這些聲明形式適用於 `const`：

```dart
dart複製程式碼
const int myInteger = 10;
const double myDouble = 3.14;

```

它們也適用於 `final`：

```dart
dart複製程式碼
final int myInteger = 10;
final double myDouble = 3.14;

```

> 注意：可變數據便於操作，因為你可以隨時更改它。但是，許多有經驗的軟件工程師已經開始欣賞不可變數據的好處。當一個值是不可變的，這意味著你可以相信沒有人會在創建後更改該值。以這種方式限制數據可以防止許多難以發現的錯誤，並使程序更容易推理和測試。
> 
> 
>  
> 
> ### 具體區別
> 
> 1. **賦值時間**：
>     - `const`：在編譯時賦值，並且值必須是編譯時常量。
>     - `final`：在運行時賦值，並且只能賦值一次。
> 2. **應用場景**：
>     - `const`：適用於那些在編譯時就已知且固定不變的值。
>     - `final`：適用於那些在運行時確定，但一旦賦值後不會再改變的值。
> 3. **內存效率**：
>     - `const` 變量是編譯時常量，可以在內存中多次使用相同的實例，有助於提高內存效率。
>     - `final` 變量在每次運行時都會創建新的實例。
> 
> 總結來說，當你需要一個編譯時常量，並且值在編譯時就能確定時，應該使用 `const`。當你需要一個運行時確定的常量，並且一旦賦值後不能改變時，應該使用 `final`。
> 

### 類型安全和推斷

- **Dart**：強類型語言，可使用 `dynamic` 允許變量類型變化，但建議避免使用。
    
    ```dart
    dart複製程式碼
    dynamic myVariable = 42;
    myVariable = 'hello'; // OK
    
    ```
    
- **Swift**：無 `dynamic` 類型。

### 類型檢查

- **Dart**：使用 `is` 關鍵字和 `runtimeType` 屬性檢查類型。
    
    ```dart
    dart複製程式碼
    print(myNumber is double); // true
    print(myNumber.runtimeType); // double
    
    ```
    
- **Swift**：使用 `is` 關鍵字檢查類型，`type(of:)` 檢查類型。
    
    ```swift
    swift複製程式碼
    print(value is Double) // true
    print(type(of: value)) // Double
    
    ```
    
    ### 類型轉換
    
    - **Dart**：需顯式類型轉換，避免隱式轉換導致的錯誤。
        
        ```dart
        dart複製程式碼
        var integer = 100;
        var decimal = 12.5;
        integer = decimal.toInt(); // 12
        
        ```
        
    - **Swift**：類似，需要顯式類型轉換。
        
        ```swift
        swift複製程式碼
        var integer = 100
        var decimal = 12.5
        integer = Int(decimal) // 12
        
        ```
        
        ### 物件和動態類型
        
        - **Dart**：可以使用 `Object?` 類型允許任何類型，包括 `null`。
            
            ```dart
            dart複製程式碼
            Object? myVariable = 42;
            myVariable = 'hello'; // OK
            
            ```
            
        - **Swift**：使用 `Any` 類型允許任何類型，不包含 `null`。
            
            ```swift
            swift複製程式碼
            var myVariable: Any = 42
            myVariable = "hello" // OK
            
            ```