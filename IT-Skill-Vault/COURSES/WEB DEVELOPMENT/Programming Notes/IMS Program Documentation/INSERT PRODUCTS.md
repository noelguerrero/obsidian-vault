
## `product-add.view.php`

****
**product-add.view.php**
```
<?php
    include('partials/header.php');
    require_once '../app/init.php';
    require_once '../app/auth.php';

    $errors = $_SESSION['product_form_errors'] ?? [];
    $oldInputs = $_SESSION['old_inputs'] ?? [];
    unset($_SESSION['product_form_errors'], $_SESSION['old_inputs']); // Reset after showing
?>


<form action="../app/database/product-add.php" method="POST"    class="productAddForm" enctype="multipart/form-data">

	<div class="productAddInputContainer">
		<label class="productInputLabel" for="">Product Name</label>
		<input type="text" class="productInputs" id="product_name" name="product_name" value="<?= htmlspecialchars($oldInputs['product_name'] ?? ''); ?>"/>
		<span class="errors"><?= $errors['product_name'] ?? '' ?></span>
	</div>
	
	<div class="productAddInputContainer">
		<label class="productInputLabel" for="">Description</label>
		<textarea class="productInputDescription" name="product_description" id="product_description"><?= htmlspecialchars($oldInputs['product_description'] ?? ''); ?></textarea>
		<span class="errors"><?= $errors['product_description'] ?? '' ?></span>
	</div>
	
	<div class="productAddInputContainer">
		<label class="productInputLabel" for="">Product Image</label>
		<input type="file" class="productInputImage" name="product_image" id="product_image" value="<?= htmlspecialchars($oldInputs['product_image'] ?? ''); ?>"/>
	</div>
	
	<input type="hidden" name="table" value="products"/>
	<button class="productAddBtn" type="submit"><i class="fa-solid fa-plus"></i> Add User</button>
	                
</form>
<?= $_SESSION['add_product_message'] ?? ''?>
<?php unset($_SESSION['add_product_message']);?>

```

****

This will import the header of html, the initialization (session), and the authorization code.

```
include('partials/header.php');
require_once '../app/init.php';
require_once '../app/auth.php';
```

****

This will initialize a array variable that catch the values of session array variable  "product_form_errors" and if its empty, it will becomes an empty array.

`$errors = $_SESSION['product_form_errors'] ?? [];`

note: this session contains the error values if their is.

***

This will initialize a array variable and catch the value of session array variable "old_inputs", and if its empty, it will becomes an empty array.

`$oldInputs = $_SESSION['old_inputs'] ?? [];`

note: this session contains the old input values if they need to display in the input fields.

****

This will unset the session variable "product_form_errors" and "old_inputs" after they display in the view.

`unset($_SESSION['product_form_errors'], $_SESSION['old_inputs']);`

****

```
<form action="../app/database/product-add.php" method="POST" class="productAddForm" enctype="multipart/form-data">
	....
</form>
```

- This attributes activates the file in the path
  `action="../app/database/product-add.php"`

- This method attribute deliver the data in a post method and store all the user input in `$_POST` super global variable.
	`method="POST"`

- This will store the file type input from the input fields and store in in the `$_FILE` super global variable
	`enctype="multipart/form-data"`

****

**Input Fields**
```
<input type="text" class="productInputs" id="product_name" name="product_name" value="<?= htmlspecialchars($oldInputs['product_name'] ?? ''); ?>"/>
```

So the input itselt it store the user input

```
<input type="text"></input>
```

This attribute will represent the specific input fields and its values.

`id="product_name"`

This will display the old input of the user (if their is)

```
value="<?= htmlspecialchars($oldInputs['product_name'] ?? '');
```

- `htmlspecialchars()` - make the values into text (whether it have some closing tags or symbols), this will prevent some input injection.
- `$oldInputs['product_name'] ?? ''` - the session variable contains the error message and it will be print, but if their is not, it will print nothing.

