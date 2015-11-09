# PHP Coding Guidelines
This guide would act as a standard reference which could be followed by a developer while doing the web development. It is recommended to follow these guidelines as the teams sticks to common standards which could be understood and followed by every one in the team in the long run of a project.



## PHP Version
Being an Open-source Technology and a ever improving Platform, the team is advised to use the latest stable version which PHP Community recommends.

Latest Versions as of Nov 9th, 2015 are listed below:

| Technology    | Latest Version|
| ------------- |:-------------|
| PHP           | 5.6.15        |
| MySql         | 5.7           |
| Apache        | 2.4.17        |

## PHP Frameworks/CMS
Following are the (Full-Stack) frameworks currently being used in the teams:
>The most popular in the PHP community is Laravel.

* Laravel `Currently Used`
* CodeIgniter
* YII

For CMS based Websites:
* Wordpress

For Web-services only (Micro Framework):
* Lumen `(Currently Used)`
* Slim

> Use [`Composer`](https://getcomposer.org/doc/00-intro.md) to update/deploy/migrate the framework library

>The framework should be kept updated to the latest security/bugfix release versions.

## Coding standards
>The developer should stick to the basic `coding standards proposed by the framework`. If a project don't use a framework, then s/he should stick to the **PSR** standards recommended by **[PHP FIG](http://www.php-fig.org/)** group.

* The code should be neatly formatted and the team works in a project should use the same Editor so that the formatting would be kept consistent throughout the project.
>Recommended Editors are:
  1. Netbeans `(Currently Used)`
  * Eclipse
  * PhpStorm

* Regarding the template pattern, the team can stick to the default template model followed by the framework. IF framework is not used, the developer may use a simple template which don't repeat the same HTML codes in different places.

* There should not be any duplicate functions/classes/in-line codes used in a project. The reusable codes needs to be move to separate entity which could be invoked from different parts of the project.

* The cron operations should not be made public. The cron file or function should not be accessible through the website link. It should be accessible only through the native PHP command line operation (CronTab, ssh access or shell script). `CronTab` needs to be used for scheduling the cron jobs.

* The data format to be shown in the interface should be in MM/DD/YYYY format.

* Always define PHP block with `<?php`

* When checking for boolean value or null, always us `===` in the if condition.

* Avoid using else whenever its not necessary
```php
if ($city == $v){
  return true;
}
return false; //There is no need to have an else condition for "return false;" statement.
```

* The password stored in the database should be hashed.
```php
//builtin hasing algorithm (uses bcrypt algorithm)
$hashedPassword = password_hash('my super cool password', PASSWORD_DEFAULT);
password_verify('the wrong password', $hashedPassword); // returns false
password_verify('my super cool password', $hashedPassword); // returns true
```


* Only the folders to which the resources are stored (say, product image, user photo, etc.), should be given the full permission.

* If payment gateway is used, proper IPN (Instant Payment Notification) like mechanism suggested by the payment gateway should be implemented.

* All data which comes inside the code should be filtered before processing it (even when it needs to be directly displayed on to the interface).

* The configuration files should not be allowed to run separately. (Follow the framework rules for the same)

* No error should be displayed in production. But error logging should be enabled.
```php
display_errors = Off
display_startup_errors = Off
error_reporting = E_ALL
log_errors = On
```

* All types of error display (even notices) needs to be fixed in the code (No suppressing of error/notice are allowed)

* In the production environment, the unexpected behaviors should be redirected to a static page (say, 404 page, permission denied page, unexpected error page, etc.)

## Performance Optimization
* Don't use the insert query in a loop. Combine the values using the loop and execute all in a single query.

```php
//Wrong way
foreach(...){
    //Query execution here: INSERT INTO users (first_name,last_name) VALUES("John", "Doe");
}

//Right way
//Query execution like this: INSERT INTO users (first_name,last_name) VALUES("John", "Doe"),("Jane", "Doe"),("Tom", "Doe");
```

* Don't copy the variables unnecessarily. Don't assign value to the variable unless its much required.

```php
//Wrong way
$var = true;
return $var;

//Right way
return true;
```
* Minify the css files and js files in production

## Code Documentation
There two types of technical documentation which needs to be done:
* Code Annotations
  * The code annotations should be done in all the files, classes, methods and properties. Below is just a sample:
  ```php
  /**
     * @name <function-class-name>
     * @desciption <description-of-the-function-or-class>
     * @param <parameter-type> <parameter> <parameter-description>
     *
     * @return <return-type> <return-data-description>
     */
     ```
  * The annotations should be generated into a HTML format using any of the following tools:
    1. [Doxygen](http://www.stack.nl/~dimitri/doxygen/index.html) `(Currently Used)`
    * [PhpDocumentor](http://www.phpdoc.org/)
    * [Apigen](http://www.apigen.org/)


* In-line Commenting
  * The in-line commenting of codes needs to be done in the complex areas of the project (For example, complex loops, calling of nested functions, important calculations, etc.)
  * Though this is not recommended by professionals, we require this to be done as it would be of much use if the project is handed over to different developers in the long run.


* Sandbox for Web-services
    * [Swagger](http://swagger.io/open-source-integrations/) is the tool which we are using to create the documentation and sandbox feature for the app developers in order for them to check and understand the web-services.

## Database
The team should stick to any of the following:
* **Default ORM/DBA** followed by the framework.

* For the Framework-less Project:
  1. **PDO** (PHP Data Object)
  * **Mysqli** (Object Oriented pattern is preffered)


* Stored Procedure should be used when multiple query operations are to be done in a single transaction which could decrease the traffic between the Apache and Mysql servers.

* The default character set of the text fields/table should be utf8_general_ci

* Innodb should be the database storage engine

* Make sure the DBA/ORM of you framework handles the SQL Injection wisely.

## Website Hosting
The developer should make sure s/he understand what s/he is doing in the hosting server provided by the client.

Few Hosting Services that could be suggested to the clients are:
* AWS `(Much preffered)`
* Rackspace
* Hostgator
* Godaddy

Linux (Cenos or Ubuntu), Apache, Mysql and PHP combination is  much preferred. If client wishes, Apache could be replace by Nginx Web Server.

If there are some tasks which would require more time to execute (say, uploading a big video/image or calling an external api in a loop), then that particular piece of function needs to be invoked to run in the background.

The developer must ensure the following from the client in the beginning of the project:
* The web-services URL needs to be encrypted or not (https:)
* Hosting Details and access
* Suggestions from client on the Framework to be used (If the client is technical)
* The type of design required (Normal, Responsive, Adaptive)
* Number of interface language to be used (By default: English only)

## Reference:-
* [PHP The Right Way](http://www.phptherightway.com/)
* [PHP.net](http://php.net/)
* [Swagger](http://swagger.io/)
* [Composer](https://getcomposer.org/)


https://github.com/bbeniston/php-coding/blob/master/coding-guidelines.md
