# PHP Coding Guidelines
This guide would act as a standard reference which could be followed by a developer while doing the web development. It is recommended to follow these guidelines as the team sticks to common standards which could be understood and followed by every one in the team in the long run of the project.

## Influenced By

* [PHP The Right Way](http://www.phptherightway.com/)

## PHP Version
Being in a OpenSource Technology and a ever improving Platform, the team is advised to use the latest stable version which PHP Communicate recommends.

Latest Versions as of Nov 6th, 2015 are listed below:

| Technology    | Latest Version|
| ------------- |:-------------|
| PHP           | 5.6.15        |
| MySql         | 5.7           |
| Apache        | 2.4.17        |

## PHP Frameworks/CMS
Following are the frameworks currently being followed in the teams:
```The most popular in the PHP community is Laravel.```
* Laravel ```Currently Used```
* CodeIgniter
* YII
* Wordpress (Not for frameworks, but only for CMS based sites)


## Coding standards
>The developer should stick to the basic ```coding standards proposed by the framework```. If a project don't use a framework, then s/he should stick to they **PSR** standards recommended by **[PHP FIG](http://www.php-fig.org/)** group.

## Code Documentation
There two types of technical documentation which needs to be done:
1. Code Annotations
  * This code annotations should be done in all the files, classes, methods and properties.
  * The annotations should be generated into a html format using any of the following tools:
    1. [Doxygen](http://www.stack.nl/~dimitri/doxygen/index.html) ```Currently Used```
    * [phpDocumentor](http://www.phpdoc.org/)
    * [apigen](http://www.apigen.org/)
2. Inline Commenting
  * The inline commenting of codes in the complex areas of the project (For example, complex loops, calling of nested functions, important calculations, etc.)
  * Through its not recommended by professional, we required this to be done as it would be of much use if the project is handed over to a different developer.


## Database
The team could stick to any of the following:
* **Default ORM/DBA** followed by the framework.
* For the Frameworkless Project:
  1. **PDO** (PHP Data Object)
  * **Mysqli** (Object Oriented pattern is preffered)
