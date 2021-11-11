### Predefined Functions :
```php
the difference between
__FUNCTION__ and __METHOD__ as in PHP 5.0.4 is that

__FUNCTION__ returns only the name of the function

while as __METHOD__ returns the name of the class alongwith the name of the function

class trick
{
      function doit()
      {
                echo __FUNCTION__;
      }
      function doitagain()
      {
                echo __METHOD__;
      }
}
$obj=new trick();
$obj->doit();
output will be ----  doit
$obj->doitagain();
output will be ----- trick::doitagain

```
### Differnt Betweeen __CLASS__ magic constant the get_class() function.
```php
The __CLASS__ magic constant nicely complements the get_class() function.
Sometimes you need to know both:
- name of the inherited class
- name of the class actually executed

Here's an example that shows the possible solution:

<?php

class base_class
{
    function say_a()
    {
        echo "'a' - said the " . __CLASS__ . "<br/>";
    }

    function say_b()
    {
        echo "'b' - said the " . get_class($this) . "<br/>";
    }

}

class derived_class extends base_class
{
    function say_a()
    {
        parent::say_a();
        echo "'a' - said the " . __CLASS__ . "<br/>";
    }

    function say_b()
    {
        parent::say_b();
        echo "'b' - said the " . get_class($this) . "<br/>";
    }
}

$obj_b = new derived_class();

$obj_b->say_a();
echo "<br/>";
$obj_b->say_b();

?>

The output should look roughly like this:

'a' - said the base_class
'a' - said the derived_class

'b' - said the derived_class
'b' - said the derived_class
```
