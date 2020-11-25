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
```
