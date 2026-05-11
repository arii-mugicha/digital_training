# DOM with JavaSccript
functionを作成したら実行されているのかを確認すること

## 基本操作
```JavaScript
const documentRoot = document;
const body = document.body;
const idSearch = domElement.getElementById("idName");
const tagSearch = domElement.getElementByTagName("TagName"); // => arrayLikeObject
const classSearch = domElment.getElementsByClassName("ClassName");
const element = domElement.querySelector("tagName.ClassName"); // 深さ優先探索 ClassNameを持つ最初のtag
const element = domElement.querySelector("tagName.ClassName1#ClassName2"); // 複数のClassNameをすべて持つtag
const element = domElement.querySelector(".ClassName"); // 不特定のタグの要素指定
const element = domElement.querySelectorAll("tagName.ClassName"); // 深さ優先探索 => NodeList
domElement.querySelectorAll(\`input[type='checkbox']\`);
```

## 隣接ノード群
```JavaScript
const childNodes = domElement.childNodes; // => arrayLike
const parentNode = domelement.parentNode;
const nextItem = item.nextSibling; // 次の兄弟要素
node.NodeType = Node.ELEMENT_NODE/TEXT_NODE/COMMENT_NODE; // (1/3/8)
domElement.textContent; // プレーンテキストの抽出 すべての子孫ノードの要素を結合した形
domNode.textContent;
```

## 生成
```
document.createElement("tag");
document.createTextNode("text");
element.appendChild(childElement);
const removeNode = element.removechild(removeElement);
element.insertBefore(element, currentNode);
element.insertBefore(element, currentNode.nextSibling); // 直後
```

## 属性取得
``` JavaScript
element.getAtteibute();
element.setAttribute("elementName", elementValue);
element.hasAttribute("elementName");
element.removeAttribute("elementName");
```

クラスリスト
``` JavaScript
element.classList;
classes.add("className");
classes.remove("className1", "className2");
classes.contains("className");
classes.toggle("className"); // === add() & remove()
```
## Event
- element.addEventListener("EventName", callbackfunction, options)
 - options = {once: true}
 - btn.addEventListener("click/mouseover")
 - document.addEventListener("DOMContentLoaded", callbackFunction)
- element.removeEventListener("event", callbackfunction)
- function callback(ev) { ev.preventDefault; } // 最初の読み込み時のEvent発火を無視
- element1.value // input要素の値を取得
- element2.checked // 二値系の値を取得
- document.forms.formNameAttributeValue
- form.name.value
- form.type.value
- ev.target // イベントの発生源
- ev.currentTarget // 登録された要素
- ev.stopPropagation() // イベントの伝搬の中断
- addEventListener(options={capture:true/false}) // キャプチャフェーズ/バブリングフェーズでコールバック実施

### Tips
すべての子ノードを削除
- while (parent.firstChild){ parent.removeChild(parent.firstChid)}
