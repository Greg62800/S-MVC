# S-MVC
**A simple and personalizable PHP MVC framwork**
### Usage
To start a website you only need to create some files in *App* directory and change config file in *Config* directory. You can also put your css, js in *Public* directory.

##### URLs :
URLs are built with this pattern : *yoursite.com/controller/method/param2/param2/param3* ...
  
e.g : *yoursite.com/post/listen/12* will create a *post* controller object and call *listen* method with an argument : *12*

##### Creating a new page :
To create a new page go to the *App/Controller* directory and create a new file called *nameController.php* where *name* is the name of your controller.

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

##### Rendering a view (with parameters) :
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

##### Using models :
Models file are in *App/Model* and must be called with *Model* at the end. E.g : *postModel.php*

The basic model structure is :
```php
<?php
	namespace App\Model;

	class nameModel{

		//Just a function for exemple purposes, create your own. Models are the part of website that retrieve data
		public function get(){
			return 'I am fine!!!!!!!';
		}

	}
```

For exemple, this model is called *nameModel.php*

Now, in your controller you can load models with *loadModel* method :
```php
<?php
	namespace App\Controller;

	class nameController extends appController{

		public function index(){
			// Will create $this->name variable automatically
			$this->loadModel('name');
			
			//Same variable name as in the view file
			$message = $this->name->get();
		
			//See documentation for compact function ;)
			$this->render('index', compact('message'));
		}

	}
```

Easy right?

##### Adding an html template :
Just modify the *default.php* file in *App/View/Template* and make your own template! Put the content with this line of code :
```php
<div id="content">
	<!-- Content generated by the framework wich add the view file into the div, don't worry ;) -->
	<?= $content ?>
</div>
```

##### More possibilities coming soon!

###Support
Email me at hugopb82@gmail.com

Follow me on twitter at https://twitter.com/hugopb82

I'm not a professionnal developper, I made it for fun but it was hard and long to do this framework. Download the source code with this link and watch an ad for 5 seconds to help me : http://adf.ly/4694918/s-mvc

You can also , if you want really help me, make a donation on paypal : https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=DYEEWGNMNZMCJ

###Copyright and License
This software is Copyright (c) 2015 by hugopb82

This is free software, licensed under the MIT License.
