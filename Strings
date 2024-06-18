### 

### 字符表示與處理

### Dart

- **特性**：使用 `String` 類型表示字符串，無 `Character` 或 `char` 類型。Dart 字符串是 UTF-16 代碼單元的集合，可通過 `.codeUnits` 訪問。Dart 提供 `runes` 屬性來獲取 Unicode 代碼點。
    
    ```dart
    dart複製程式碼
    var salutation = 'Hello!';
    print(salutation.codeUnits); // [72, 101, 108, 108, 111, 33]
    
    ```
    
    ```dart
    dart複製程式碼
    const dart = '🎯';
    print(dart.runes); // (127919)
    
    ```
    

### Swift

- **特性**：使用 `Character` 類型表示單個字符，`String` 類型表示字符串。
    
    ```swift
    swift複製程式碼
    let letter: Character = "a"
    let greeting: String = "Hello, Swift!"
    
    ```
    

### 2. 字符串插值

### Dart

- **特性**：支持字符串插值，用 `$` 或 `${}` 包含變量或表達式。
    
    ```dart
    dart複製程式碼
    const name = 'Ray';
    const introduction = 'Hello my name is $name'; // 'Hello my name is Ray'
    
    ```
    

### Swift

- **特性**：也支持字符串插值，用 `\()` 包含變量或表達式。
    
    ```swift
    swift複製程式碼
    let name = "Ray"
    let introduction = "Hello, my name is \(name)"
    
    ```
    

### 3. 原始字符串

### Dart

- **特性**：支持原始字符串，使用 `r` 前綴。
    
    ```dart
    dart複製程式碼
    const rawString = r'My name \n is $name.';
    
    ```
    

### Swift

- **特性**：無原始字符串支持，但可以通過使用多個反斜杠實現類似效果。

### 4. 多行字符串

### Dart

- **特性**：支持多行字符串，使用三個單引號或雙引號。
    
    ```dart
    dart複製程式碼
    const bigString = '''
    You can have a string
    that contains multiple
    lines
    by
    doing this.''';
    
    ```
    

### Swift

- **特性**：支持多行字符串，使用三個雙引號。
    
    ```swift
    swift複製程式碼
    let bigString = """
    You can have a string
    that contains multiple
    lines
    by
    doing this.
    """
    
    ```
    

### 5. 編碼字符

### Dart

- **特性**：可以插入 Unicode 代碼字符，使用 `\u` 或 `\u{}`。
    
    ```dart
    dart複製程式碼
    print('I \u2764 Dart\u0021'); // I ❤️ Dart!
    print('I love \u{1F3AF}'); // I love 🎯
    
    ```
    

### Swift

- **特性**：可以使用 Unicode 標量值表示字符，使用 `\u{}`。
    
    ```swift
    swift複製程式碼
    print("I \u{2764} Swift\u{21}") // I ❤️ Swift!
    
    ```