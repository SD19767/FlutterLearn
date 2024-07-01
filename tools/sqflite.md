# sqflite

[可以看 sqflite 的 pub.dev 的文件](https://pub.dev/packages/sqflitehttps:/)

### 安裝

```dart
dependencies:
  sqflite:
```

## Usage example

```dart
import 'package:sqflite/sqflite.dart';
```

這邊會用到文件夾的管理功能，記得也要 import
```dart
import 'package:path/path.dart' as path;
```

## overview

sql 的流程，會事先取得 path，會需要先取得path的原因是因為每一個裝置(平台)的路徑不一定會一樣。之後會在path 選擇一個 DB。因為一個path 可能會有多個DB。

## 取得 sql 的 path

SQLite資料庫是檔案系統中由路徑標識的檔案。 如果是相對的，此路徑是相對於getDatabasesPath（）獲得的路徑，這是Android上的預設資料庫目錄和iOS/MacOS上的文件目錄。

```dart
var databasesPath = await getDatabasesPath();
```

> 取得 path的方法是一個 Future，需要使用 async/await 處理
 
 取的 path 之後，我們利用 DB 的名稱組合路徑。
 ```dart
 String path = join(databasesPath, 'demo.db');
 ```

 > join 的 方法是 'package:path/path.dart'，無法使用可以檢查是否有引入。

## 刪除資料庫

```dart
await deleteDatabase(path);

```

## 開啟資料庫並創建表格
```dart
Database database = await openDatabase(path, version: 1,
    onCreate: (Database db, int version) async {
  await db.execute(
      'CREATE TABLE Test (id INTEGER PRIMARY KEY, name TEXT, value INTEGER, num REAL)');
});
```
openDatabase(path, version: 1, onCreate: ...)：開啟或創建資料庫。
onCreate 回調函數：在資料庫創建時執行的操作，這裡創建了一個名為 Test 的表格，包含 id, name, value, 和 num 四個欄位。


## 更新記錄

```dart
int count = await database.rawUpdate(
    'UPDATE Test SET name = ?, value = ? WHERE name = ?',
    ['updated name', '9876', 'some name']);
print('updated: $count');
```
database.rawUpdate(...)：更新 Test 表中 name 為 'some name' 的記錄，設置新的 name 和 value 值。

## 查詢記錄

```dart
List<Map> list = await database.rawQuery('SELECT * FROM Test');
List<Map> expectedList = [
  {'name': 'updated name', 'id': 1, 'value': 9876, 'num': 456.789},
  {'name': 'another name', 'id': 2, 'value': 12345678, 'num': 3.1416}
];
print(list);
print(expectedList);
assert(const DeepCollectionEquality().equals(list, expectedList));
```
database.rawQuery('SELECT * FROM Test')：查詢 Test 表中的所有記錄。
比較查詢結果與預期結果。


# SQL 語法

## 查詢表單
SELECT 與 FROM 敘述是從指定的資料表中選擇欄位的查詢語法，SELECT * 表示選擇資料表的「所有」欄位
```sql
SELECT *
  FROM table_name;
```
SELECT column_name 表示只選擇指定欄位
```sql
SELECT * column_name
  FROM table_name;
```
若想指定多個欄位，可用逗號 , 將多個欄位名稱隔開
```sql
SELECT * column_name1,
         column_name2
  FROM table_name;
```

## 插入或是覆蓋
```sql
INSERT INTO `資料表名稱` (`欄位1`,`欄位2`,`欄位3`)
VALUES('欄位1內容','欄位2內容','欄位3內容')
```
example
```sql
'''
INSERT OR REPLACE INTO $tableName (id, name, status)
VALUES(?,?,?)
''',
[task.id, task.name, task.status]);
  }
```

## 更新 Update

```sql
  Future<int> updateTask(Task task) async {
    if (database == null) {return 0;}
    return await database!.rawUpdate(
      '''
      UPDATE $tableName
      SET name = ?, status = ?
      WHERE id = ?
      ''',
      [task.name, task.status.index, task.id],
    );    
  }
```