****

This will display a error message if this field its not fill up by a user

```
<span class="errors"><?= $errors['product_description'] ?? '' ?></span>
```

and if their is not an error it shows nothing.

**note: all the input fields work same at this, except for input type="hidden", and input type="file" , since the uploaded file can't retain.**

****

This input type hidden, besically it contains the specific table in database that the data should be deliver in.

`<input type="hidden" name="table" value="products"/>`

- `name="table"` - it represent the input field
- `value="products"` - its value

note: currently im not using this, because it will leak the specific column in database, i just include it for back-up purpose. But for safety you can just remove it.

****

This will submit all the data

`<button type="submit">Add User</button>`

****

This will display a response from the backend, if the data is successfully registered.

`<?= $_SESSION['add_product_message'] ?? ''?>`

And this will remove that display message

`<?php unset($_SESSION['add_product_message']);?>`

****



## `product-add.php`

`product-add.php`
```
<?php

    require_once '../init.php';

    $errors = [];

    if($_SERVER["REQUEST_METHOD"] === "POST")
    {
        $productName = trim($_POST['product_name']);
        $productDescription = trim($_POST['product_description']);

        if(empty($productName))
        {
            $errors['product_name'] = "Product name must be filled!";
        }

        if(empty($productDescription))
        {
            $errors['product_description'] = "Product description must be filled!";
        }

        if(!empty($errors))
        {
            $_SESSION['product_form_errors'] = $errors;
            $_SESSION['old_inputs'] = $_POST;
            $_SESSION['old_inputs']['product_image'] = $_FILES['product_image'];
            header("location:" . SITEURL . "view/product-add.view.php");
            exit;
        }

        if(isset($_FILES['product_image']['name']) && $_FILES['product_image']['name'] != '')
        {
            $product_image_name = $_FILES['product_image']['name'];
            $product_image_name = basename($product_image_name);

            //Getting Image Extention
            $image_ext = pathinfo($product_image_name, PATHINFO_EXTENSION);

            //Sanitizing Product Name
            $safeProductName = preg_replace("/[^a-zA-Z0-9_-]/", "_", $productName);
            
            //Renaming Image
            $codeProductName = $safeProductName . '_no_' . rand(0000, 9999) . '.' . $image_ext;

            //Upload Image to the location "product_images"
            $source_path = $_FILES['product_image']['tmp_name'];
            $destination_path = "../../assets/images/product_images/" . $codeProductName;
            $upload = move_uploaded_file($source_path, $destination_path);

            if($upload == FALSE)
            {  
                $_SESSION['add_product_message'] = "File upload failed";
                header("location:" . SITEURL . "view/product-add.view.php");
                exit;
            }
        }
        else
        {
            $codeProductName = "";
        }

        $created_by = $_SESSION['user']['id'];
        
        $addProductQuery = "INSERT INTO products SET product_name = :product_name, product_description = :product_description, product_img = :product_img, created_by = :created_by, created_at = NOW(), updated_at = NOW()";
        
        $stmt = $conn->prepare($addProductQuery);
        $stmt->bindParam(':product_name', $productName);
        $stmt->bindParam(':product_description', $productDescription);
        $stmt->bindParam(':product_img', $codeProductName);
        $stmt->bindParam(':created_by', $created_by);

        try
        {
            $stmt->execute();
            $_SESSION['add_product_message'] = "<div class='formOutputContainer'><span class='insertSuccess'>Product successfully registered!</span></div>";
            header("location:" . SITEURL . 'view/product-add.view.php'); // Change path if needed
            exit;      
        }
        catch(PDOException $e)
        {
            $_SESSION['add_product_message'] = "<div class='formOutputContainer'><span class='insertSuccess'>Product successfully registered!</span></div>";
            $_SESSION['old_inputs'] = $_POST;
            header("location:" . SITEURL . 'view/product-add.view.php'); // Change path if needed
            exit;  
        }
    }
?>
```