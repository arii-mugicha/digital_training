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

// nextInt/ nextDouble/ next
scanner.nextInt(); // 次の半角スペースまたはか改行までを区切りとしてintで受ける
```

# 記述
```java
// 宣言
datatype variable = value;

// array
datatype[] variable = new datatype[length];
datatype[] variable = new datatype[] {arg1, arg2, ...};
int length = array.length;

//文字列結合
str 1 + str2;

// 文字列分割
string.split("sepalater");
string.split(""); // 一文字ずつ
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
int i = Integer.valueOf(value); // Integer型を返戻しUnboxingする 型の変換を自動的に行う
Double.parseDouble(value);
Boolean.parseBoolean(value);
(datatype)value
Integer.toString(int);
String s = String.valueOf(value);
Character.geteNumericValue();
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

# for
```java
for (int i=init; condition; increment){}
for (datatype arg : array){
  // process
}
```

# math
```java
import java.lang.Math;
Math.ciel(num)
```

# Class
```java
// enum
public enum EnumName{
  arm1, arm2, ...;
  // can define methods
}

// class
public class ClassName{
  // field
  private/public datatype fieldname;
  // constructor
  private/public ClassName(classtypes values){
    // process
  }
  // parse
  private/public ClassName anotherConstructorName(values){}

  // statics
  static Datatype variable = value; // インスタンスを作成せずにアクセス可能なクラスフィールド

  // final
  final type valiable = ...; // 不変変数
}

// instance
ClassName instance = new ClassName(values);
ClassName instance = new ClassName.anotherConstructorName(values);

// inheritance
public class NewClassName extends Inherit{
  // same as others
}
```

# method
```java
// 可変長の引数
public/private return_type functionName(Datatype... values){}
```
