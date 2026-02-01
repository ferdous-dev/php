### Sessions
- Sessions store user data **on the server** across multiple page requests for a single user.
- `session_start()` must be called before any output.
- Data is stored in the `$_SESSION`.
- Session ID is usually stored in a cookie

```php
session_start();
$_SESSION["username"] = "ferdous";
echo "Welcome " . $_SESSION["username"];
```

#### Common Uses
- User login state
- Shopping cart
- CSRF tokens

---
### Cookies

- Cookies store small pieces of data **in the user’s browser**.
- Use `setcookie()` to create, `$_COOKIE` to read.

```php
setcookie("username", "ferdous", time() + 3600, "/"); // 1 Hour

if (isset($_COOKIE['username'])) {
    echo "Hello " . $_COOKIE['username'];
}
```


#### Session vs Cookie

| Feature    | Session                             | Cookie                       |
| ---------- | ----------------------------------- | ---------------------------- |
| Stored In  | Server                              | Browser                      |
| Security   | More secure                         | Less secure                  |
| Size Limit | Depends on server settings          | ~4KB                         |
| Lifetime   | Browser close or timeout            | Can set specific expiration  |
| Use Case   | Login sessions, cart data, CSRF key | Remember me , language pref. |
#### Best Practices
- Never store sensitive data in cookies
- Regenerate session ID after login
- Use cookies only for non-critical data
- Always start session before HTML output