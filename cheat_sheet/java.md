# プログラムの作成
``` java
public class Main { // クラス名とファイル名は一致する
  public static void main(String[] args) {
  }
}
```

# 標準出力
```java
System.out.println(String);
```
# 標準入力
```java
import java.util.Scanner;

Scanner scanner = new Scanner(System.in);
String recieved = scanner.nextLine();
scanner.close():
```

# 記述
```java
// 宣言
datatype variable = value;

//文字列結合
str 1 + str2;
```

# データ型
|データ型||
|--|--|
|整数値|`byte`, `short`, `int`, `long`|
|実数地|`double`, `float`|
|真偽値|`boolean`|

# キャスト
```java
Integer.parseInt(value);
Double.parseDouble(value);
Boolean.parseBoolean(value);
(datatype)value
Integer.toString(int);
```

# 条件分岐
```java
// comparsion string
str1.equals(str2);
```

# メソッド定義
```java
datatype methodName(datatype argument){
  // process
  return data;
}
```
