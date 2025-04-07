#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Can you get the flag?
Go to this [website](http://saturn.picoctf.net:65014/) and see what you can discover.
# Hints
- Is there more code than what the inspector initially shows?
# Solución
Primero entramos a la página web y vemos lo siguiente:
```
# On Includes

Many programming languages and other computer files have a directive, often called include (sometimes copy or import), that causes the contents of a second file to be inserted into the original file. These included files are called copybooks or header files. They are often used to define the physical layout of program data, pieces of procedural code and/or forward declarations while promoting encapsulation and the reuse of code.

  

Source: Wikipedia on Include directive

Say hello
```

Si presionamos el botón de 'say hello' vamos lo siguiente:
>This code is in a separate file!

Por lo que inspeccionamos el código para ver que hace el botón.
```html
|<!DOCTYPE html>|
||<html lang="en">|
||<head>|
||<meta charset="UTF-8">|
||<meta name="viewport" content="width=device-width, initial-scale=1.0">|
||<meta http-equiv="X-UA-Compatible" content="ie=edge">|
||<link rel="stylesheet" href="[style.css](http://saturn.picoctf.net:65014/style.css)">|
||<title>On Includes</title>|
||</head>|
||<body>|
||<script src="[script.js](http://saturn.picoctf.net:65014/script.js)"></script>|
|||
||<h1>On Includes</h1>|
||<p>Many programming languages and other computer files have a directive,|
||often called include (sometimes copy or import), that causes the|
||contents of a second file to be inserted into the original file. These|
||included files are called copybooks or header files. They are often used|
||to define the physical layout of program data, pieces of procedural code|
||and/or forward declarations while promoting encapsulation and the reuse|
||of code.</p>|
||<br>|
||<p> Source: Wikipedia on Include directive </p>|
||<button type="button" onclick="greetings();">Say hello</button>|
||</body>|
||</html>|
|||
```

Nos dirigimos al archivo de [[Javascript]] para ver que contiene:
```javascript
function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_df589022}
```
>Y encontramos la parte final de la bandera.

Inspeccionamos el archivo [[CSS]] para ver si nos da más información:
```css
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */
```

Y así encontramos el resto de la bandera.
## Respuesta
picoCTF{1nclu51v17y_1of2_f7w_2of2_df589022}