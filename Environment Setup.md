### Regular PHP MySQL Setup
1. Download & install XAMPP
2. Check your PHP version in terminal `php -v`
3. Download and install composer
4. Check composer version in terminal `composer -v`
5. Download VS code
### VS Code Extensions for PHP
- PHP Debug
- PHP IntelliSense
- PHP Server
- MySQL by Weijan Chen
- PHP Intelephense
- Auto Rename Tag
### Xdebug Setup
- Paste `XDebug` dll file inside XAMPP/php/ext
- Open php.ini and add properties

```
xdebug.mode=debug
xdebug.start_with_request=yes
xdebug.client_port=9003
xdebug.client_host = localhost
zend_extension="C:\xampp\php\ext\xdebug.dll"
```

Again check PHP version in terminal `php -v`

#php