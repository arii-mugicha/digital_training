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
}
// create instance
const newinstance = new ClassName()
// access field
instance.field;

// call getter/setter
instance.getterName // NOT METHOD
instance.setter = setValue;
```
## prototypeベース記法
