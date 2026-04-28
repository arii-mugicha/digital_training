## File Overview
``` html
<!DOCTYPE html>

<html>
  <header>
    <meta charset="utf-8"> (e.g.)

    (<style></style>)
  </header>
  <body>
  </body>
<html>
```

## tag
```html
<tag style = "...">
<tag id = "...">  <=> #id {css details}
<tag class = "...">  <=> .class{css details}

list
<ul/ol>
  <li> </li>
</ul/ol>

table
<table>
  <tbody>
    <tr>:行の作成
      <td></td> <td></td> 
    </tr>
  <tbody>
</table>

form
<form method="GET/POST" action="url">
</form>

submit
<button type="submit">display</button>

input
<div>
  <input type="text" name="name">
  <input type="checkbox" name="name" value="true">
  <label for="id_value">
    <input type="xxx" id="id_value" ...>
  </label>
</div>
<textarea></textarea>
```

## link
```html
hyperlink
<a href="url">
img
<img src="url" alt="explain">
style
<link href="style_path_or_url.css" rel="stylesheet">
```

## js
```javascript
<button onclick="alert(`hoge`)">name</button>
// external file
<script src="url"></script>
```
