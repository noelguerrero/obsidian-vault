## Avoid repeating the source code by using include method.

```
<?php include('path_file');?>

Example to avoid creating again the footer in different page you can just include it:
<?php include('../file/footer.php');?>
```


## `mysqli_connect()`
Establishes a connection to the MySQL database server.
```
Syntax:
$variable = mysqli_connect('Hostname or IP address or domain', 'database_name', 'database_password');

Example:
$conn = mysqli_connect('localhost', 'root', '');
```


## `mysqli_select_db()`
Selects a specific database to use **after** establishing the connection.

```
Syntax:

$variable = mysqli_select_db($connection_variable, 'database_name');
```


## Create constant variables to avoid repeating variables

```
Syntax:
define('variable_name', 'value');

Example:
define('DB_NAME', 'food-order');

Note: but if we call it we dont need to put "$"
Example: echo DB_NAME;
```


## `$_SESSION` 

It stores and manage temporary value for a specific user while they interact with  website. It helps **track user activity** across multiple pages. And it ends when the user log out, close the browser and when the session is timeout

```
Syntax:

$_SESSION['Name'] = "value";

Example:
$_SESSION['cart'] = ['shoes', 'watch'];
```

### `unset($_SESSION[])`

Unset or remove the session value
```
Syntax and example: 

unset($_SESSION['cart']);
```


## DIFFERENCE BETWEEN `<?php ?>` and `<?= ?>`

| Syntax     | Purpose                     | Example                        |
| ---------- | --------------------------- | ------------------------------ |
| `<?php ?>` | General PHP logic execution | `<?php echo $name; ?>`         |
| `<?= ?>`   | Shorthand for `echo`        | `<?= $name ?>` (faster output) |


## `mysqli_num_rows();`
This function get the total number of rows in database


## `mysqli_fetch_assoc()`
Will get all the data in database

```
Syntax and example:

$sql = "SELECT * FROM tbl_admin";
$res = mysqli_query($conn, $sql);
$data=mysqli_fetch_assoc($res);
```


## `header()`
is a function that redirect you into specific page
```
Syntax:

header("location:" .link/file_path);

Example:

header("location:" . 'http://localhost/food-order/admin/delete-admin.php');
```

## POST and GET

```
$_POST - Passing the data into form

$_GET - Passing the data into URL
```


## Don't use "" when you are inside in the "" as well
```
//Error because "success" uses double cotation inside the double cotation 
$_SESSION['delete'] = "<div class="success">Admin Deleted Successfully</div>";

//Instead use '' <-- single cotation like this 'success'
$_SESSION['delete'] = "<div class='success'>Admin Deleted Successfully</div>";

```



## `session_destroy()`
Destroy all session - it uses when doing a logout logic.


## `enctype="multipart/form-data"`
it is a attribute and attribute value in form element. if you are using input type file, you need this attribute to prevent the image or other file corrupt.

## `$_FILES()`
A super global variable in php that use for file variable

File variable is like a array, it looks like this
![[Pasted image 20250411210652.png]]

So to refer the variables inside that array we need to use the `$_FILES()`
```
Example
<form>
<input type="file" name="image">
<form>

$image_name = $_FILES['image']['name'];
$source = $_FILES['image']['tmp_name'];
$image_size = $_FILES['image']['size'];
```

## `move_uploaded_file()`
It is a method to upload file 
```
Example:
$source_path = $_FILES['image']['tmp_name'];
$destination_path = "../images/category/" . $image_name;

$upload = move_uploaded_file($source_path, $destination_path);
```


## `explode()`
hinahati nito yung isang data into parts
```
Example:
//food.jpg
$image_name = $_FILES['image']['name'];

//end() - kukunin nya yung nasa dulo na value
 echo $ext = end(explode('.', $image_name));
```
Output: jpg



## `move_upload_file`
Inupload nya yung isang file sa specific na lugar

```
Example:
$source_path = "C:\xampp\tmp\php9533.tmp";
$destination_path = "../images/category/food.jpg";

move_upload_file($source_path, $destination_path);
```


## `trim()`
Nireremove na yung mga hidden spaces sa isang value, but if yung space ay maykasunod ng char ireretain nya parin yun.
it is good practices sa pag cocode because sometimes di natin namamalayan na may space pala yung value ng isang variable.
```
Example:
$name = trim($_POST['name']);
```


## `unlink()`
Nireremove nya yung image or file sa folder

```
Example: 

$remove_path = "../images/category/".$current_image;
$remove = unlink($remove_path);
```