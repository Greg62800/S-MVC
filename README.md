# S-MVC
** A simple and personalizable PHP MVC framwork **
### Usage :
To start a website you only need to create some files in *App* directory and change config file in *Config* directory. You can also put your css, js in *Public* directory.

##### URLs :
URLs are built with this pattern : *yoursite.com/controller/method/param2/param2/param3* ...
  
e.g : *yoursite.com/post/listen/12* will create a *post* controller object and call *listen* method with an argument : *12*

##### Creating a new page :
To create a new page go to the *App/COntroller* directory and create a new file called *nameController.php* where *name* is the name of your controller.

The basic structure for a controller is :
```php
<?php
	namespace App\Controller;

	class nameController extends appController{

		public function index(){
			echo('You're on the name Controller, calling the index method. Well Done!');
		}

	}
```
