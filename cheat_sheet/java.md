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
```

## 文字列
```java
//文字列結合
str 1 + str2;

// 文字列分割
string.split("sepalater");
string.split(""); // 一文字ずつ

// index access
string.charAt(index);

string.equals(anotherString);
int comp = str1.compareTo(); // str1 < str2 -> minus (辞書順)
int comp = st1.compareToIgnoreCase();
string.startsWight(prefix [, offset]);
string.endsWith(suffix);
string.contains(substr);
string.indexOf(substr [, offset]);
string.lastIndexOf(substr);
string.replace(beforePattern, afterPattern);
string.substring(startIndex, endIndex);

string.trim();
string.strip();
string.stripLeading();
string.stripTeailing();

String.join("concatinator", String[]);

String(char[]); // join without space
String(int[] codePoint, int offset, int count); // offset:部分文字列開始位置 count:文字列長
string.chars().toArray(); // -> int[]
string.chars().forEach();
(char)i // -> char

// char
char.isDigit(c); // if c is number(digit) return true
char1 == char2;

//String builder
StringBuilder builder = new StringBuilder("");
builder.append("appendix");
builder.insert(index, appendix);
builder.deleteCharAt(index);
builder.delete(startIndex, endIndex);
builder.setCharAt(index, char);
builder.replace(startIndex, endIndex, string);
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
String.fomat("%.nf", doubleNumber);
String.fomat("%num$s %num$s", repeatedString);
String.fomat("%aNx", val); // a形式でN桁のxを表示
// a '0':0埋め, ' ':右揃え, '-':左揃え,   N:N桁右揃え, .N:最大N桁
String.fomat("%,d", num); // ,区切り整数

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
List<RapperClass> list = new ArrayList<>(capacity);


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

## lambda式
```java
Runnable runnerName = (arguments) -> {
	// process
};
runnerName.run()

// method reference
ClassName::methodName // static method
instanceName::methodName // instance method

map.forEach((key, value) -> {});
```

```java
// Comarable Interface
interface Compareable{
	int CompareTo(T o){} // 引数が自分より大きいときに正,小さいときに負、同じで0
}

list.sort(null); // ListArgumentDatatype::compareTo
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
//ユーザ名と最高スコアを出力
System.out.println(
	userScoresList.entrySet().stream()
	.map(entry -> Map.entry(
	entry.getKey(), 
  	entry.getValue().stream().max(Integer::compareTo).orElse(0)
	))
	.max(Comparator.comparing(Map.Entry::getValue))
	.get().getKey()
);

map.values().stream()
	.map(v -> v.stream()
		.mapToInt(x -> x)
		.max().getAsInt())
	.max(Comparator.naturalOrder())
	.orElse(-1);

maxMap.entrySet()
	.stream()
	.filter(entry -> entry.getValue() == max)
	.map(Map.Entry::getKey)
	.min(Comparator.naturalOrder())
	.get();
```

## LinkedList
```java
LinkedList<type> list = new LinkedList<>;
list.addFirst();
list.addLast();
list.getFirst();
list.getLast();
list.removeFirst();
list.removeLast();
```

## Maps
``` java
HashMap // random order
TreeMap // dictional order
LinkedHashMap // additional order

// required by HashMap
int hashCode(){};
boolean equals(Object o){};

// required by TreeMap
int compareTo(Object o){} // implements Comparable
// OR
int compare(Object o1, Object 02){}; // implements Comparator<Type>
new TreeMap<>(new ImplementedComparatorClass)

```

## Collections
```java
Collections.addAll(list, element1, element2, ...);

Collections.unmodifiableList(list); // immutable list
Collections.synchronizedList(list);
Collections.unmodifiableMap(map); // immutable map
Collections.synchronizedMap(map);
```


# 例外処理
## Excecption
```java
try {
	// do something
} catch (ExceptionName e){
	e.printStackTrace();
} catch (ExcptionName1 e1 | ExcptionName2 e2){...
} finally {
	// do NOT return
}

// try-with-resource
try (datatype valiable = initialCoding){} // 対象リソースを解放

// Exception
Exception // somtime anti-pattren
IOException
NoSuchFileException
UnsupportedEncodingException
ArithmetixException
NullPointerException
ArrayIndexOutOfBoundsException
IllegalArgumentException

methodNames() throws ExceptionName{};
throw new ExceptionName();
```
## Error
```java
OutOfMemoryError
StackOverflowError

// assertion;
assert boolean; // if false throw AssertionError
```

## FileIO
```java
import java.nio.file.Files;
import java.io.File;
import java.io.IOException;
// FileReading
Files.readAllBytes(file.toPath(), encoding);
```

## JDBC
```java
import java.sql.*;

// load Driver
Class.forName(drivername); // "org.sqlite.JDBC", "com.mysql.jdbc.Driver", "org.postgresql.Driver"
// define url
String url = "jdbc:protocol:information"; // "jdbc:sqlite:db_path"
// connect DB
Connection connection= DriverManager.getConnection(url);
try{
// execute SQL
	PreparedStatement pstmt = connection.prepareStatement("SQL Instruction");
	ResultSet rs = pstmt.executeQuery();
	// show
	while (rs.next()) {
		Syste.out.prinltn(rs.getString(index)...)
	}
	// rs.close()
	// pstmt.close()
} finally {
	connection.close();
}

// try-with-resourceは複数の宣言も可能
try (
	statement1;
	statement2;
)

```

### Execute Query
```java
preparedStatement.executeQuery();
preparedStatement.executeUpdate(); // update like query


rs.getString(index); // index starts with 1;
rs.getString(columnName);
rs.getInt(indexOrColumnName); // return default 0
rs.getShort();
rs.getLong();
re.getBoolean();

// execution text generate
String sql = "select * from users where age > ?";
PrepareSatatement pstmt = connection.prepareStatement(sql);
pstmt.setInt(1, age); // set first ? to age;
pstmt.setStrin(index, string);
pstmt.setNull(index, Types.NULL);
```

### DatabaseMetaData
```
DatabaseMetadata dmd = connection.getMetaData();
String dmname = dmd.getDatabaseProduceName();
String version = dmd.getDatabaseProductVersion();
ResultSet rs = dmd.getTypeInfo(); 
rs.getString("TYPE_NAME"); // supported type info
ResultSet rs = dmd.getTables(
  String catalog, // null
  String schemaPattern, // null
  String tableNamePattern, // "%"
  String[] types // null
);
ResultSet rs = dmd.getColumns(
  String catalog,
  String schemaPattern,
  String tableNamePattern,
  String[] types
);
```
