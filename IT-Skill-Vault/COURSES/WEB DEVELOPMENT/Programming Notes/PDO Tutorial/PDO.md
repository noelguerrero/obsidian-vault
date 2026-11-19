	
## PDO
The **PHP Data Objects (PDO)** extension defines a lightweight, consistent interface for accessing databases in PHP
- Multiple Databases.
- Security / Prepared Statements
- Reusability
- Error Handling 

## Prepared Statements
PHP prepared statements. They are templates for sending queries or uploading data to SQL databases.

Using PDO or MYSQLi, prepared statements provide an additional layer of security as the values are being sent to the server separately from the query


## To Check If We have already installed PDO Extension
```
<?php
    print_r(PDO::getAvailableDrivers());
?>
```
![[Pasted image 20250403131944.png]]
Note: its ok that only mysql only in there, since we only focus on using mysql query



## Creating a Connection in DATABASE
```
//DB Connection

	//Declaring Database Credentials
    $host = "localhost";
    $user = "root";
    $password = "";
    $dbname = "employee";

    //$dsn -> Data Source Name
    $dsn = "mysql:host=$host;dbname=$dbname";

  
    //Create PDO Instance -> usually it named $conn or $connections
    $pdo = new PDO($dsn, $user, $password);
```



## Creating a Query
```
//Connection
$pdo = new PDO($dsn, $user, $password);

//Query
$stmt = $pdo->query("SELECT * FROM userdata");
```

Note: 
- the "->" used para magamit yung methods sa loob ng object or class
- "$stmt" -  it means statement.



## Displaying a data or values from database 
```
//Connection
$pdo = new PDO($dsn, $user, $password);

//Query
$stmt = $pdo->query("SELECT * FROM userdata");

//Display all the values using while loop
while($row = stmt->fetch(PDO::FETCH_ASSOC))
{
	$row['first_name'], " " . $row['last_name'];
}
```

Note: 
- PDO::FETCH_ASSOC - Fetch all the values inside an array like mysqli_fetch_assoc();

## Displaying OBJECT
```
//Connection
$pdo = new PDO($dsn, $user, $password);

//Query
$stmt = $pdo->query("SELECT * FROM userdata");

//Display all the values using while loop
while($row = $stmt->fetch(PDO::FETCH_OBJ))
{
	echo $row->first_name . " " . $row->last_name;
}
```
Note:
- PDO::FETCH_OBJ - fetch all the properties and method of a class into a specific container.

## You can set a default Fetch styles

```
//Connection
$pdo = new PDO($dsn, $user, $password);

//Setting a default fetch style
$pdo->setAttribute(PDO::ATTR_DEFAULT_FETCH_MODE, PDO::FETCH_ASSOC);
//In the second parameter you can place your specific Fetch type.

//Query
$stmt = $pdo->query("SELECT * FROM userdata");
$stmt->execute()

//Display all the values using while loop
while($row = stmt->fetch(PDO::FETCH_ASSOC))
{
	$row['first_name'], " " . $row['last_name'];
}
```


## PREPARED STATEMETS

### POSITIONAL STATEMENTS

#### POSITIONAL PARAMETER
It uses "?" as a placeholder
```
 // A. POSITIONAL PARAMETERS

//We assume that the value of this variable is a user input to find the male user data.

$gender = "male";
  
//"?" it means nirereserve mo lang yung position nayun or gagawin mo syang placeholder
//Query with a placeholder "?"
$sql = "SELECT * FROM userdata WHERE gender=?";

//Prepare the SQL query
$stmt = $pdo->prepare($sql);

//This will take the inputs and place it into the placeholder "?" and execute the query.
$stmt->execute([$gender]);

  
//Fetch all the values in a specific container or variable
$users = $stmt->fetchAll(PDO::FETCH_ASSOC);

//Display the data
foreach($users as $user_data){
	echo $user_data['first_name'] . " " . $user_data['last_name'] . "<br>";
}
```

Note: yung positional parameters is naka base yung placeholder sa pagkakasunod ng parameter.
```
$sql = "DELETE FROM userdata WHERE id = ? AND first_name = ?"; <-- Naka base ito sa
$stmt = $pdo->prepare($sql);
$stmt->execute([$id, $Noel]); <-- pag kakasunod neto
```


