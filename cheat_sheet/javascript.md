切り上げ  

切り捨て  
四捨五入  

## for-of 構文
for (let/const element of Iter){}

## Objectの要素列挙
keys
- Object.keys(object_instance)

values
- Object.values(object_instance)

entries (list of [value, key])
- object.entries(object_instance)

## 型変換
num -> string  
- num.toString()
- String(num)

string -> num  
- parseInt(str)

num -> boolean  
- Boolean(num)

## 3項演算子
condition ? true_value : false_value

## switch
switch (condition) {  
  case conditionアーム1: 処理  
  break;  
}

## JSONと文字列の変換
JSONオブジェクトを文字列として獲得：JSON.atringify(obj)
文字列をJSONオブジェクトとして変換：JSON.parse(string)

## array
clone
- Array.from(array)

slice
- array.slice(start, end)

search
- array.indexOf(value)
- array.lastIndexOf(value)
- array.includes(value)

join
- array.join(concatinater)  


## higher-order function
- array.some(func(item) -> boolean) -> boolean
- array.every(func(item) -> boolean) -> boolean
- array.forEach((item, index) => {処理})
- array.filtrer(func(item) -> boolean)
  - 真のもののみを抽出した配列になる
- array.map(func(item) -> return_type)
- array.find(func(item) -> boolean)
  - extract first element
- array.findIndex(func(item) -> boolean)
- array.sort((a,b) => a-b)
  - 昇順ソート
- array.sort((a,b) => a.localeCompere(b));
- array.reduce(func((acc, item) -> return type, init)


## Optional Chain
- obj?.unknown_property
  - if not-exsist => undifined
- falsty_value || default => default
- null/undefined ?? default => default

## string
- str[index]
- str.slice(i,j)
- str.trim()
- str.replace(before_pattern, after_pattern)
- str.replace_all(before_pattern, after_pattern)
- str.toUpperCase()
- str.split(split_pattern)

## class
- class className{
    property;  
    #privateProperty = value; // init  
    static sproperty = value;  
    get getterName(){}  
    set setterName(value){}  
    constructor(setValues) {this.value=setValue;}  
  }
- const instance = new className();
- instance.constructor.stataicProperty;

## Date Object
```JavaScript
// create instance
const date = new Date();
const date = new Date(year, month, date, hour, minute, second); // month は 0 スタート
const date = new Date(parseFormatString); // can attach offset ('+09:00')
// parse
dateObject.toString();
dateObject.toDateString(); // 日付部分のみ文字列
dateObject.toISOString();
// get 
```
