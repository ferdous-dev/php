PHP supports different types of errors:
- **Syntax Errors**: Mistakes in code grammar (e.g., missing semicolon).
- **Runtime Errors**: Occur during execution (e.g., file not found).
- **Logical Errors**: Code runs but produces incorrect results.
PHP provides structured error handling using `try`, `catch`, `throw`, and `finally`:
```php
try {
    if (!file_exists("somefile.txt")) {
        throw new Exception("File not found.");
    }
} catch (Exception $e) {
    echo "Caught exception: " . $e->getMessage();
} finally {
    echo "This block is always executed.";
}
```
- `try`: Wrap code that might fail.
- `throw`: Manually raise an exception.
- `catch`: Handle exceptions.
- `finally`: Always runs (cleanup or logging).
#### Custom Exception Example
```php
class MyException extends Exception {}

try {
    throw new MyException("Something went wrong");
} catch (MyException $e) {
    echo $e->getMessage();
}
```
#### Custom Error Handler (Procedural)
```php
function customError($errno, $errstr) {
    echo "Error [$errno]: $errstr";
}

set_error_handler("customError");
echo 10 / 0;
```
```