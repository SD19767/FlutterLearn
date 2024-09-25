在 Flutter 中，`TextField` 是用來接收用戶輸入的一個基本組件。以下是一個簡單的教學，介紹如何在 Flutter 中使用 `TextField`。

### 1. 基本用法
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('TextField 範例'),
        ),
        body: Center(
          child: Padding(
            padding: const EdgeInsets.all(16.0),
            child: TextField(
              decoration: InputDecoration(
                border: OutlineInputBorder(),
                labelText: '請輸入文字',
              ),
            ),
          ),
        ),
      ),
    );
  }
}
```
### 2. 添加控制器來取得輸入內容
可以使用 `TextEditingController` 來管理 `TextField` 的輸入內容。

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: TextFieldExample(),
    );
  }
}

class TextFieldExample extends StatefulWidget {
  @override
  _TextFieldExampleState createState() => _TextFieldExampleState();
}

class _TextFieldExampleState extends State<TextFieldExample> {
  final TextEditingController _controller = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('TextField 範例'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: [
            TextField(
              controller: _controller,
              decoration: InputDecoration(
                border: OutlineInputBorder(),
                labelText: '請輸入文字',
              ),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: () {
                print('輸入的文字: ${_controller.text}');
              },
              child: Text('顯示輸入內容'),
            ),
          ],
        ),
      ),
    );
  }
}
```

### 3. 使用 `onChanged` 和 `onSubmitted` 回調
可以使用 `onChanged` 來監聽輸入過程中的變化，`onSubmitted` 則是在輸入完成（通常是按下鍵盤上的確定或回車鍵）時觸發。

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: TextFieldCallbacksExample(),
    );
  }
}

class TextFieldCallbacksExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('TextField 回調範例'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: TextField(
          decoration: InputDecoration(
            border: OutlineInputBorder(),
            labelText: '請輸入文字',
          ),
          onChanged: (text) {
            print('文字改變: $text');
          },
          onSubmitted: (text) {
            print('輸入完成: $text');
          },
        ),
      ),
    );
  }
}
```

### 4. 自定義 `TextField` 樣式
你可以透過 `InputDecoration` 來自定義 `TextField` 的外觀。

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: CustomTextFieldExample(),
    );
  }
}

class CustomTextFieldExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('自定義 TextField'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: TextField(
          decoration: InputDecoration(
            labelText: '請輸入文字',
            labelStyle: TextStyle(color: Colors.blue),
            border: OutlineInputBorder(
              borderRadius: BorderRadius.circular(15.0),
            ),
            enabledBorder: OutlineInputBorder(
              borderRadius: BorderRadius.circular(15.0),
              borderSide: BorderSide(color: Colors.green, width: 2.0),
            ),
            focusedBorder: OutlineInputBorder(
              borderRadius: BorderRadius.circular(15.0),
              borderSide: BorderSide(color: Colors.red, width: 2.0),
            ),
            prefixIcon: Icon(Icons.person),
            suffixIcon: Icon(Icons.check),
          ),
        ),
      ),
    );
  }
}
```

### 5. 常見屬性與用法說明
- `controller`: 管理 `TextField` 的輸入內容。
- `decoration`: 用於設置 `TextField` 的外觀樣式，比如提示文本、邊框樣式等。
- `keyboardType`: 指定輸入鍵盤的類型，如 `TextInputType.number` 表示數字鍵盤。
- `obscureText`: 如果設為 `true`，會隱藏輸入的文字（通常用於密碼輸入）。
- `maxLength`: 限制輸入的最大字數。
- `onChanged`: 當文字變化時調用的回調函數。
- `onSubmitted`: 當用戶完成輸入並提交時調用的回調函數。
