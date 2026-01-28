## **Built-in Functions:** 
Predefined functions provided by the language for common tasks (e.g., input/output operations, mathematical computations).
### 1. String Functions(Most Used):
**String concatenation**
```php
$firstName = "Ferdous";
$lastName  = "Ahmed";

// Dot operator
$fullName = $firstName . " " . $lastName; // Output: Ferdous Ahmed

// Variable interpolation (double quotes only)
$date    = "29th July";
$expense = "1580 Taka";
$result  = "On {$date}, total expense = {$expense}";
//output: On 29th July, total expense = 1580 Taka

echo $fullName;
echo $result;
```
📌 **Note:** Variable interpolation works **only with double quotes**, not single quotes.

---
**`strlen()`**: returns the length of a string.
```php
$string = "Hello, world!";
echo strlen($string); // Output: 13
```

**`substr()`**: returns part of a string.
```php
$string = "Ferdous, Ahmed!";
$substring = substr($string, 8, 5); // start at index 8, take 5 characters
echo $substring; // Output: Ahmed
```

**`strpos()`**: Finds the position of the first occurrence of a substring in a string.
```php
$string = "Ferdous Ahmed";
$position = strpos($string, "Ahmed");
echo $position; // Output: 8
```
⚠️ **Important: Always use strict comparison**
```php
if (strpos($string, "Ahmed") !== false) {
    // found
}
```
📌 Reason: `strpos()` can return `0`, which is `false` in loose comparison.

---
**Case Conversion**

```php
$string = "ferdous ahmed";

echo strtoupper($string); // FERDOUS AHMED
echo strtolower($string); // ferdous ahmed
echo ucfirst($string);    // Ferdous ahmed
echo ucwords($string);    // Ferdous Ahmed
```
---
**`trim()`**: Strips whitespace (or other characters) from the beginning and end of a string.
```php
$string = "   Hello, world!   ";
$trimmedString = trim($string);
echo $trimmedString; // Output: Hello, world!
```
**Related:** 
```php
ltrim(); // left side
rtrim(); // right side
```

---
**`explode()` / `implode()`**
```php
$string = "apple,banana,orange";
$array  = explode(",", $string);

echo implode(", ", $array); // apple, banana, orange
```
📌 Think:
- `explode()` → string ➜ array
- `implode()` → array ➜ string

---

**`str_replace`**: Replaces all occurrences of a search string with a replacement string.
```php
$wrongName = "Ferdous  Ahmed..";
$fixedName = str_replace(["  ",".."], [" ", "."], $wrongName);
echo $fixedName; // Output: Ferdous Ahmed.
```

---
**`Less Common(Keep for reference)`**
```php
strrev($string);        // Reverse string
str_repeat("*-", 5);   // *-*-*-*-*-
str_shuffle($string);  // Random shuffle
```
### 2. Variable & Debugging Functions (Very Important)

```php
$name = "Ferdous";

gettype($name);   // string
var_dump($name);  // type + value (best for debugging)
print_r($name);   // human-readable

```
**Type Checking**

**`print_r`** and **`var_dump`** :  Print the whole variable
```php
is_string($name); // true
isset($name);     // true (variable exists and not null)
empty($name);     // false
```
📌 **Tip:**
- `var_dump()` → developers
- `print_r()` → quick inspection
##### Note
- Strings are **byte-addressable** like arrays:
```php
$name = "Ferdous";
echo $name[0]; // F
```
- String positions are called **offsets**
- Full reference: [https://www.php.net/manual/en/ref.strings.php](https://www.php.net/manual/en/ref.strings.php)
### 3. Mathematical Functions:

**rand()**: Generates a random integer.
```php
$dice = rand(1, 6);
echo "You rolled: " . $dice;
```
💡 **Modern PHP prefers**
```php
random_int(1, 6); // Cryptographically secure
```
### 4. Array Functions(High Priority)

**Sorting Arrays**
```php
sort($numbers);   // Ascending (indexed array)
rsort($numbers);  // Descending

$person = ["name" => "John", "age" => 30, "city" => "New York"];
asort($person);  // Sorts associative array by values
ksort($person);  // Sorts associative array by keys
```

---

**Array Search**
```php
$numbers = [1, 2, 3, 4, 5];
$key = array_search(3, $numbers);
echo $key;  // output: 2 (PHP finds it at index 2)

in_array(3, [1, 2, 3]);       // output: true

$person = ["name" => "John", "age" => 30, "city" => "New York"];
if (array_key_exists("age", $person)) {
    echo "Age is " . $person["age"];  // output: Age is 30
}
```
**Merging Arrays**
```php
array_merge([1, 2], [3, 4]); // [1,2,3,4]
```
Must-Know Advanced Array Functions 🔥
```php
array_map();
array_filter();
array_reduce();
```
📌 **Very important for real-world PHP**

---
**JSON encoding/decoding** as a common way to serialize PHP arrays:
```php
$arr = ["name" => "John", "age" => 30];
echo json_encode($arr); // Output: {"name":"John","age":30}

$data = json_decode($json, true); // true = associative array
```

---
**Quick Array Reference**
- `array_push()` – Add to end
- `array_pop()` – Remove from end
- `array_shift()` – Remove from beginning
- `array_merge()` – Combine arrays
- `array_search()` – Find a value's key
- `sort()`, `rsort()` – Sort indexed arrays
- `ksort()`, `asort()` – Sort associative arrays
### 5. Date and Time Functions

**`date()`**
```php
echo date("Y-m-d H:i:s");
```
Common format characters:
```ini
Y = year
m = month
d = day
H = hour
i = minute
s = second
```
### 6. File System Functions(Core Basics)

```php
file_exists("data.txt");

$file = fopen("data.txt", "w");
fwrite($file, "Hello PHP");
fclose($file);
```
📌 Always close files to avoid memory issues.
### 7. Database Functions
**`mysqli_connect()`**
```php
$conn = mysqli_connect("localhost", "user", "password", "database");
```
⚠️ **Real projects should use**
- Prepared statements
- PDO (recommended)
### Modules/Packages(Extensions)
Collections of related functions and classes that **extend PHP’s functionality** beyond the core language.
- Some modules are **built-in** (e.g., `mysqli`, `json`, `mbstring`)
- Others can be **installed via Composer** (PHP’s package manager)
- They let you do things like:
    - Work with databases (`PDO`, `mysqli`)
    - Handle images (`GD`, `Imagick`)
    - Manage HTTP requests (`Guzzle`)
💡 Think of modules like “toolboxes” — each one adds a set of specialized tools to PHP.

← [[05-Arrays-and-Data-Structures|05. Data Structures]] | [[07-Object-Oriented-Programming]] →