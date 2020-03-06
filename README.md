# PHP7-Mini-app-Namespace.
For your PHP 7 activity you need to set up a `psr-4` autoloader class and implement `use` declaration and class `namespacing`

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


1.) Implement **5 calling functions** for every namespace class

* Students Object

* Instructor Object

* Course Object

2.) Inside `BoomCamp/index.php` instantiate your created objects


Finished : Submit a link of the source code to the Google Classroom assignment related to this project.
