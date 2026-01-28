## Function in PHP
PHP provides us with two major types of functions:

---
### User Defined Function: 
To define a function in PHP, use the `function` keyword followed by the function name, parentheses (which may include parameters), and curly braces containing the function body.
```php
function functionName($parameter1, $parameter2) {
    // Function body
    return $parameter1 + $parameter2;
}
```

###### Function with Parameters and Default Values:
 - The `greet` function takes one parameter with a default value and returns a greeting string
```php
// Function with Parameters and Default Values
function greet($name = "Guest") {
    return "Hello, $name";
}

echo greet("Alice"); // Outputs: Hello, Alice
echo greet(); // Outputs: Hello, Guest
```

###### Function with Multiple Parameters:
- The `add` function takes two parameters and returns their sum.
```php
// Function with Multiple Parameters
function add($a, $b) {
    return $a + $b;
}

$result = add(10, 20);
echo $result; // Outputs: 30
```

###### Function with Array Parameter:
- The `printFruits` function takes an array as a parameter and prints each element.
```php
// Function with Array Parameter
function printFruits($fruits) {
    foreach ($fruits as $fruit) {
        echo $fruit . " ";
    }
}

$fruits = array("Apple", "Banana", "Mango");
printFruits($fruits); // Outputs: Apple Banana Mango 
```

###### Anonymous Functions (Closures):
Closures (anonymous functions) are useful when we want to create inline logic that doesn’t need a named function.
- The `ages` variable holds an anonymous function that returns even only the adults (18+).
```php
// Anonymous Functions (Closures)
$ages = [12, 17, 18, 20, 15, 30];

$adults = array_filter($ages, function($age) {
    return $age >= 18; // Keep only ages 18 or older
});

print_r($adults); //  Array([2]=>18 [3]=>20 [5]=>30);
```

###### Callback Functions:
- The `applyFunction` function takes a value and a callback function as parameters and applies the callback to the value. The `square` function is used as a callback to square the number.
```php
function applyFunction($value, $function) {
    return $function($value);
}

$square = function($x) {
    return $x * $x;
};

echo applyFunction(4, $square); // Outputs: 16
```
*Why use callbacks?*
Callbacks allow us to pass one function to another — commonly used in functional programming and array operations.
###### Variadic Function:
- The `worldCountryList` function can take indefinite number of arguments using `...` spread operator
```php
function worldCountryList(...$country) {
	print_r($country);
}

worldCountryList("Bangladesh", "Iran", "Turkey", "Malaysia"); // Return an array
```
### Built-in Functions:
Check [[06-Standard-Libraries]]

See also:
→ Next: [[03-Control-Structures]]
← Back: [[05-Arrays-and-Data-Structures]]