## Sessions and Cookies

### Sessions
- Sessions store data across multiple page requests for a single user.
- `session_start()` must be called before any output.
- Data is stored in the `$_SESSION` superglobal.
```php
session_start();
$_SESSION["username"] = "ferdous";
echo "Session started. Username is " . $_SESSION["username"];
```
### Cookies

- Cookies are stored on the client’s browser.
- Use `setcookie()` to create, `$_COOKIE` to read.
```php
setcookie("username", "ferdous", time() + 3600); // 1 hour
if (isset($_COOKIE["username"])) {
    echo "Hello, " . $_COOKIE["username"];
}
```

| Feature    | Session                             | Cookie                        |
| ---------- | ----------------------------------- | ----------------------------- |
| Stored In  | Server                              | Client (browser)              |
| Size Limit | Depends on server settings          | ~4KB                          |
| Duration   | Until browser close or timeout      | Can set specific expiration   |
| Use Case   | Login sessions, cart data, CSRF key | “Remember me”, language pref. |