# SQL Style Guide

The purpose of this style guide is to outline the programming style and formatting preferred for SQL programs.

There are various existing SQL style guides that have been drawn on in making this guide, including:

- [SQL Style Guide](https://www.sqlstyle.guide/)
- [Mozilla SQL Style Guide](https://docs.telemetry.mozilla.org/concepts/sql_style.html)

## 1) Files & Coding Structure
- Files must use the UTF-8 character set encoding
- All files must end with a single empty line
- Filenames should be saved as ```camelCase.sql```

## 2) Spacing & Line ending
- SQL code must be indented by 2 spaces for each indent level
- Each SQL statement should end with a semi-colon ```;```
- There should be no trailing whitespace at the end of lines
- Opening and Closing brackets should be tight to their contents and not have additional spaces within the brackets, e.g. ```FOREIGN KEY (`UserID`) ```
- Spaces and new lines should be used to align code to improve read-ability, with each main keyword starting a new line
- Use double-dash for single-line comments, e.g. ```-- Comment``` and ```/* ... */``` for multi-line comments

## 3) Operators
- Put a space before and after all operators, e.g. ```WHERE `UserID` = '1' ```
- For Logical operators, use the words ```AND``` and ```OR```
- For negation, use the word ```NOT```

## 4) Naming and Declaring
- All SQL keywords must be in UPPER case, e.g, ```SELECT```
- All Data-types must be in UPPER case, e.g. ```VARCHAR```
- Boolan values ```TRUE``` and ```FALSE```, as well as ```NULL``` should all be in UPPER case
- Database and Table names should be in lower_case_separated_by_underscores
- Field names, indexes, events and stored routines should be in PascalCase. This is prefered to differentiate SQL fields from PHP/JS variables usually written in camelCase.
- Enclose database, table and field names in back-ticks, e.g. ```SELECT `users`.`UserID` AS `ID`...```
- Tables and Views should generally be plural, with Fields being singular
- For any primary key ID field, include the table name in the field name, e.g. ```users.UserID```. For all other fields avoid using the table name as the prefix to the field name, e.g. ```users.Address``` instead of ```users.UserAddress```
- Strings should be declared using single-quotes
- Numeric values and NULL should NOT be enclosed in quotes
- Use data-type ```TINYINT(1)``` for status fields, and follow them with a ```COMMENT '0=Inactive, 1=Active'``` detailing the relevant status code settings

## 5) Table and View Creation
- Use the following format and layout for creating tables in a SQL file:
```sql
CREATE TABLE IF NOT EXISTS `users` (
  `UserID` INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `Username` VARCHAR(40) NOT NULL UNIQUE,
  `RecordStatus` TINYINT(1) NOT NULL DEFAULT 1 COMMENT '0=Inactive, 1=Active'
);
```
- If a SQL query with JOIN's is used regularly then create this as VIEW, e.g.:
```sql
CREATE VIEW IF NOT EXISTS `messages_view` AS SELECT
  `messages`.`MessageID` AS `MessageID`,
  `messages`.`SenderID` AS `SenderID`,
  `users`.`username` AS `SenderName`,
  FROM `messages`
  LEFT JOIN `users` ON `users`.`UserID` = `messages`.`SenderID`;
```

## 6) Select, Insert and Update SQL commands in PHP
- Use the PHP PDO Class for connecting by PHP to the SQL Server and retrieving/updating data
- Create a ```$sql``` variable with the relevant SQL commands and then use the PDO methods to execute this on the server
- An example SELECT SQL statement would be:
```sql
$sql = "SELECT *
        FROM `books`
        WHERE `BookID` = '{$bookID}'";
```
- An example INSERT SQL statement would be:
```sql
$sql = "INSERT INTO `books` (`Title`, `Author`)
        VALUES ('{$title}', '{$author}')";
```
- An example UPDATE SQL statement would be:
```sql
$sql = "UPDATE `books`
        SET `RecordStatus` = '{$recordStatus}'
        WHERE `BookID` = '{$bookID}'";
```
