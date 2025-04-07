#Hacking #Web #Software #Computación 

# Directory Traversal
Técnica para acceder a archivos fuera del directorio web usando:
- Rutas relativas (`../`)
- Caracteres especiales (`%2e%2e%2f` = ../)

Ejemplo peligroso:
```php
file_get_contents($_GET['file']);  // user_input = ../../etc/passwd
```