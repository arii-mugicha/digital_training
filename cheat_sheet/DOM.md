# DOM with JavaSccript
- const documentRoot = document;
- const body = document.body;
- const idSearch = domElement.getElementById("idName");
- const tagSearch = domElement.getElementByTagName("TagName"); // => arrayLikeObject
- cosnt classSearch = domElment.getElementsByClassName("ClassName");
- const element = domElement.querySelector("tagName.ClassName"); // 深さ優先探索 ClassNameを持つ最初のtag
- const element = domElement.querySelector("tagName.ClassName1#ClassName2"); // 複数のClassNameをすべて持つtag
- const element = domElement.querySelector(".ClassName"); // 不特定のタグの要素指定
- const element = domElement.querySelectorAll("tagName.ClassName"); // 深さ優先探索


- const childNodes = domElement.childNodes // => arrayLike
- const parentNode = domelement.parentNode
- const nextItem = item.nextSibling // 次の兄弟要素
- node.NodeType = Node.ELEMENT_NODE/TEXT_NODE/COMMENT_NODE (1/3/8)
- domElement.textContent // プレーンテキストの抽出 すべての子孫ノードの要素を結合した形
- domnode.textContent

 - document.createElement("tag")
 - document.createTextNode("text")
 - element.appendChild(childElement)
 - const removeNode = element.removechild(removeElement)
 - element.insertBefore(element, currentNode)
 - element.insertBefore(element, currentNode.nextSibling) // 直後
 - 
