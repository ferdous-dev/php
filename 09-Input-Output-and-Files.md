### 1. Standard Output

Used to display data to the browser.
```php
echo "This is an output statement.";
```

---

### 2. User Input (HTML Form → PHP)

HTML Form
```html
<!-- HTML Form -->
<form method="post" action="input.php">
    <input type="text" name="name">
    <input type="submit">
</form>

```
```php
// PHP file
if ($_SERVER["REQUEST_METHOD"] == "POST") {
	// htmlspecialchars prevents XSS
    $name = htmlspecialchars($_POST['name']);
	    echo "Hello, " . $name;
}

//Best Practice (Recommended)
	$name = filter_input(INPUT_POST, 'name', FILTER_SANITIZE_SPECIAL_CHARS);
```

### 3. File Input / Output (File I/O)

**Reading a File**
```php
$filename = "file.txt";
if (file_exists($filename)) {
    $file = fopen($filename, "r");
    $data = fread($file, filesize($filename));
    fclose($file);
    echo $data;
} else {
    echo "File not found.";
}
```

**Writing to a File:**
```php
$filename = "file.txt";
$file = fopen($filename, "w");
if ($file) {
    fwrite($file, "Hello, World!");
    fclose($file);
    echo "Data written to file.";
} else {
    echo "Unable to open file.";
}
```

### 4. File Mode

| Mode | Description                |
| ---- | -------------------------- |
| `r`  | Read only                  |
| `w`  | Write only (truncate file) |
| `a`  | Append to file             |
| `r+` | Read/Write                 |

---

### 5. Best Practices

- Always check `file_exists()`
- Use `file_get_contents()` / `file_put_contents()` for simplicity
- Sanitize all user input
- Never trust form data
- Avoid writing files from user input directly
- Handle file permissions properly