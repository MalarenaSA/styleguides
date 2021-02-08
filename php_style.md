# PHP Style Guide

The purpose of this style guide is to outline the programming style and formatting preferred for PHP programs.

There are various existing PHP style guides that have been drawn on in making this guide, including:

- [PHP Framework Interop Group's PSR-12](https://www.php-fig.org/psr/psr-12/)
- [Drupal Coding Standards](https://www.drupal.org/docs/develop/standards/coding-standards)
- [CodeIgniter4 Style Guide](https://github.com/codeigniter4/CodeIgniter4/blob/develop/contributing/styleguide.rst)
- [MIT Sloan PHP Code Style Guide](https://mitsloan.mit.edu/shared/content/PHP_Code_Style_Guide.php)

## 1) Files & Coding Structure
- Files must use the UTF-8 character set encoding and must use the UNIX LF (linefeed) line ending (this should also be set in the ```.gitattributes``` file)
- PHP Elements (Tags) should either be ```<?php  ?> ``` or the short-echo ```<?=  ?>```
- When the opening ```<?php``` tag is on the first line of a file it must be on its own line with nothing else included on that line. This should be followed by a line with the ```declare(strict_types=1)``` declaration
- All PHP ```namespace``` and ```use``` declarations, and other class ```require``` and ```include``` statements should be placed at the top of the PHP file, even for files containing a mix of HTML and PHP
- Anywhere you are unconditionally including a class file, use ```require_once ""```. Anywhere you are conditionally including a class file, use ```include_once""```
- Process any GET data, and clear using ```$_GET = [];```, then process any POST data, and clear using ```$_POST = [];``` (and the same with ```$_FILES = []``` if used)
- Line lengths should generally be no longer than 80 characters, but lines containing function names, class definitions, variable declarations, etc. can exceed 80 characters if they are simple to read and understand
- Comments should generally be included BEFORE the code they are explaining. For in-line comments, include 2 spaces after the code and before the comment. For files, functions and classes include detailed DocBlock comments
- For files containing just PHP code, or ending in PHP mode, the closing ```?>``` should be omitted
- All files must end with a single empty line
- Filenames should be saved as ```camelCase.php```

## 2) Spacing & Line ending
- PHP code must be indented by 2 spaces for each indent level, including code that is imbedded within HTML
- When including ```<?php  ?>``` in HTML, ensure the ```<?php``` opening element is positioned on the same line as the previous closing HTML ```</...>``` element, to avoid extra whitespace being output
- Each PHP statement should end with a semi-colon ```;``` although when using the short-echo format semi-colons are not required
- There should be no trailing whitespace at the end of lines
- Opening and Closing brackets should be tight to their contents and not have additional spaces within the brackets, e.g. ```($a = $b)```
- Spaces and new lines should be used to align blocks of code, array definitions or long string concatenations to improve code read-ability

## 3) Operators
- Unary operators should not have spaces between the operator and operand, e.g. ```$i++```
- Binary operators should have a space before and after the operator, e.g. ```$variable = ($a + $b) * $c;```. This includes the concatenation operator, e.g. ```$string = "Hello " . "World";```
- For Ternary operators, it is preferable to keep the "if" part in brackets, e.g. ```$variable = ($expr) ? "Yes" : "No";```
- For Logical operators, use the symbol versions ```&&``` and ```||``` instead of ```AND``` and ```OR```
- The Logical negation operator should not be separated from its argument with a space, e.g. ```!$empty()``` or ```!=```

## 4) Naming and Declaring
- All PHP keywords must be in lower case
- The keywords ```require ""```, ```require_once ""```, ```include ""``` and ```include_once ""``` are all statements and must be followed by quotes and not brackets
- Boolean values ```true``` and ```false```, as well as ```null``` should all be in lower case
- Class names and namespaces should be declared in PascalCase
- Class methods should be declared in camelCase and must have visibility declarations (e.g. ```private```, ```protected``` or ```public```)
- When instantiating a new class, parentheses must always be present even when there are no arguments passed to the constructor, e.g. ```$variable = new Model();```
- Functions and Variables should be declared in camelCase
- Constants should be declared in CAPITALS_SEPARATED_BY_UNDERSCORES
- Strings should be declared using double-quotes, e.g. ```$string = "Hello World";```
- Variables used within strings should be included within curly brackets, e.g. ```echo "Result: {$result}";```. Use the concatenation operator for more complex strings that include functions, e.g. ```$completed = "Completed on: " . $date("Y-m-d") . " by: " . $user;```
- Arrays should be declared using square brackets, with commas between each item, and with the final item including a trailing comma, e.g. ```$array = [item1, item2,];```. For associative arrays, there should be spacing around the ```=>``` key association operator, e.g. ```$array = [$key => $value,]```. For large arrays, each item or key/value pair should be on a separate line

## 5) Functions and Class Methods
- The format (including spacing and braces) of declaring functions should be:
```php
function myFunction(arg1, arg2 = null) {
  // code;
}
```
- The format (including spacing and braces) of declaring class methods should be:
```php  
class ClassName {
  public function myFunction($arg1, $arg2 = null){
    // code;
  }
}
```
- When making a method or function call there should not be a space between the method or function name and the opening bracket, e.g. ```myFunction("test");``` or ```ClassName->myFunction("test");```
- All functions and methods should be commented with a DocBlock comment which describes the purpose, parameters and return values

## 6) Control Structures
- The format (including spacing and braces) of control structures should be:
```php  
if ($expr) {
  // code;
} else {
  // code;
}
```
- This format should be used even when there is only 1 action from an ```if``` statement
- A ```for``` statement would start: ```for ($i = 0; $i <  10; $i++) {```
- A ```foreach``` statement would start: ```foreach ($iterable as $key => $value) {```
- The keyword ```elseif``` should be used instead of two separate keywords ```else if```
- When imbedding control structures within HTML the alternative syntax of ```if () :```, ```elseif() :```, ```else :```, ```endif;``` / ```for () :```, ```endfor;``` / ```foreach () :```, ```endforeach;``` etc. should be used (with a space between the end bracket and colon) in order to avoid confusion with where to place opening and closing curly brackets
