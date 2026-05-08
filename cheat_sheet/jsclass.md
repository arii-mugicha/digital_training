## Classベース記法
```JavaScript
class ClassName{
  field;
  fieldInit = InitialValue;
  constructor(value1, value2, ...){
    this.field = initial_value;
  }
  methodName(values){
    // method progress
  }

  #privateField;
  #privateMethod(values){
    // method progress
  }

  // gettter/setter
  get getterName(){
    return fieldValue;
  }
  set setterMethod(value){
    this.fieldName = value;
  }

  // static field
  static staticField = initial_value;
  static staticMethod(values) {
    // method progress
  }
}

// create instance
const newinstance = new ClassName()
// access field
instance.field;

// call getter/setter
instance.getterName // NOT METHOD
instance.setter = setValue;

// access stataic field
ClassName.staticField;
instanceName.constructor.staticField; // instanceName.constructor === ClassName

```

## module定義
```JavaScript
// Objectとしてグローバル変数にまとめる
var myModule = {
  functionName(){
    // method progress
  }
}
// call module
myModule.moduleFunction()

// call from another file
window.moduleName();

// export to another file
export { ObjectName };
export const constantValue = value;
export class ExportClass{};
// importfrom another file
import { moduleName } from 'moduleFilePath';

// CommonJS export
module.exports = objectName;
// CommonJS import
Const {ObjectName} = require('modulePath')
```

## クラス継承 Class Inheritance
```JavaScript
class InheritedClassName extends InheritClassName{
  constructor(values){
    super(values);
  }

  newField;
  newMethod(){}

  overrideFunction(values){
    super.overridefunstion();
    // other procudures
  }
}
```

## prototypeベース記法
```JavaScript
function ClassName(values){
  this.fieldName = value;
  this.methodName = functin(values) {
    // method progress
  }
}

// create & access instance
const instanceName = new ClassName(values);
instanceName.fieldName;

// define by prototype
ClassName.prototype.methodName = functino(){
  // method progress
}

// override instance
instance.overrideMethod = function(values){}; // インスタンスのみoverride


// inheritance
InheritedClass.prototype = Object.create(InheritClass.prototype)
// constructor inheritance
function InheritedClassName(values){
  InheritClassName.call(this, values);
}
// override class
InheritedClassName.prototype.inheritMethodName = function(values){};
// getter/setter
Object.defineProperty(ClassName.prototype, propertyName{
  get(){
    return return_value;
  },
  set(value){
    // setter
  }
});
```

## 参照
``` JavaScript
-- Premitive Type は値渡し
-- Object は参照渡し
```
