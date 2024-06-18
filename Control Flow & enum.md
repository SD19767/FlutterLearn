以下是將 Dart 教學文件中的知識刪減為 Swift 相同的知識，並顯示與 Swift 知識相異的部分的對照：

### Audio Enumerations (Swift)

1. **定義 `AudioState` 枚舉並給出代表 `playing`、`paused` 和 `stopped` 狀態的值**：

   ```swift
   enum AudioState {
       case playing
       case paused
       case stopped
   }
   ```

2. **創建一個名為 `audioState` 的常量並給它一個 `AudioState` 值**：

   ```swift
   let audioState: AudioState = .playing
   ```

3. **寫一個 `switch` 語句，根據值打印消息**：

   ```swift
   switch audioState {
   case .playing:
       print("The audio is playing.")
   case .paused:
       print("The audio is paused.")
   case .stopped:
       print("The audio is stopped.")
   }
   ```

## 主要點

### Swift 與 Dart 相同的知識

- 布林數據類型 `Bool` 可以表示 `true` 或 `false`。
- 比較運算符，所有這些運算符都返回布林值：

  - 相等 `==`
  - 不相等 `!=`
  - 小於 `<`
  - 大於 `>`
  - 小於或等於 `<=`
  - 大於或等於 `>=`

- 使用布林邏輯 (`&&` 和 `||`) 組合比較條件。
- `if` 語句用於根據條件進行簡單決策。
- 在 `if` 語句後使用 `else` 和 `else if` 擴展決策。
- 變量和常量屬於某個範圍，超出該範圍就無法使用它們。一個範圍繼承其父範圍的變量和常量。
- 三元運算符 (`a ? b : c`) 可以替換簡單的 `if-else` 語句。
- `switch` 語句可以替換長的 `else-if` 鏈。
- 枚舉定義了一種新類型，具有有限列表的不同值。

### Swift 與 Dart 相異的知識

- **Swift 的枚舉語法**：

  Dart 中的枚舉定義和使用與 Swift 略有不同。以下是 Swift 中的枚舉定義和使用方式：

  ```swift
  // Swift 中的枚舉定義
  enum AudioState {
      case playing
      case paused
      case stopped
  }

  // 使用 Swift 枚舉
  let audioState: AudioState = .playing

  switch audioState {
  case .playing:
      print("The audio is playing.")
  case .paused:
      print("The audio is paused.")
  case .stopped:
      print("The audio is stopped.")
  }
  ```

  Dart 中的枚舉定義和使用方式如下：

  ```dart
  // Dart 中的枚舉定義
  enum AudioState {
      playing,
      paused,
      stopped
  }

  // 使用 Dart 枚舉
  AudioState audioState = AudioState.playing;

  switch (audioState) {
    case AudioState.playing:
      print("The audio is playing.");
      break;
    case AudioState.paused:
      print("The audio is paused.");
      break;
    case AudioState.stopped:
      print("The audio is stopped.");
      break;
  }
  ```

這些對比顯示了 Swift 和 Dart 在基本結構和功能上的相似性，同時也指出了它們在語法上的差異。