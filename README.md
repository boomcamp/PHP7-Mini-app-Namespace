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

* Step 6. ) Start your `xampp` server and navigate to `http://localhost/BoomCamp` you should now have "Jino Lacson" as a result.

**Console Output**

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ composer install
Loading composer repositories with package information
Updating dependencies (including require-dev)
Nothing to install or update
Generating autoload files
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php
Jino Lacson
```

# Requirements

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

class Student 
{
    private $instance = null;

    public function __construct(Database $instance) {
        $this->instance = $instance;
    }

    public function addStudent(string $student) {
        return $this->instance->save('YOUR QUERY');
    }

    public function getStudent() : string{
       return $this->instance->get('YOUR QUERY');
    }
}

$instance = new Database('localhost', 'root', '', 'namespace_db');
$user = new Student($instance);
$user->addStudent("Gino Aquino");
$user->getStudent(); //Gino Aquino

?>
```

3.) Implement **5 calling functions** for every namespace class

* Students Object

* Instructor Object

* Course Object

4.) Inside `BoomCamp/index.php` instantiate your created objects

5.) Create your basic PDO `crud` operations for every class objects, [arguments](https://alvinalexander.com/php/php-read-command-line-arguments-in-php) should be readable in terminal.

Example Insert for instructor class:

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php insert Jino Lacson 
Created    : Jino Lacson was created...
```

Example Update for instructor class:

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php update 1 JINO LACSON 
Updated    : JINO LACSON was updated...
```

Example Delete for instructor class:

```
dev@jino:/opt/lampp/htdocs/BoomCamp$ php index.php delete 1 
Deleted    : JINO LACSON was deleted...
```

Finished : Submit a link of the source code to the Google Classroom assignment related to this project.
