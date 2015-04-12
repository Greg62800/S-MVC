# S-MVC
**A simple and personalizable PHP MVC framwork**
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
			echo('You are on the name Controller, calling the index method. Well Done!');
		}

	}
```
Then if you go to *yoursite.com/name/* this message will appear!

##### Passing parameters :
In your methods you can specify the parameters you want :
```php
<?php
	namespace App\Controller;

	class nameController extends appController{

		public function index($param = null){
			$param = is_null($param) ? '' : $param;
			echo('You are on the name Controller, calling the index method. Well Done! Param : ' . $param);
		}

	}
```
**Put all your arguments with a default value because user can go to an url without passing parameters in this one!!!**

##### Rendering a view (with parameters):
Quiet simple!

Create a file in *App/View*. E.g :
```php
<h1>Index view</h1>
<p>Today the message is : <?= $message ?></p>
```
In your controller :
```php
<?php
	namespace App\Controller;

	class nameController extends appController{

		public function index(){
			//Same variable name as in the view file
			$message = 'You are on the name Controller, calling the index method. Well Done!';
		
			//See documentation for compact function ;)
			$this->render('index', compact('message'));
		}

	}
```

