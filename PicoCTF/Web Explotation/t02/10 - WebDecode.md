#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Do you know how to use the web inspector?Start searching [here](http://titan.picoctf.net:56540/) to find the flag
# Hints
- Use the web inspector on other files included by the web page.
- The flag may or may not be encoded
# Solución
Primero ingresamos a la página web y la inspeccionamos.
```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html lang="en">|
||<head>|
||<meta charset="UTF-8">|
||<meta http-equiv="X-UA-Compatible" content="IE=edge">|
||<meta name="viewport" content="width=device-width, initial-scale=1.0">|
||<link rel="stylesheet" href="[style.css](http://titan.picoctf.net:56540/style.css)">|
||<link rel="shortcut icon" href="[img/favicon.png](http://titan.picoctf.net:56540/img/favicon.png)" type="image/x-icon">|
||<!-- font (google) -->|
||<link href="[https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;1,400&display=swap](https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;1,400&display=swap)" rel="stylesheet">|
||<title>Home</title>|
||</head>|
||<body>|
||<header>|
||<nav>|
||<div class="logo-container">|
||<a href="[index.html](http://titan.picoctf.net:56540/index.html)"><img src="[img/binding_dark.gif](http://titan.picoctf.net:56540/img/binding_dark.gif)" alt="logo"></a>|
||</div>|
||<div class="navigation-container">|
||<ul>|
||<li><a href="[index.html](http://titan.picoctf.net:56540/index.html)">Home</a></li>|
||<li><a href="[about.html](http://titan.picoctf.net:56540/about.html)">About</a></li>|
||<li><a href="[contact.html](http://titan.picoctf.net:56540/contact.html)">Contact</a></li>|
||</ul>|
||</div>|
||</nav>|
||</header>|
||<section class="banner">|
||<h1>Ha!!!!!! You looking for a flag?</h1>|
||<p>Keep Navigating</p>|
|||
||</section><!-- .banner -->|
||<section class="sec-intro">|
||<div class="col">|
||<p>Haaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa</p>|
||<p>Keepppppppppppppp Searchinggggggggggggggggggg</p>|
||<img src="[./img/multipage-html-img1.jpg](http://titan.picoctf.net:56540/img/multipage-html-img1.jpg)" alt="person">|
||<figcaption>Don't give up!</figcaption>|
||</div>|
||</section><!-- .sec-intro -->|
|||
||<footer>|
||<div class="bottombar">Copyright © 2023 Your_Name. All rights reserved.</div>|
||</footer>|
|||
||</body>|
||</html>|
```

Como nos sugiere la pista empezamos a inspeccionar archivos referenciados en el [[HTML]].
En los códigos que vemos, observamos algo bastante extraño (como codificado en [[Codificación Base 64]])
```html
<section class="about" notify_true="cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMjgzZTYyZmV9">
```
Nos apoyamos de ciberchef y encontramos la bandera.
## Respuesta
picoCTF{web_succ3ssfully_d3c0ded_283e62fe}