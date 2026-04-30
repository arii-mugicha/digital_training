# DOM with JavaSccript
- const documentRoot = document;
- const body = document.body;
- const idSearch = domElement.getElementById("idName");
- const tagSearch = domElement.getElementByTagName("TagName"); // => arrayLikeObject
- cosnt classSearch = domElment.getElementByClassName("ClassName");
- const element = domElement.querySelector("tagName.ClassName"); // 深さ優先探索 ClassNameを持つ最初のtag
- const element = domElement.querySelector("tagName.ClassName1#ClassName2"); // 複数のClassNameをすべて持つtag
- const element = domElement.querySelector(".ClassName"); // 不特定のタグの要素指定
- const element = domElement.querySelectorAll("tagName.ClassName"); // 深さ優先探索
