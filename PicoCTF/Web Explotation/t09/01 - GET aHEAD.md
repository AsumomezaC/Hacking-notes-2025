#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:53554/](http://mercury.picoctf.net:53554/)
# Hints
- Maybe you have more than 2 choices
- Maybe you have more than 2 choices
# Solución
Primero inspeccionamos la pagina web ([[HTML]]).

```html
|<html>|
||<head>|
||<title>Red</title>|
||<link rel="stylesheet" type="text/css" href="[//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css](http://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css)">|
||<style>body {background-color: red;}</style>|
||</head>|
||<body>|
||<div class="container">|
||<div class="row">|
||<div class="col-md-6">|
||<div class="panel panel-primary" style="margin-top:50px">|
||<div class="panel-heading">|
||<h3 class="panel-title" style="color:red">Red</h3>|
||</div>|
||<div class="panel-body">|
||<form action="index.php" method="GET">|
||<input type="submit" value="Choose Red"/>|
||</form>|
||</div>|
||</div>|
||</div>|
||<div class="col-md-6">|
||<div class="panel panel-primary" style="margin-top:50px">|
||<div class="panel-heading">|
||<h3 class="panel-title" style="color:blue">Blue</h3>|
||</div>|
||<div class="panel-body">|
||<form action="index.php" method="POST">|
||<input type="submit" value="Choose Blue"/>|
||</form>|
||</div>|
||</div>|
||</div>|
||</div>|
||</div>|
||</body>|
||</html>|
|||
```

Al tratar de hace un cambio de código directo, esto no funciona (se reevierte).

Por lo que empleamos [[curl]] para mandar el 'HEAD'.
```bash
C:\Users\52492>curl -X HEAD http://mercury.picoctf.net:53554/
Warning: Setting custom HTTP method to HEAD with -X/--request may not work the
Warning: way you want. Consider using -I/--head instead.

C:\Users\52492>curl -I http://mercury.picoctf.net:53554/
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_2e5ba39f}
Content-type: text/html; charset=UTF-8
```
>Vemos que Head ya no existe y se reemplaza con -I
## Respuesta
picoCTF{r3j3ct_th3_du4l1ty_2e5ba39f}