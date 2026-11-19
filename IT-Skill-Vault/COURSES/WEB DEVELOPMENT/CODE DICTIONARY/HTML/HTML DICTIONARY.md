HTML layout
```
<!DOCTYPE html>

<html>

<head> 

    <title>First Hello World</title>

</head>

<body>

</body>

</html>
```


### Comments Syntax:
`<!-- Comment here -->`


### HTML Paragraph:
` <p> paragraph here </p>`


### Headings:
```
<h1> Heading 1 </h1>
<h2> Heading 2 </h2>
<h3> Heading 3 </h3>
<h4> Heading 4 </h4>
<h5> Heading 5 </h5>
<h6> Heading 6 </h6>
```


### Break Element (Space)
`<br>`  <-- No end tag


### Text Format Element:
```
<b> bold </b>

<strong> Important </strong>

<i> Italic </i>

<em> Emphasized </em>

<mark> Marked </mark>

<small> Smaller </small>

<del> Deleted </del>

<ins> Inserted <ins>

<sub> Subscript </sub>

<sup> Superscript </sup>
```

![[Screenshot 2024-11-07 213442.png]]



### Anchor (to link a URL in text, image, and etc)
`<a href="link of page here">  </a>`

### Attributes of Anchor tag

| Attribute | Description                                                                                |
| --------- | ------------------------------------------------------------------------------------------ |
| href      | Indicates the url it will go to                                                            |
| target    | Indicates where the link will open example: it open the link in new tab or the current tab |


### Target Attribute in Anchor tag
```
Example how to insert target attribute:

Code 1:
<a href = "home.html" target= "_blank">home</a>

Code 2:
<a href = "about.html" target= "_self">About</a>
```

| _blank    | Bubuksan nya yung link sa new tab             |
| --------- | --------------------------------------------- |
| **_self** | **Bubuksan nya yung link but sa current tab** |


### Image Insertion
`<image src="image link or file name"></image>`

### Image Attributes

| ATTRIBUTE | DESCRIPTION                               |
| --------- | ----------------------------------------- |
| src       | Indicates the file path to load the image |
| width     | Indicates the width                       |
| height    | Indicates the height                      |
| alt       | Text show when image fails to load        |

Example of Alt:
`<image src="image.png" alt="error image"/>`


### File paths
Ginagamit lang ito pag yung picture or other resources ay nasa labas ng folder.

| Value              | Description                                                                                                                    |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| "name.png"         | The file is in the same folder.                                                                                                |
| "images/name.png"  | The file is in the folder: images in the current folder.                                                                       |
| "/images/name.png" | The file is in the folder: images at the root of the current web.                                                              |
| "../name.png"      | The file is in the folder one level up from the current folder (.. meaning nag back sya one level up from the current folder.) |
| Absolute Path      | The file's path is fully specified like url or complete path of a certain file.                                                |

Example code:
`<image src="image/name.png"></image>`

### You can link a page on image file
```
Example:

<a href="home.html"> 
	<img src="name.png" alt="error"/>
</a>
```