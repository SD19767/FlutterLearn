# Expressions, Variables & Constants(註釋，變量，常量)
### 注釋

- **Dart**：支持單行注釋（`//`）、區塊注釋（`/* ... */`）、嵌套注釋和文檔注釋（`///` 和 `/** ... */`）。

```dart
// 單行註釋
/* 區塊註釋 */
/* 嵌套註釋 /* 內部註釋 */ 外部註釋 */
```

- **Swift**：支持單行注釋（`//`）和區塊注釋（`/* ... */`），但不支持嵌套注釋。

```swift
// 單行註釋
/* 區塊註釋 */
```

### 變數和常量

- **Dart**：使用 `final` 和 `const` 宣告不可變變量。`var` 關鍵字允許類型推斷，但變量類型一旦設置不可變更。

```dart
// 變量和常量
final int myFinal = 10;
const int myConst = 20;
var myVar = 30;
```

- **Swift**：使用 `let` 宣告常量，`var` 宣告變量。沒有 `final` 和 `const` 的區分。

```swift
let myConst: Int = 20
var myVar: Int = 30
```

### 類型安全和推斷

- **Dart**：強類型語言，可使用 `dynamic` 關鍵字允許變量類型變化，但建議避免使用。

```dart
dynamic anyType = 10;
anyType = 3.14; // OK
anyType = "Hello"; // OK
```

- **Swift**：強類型和類型推斷語言，無 `dynamic` 類型。

```swift
// 類型安全
var number: Int = 10
number = 20 // OK
// number = 3.14 // 錯誤
```