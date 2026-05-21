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
  super(); // 親クラスコンストラクタ
  super.parentMethod();
  protected Datatype methosName(values){} // パッケージ内または継承クラスでのみ呼び出すことが可能
  @Override // override parent's method
  // same as others
}
```

# method
```java
// 可変長の引数
public/private return_type functionName(Datatype... values){}
```

# enum
```java
enum EnumName{
  arm1,...
}

// compare
enumInstance.compareTo(anotherEnumInstance); // -> -int, 0, int

// get defined order
EnumType.ArmName.ordinal();

// get all values
Enumtype.values();

// construct
EnumName.valueOf("ArmName");
```

# Random
```java
import java.util.Random;
Random r = new Random();
r.nextInt(i); // generate random Int between 0 to i;
```

# Collection

## List
```java
import java.util.List(); // Interface
import java.util.ArrayList(); // Class

// generate
List<RapperClass> list = new ArrayList<>();


list.add(value);
list.add(index, value);
import java.util.Arrays;
List<type> list = ArrayList<>(Arrays.asList(value1, ...)); // can add
List<type> list = Arrays.asList(value1, ...); // cannot add

list.get(index);
list.indexOf();
list.size();
list.set(index, value);
list.remove(index); // -> removed_value
list.remove(value); // -> boolean
// list.remove(new Integer(1)); remove int
list.clear();
list1.addAll(list2); // not change list2
```

## Map
```java
import java.util.Map;
import java.util.HashMap;

Map<KeyType, ValueType> map = new HashMap<>();
Map<KeyType, ValueType> map = new HashMap<>(){
  {
    put(key, val);
    put(key, val);
    ...
  }
};


map.put(key, value);
map.putIfAbsent(key, value);
map.get(key); // if key is absent return null
map.getOrDefault(key, default);
map.size();
map.containsKey(key);
map.containsValue(value);
map1.putAll(map2); // map2 is not changed
map.remove(key);
map.clear();

map.keySet(); // -> Set<KeyType>
map.values(); // -> Collection<ValueType>
map.entrySet(); // -> Map.Entry<key, value>
map_entry.getKey(); 
map_entry.getValue(); 
```

## Stream API
```java
list.stream(); // List<Datatype> to Stream<Datatype> (java.util.stream.Stream)

import java.util.stream.Collectors;
stream.collect(Collectors.toList()); // Stream<Datatype> to List<Datatype>

// method -> Stream
stream.filter(func(stream_datatype)->bool);
stream.distinct();
stream.map(func(stream_datatype) -> new_stream_datatype);
stream.reduce(init, (acc, val) -> return_value);
stream.reduce((acc, val) -> return_val); // ->Optional<Datatype>

// Optional
stream.findFirst(); // -> Optional<Stream_datat_type>
optional.isPresent(); // -> bool
optional.orElse(v); // if !optional.isPresent() return v else
optional.get(); // 中身がある前提で取り出す

optional.ifPresent(func(val)); // if isPresent execute func
// same as Stream, Optional can use filter, map, flatMap, orElseGet, orElseThrow
```

## Iterator
```java
// generate
list.iterator();
iterator.hasNext(); // -> bool;
iterator.next(); // -> iterator_datatype

hashmap.keySet().iterator();
hashmap.values().iterator();

iterator.remove(); // 現在見ている要素を削除
```


## tips 
```java
ユーザ名と最高スコアを出力
		System.out.println(
      userScoresList.entrySet().stream()
        .map(entry -> Map.entry(
          entry.getKey(), 
          entry.getValue().stream().max(Integer::compareTo).orElse(0)
        ))
        .max(Comparator.comparing(Map.Entry::getValue))
      	.get().getKey()
    );
```