#### NAMED PARAMETER
It uses :name as the placeholder.
```
// B. NAMED PARAMERTERS

//We assume that the value of this variable is a user input to find the female user data.

$gender = "female";

//Query
$sql = "SELECT * FROM userdata WHERE gender=:gender";

//Prepare the SQL query
$stmt = $pdo->prepare($sql);

//This will take the inputs and place it into the placeholder ":gender" and execute the query.
// "gender" is the placeholder name in database
$stmt->execute(['gender' => $gender]);

//Fetch all the values in a specific container or variable
$users = $stmt->fetchAll(PDO::FETCH_ASSOC);

//Display the data
foreach($users as $user_data){
	echo $user_data['first_name'] . " " . $user_data['last_name'] . "<br>";
}
```


## Getting a Specific Record Example
```
//We assume that this is the input of user
$id = 1;

//Query
$sql="SELECT * FROM userdata WHERE id=:id";

//Prepare SQL
$stmt = $pdo->prepare($sql);

//Place the inputs in placeholder and execute the code
$stmt->execute(['id' => $id]);

//Fetch the record into a variable 
$user_data = $stmt->fetch(PDO::FETCH_ASSOC);

//Display the data (it is a array format)
echo $user_data['first_name'] . " " . $user_data['last_name'];
```



## Getting the num rows 
```
//EXAMPLE USER INPUT
$gender = "male";

//Query
$sql = "SELECT * FROM userdata WHERE gender=:gender";

//Prepare query
$stmt = $pdo->prepare($sql);

//Place the input into placeholder and execute the query

$stmt->execute(['gender' => $gender]);

//Count the rows
$userCount = $stmt->rowCount();

//Display the num rows
echo $userCount;
```


## INSERT
```
//INSERT

//Assume that this is from web forms
$first_name = "Liz";
$last_name = "Guerrero";
$gender = "female";
$email = "lizguerrero@gmail.com";

//Query
$sql = "INSERT INTO userdata(first_name, last_name, gender, email) VALUES(:first_name, :last_name, :gender, :email)";

//Prepare Query
$stmt = $pdo->prepare($sql);

//Place the values into placeholder and execute the code
$stmt->execute(['first_name' => $first_name, 'last_name' => $last_name, 'gender' => $gender, 'email' => $email]);


//For feedback purposes -> it display "1" if we insert the data successful
echo $stmt->rowCount();
```


## UPDATE
```
//UPDATE

//Assume that this is user input
$first_name = "Noel";
$last_name = "Guerrero";
$gender = "Male";
$email = "noelguerrero@gmail.com";
$id = 1;

//Query
$sql = "UPDATE userdata SET first_name=:first_name, last_name=:last_name, gender=:gender, email=:email WHERE id=:id";

//Prepare Query
$stmt = $pdo->prepare($sql);

//Fill the placeholders and execute the query
$stmt->execute(['first_name' => $first_name, 'last_name' => $last_name, 'gender' => $gender, 'email' => $email, 'id' => $id]);



//For feedback purposes -> it display "1" if we update the data successful
echo $stmt->rowCount();
```


## DELETE
```
//DELETE

  
//User input
$id = 5;

//Query
$sql = "DELETE FROM userdata WHERE id = :id";

//Prepare query
$stmt = $pdo->prepare($sql);

//Fill the placeholder and execute the code
$stmt->execute(['id' => $id]);

  
//For feedback purposes -> it display "1" if we delete the data successful
echo $stmt->rowCount();
```


## SEARCH
```
//SEARCH

//User input
$search = "%as%";

//Query
$sql = "SELECT * FROM userdata WHERE last_name LIKE :search";

//Prepare Query
$stmt = $pdo->prepare($sql);

//Fill up the placeholder and Execute the Query
$stmt->execute(['search' => $search]);

//Set default fetch style
$pdo->setAttribute(PDO::ATTR_DEFAULT_FETCH_MODE, PDO::FETCH_ASSOC);

//FETCH ALL THE DATA
$employee_data = $stmt->fetchALL();

//DISPLAY DATA
foreach($employee_data as $user_data)
{
	echo $user_data['last_name'] . " " . "<br>";
}
```



## fetch() and fetchALL

stmt->fetch()   - Fetch a single record
stmt->fetchAll() - Fetch multiple records
