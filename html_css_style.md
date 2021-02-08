# HTML & CSS Style Guide

The purpose of this style guide is to outline the programming style and formatting preferred for HTML and CSS programs.

There are various existing HTML and CSS style guides that have been drawn on in making this guide, including:

- [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html)
- [MDN HTML guidelines](https://developer.mozilla.org/en-US/docs/MDN/Guidelines/Code_guidelines/HTML)
- [w3schools HTML Style Guide](https://www.w3schools.com/html/html5_syntax.asp)

## 1) General
- Files must use the UTF-8 character set encoding
- Filenames should be saved as ```camelCase.html``` for HTML files or ```camelCase.css``` for CSS files. Files that include PHP with the HTML code should be saved as ```camelCase.php```
- HTML and CSS code must be indented by 2 spaces for each indent level
- Use ```https://``` for all links to hrefs, images, source files, @imports, etc.
- Use lowercase for all HTML element names, attributes and attribute values, and for all CSS selectors, properties and property values
- Use lowercase-with-hyphens for all class names
- Use camelCase for all ```id=``` and ```name=``` attributes
- Spaces and new lines should be used to align code within blocks to improve read-ability
- There should be no trailing whitespace at the end of lines

## 2) HTML-specific rules
- Do not include spaces between attibutes and their values, and always enclose attribute values in double-quotes, e.g. ```<div class="myClass">```. An exception to this is when using PHP to output HTML, the PHP string will be in double-quotes, and the attributes then in single-quotes, e.g. ```echo "<div class='myClass'>"```
- Close all HTML elements with their closing tag, e.g. ```<p>Hello World</p>```
- Close all empty elements, e.g. use ```<br />``` instead of ```<br>```
- Use HTML elements for what they were created for, such as ```<h#>``` for headings, ```<p>``` for paragraphs, ```<a>``` for anchor links, etc.
- Always specify the ```alt``` attribute for images. It is also best practice to define the ```width``` and ```height``` attributes, either within the element or via CSS
- Omit the ```type``` attribute for style sheets (unless not using CSS) and scripts (unless not using JavaScript)

## 3) HTML layout
- Always declare the HTML5 document type, language and charset at the top of the HTML document
- The overall layout of HTML files should be as follow:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="description" content="DescriptionContent" />
  <meta name="keywords" content="Keywords" />
  <meta name="author" content="Author" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta http-equiv="X-UA-Compatible" content="ie=edge" />
  <title>Document Title</title>

  <link rel="stylesheet" href="https://...Links to any CSS stylesheets" />

  <script src="https://...Links to JavaScript scripts"></script>
</head>
<body>
  <!-- Main Body of code -->
</body>
</html>

```

## 4) CSS-specific rules
- When including CSS within an HTML attribute, use the format ```style="property1:value1; property2:value2;"```
- Within a CSS file, always put each rule in a separate block, with the selector name followed by a space and curly-brackets, e.g. ```body {```, and each declaration being on a separate line in the format of ```property: value;```, ending with a semi-colon (even for the last item)
- Include a blank line between each block
- Avoid qualifying ID and Class names with type selectors and avoid unnecessary ancestor selectors to improve performance
- Group declarations within each block by similar actions, e.g. top, right, bottom, left together to specify the positions of an element

## 5) CSS layout
- An example layout of a CSS files should be as follow:
```css
body {
  color: blue;
}

a {
  text-decoration: none;
}

.ex1 {
  border: 1px solid black;
  padding: 10px;
}

#ex2 {
  margin-bottom: 50px;
}
```
