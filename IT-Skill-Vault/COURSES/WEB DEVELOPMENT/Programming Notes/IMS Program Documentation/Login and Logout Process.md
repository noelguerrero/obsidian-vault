
**Note: All the files are connected make sure you read each notes**


## LOGIN

**Sample source code in login.php**
```
<?php
    require_once '../app/init.php';

    if(isset($_SESSION['user'])) header("location:" . SITEURL . 'view/dashboard.php');

    if($_POST){
        $username = $_POST['username'];
        $password = $_POST['password'];
        
        $query = "SELECT * FROM users WHERE email=:email AND password=:password";
        $stmt = $conn->prepare($query);
        $stmt->bindParam(':email', $username);
        $stmt->bindParam(':password', $password);
        $stmt->execute();

        if($stmt->rowCount() > 0)
        {
            $stmt->setFetchMode(PDO::FETCH_ASSOC);
            $user = $stmt->fetchAll()[0];
            $_SESSION['user'] = $user;
            // var_dump($_SESSION['user']);
            // die;
            header("location:" . SITEURL . 'view/dashboard.php');
        } 
        else
        {
            $_SESSION['login-error-message'] = "Please make sure that username and password are correct";
            header("location:" . SITEURL . 'view/login.php');
            exit;
        }
    }
?>

<body>
	<form action="login.php" method="POST">
	<label for="">Username:</label>
    <input type="text" name="username" placeholder="username"/>

	<label for="">Password:</label>
    <input type="password" name="password" placeholder="password"/>
</form>
<body>
```


**the init section include the `session_start()` method**
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


**the line:** 
`if(isset($_SESSION['user'])) header("location:" . SITEURL . 'view/dashboard.php');` 

It is a if statement that check if the `$_SESSION['user']` exist and, it exist it  automatically redirect into dashboard or homepage, so that we can avoid to visit login page when we are already login.


**Then this part** 
```
   //This condition runs when we the form is submit
   if($_SERVER["REQUEST_METHOD"] === "POST"){
		//Get the user input
        $username = $_POST['username'];
        $password = $_POST['password'];

		//Query
        $query = "SELECT * FROM users WHERE email=:email AND password=:password";
        
       //Prepare the query and execute it
        $stmt = $conn->prepare($query);
        $stmt->bindParam(':email', $username);
        $stmt->bindParam(':password', $password);
        $stmt->execute();
```
This part will receive the inputs, and find if their is a email same in the database.


**This condition will run if their is only one result.**
```
if($stmt->rowCount() === 1)
{
	$stmt->setFetchMode(PDO::FETCH_ASSOC);
    $user = $stmt->fetch();
	//Verify the password here...
}
else
{
	$_SESSION['login-error-message'] = "Please make sure that username and password are correct";
	header("location:" . SITEURL . 'view/login.php');
   exit;
}
```
If the result is only one, it fetch all data of the specific user that want to login. And runs the very password code block, else it direct into login page with error message.

**Verify password**
```
if(password_verify($password, $user['password']))
{
	$_SESSION['user'] = $user;
	header("location:" . SITEURL . 'view/dashboard.php');
    exit;
}
```
This part get and password inputed by the user and the password of the specific user that want to login (that in the database), and if they are the same (true), it create a sesson variable that store all the data of that specific user and direct to the dashboard. And also it will serve as a token when we are already login.



## LOGOUT

**Source Code:**
```
<?php
    require_once 'init.php';

    //Remove the session variable
    session_unset();
    session_destroy();
    header("location:" . SITEURL . 'view/login.php');
?>
```
It will import all the active session, then it unset the session and destroy it. And it will direct into login page.