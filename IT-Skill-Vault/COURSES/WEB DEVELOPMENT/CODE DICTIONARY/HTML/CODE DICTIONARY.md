
# A. STRUCTURE

### Structure of HTML
```
<!DOCTYPE html>

<html>

<head>

    <title>First Hello World</title>

</head>

<body>
	<p>Hello World</p>
</body>

</html>
```




# B. TEXT AND ELEMENT

### Comment:
`<!-- Commnents here -->`

### HTML Paragraph:
`<p> Paragraph here </p>`

### HTML Heading:
```
<h1> Heading 1 </h1>
<h2> Heading 2 </h2>
<h3> Heading 3 </h3>
<h4> Heading 4 </h4>
<h5> Heading 5 </h5>
<h6> Heading 6 </h6>
```


### Break Element (Space):
`<br>`


### Text Formats:
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




# C. ATTRIBUTES

### Anchor Element:
`<a href="link here"></a>`

### Anchor Attributes:
| Attribute | Description                                                    |
| --------- | -------------------------------------------------------------- |
| href      | Indicates the url it will go to                                |
| target    | Indicates where the link will open example: it open in new tab |

### Types of Target Attributes

| _Blank    | Bubuksan nya yung link sa another tab                  |
| --------- | ------------------------------------------------------ |
| **_self** | **Bubuksan nya yung link sa current tab na ginagamit** |
Example Code:
```
Code 1
<a href = "home.html" target= "_blank">home</a>

Code 2
<a href = "about.html" target= "_self">About</a>
```




# D. IMAGE & FILES

### Image Element:
`<image src="Img_link/filename "></image>`

### Image Attribute
| ATTRIBUTE | DESCRIPTION                               |
| --------- | ----------------------------------------- |
| src       | Indicates the file path to load the image |
| width     | Indicates the width                       |
| height    | Indicates the height                      |
| alt       | Text show when image fails to load        |

Example code of with application of alt:
`<image src="image.png" alt="error"/>` <-- It shows an "error" message when the image faild to load.


### File Path
It uses when the image or other file is outside the folder

| Value              | Description                                                                                                                    |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| "name.png"         | The file is in the same folder.                                                                                                |
| "images/name.png"  | The file is in the folder: images in the current folder.                                                                       |
| "/images/name.png" | The file is in the folder: images at the root of the current web.                                                              |
| "../name.png"      | The file is in the folder one level up from the current folder (.. meaning nag back sya one level up from the current folder.) |
| Absolute Path      | The file's path is fully specified like url or complete path of a certain file.                                                |
Example Code:
`<image src="images/name.png"></image>`


# E. AUDIO & VIDEO

### Source Element
`<source src="music.mp3" type="audio/mp3">`

### Source Attributes:
| Attribute | Description                                             |
| --------- | ------------------------------------------------------- |
| src       | Indicates the file path                                 |
| type      | Indicates the MIME-type of the resouce or the file type |

### Audio Controls:

**Example Code 1 Long Method:**
```
<audio controls>
	//First Option
	<source src="music.mp3" type="audio/mp3">
	
	//Second Option if di gumana yung first resources
	<source src="music.ogg" type="audio/ogg">
	
	//Third option if di gumana yung 2 resources ito ididisplay nya
	Browser doesn't support the audio tag.
</audio>
```

**Example Code 2 Short Method:**
```
<audio src="music.mp3" controls>
	Browser doesn't support the audio tag
</audio>
```


### Audio Control Attributes:
| Attribute | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| src       | Indicates the file path.                                              |
| controls  | Shows controls like play, pause.                                      |
| autoplay  | Play audio automatically when loaded (doesn't work on some browsers). |
| muted     | The audio would be muted by default.                                  |
| loop      | Makes the audio replay infinite times.                                |
Example Code:
```
<!--LONG METHOD-->

   <audio controls loop>

        <source src="testing.mp3" />

        Audio Error.....

   </audio>

   <br>

   <h2>Example 2 (naka muted)</h2>
```

```
 <!--SHORT METHOD-->

   <audio src="testing.mp3" type="audio/mp3" controls muted>

        Error...

   </audio>
```

### Video Element
**Example 1: long method**
```
<video width="320" height="240" controls>
	<source src="vid.mp4" type="audio/mp4">
	<source src="vid.ogg" type="audio/ogg">
	//Text message if files not working
	Browser doesn't support the video tag
</video>
```

**Example 2: short method**
```
<video src="vid.mp4" width="320" height="240" controls>
	Browser doesn't support the video tag. 
</video>
```

### Video Element Attribute

| Attribute | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| src       | Indicates the file path.                                              |
| controls  | Shows controls like play, pause.                                      |
| autoplay  | Play audio automatically when loaded (doesn't work on some browsers). |
| muted     | The audio would be muted by default.                                  |
| loop      | Makes the audio replay infinite times.                                |
| width     | Sets the width of the video player                                    |
| height    | Sets the height of the video player                                   |
Example Code:
```
<video controls loop width="500" height="500">
        <source src="testingVideo.mp4" type="video/mp4"/>
        Audio Error.....
</video>
```




# F. TABLES
```
<table>
	<tr> <-- TABLE ROW 1
		<th>TITLE 1</th>  <-- TABLE HEADING (NAKA HIGHLIGHT)
		<th>TITLE 2</th>
	</tr>

	<tr> <-- TABLE ROW 2
		<td>Content 1</td> <-- TABLE DATA (HINDI NAKA HIGHLIGHT)
		<td>Content 2</td>
	</tr>
</table>
```

Output:

| TITLE 1   | **TITLE 2** |
| --------- | ----------- |
| CONTENT 1 | CONTENT 2   |



# G. LISTS

### Types of List
1. Uordered List `<ul>`
	* List without numbering
2. Ordered List `<ol>`
	* List with numbering


### List Element:
```
	<li> Item 1 <li>
	<li> Item 2 <li>
	<li> Item 3 <li>

Note: <li> tags are used within <ol> or <ul> elements.
```


### Under Ordered List:
```
<ul>
	<li>C<li>
	<li>C++<li>
	<li>C#<li>
	<li>Python<li>
	<li>Java<li>
</ul>
```

**Output:**
![[Screenshot 2024-11-21 200048.png]]

### Nested unordered list.
```
<ul>
	<li>Fruits<li>
	<ul>
		<li>Apple<li>
		<li>Orange<li>
	</ul>
	
	<li>Vagetales<li>
	<ul>
		<li>Cabbage<li>
		<li>Celery<li>
	<ul>
</ul>
```

**Output:**
![[Screenshot 2024-11-21 201118.png]]\


### Ordered List
```
<ol>
	<li>A</li>
	<li>B</li>
	<li>C</li>
</ol>
```
**Output:**
![[Screenshot 2024-11-21 201738.png]]

**Example 2:**
```
<ol>
	<li value="10">A</li>
	<li>B</li>
	<li>C</li>
</ol>

Note: Meaning ng value="10", sa number 10 sya magiisatart magbilang.
```
**Output:**
![[Screenshot 2024-11-21 201712.png]]



### Nested Ordered List
```
<ol>
          <li>A</li>
          <ol>
               <li>a</li>
               <li>b</li>
               <li>c</li>
          </ol>
          <br>
          <li>B</li>
          <ol>
               <li>a</li>
               <li>b</li>
               <li>c</li>
          </ol>
     </ol>
```
**Output:**
![[Screenshot 2024-11-21 202111.png]]

Note: Pwedeng paghaluin ang `<ul>` and `<ol>`.