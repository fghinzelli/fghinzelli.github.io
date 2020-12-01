## PHP Notes

### Execute test of compatibility

 https://blog.fortrabbit.com/php-testing

 phpco -p --colors --extensions=php --runtime-set testVersion 7.4 .


### PDO

``` $pdo = new PDO('DSN:<parameteres>');
$statement = $pdo->exec('CREATE TABLE tableTest (id PRIMARY KEY, name TEXT');

$query = $pdo->query('SELECT * FROM tableTest');
$query->fetch(); // One item or item by item
$query->fetchAll(); // All itens

/* Prepared statement */

$sql = "SELECT * FROM students WHERE name = ?";
// $sql = "SELECT * FROM students WHERE name = :name";
$preparedStatement = $pdo->prepare($sql);
$preparedStatement->bindValue(1, 'MyName');
//$preparedStatement->baindValue(':name', 'MyName');
$preparedStatement->execute(); // Returns a bool value
```

### Display Errors
```
/* On php.ini */
display_errors = On

/* In Header of the file file .php */
ini_set('display_errors', 1);
error_reporting(E_ALL);
```
