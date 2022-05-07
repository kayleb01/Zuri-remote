# Pass a pointer from A to B

```

function A(&$string)
{
    echo $string;
}
 function B(&$string)
 {
    echo A($string);
 }
 
$str = "Pointers";
 echo B($str);

```