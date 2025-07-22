## 1. Sequential Control:
This is the default mode where statements are executed one after the other in the order they appear in the code.
```php
// Sequential Control
echo "Hello";
echo " World";
```
## 2. Selection Control (Decision Making):
This structure allows the program to make decisions and execute different code based on certain conditions.
   Examples:
- **if** statement
- **else** statement
- **else if (elif)** statement
- **switch** statement (or **case** statement in some languages)
```php
// Selection Control
$x = 10;
if ($x > 5) {
    echo "x is greater than 5";
} else {
    echo "x is less than or equal to 5";
}
```
**Ternary Operator** is a shorthand for an `if-else` statement. It takes three operands:
```php
(condition) ? value_if_true : value_if_false;
```
```php
$age = 20;
$status = ($age >= 18) ? "Adult" : "Minor";
echo $status; // Outputs: Adult
```
**Breakdown**:
- **Condition**: `$age >= 18`
- If **true** → returns `"Adult"`
- If **false** → returns `"Minor"`
## 3. Repetition Control (Loops): 
This structure allows the program to execute a block of code multiple times.
  Examples:
- **for** loop
- **while** loop
- **do-while** loop (or **repeat-until** loop in some languages)
## Loops in PHP 
```php
// Repetition Control
// for loop
for ($i = 0; $i < 5; $i++) {
    echo $i;
}

// while loop
$count = 0;
while ($count < 5) {
    echo $count;
    $count++;
}

// do-while loop
$count = 0;
do {
    echo $count;
    $count++;
} while ($count < 5);
```
### `foreach` Loops
- When we only need the **values**:
```php
$fruits = ["apple", "banana", "cherry"];

foreach ($fruits as $fruit) {
    echo $fruit . " ";
}
// Output: apple banana cherry

$person = ["name" => "John", "age" => 30, "city" => "New York"];

foreach ($person as $key => $value) {
    echo "$key: $value ";
}
// Output: name: John age: 30 city: New York 
```
### Loop Control Keywords

- `break`: Exits the loop completely
- `continue`: Skips to the next iteration

```php
for ($i = 0; $i < 5; $i++) {
    if ($i == 3) break;
    echo $i; // Output: 012
}```
These examples cover the basics of control structures in PHP, demonstrating how to manage the flow of control within a program.

See also:
- [[2. Variables & Data Types]]
- [[4. Functions and Procedures]]