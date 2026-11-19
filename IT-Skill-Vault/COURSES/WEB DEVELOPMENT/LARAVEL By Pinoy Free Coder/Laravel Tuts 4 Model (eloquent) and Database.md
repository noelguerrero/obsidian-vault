## CONNECTION IN DATABASE

- Configure the database info into `.env` or `database.php` file, but it is recommended that you configure into `.env` file
- Terminal: `php artisan migrate`  

## UTILIZING FAKER OR DUMMY DATA GENERATOR

- Uncomment this in part in `database/seeders/DatabaseSeeder.php` and configure in `factory(10)` how many dummy data that you want. 
```
public function run(): void
    {
        User::factory(10)->create();
	    
	    ...
    }
```

- Then in the terminal `php artisan migrate:refresh --seed`
![[Pasted image 20251222211222.png]]

Note: the `migrate:refresh` - it basically do is to delete the table first before it creates a new one


## MODEL

**eloquent class** - It is a object relation mapper that laravel creates to make it easy for us to manipulate data in database.

### Creating a model

**Terminal** 
`php artisan make:model Modelname` 
(noted: capital case in first part of the name)

**Example**
`php artisan make:model Students`
![[Pasted image 20251222212618.png]]

****

## Creating a dummy data generator

### A. Create migration

**Terminal:** `php artisan make:migration migrationName`
**Example:** `php artisan make:migration students_table --students`

note: the `--students` means we append a column in existing **students** table

![[Pasted image 20251222214455.png]]

In that migration file add this
```
public function up(): void
    {
        Schema::create('students', function (Blueprint $table) {
            $table->id();
            $table->string('first_name');
            $table->string('last_name');
            $table->string('gender');
            $table->string('age');
            $table->string('email')->unique();
            $table->timestamps();
        });
    }


    public function down(): void
    {
        Schema::dropIfExists('students');
    }
};
```

**Noted:** Always put `timestamps()` in the migrations and factories, because the seeder requires it. 

### B. Create Factories

**Terminal:**`php artisan make:factory FactorName`
**Example:** `php artisan make:factory StudentsFactory`

![[Pasted image 20251222215221.png]]
Note: Make sure that u used the name of the model (like students) and add factory in the end

**StudentsFactory**
```
public function definition(): array
    {
        return [
            'first_name' => fake()->firstName(),
            'last_name' => fake()->lastName(),
            'gender' => fake()->randomElement(['male', 'Female']),
            'age' => fake()->numberBetween($min = 18, $max = 25),
            'email' => fake()->unique()->safeEmail(),
        ];
    }
```

Note: the `safeEmail()` - it generate unique email, it is crucial since we declare in the email column of Students migrations that the email must be unique.


### C. In `DatabaseSeeder.php` Add this

```
public function run(): void
    { 
        \App\Models\Students::factory(100)->create();
    }
```


### D. Type `php artisan migrate:refresh --seed`

**Terminal:**
`php artisan migrate:refresh --seed`

![[Pasted image 20251222225403.png]]


****

## UTILIZING BOTH ROUTE, MODEL, AND CONTROLLER

**StudentController.php**
```
<?php
namespace App\Http\Controllers;

use App\Models\Students;
use App\Http\Controllers\Controller;
use Illuminate\Http\Request;

class StudentController extends Controller
{
    public function index()
    {  
        $data = Students::all();
        return view('students.index', $data);
    }
}
```

- `$data = Students::all();` - basically get all the data from students table and put it into `$data` variable. By using this we don't need to put query in the model.

- in `view('students.index');`  
	- `students` - folder name
	- `index` - file name

- `all()` - it is a eloquent function of laravel.


**students/index.blade.php**
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student</title>
</head>
<body>
    <ul>
        @foreach($students as $student)

            <li>{{ $student->first_name}} {{ $student->last_name}}</li>

        @endforeach
    </ul>
</body>
</html>
```

- The `@foreach and @endforeach` - is from laravel
- You can do either this `$student['first_name]`  or `$student->first_name` 

![[Pasted image 20251223204959.png]]

****

## RELATIONAL QUERY OR ELOQUENT FUNCTION

### `all();`
- it basically get all the data from the table

**Example syntax:**
`$data = Student::all();`




### `where();`
- When we want to get a specific data.

**Example:**
```
$data = Students::where('id', 1)->get();
```

- `id` - is a column name in students table
- `1` - is the specific id that we want
- `get()` - is a trailing function that we need to put.

![[Pasted image 20251223211036.png]]


#### Data between a letter or start with something else?

Getting the data with bert

```
$data = Students::where('fist_name', 'like', '%bert%')->get();
```

![[Pasted image 20251223211754.png]]


#### Data by Operations

Getting the students data that is age are greater than or equl to 20

```
$data = Student::where('age', '>=', 20)->get();
```


![[Pasted image 20251223212455.png]]



#### Data by Order by

```
$data = Students::where('age', '>=', 20)->orderBy('first_name', 'asc')->get();
```

![[Pasted image 20251224115718.png]]



#### Limiting data

```
$data = Students::where('age', '>=', 20)->orderBy('first_name', 'asc')->limit(5)->get();
```

![[Pasted image 20251224120020.png]]


#### Grouping the data

Counting the Male and female

```
$data = DB::table('students')->select(DB::raw('count(*) as gender_count, gender'))->groupBy('gender')->get();
```

- `DB` - it is a global database variable. When using this variable you need to import it first
	- `use Illuminate\Support\Facades\DB;`

**View**
```
<li>{{ $student->gender}} {{ $student->gender_count}}</li>
```

![[Pasted image 20251224121411.png]]


#### Exceptions

Example of using exception is avoiding request to the specific data that didn't exist in the database.

##### `firstOrFail();`
- it is same as `get()` it gets the data, but if its unavailable it returns an error code.

```
$data = Students::where('id', 26)->firstOrFail();
```

![[Pasted image 20251224123208.png]]


##### `findOrFail`
- it is use in routes

**routes.php**
```
Route::get('/students/{id}', [StudentController::class, 'show']);
```

**StudentController**
```
public function show($id)
    {
        $data = Students::findOrFail($id);
        return view('students.index', ['students' => $data]);
    }
```

**View**
```
{{students->first_name}}
```

**Route** `http://127.0.0.1:8000/students/101)`

![[Pasted image 20251224124520.png]]
Since the data didn't exist this will be the output.