## File Overview
``` html
<!DOCTYPE html>

<html>
  <head>
    <meta charset="utf-8"> (e.g.)

    (<style></style>)
  </head>
  <body>
    <header>
      <nav></nav>
    </header>
    <main>
      <section>
        <article></article>
      </section>
    </main>
    <aside></aside>
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
<a href="url" target="_blank"></a> <!-- 新しいタブで開く -->
img
<img src="url" alt="explain">
style
<link href="style_path_or_url.css" rel="stylesheet">
```

## HTML5
```html
highright
<mark></mark>
abbriviation
<abbr title="title"></abbr>
ruby
<ruby>
  個人的<rp>(</rp><rt>こじんてき</rt><rp>)</rp>
</ruby>
time
<time datetime="">2017/5/31</time>
figure
<figure>
  <img src="" alt="">
  <figcaption>explain</figcaption>
<figure>

input
<input type="number" min="" max="" step="">
<input type="email/tel/date">

progress
<progress value="" max=""></progress>

範囲
<meter value="" max="" min="" high="" low="">

video
<video width="" height="" poster="loadingIMGpath" controls autoplay>
  <source src="videoURL" type="videoType">
  defualt text
<video>

audio
<audio controls>
  <source src="" type="audioType">
</audio>
```


## js
```javascript
<button onclick="alert(`hoge`)">name</button>
// external file
<script src="url"></script>
```
