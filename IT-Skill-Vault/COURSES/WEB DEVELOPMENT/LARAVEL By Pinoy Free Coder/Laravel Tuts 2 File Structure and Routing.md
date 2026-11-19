
##  A. `app` folder
It includes the http controllers and Model that necessary for MVC pattern 

****

## B. `routes` folder
there are 4 types of routes that we can use:

- `api.php` - it basically i will only do is process http request and the developer is responsible to control what data that we give. And it utilize middleware group either authentication or processing the data.

-  `channels.php` - the tuts didn't discuss it but we can search and watch tuts about laravel broadcasting.

- `console.php` - Laravel give as a capability to create our artisan command (e.g `php run email` that can send email).

- `web.php` - it receives http request that uses in web applications. Also it utilize middleware.

****

## C. `bootstrap` folder
it is not the bootstrap library. It basically it combines the core classes in one place

****

## D. `config` folder
It contains many important configuration files like:
- `app.php` - that is the same purpose of `.env` file. If we don't want to use `.env` file we can use the `app.php` file.
- `auth.php` - that contains default password and guards.
- `cache.php` - for cache. **laravel used file for cache but we can cookie instead if we want.**
- `database.php` - that contains database connections and configurations.
- `filesystem.php` - this contains the configurations of the file locations. Its either local or uses AWS.
- `hashing.php`
- `logging.php`
- etc..

****

## E. `database` folder
it includes the folders:

- migrations folder - that contains some tables (it is automatically set).
- seeders folder - it contains `DatabaseSeeder.php` file that populate the data or create fake records (e.g user data).
- factories folder - it contains `UserFacotry.php` that contains random example data that get by `DatabaseSeeder.php` when we create fake records or data.

****

## F. `lang` folder
it contains en folder (english) that contains english feedbacks like example when we type wrong password it will provide wrong password feedback. Also we can add cn folder for chinese and etc...

****

## G. `public` folder
It contains the index.php and other necessary file for routing.

****

## H. `resources` folder
It contains CSS, JS, and view files

****

## I. `storage` folder
This where we store files, when we run a move file application that files is place in this folder.


****

## J. `test` folder
For QA but the tuts didn't discuss it.

****

## K. `vendor` folder
This is where composer store the packages that needed by laravel.

****

## L. `package.json` file
for note packages.

****

## M. `.env` file
it basically contains the configurations in our project.

- Note: the config folder that contains config files is the dafault configuration of our project, we used `.env` file if we don't want to configure the files that in config folder. So basically the .env file is a shorcut file for configurations.  

****

 
## ROUTING
There are many types of routes in laravel
### A. `Route::get();`

### B. `Route::post();`

The commonly used are `get();`, `post();`, `put();`, and `delete();`.
### C. `Route::put();`  
- Edit or update the data

### D. `Route:patch();` 
- Remove whole data and changing it a new one.

### E. `Route::delete();` 
- for deleting data

###  F. `Route::options();` 
- for a http request that only allow specific method (search for more info).

### G. `Route::match();` 
- for passing or delivering a array
example:
```
Route::match(['get', 'post'], '/', function(){
		return 'POST and GET is allowed';
	});
```
this code it receive either get or post method request of the user.

### H. `Route::any();` 
- it allowed all the request type like post, get, put, patch and etc from the users.

**If we only need to show a landing page we can make the route code short like this**
```
Route:view('/welcome', 'welcome');
```

### I. `Route::redirect();`
- for redirecting a specific page
example:
```
Route::get('/about', function(){
	return 'about';
});

Route::redirect('/gotoabout', '/about');
```
note: The route must exist first before we can redirect the route.

- `'/gotoabout'` - represent the trigger url
- `'/about'` - represent the target url

### J. `permanentRedirect();`
- it is usually work when a http to https, but this thing is configure on the hosting

```
Route::permanentRedirect('/gotoabout', '/about' function() {
	return 'redirect';
});
```


****
## REQUEST AND RETURN

### REQUEST
- it is a request the came from user example: post request when we fill up a form, or a get request when we getting a specific data.

We can see the data inside the request, like the form data inside in a POST request. 

```
Route::('/user', function(Request, $request){
	
});
```

### `dd();` 
- default laravel debugger. Same function as `var_dump`
- dd - means die dump

```
//Importing request file
use Illuminate\Http\Request;

Route::get('/users', function(Request $request){
    dd($request);
    return NULL;
});
```

![[Pasted image 20251119204112.png]]

note: example it display what data are in `$request` variable.


### RESPOND
- it is the our feedback or response on the request example: we respond or deliver a data on the post or get request the came from user.

### `response();`
- it is a built in function that we can place inside what should we respond (eg. data, text, and etc).

**Example:**
```
Route::get('/get-text', function({
	return response('Hello World');
}));
```

![[Pasted image 20251119205322.png]]

**Also we can add more lines of code**

```
Route::get('/get-text', function({
	return response('Hello World', 200)->header('Content-Type', 'text/plain');
}));
```
200 - it is the http status code for successful
![[Pasted image 20251119205903.png]]


#### How can we add parameters in URL
```
Route::get('/users/{id}', function($id){
	return response($id, 200);
});
```

![[Pasted image 20251119210508.png]]

**How about multiple parameters**
```
Route::get('/user/{id}/{name}', function($id, $name){
    return response("User id is: ".$id." and name is: ".$name);
});
```
![[Pasted image 20251119210928.png]]


#### How to return a json data
```
Route::get('request-json', function(){
	return response()->json(['name' => 'Noel', 'age' => '21']);
});
```
`json();` - is a built in json function in laravel.

![[Pasted image 20251119211936.png]]


#### How about we want the user to download a specific file?


```
Route::get('/request-download', function(){	
	$path = public_path().'/sample.txt';
	$name = 'sample.txt';
	$header = array(
		'Content-Type : application/text-plain'
	);
	
	return response()->download($path, $name, $headers);
});
```

`public_path()` - the address of the index file
`$headers` - file type (eg.. Excel, pdf, and so on...)

![[Pasted image 20251119213812.png]]

**Also you can**
```
Route::get('/request-download', function(){
    $path = public_path('sample.txt');
    $name = 'sameple.txt';
    $headers = array(
        'Content-Type: application/text-plain'
    );

    return response()->download($path, $name, $headers);
});
```


### `php artisan route:list`
If we have multiple route, by using this code we can see all the route in our project

IDE Terminal
```
php artisan route:list
```

![[Pasted image 20251119214440.png]]