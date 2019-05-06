# html

## Basic

### 结构

HTML  必须以文档类型声明开始<!DCOTYPE html>,开始于<html>结束于</html>,可见区域位于<body></body>标签内

### 元素

HTML元素内容位于一堆闭合的标签内，所有的元素都可以包含元素

### 属性

元素可以包含属性。属性提供元素的其他信息并始终位于起始标签，使用键值对的方式定义

### 标题

标题<h1>~<h6> <hr>水平分割

### 段落

```
<p> defines paragraphs
<br> line break
<pre> defines preformatted text
```

### 文本格式

```
<b> - Bold text
<strong> - Important text
<i> - Italic text
<em> - Emphasized text
<mark> - Marked text
<small> - Small text
<del> - Deleted text
<ins> - Inserted text
<sub> - Subscript text
<sup> - Superscript text
```

### 语录

```
<q> defines a short quotation
<blockquote> defines a section that is quoted form another soure
```

### CSS

```
Inline - by using the style attribute in HTML elements
Internal - by using a <style> element in the <head> section
External - by using an external CSS file

border property defines a border around an HTML element
padding property defines a padding (space) between the text and the border
margin property defines a margin (space) outside the border:
```

### Table

```
An HTML table is defined with the <table> tag.

Each table row is defined with the <tr> tag. A table header is defined with the <th> tag. By default, table headings are bold and centered. A table data/cell is defined with the <td> tag.

Use the HTML <table> element to define a table
Use the HTML <tr> element to define a table row
Use the HTML <td> element to define a table data
Use the HTML <th> element to define a table heading
Use the HTML <caption> element to define a table caption
Use the CSS border property to define a border
Use the CSS border-collapse property to collapse cell borders
Use the CSS padding property to add padding to cells
Use the CSS text-align property to align cell text
Use the CSS border-spacing property to set the spacing between cells
Use the colspan attribute to make a cell span many columns
Use the rowspan attribute to make a cell span many rows
Use the id attribute to uniquely define one table
```

Lists

```
An unordered list starts with the <ul> tag. Each list item starts with the <li> tag.
The list items will be marked with bullets (small black circles) by default:

Use the HTML <ul> element to define an unordered list
Use the CSS list-style-type property to define the list item marker
Use the HTML <ol> element to define an ordered list
Use the HTML type attribute to define the numbering type
Use the HTML <li> element to define a list item
Use the HTML <dl> element to define a description list
Use the HTML <dt> element to define the description term
Use the HTML <dd> element to describe the term in a description list
Lists can be nested inside lists
List items can contain other HTML elements
Use the CSS property float:left or display:inline to display a list horizontally
```

### Block(块)
A block-level element always starts on a **new line** and **takes up the full width available** (stretches out to the left and right as far as it can).
```
<address> <article> <aside> <blockquote> <canvas> <dd> <div> <dl> <dt> <fieldset> <figcaption>
<figure> <footer> <form> <h1>-<h6> <header> <hr> <li> <main> <nav> <noscript> <ol> <p> <pre> <section> <table> <tfoot> <ul> <video>
```

Inline Elements(内联元素)

An inline element **does not start on a new line** and **only takes up as much width as necessary.**s

```
<a> <abbr> <acronym> <b> <bdo> <big> <br> <button> <cite> <code> <dfn> <em> <i> <img> <input> <kbd><label> <map> <object> <output> <q> <samp> <script> <select> <small> <span> <strong> <sub> <sup><textarea> <time> <tt> <var>
```

### class

In CSS, to select elements with a specific class, write a period (.) character, followed by the name of the class:

```
Tip: The class attribute can be used on any HTML element.

Note: The class name is case sensitive!

Tip: You can learn much more about CSS in our [CSS Tutorial](https://www.w3schools.com/css/default.asp).
```

### id

The `id` attribute specifies a unique id for an HTML element (the value must be unique within the HTML document).The id value can be used by CSS and JavaScript to perform certain tasks for a unique element with the specified id value.In CSS, to select an element with a specific id, write a hash (#) character, followed by the id of the element:

```
Bookmarks with ID and Links
HTML bookmarks are used to allow readers to jump to specific parts of a Web page.
Bookmarks can be useful if your webpage is very long.To make a bookmark, you must first create the bookmark, and then add a link to it.When the link is clicked, the page will scroll to the location with the bookmark.
```

### script

The `<script>` tag is used to define a client-side script (JavaScript)The `<script>` element either contains scripting statements, or it points to an external script file through the `src` attribute.

### header

The `<head>` element is a container for metadata (data about data) and is placed between the `<html>` tag and the `<body>` tag.HTML metadata is data about the HTML document. Metadata is not displayed.Metadata typically define the document title, character set, styles, links, scripts, and other meta information.The following tags describe metadata: `<title>`, `<style>`, `<meta>`, `<link>`, `<script>`, and `<base>`.