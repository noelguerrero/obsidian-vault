
**Laravel Prerequisites**
- PHP Programming
- MVC 
- HTML and CSS
- Composer (we need to install it)
- Xampp


## SETTING UP

### A. Installing Composer

- you can download it in `getcomposer.org`
- Then install

**Composer**
- Application dependency manager - It get the dependencies and libraries that we need in our laravel.
- Example: it will get a php version from the google that match on the laravel that we use. And also it will not only work on the laravel but the other framework like CodeIgniter and etc...

**Note: your php version must be PHP v8 because it is the minimum require in the laravel**. You can see the php version in xampp, in the admin of apache. Some other dev download separate PHP

**Note: Before you configure the configuration you must into the specific folder where you create laravel projects to make it clean**

**Im create a folder here**`\c\projects\laravel`

**Commands**
`cd ..` back 
`cd foldername` go to specific folder

**After the installation you must open the terminal and type this**
```
php --version
```
![[Pasted image 20251111103330.png]]

then
```
composer
```
![[Pasted image 20251111103411.png]]


### B. Installing Laravel CLI
- in the same terminal type: `composer global require laravel/installer`
![[Pasted image 20251111105109.png]]

****


## Laravel Commands

### Creating Laravel
on the terminal
Syntax: `laravel new projectname`

Example: `laravel new laravel-practice`


### Open the folder into VScode
syntax: `code ..`


### Run our laravel project
On the terminal of IDE type this: `php artisan serve`
then crl+click the address in the terminal
![[Pasted image 20251114104651.png]]

### Used `composer install` if there is no composer.lock
Syntax: `composer install`

### Error encounter
![[Pasted image 20251111113238.png]]
You can type this: `composer install` to fix it

But if this will show up it means you php cannot run in CLI mode
![[Pasted image 20251111113631.png]]

**So to fix that**
- go to the php ini file on the folder
![[Pasted image 20251111113829.png]]

- find the extention
![[Pasted image 20251111114038.png]]

- Add this and save
![[Pasted image 20251111114327.png]]


### `Connecting database`
To connect the database from laravel just configure this part of the `.env` file base on your details.
![[Pasted image 20251114113944.png]]

Then on the terminal:
```
php artisan migrate
```
It automatically creates necessary tables for your project