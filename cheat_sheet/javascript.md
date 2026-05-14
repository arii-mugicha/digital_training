切り上げ  

切り捨て  
四捨五入  

## 初期化
```
instance = {}; // Object
instance = new Set(); // Set
```

## for-of 構文
```JavaScript
for (let/const element of Iter){}
```
## Objectの要素列挙
```JavaScript
Object.keys(object_instance);
Object.values(object_instance);
object.entries(object_instance); // list of [value, key]
```

## 型変換
```JavaScript
// num -> string  
num.toString();
String(num);

//string -> num  
parseInt(str);

// num -> boolean  
Boolean(num);
```

## 3項演算子
```JavaScript
condition ? true_value : false_value
```

## switch
```JavaScript
switch (condition) {  
  case conditionアーム1: 処理  
  break;  
}
```

## JSONと文字列の変換
```JavaScript
JSON.atringify(obj); // JSONオブジェクトを文字列として獲得
JSON.parse(string); // 文字列をJSONオブジェクトとして変換
```

## array
```JavaScript
// clone
Array.from(array);

// slice
array.slice(start, end);

// search
array.indexOf(value);
array.lastIndexOf(value);
array.includes(value);

// join
array.join(concatinater)

// delete
array.splice(index, number);
```

## 高階関数
```javascript
(items) => {process};
```
```javascript
array.some(func(item) -> boolean); // func:trueなるものが存在するかのbooleanを返戻
array.every(func(item) -> boolean); // func:trueなるものがすべてかbooleanを返戻
array.forEach((item, index) => {
    // process
  }
);
array.filtrer(func(item) -> boolean); // trueなる要素を抽出した配列を返戻
array.map(func(item) -> return_type); // 各要素を変換して配列にする
array.find(func(item) -> boolean); // trueなる最初の要素を抽出
array.findIndex(func(item) -> boolean);
array.sort((a,b) => a-b); // 昇順ソート
array.sort((a,b) => a.localeCompere(b)); // 文字列ソート
// ソートは高階関数なしでも動く
array.reduce(func((acc, item) -> return type, init); // fold
```

## Optional Chain
``` JavaScript
obj?.unknown_property; // unknown_propertyが存在しない時、undifinedを返戻する
falsty_value || default; // || 演算子によってfalsty_valueであるときにdefaultを返戻 
null/undefined ?? default; // return default
```

## 文字列操作
``` JavaScript
str[index];
str.slice(i,j);
str.trim();
str.replace(before_pattern, after_pattern);
str.replace_all(before_pattern, after_pattern);
str.toUpperCase(); // same as toLowerCase()
str.split(split_pattern);
```

## Date Object
```JavaScript
// create instance
const date = new Date();
const date = new Date(year, month, date, hour, minute, second); // month は 0 スタート
const date = new Date(parseFormatString); // can attach offset ('+09:00')
const date = new Dare(dateObject.getTime());

// parse
dateObject.toString();
dateObject.toDateString(); // 日付部分のみ文字列
dateObject.toISOString();

// get
dateObject.getFullYear()
dateObject.getDate() // etc.
dateObject.getTime(); // get Epoch Time (millisecond)

// set
dateObject.setDate(value);

// comparsion
dateObject1 < dateObejct2;
dateObject1.getTime() === dateObject2.getObject(); // eq must be epoch time
dateObject === dateObeject;

// diff (milliseconds)
milliseconds = dateObject1 - dateObject2;

```
