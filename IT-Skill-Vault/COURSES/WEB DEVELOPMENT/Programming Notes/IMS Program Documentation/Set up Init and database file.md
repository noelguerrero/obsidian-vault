
**Note: All the files are connected make sure you read each notes**

## DATABASE FILE

**database.php or connection.php**
```
<?php
	//Create a constant variable for URL 
	define('SITEURL', 'https://localhost/Inventory Management/');

	//Host Name
	$host = 'localhost';
	
	//Database name  
    $dbName = 'inventory_management';
    
    //Database Username
    $dbUser = 'root';
    
    //Database Password
    $dbPassword = '';

	//Data Source Name
    $dsn = "mysql:host=$host;dbname=$dbName"; 

	//Connecting to database
	try{
		$conn = new PDO($dsn, $dbUser, $dbPassword);
		
		//Set the PDO error mode to exception.
        $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        
	}catch (\Exception $e){
		//This will output an error message if the connection is failed
		echo $e->getMessage()
	}
?>
```
note:
- Constant variable name must capitalize, **syntax:** `define('VARIABLENAME', value);`



## INITIALIZATION FILE
this file contains the **session_start()**, database connection, and other functions.

**init.php**
```
<?php
    if (session_status() === PHP_SESSION_NONE)
    {
	    //Starting Session
        session_start();
    }

	//importing database connection
    require_once 'connection.php';
?>
```