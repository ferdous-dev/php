
**Quick Recap**
- `$variable`: Defines a variable
- `if`, `else`: Conditional logic
- `for`, `foreach`: Looping
- `function`: Define reusable code
- `array`, `associative array`: Data collections
- `class`, `object`: OOP basics
- `try-catch`: Error handling
---
## Here’s a basic overview of PHP's structure and key components:

```php
<?php
/*
|--------------------------------------------------------------------------
| 1. VARIABLES
|--------------------------------------------------------------------------
| Variables store data we want to use later.
*/

$age = 20;                 // Integer
$height = 5.9;             // Float
$name = "Alice";           // String
$isStudent = true;         // Boolean

/*
|--------------------------------------------------------------------------
| 2. CONDITIONAL STATEMENT
|--------------------------------------------------------------------------
| Used to make decisions.
*/

if ($age >= 18) {
    echo "You are an adult.";
} else {
    echo "You are a minor.";
}

/*
|--------------------------------------------------------------------------
| 3. LOOP
|--------------------------------------------------------------------------
| Repeats code multiple times.
*/

for ($i = 1; $i <= 3; $i++) {
    echo "Loop number: $i\n";
}


/*
|--------------------------------------------------------------------------
| 4. FUNCTION
|--------------------------------------------------------------------------
| A reusable block of code.
*/

function add($a, $b) {
    return $a + $b;
}

$result = add(5, 7);
echo $result . "\n";

/*
|--------------------------------------------------------------------------
| 5. ARRAYS
|--------------------------------------------------------------------------
| Used to store multiple values.
*/

$fruits = ["Apple", "Banana", "Cherry"];

foreach ($fruits as $fruit) {
    echo $fruit . "\n";
}

/*
|--------------------------------------------------------------------------
| 6. ASSOCIATIVE ARRAY
|--------------------------------------------------------------------------
| Uses keys instead of numbers.
*/

$user = [
    "name" => "Alice",
    "age"  => 30
];

foreach ($user as $key => $value) {
    echo "$key: $value\n";
}

/*
|--------------------------------------------------------------------------
| 7. CLASS (OBJECT-ORIENTED PHP)
|--------------------------------------------------------------------------
| A blueprint for creating objects.
*/

class Person {
	// private means these properties cannot be accessed directly from outside the class
    private $name;
    private $age;

    public function __construct($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }

    public function greet() {
        echo "Hello, my name is {$this->name} and I am {$this->age} years old";
    }
}

$alice = new Person("Alice", 30);
$alice->greet();

/*
|--------------------------------------------------------------------------
| 8. ERROR HANDLING
|--------------------------------------------------------------------------
| Prevents crashes when something goes wrong.
*/

try {
    if ($age < 0) {
        throw new Exception("Age cannot be negative.");
    }
} catch (Exception $error) {
    echo $error->getMessage();
}
?>

```

This example covers the essential components of PHP, providing a solid foundation for understanding its basic structure and functionality.