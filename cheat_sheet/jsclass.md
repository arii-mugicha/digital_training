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
```

## prototypeベース記法
