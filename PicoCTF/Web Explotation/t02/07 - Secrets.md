#Software #Hacking #WebExplotation #Web #Internet 
# Definición
We have several pages hidden. Can you find the one with the flag?The website is running [here](http://saturn.picoctf.net:51568/).
# Hints
- folders folders folders
# Solución
Al entrar lo primero que hacemos es inspeccionar la página
```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html>|
||<head>|
||<meta charset="UTF-8" />|
||<meta|
||name="viewport"|
||content="width=device-width, initial-scale=1, shrink-to-fit=no"|
||/>|
||<meta name="description" content="" />|
||<!-- Bootstrap core CSS -->|
||<link href="[vendor/bootstrap/css/bootstrap.min.css](http://saturn.picoctf.net:51568/vendor/bootstrap/css/bootstrap.min.css)" rel="stylesheet" />|
||<!-- title -->|
||<title>home</title>|
||<!-- css -->|
||<link href="[secret/assets/index.css](http://saturn.picoctf.net:51568/secret/assets/index.css)" rel="stylesheet" />|
||</head>|
||<body>|
||<!-- ***** Header Area Start ***** -->|
||<div class="topnav">|
||<a class="active" href="[#home](http://saturn.picoctf.net:51568/#home)">Home</a>|
||<a href="[about.html](http://saturn.picoctf.net:51568/about.html)">About</a>|
||<a href="[contact.html](http://saturn.picoctf.net:51568/contact.html)">Contact</a>|
||</div>|
|||
||<div class="imgcontainer">|
||<img|
||src="[secret/assets/DX1KYM.jpg](http://saturn.picoctf.net:51568/secret/assets/DX1KYM.jpg)"|
||alt="https://www.alamy.com/security-safety-word-cloud-concept-image-image67649784.html"|
||class="responsive"|
||/>|
||<div class="top-left">|
||<h1>If security wasn't your job, would you do it as a hobby?</h1>|
||</div>|
||</div>|
||</body>|
||</html>|
|||
```

Al inspeccionarla vemos que tenemos una carpeta extraña llamada secret, por lo que accedemos a ella. Esta nos dice que vamos bien, por lo que volvemos a inspeccionar la página.
```html
|<!DOCTYPE html>|
||<html>|
||<head>|
||<title></title>|
||<link rel="stylesheet" href="[hidden/file.css](http://saturn.picoctf.net:51568/secret/hidden/file.css)" />|
||</head>|
|||
||<body>|
||<h1>Finally. You almost found me. you are doing well</h1>|
||<img src="[https://media1.tenor.com/images/0a6aff9f825af62c05adfbd75039cc7b/tenor.gif?itemid=4648337](https://media1.tenor.com/images/0a6aff9f825af62c05adfbd75039cc7b/tenor.gif?itemid=4648337)" alt="Something Like That GIF - Andy Parksandrecreation Wtf GIFs" style="max-width: 833px; background-color: rgb(151, 121, 85);" width="833" height="937.125">|
||</body>|
||</html>|
|||
```

Y vemos que esta a su vez también contiene una carpeta sospechosa: 'hidden'. En esta nueva pagina al inspeccionarla vemos lo siguiente:
```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html>|
||<head>|
||<title>LOGIN</title>|
||<!-- css -->|
||<link href="[superhidden/login.css](http://saturn.picoctf.net:51568/secret/hidden/superhidden/login.css)" rel="stylesheet" />|
||</head>|
||<body>|
||<form>|
||<div class="container">|
||<form method="" action="/secret/assets/popup.js">|
||<div class="row">|
||<h2 style="text-align: center">|
||Login with Social Media or Manually|
||</h2>|
||<div class="vl">|
||<span class="vl-innertext">or</span>|
||</div>|
|||
||<div class="col">|
||<a href="[#](http://saturn.picoctf.net:51568/secret/hidden/#)" class="fb btn">|
||<i class="fa fa-facebook fa-fw"></i> Login with Facebook|
||</a>|
||<a href="[#](http://saturn.picoctf.net:51568/secret/hidden/#)" class="twitter btn">|
||<i class="fa fa-twitter fa-fw"></i> Login with Twitter|
||</a>|
||<a href="[#](http://saturn.picoctf.net:51568/secret/hidden/#)" class="google btn">|
||<i class="fa fa-google fa-fw"></i> Login with Google+|
||</a>|
||</div>|
|||
||<div class="col">|
||<div class="hide-md-lg">|
||<p>Or sign in manually:</p>|
||</div>|
|||
||<input|
||type="text"|
||name="username"|
||placeholder="Username"|
||required|
||/>|
||<input|
||type="password"|
||name="password"|
||placeholder="Password"|
||required|
||/>|
||<input type="hidden" name="db" value="superhidden/xdfgwd.html" />|
|||
||<input|
||type="submit"|
||value="Login"|
||onclick="alert('Thank you for the attempt but oops! try harder. better luck next time')"|
||/>|
||</div>|
||</div>|
||</form>|
||</div>|
|||
||<div class="bottom-container">|
||<div class="row">|
||<div class="col">|
||<a href="[#](http://saturn.picoctf.net:51568/secret/hidden/#)" style="color: white" class="btn">Sign up</a>|
||</div>|
||<div class="col">|
||<a href="[#](http://saturn.picoctf.net:51568/secret/hidden/#)" style="color: white" class="btn">Forgot password?</a>|
||</div>|
||</div>|
||</div>|
||</form>|
||</body>|
||</html>|
|||
```

Y vemos una carpeta llamada 'superhidden', así que probamos suerte. Al entrar la inspeccionamos y finalmente vemos la bandera.
```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html>|
||<head>|
||<title></title>|
||<link rel="stylesheet" href="[mycss.css](http://saturn.picoctf.net:51568/secret/hidden/superhidden/mycss.css)" />|
||</head>|
|||
||<body>|
||<h1>Finally. You found me. But can you see me</h1>|
||<h3 class="flag">picoCTF{succ3ss_@h3n1c@10n_790d2615}</h3>|
||</body>|
||</html>|
|||
```
## Respuesta
picoCTF{succ3ss_@h3n1c@10n_790d2615}