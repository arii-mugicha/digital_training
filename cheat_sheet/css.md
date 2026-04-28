## CSS file header
```css
@charset "UTF-8"
```

## セレクタ
```css
要素セレクタ
element {}
クラスセレクタ
.class{}
IDセレクタ
#id{}
属性セレクタ
[attribute=xxx]{}
ユニバーサルセレクタ
* {}

擬似クラス
p:hover{} カーソルが上にある
p:visited{} 閲覧したコンテンツ
p:checked{} フォームがチェック済み
p:active{} クリックしている間
```

## 擬似要素
```css
tag::before/after{content:"*"}
```

## セレクタの指定
```css
子孫セレクタ(スペース区切り)
.parent .child{}
特定の要素の直下の子要素
.parent > .child{}
特定の要素の直接の後続の要素、隣接セレクタ
.parent + .child{}
特定の要素の後半の要素
.parent ~ .child{}
複数のセレクタ(,区切り)
.box1, .box2{}
```

## 雑記
```css
.democlass{
  backbround:,
height,
width,
padding: top right bottom left, 
margin: top right bottom left, (auto?)
display:hide/block,
font-size:,
font-family,
font-weight

}
```
