以下是針對 Flutter 中使用 GetX 的教學文件：

# Flutter GetX 教學文件


```mermaid
graph TD
    A[Get] --> B[State Management\n(狀態管理)]
    A --> C[Route Management\n(路由管理)]
    A --> D[Dependency Injection\n(依賴注入)]
    A --> E[Other Features\n(其他功能)]
    
    B --> B1[GetBuilder\n(高效且易用，僅當需要更新時才重建)]
    B --> B2[GetX\n(反應式狀態管理，可以自動追踪變量的變化並更新 UI)]
    B --> B3[Obx\n(反應式狀態管理，可以自動追踪變量的變化並更新 UI)]
    
    C --> C1[Get.to()\n(導航到新頁面)]
    C --> C2[Get.off()\n(導航並關閉當前頁面)]
    C --> C3[Get.offAll()\n(導航並關閉所有先前的頁面)]
    C --> C4[Get.back()\n(返回上一頁)]
    
    D --> D1[Get.put()\n(將實例注入到依賴中)]
    D --> D2[Get.lazyPut()\n(當需要時才創建實例)]
    D --> D3[Get.find()\n(獲取已經注入的實例)]
    
    E --> E1[Get.snackbar()\n(快速顯示通知)]
    E --> E2[Get.dialog()\n(顯示對話框)]
    E --> E3[Get.bottomSheet()\n(顯示底部抽屜)]
    E --> E4[GetConnect\n(用於進行 HTTP 請求和 websocket 連接)]
```

這樣在支持 Mermaid 的 Markdown 編輯器或在線工具中生成的心智圖會包含雙語標籤和每個功能的說明。

`get` 是 Flutter 的一個輕量級且功能強大的狀態管理、路由和依賴注入套件。以下是 `get` 套件的主要特點和功能：

### 狀態管理 (State Management)
`get` 提供了一種簡單易用的狀態管理解決方案，無需上下文（context）即可更新 UI。主要使用 `GetBuilder`、`GetX` 和 `Obx` 等小部件來進行狀態管理：

- **GetBuilder**: 高效且易用，僅當需要更新時才重建。
- **GetX** 和 **Obx**: 反應式狀態管理，可以自動追踪變量的變化並更新 UI。

### 路由管理 (Route Management)
`get` 簡化了路由的使用，提供了一種無需上下文的導航方式。可以輕鬆地定義、管理和導航不同的頁面：

- **Get.to()**: 導航到新頁面。
- **Get.off()**: 導航並關閉當前頁面。
- **Get.offAll()**: 導航並關閉所有先前的頁面。
- **Get.back()**: 返回上一頁。

### 依賴注入 (Dependency Injection)
`get` 提供了一種簡單高效的依賴注入方式，使得在任何地方都可以輕鬆獲取和管理依賴：

- **Get.put()**: 將實例注入到依賴中。
- **Get.lazyPut()**: 當需要時才創建實例。
- **Get.find()**: 獲取已經注入的實例。

### 其他功能
除了以上的主要功能，`get` 還提供了以下一些實用功能：

- **GetBuilder** 和 **SimpleBuilder**: 簡單易用的狀態管理小部件。
- **Get.snackbar()**: 快速顯示通知。
- **Get.dialog()**: 顯示對話框。
- **Get.bottomSheet()**: 顯示底部抽屜。
- **GetConnect**: 用於進行 HTTP 請求和 websocket 連接。

### 使用範例
以下是一些基本的使用範例：

```dart
// 導航到新頁面
Get.to(NextPage());

// 定義和使用狀態管理
class Controller extends GetxController {
  var count = 0.obs;
  void increment() => count++;
}

class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final Controller c = Get.put(Controller());
    return Scaffold(
      appBar: AppBar(title: Text("Get Example")),
      body: Center(
        child: Obx(() => Text("Count: ${c.count}")),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: c.increment,
        child: Icon(Icons.add),
      ),
    );
  }
}
```

### 安裝
在 `pubspec.yaml` 文件中添加 `get` 依賴：

```yaml
dependencies:
  flutter:
    sdk: flutter
  get: ^4.3.8
```

然後運行 `flutter pub get` 來安裝依賴。
