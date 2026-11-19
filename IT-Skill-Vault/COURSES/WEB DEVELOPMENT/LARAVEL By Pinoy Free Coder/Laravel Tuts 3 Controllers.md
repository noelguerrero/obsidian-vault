
## Controllers

### Creating a controller
On Terminal:
```
php artisan make:controller controllername
```
Example:
```
php artisan make:controller UserController
```


### PHP Intelephense
![[Pasted image 20251206104136.png]]

This extention remind you if you forgot to put the closing tag or semicolons.


## Using the Controller

UserController
```
<?php
namespace App\Http\Controllers;
use App\Http\Controllers\Controller;
use Illuminate\Http\Request;  

class UserController extends Controller
{
    public function index()
    {
        return 'Hello from UserController';
    }
}
```

web.php
```
use App\Http\Controllers\UserController;

Route::get('/users', [UserController::class, 'index']);
```
Reminder: that you need to Import the UserController file in the route file so that you can call it.

![[Pasted image 20251206110045.png]]


Add ons:
Some of developers do routes like this
```
Route::get('/users', [UserController@index]);
```


The previous version of laravel they route like this but now its not working
```
Route::get('/users', 'UserController@index');
```


## Passing a variable

UserController
```
class UserController extends Controller
{
    public function show($id)
    {
        return "User ID: " . $id;
    }
}
```

web.php
```
Route::get('/users/{id}', [UserController::class, 'show']);
```

![[Pasted image 20251206114514.png]]


## Passing data from Controller to View file

UserController
```
public function show($id)
{
	$data = array(
		'name' => 'Noel',
		'Age' => 21,
		'email' => 'noelguerrerojr@gmail.com',
		'id' => $id
	);
	
	return view('user', ['data' => $data]);
}
```
We need to pass the $data variable into array also when we return it.

user.blade.php  <-- This is the name of view file
```
@dd($data);
```
or
```
<?php dd($data);?>
```

![[Pasted image 20251206120603.png]]

## We can use the template of blade on displaying data

**Controller**
```
public function show($id)
{
	$data = array(
		'name' => 'Noel',
		'Age' => 21,
		'email' => 'noelguerrerojr@gmail.com',
		'id' => $id
	);
	
	return view('user', ['data' => $data]);
}
```

View File
```
{{ $name }}
```

![[Pasted image 20251218201150.png]]


### MIDDLEWARE

In **web development**, **middleware** is a piece of software that sits **between a client’s request and the server’s response**. It **intercepts, processes, or modifies** the request or response before it reaches its final destination.

 **Simple idea:**
Request → Middleware → Controller 
OR
App Logic → Middleware → Response

### What middleware is used for

Middleware is commonly used to handle **cross-cutting concerns**, such as:

- ✅ **Authentication** – check if a user is logged in
- 🔐 **Authorization** – check if a user has permission
- 🛡️ **Security** – protect against CSRF, XSS, etc.
- 🧾 **Logging** – record requests and errors
- 🚦 **Rate limiting** – limit how many requests a user can make
- 🌐 **CORS** – control which domains can access your API
- 🧹 **Input validation & sanitization**


#### How to use middleware?

**In this scenario we used auth function**

**Example 1:**

**web.php**
```
Route::get('/user/{id}', [UserController::class, 'show'])->middleware('auth');
```

**Link in the URL bar:**
```
http://127.0.0.1:8000/users/1
```

**This will show since we have not login route in our route file**
![[Pasted image 20251218202645.png]]


**Example 2:**

In this scenario we use alias to login when we implement auth function
```
Route::get('/login', [UserController::class, 'index'])->name('login');

  

Route::get('/users/{id}', [UserController::class, 'show'])->middleware('auth');
```


**Link in the URL bar:**
```
http://127.0.0.1:8000/users/1
```


![[Pasted image 20251218203130.png]]


### ANOTHER WAY OF PASSING DATA

**UserController**
```
use App\Http\Controllers\Controller;
use Illuminate\Http\Request;

class UserController extends Controller
{
    public function index()
    {
        return 'Hello from UserController';
    }  

    public function show($id)
    {
        return view('user')
            ->with('name', 'Noel')
            ->with('id', $id)
            ->with('age', 30);
    }
}
```

**User view file**
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p> {{ $name }} </p>
    <p> {{ $id }} </p>
    <p> {{ $age }} </p>
</body>
</html>
```

![[Pasted image 20251218204446.png]]