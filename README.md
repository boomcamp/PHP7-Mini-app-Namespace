# Introduction
For your PHP 7 activity you need to set up a `psr-4` compliant to autoload class and implement `use` declaration and class `namespacing`

### The initial Set-Up

* Step 1.) Create `BoomCamp/composer.json` file this will be the base setup of our `class autoloader`.

```
{
    "name": "BoomCamp autoloader Demo",
    "description": "An example demonstration of namespacing with class autoloader",
    "autoload": {
        "psr-4": { 
            "Classes\\" : "classes/"
        }
    }
}
```

* Step 2.) Create the `BoomCamp/bootstrap.php` file it will load the generated `vendor/` folder to be used by the application.

```
<?php
define('ROOT', __DIR__ . DIRECTORY_SEPARATOR);
define('VENDOR', ROOT . 'vendor' . DIRECTORY_SEPARATOR);
require VENDOR . 'autoload.php';
?>
```

* Step 3.) Create the `BoomCamp/classes/Mentors.php` example class to return an example output.

```
<?php 
namespace Classes;

class Mentors {
    private $mentor;
    public function __construct($mentor) {
        $this->mentor = $mentor;
    }

    public function getMentor() : String {
        return $this->mentor;
    }
}
```

* Step 4.) Create `BoomCamp/index.php` page file this is the main landing page of the application.

```
<?php
require __DIR__ .'/bootstrap.php';

use Classes\Mentors;
$mentor = new Mentors("Jino Lacson");
echo $mentor->getMentor();
?>
```

* Step 5.) Run `composer install` to install `psr-4` and other related dependencies.

* Step 6. ) Open up terminal and start your `xampp` server, type `php index.php` you should now have "Jino Lacson" as the result.

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php
Jino Lacson
```

# Requirements

Your main task is to implement object oriented design with the new PHP 7 syntax in this application.

1.) Usage of PDO connection class [singleton pattern](https://phpenthusiast.com/blog/the-singleton-design-pattern-in-php) to connect `one connection instance` for Students, Instructor and Course objects.

2.) Usage of dependency injection.

Example Snippet:

```
<?php

interface IDB {
	//Your implementation
}

class Database implements IDB {
	//Your implementation for connection
} 

class Instructor 
{
    private $instance = null;

    public function __construct(Database $instance) {
        $this->instance = $instance;
    }

}

$instance = new Database('localhost', 'root', '', 'namespace_db');
$user = new Instructor($instance);

//Ensure to close any open connections after transactions
?>
```

3.) Implementation of CRUD functionalities for every namespace class.

* Students

* Instructor

* Course

6.) [Arguments](https://alvinalexander.com/php/php-read-command-line-arguments-in-php) should be readable in terminal.

Example output for `Instructor` object:

Insert:

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php instructor insert Jino Lacson 
Created    : Jino Lacson was created...
```

Display:

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php instructor display
Lists    : 
1.) Jino Lacson
2.) Aodhan Hayter
3.) Greg Doermann
```

Update :

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php instructor update 1 JINO LACSON 
Updated    : JINO LACSON was updated...
```

Delete :

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php instructor delete 1 
Deleted    : JINO LACSON was deleted...
```

7.) Should also have a way to interact using HTML forms for CRUD operations.

8.) Responsive layouts is bonus.

# Finished

Submit a link to your fork of this repository to the Google Classroom assignment related to this project, Goodluck!.
