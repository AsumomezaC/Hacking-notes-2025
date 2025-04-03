#Software #Hacking #WebExplotation #Web #Internet 
# Definición

# Hints
- Access the webpage and try to match the regular expression associated with the text field
# Solución
Antes que nada debemos saber que es una [[Expresión Regular]].

Una vez sabiendo esto inspecciónanos el código fuente.

```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html>|
|||
||<head>|
||<!-- <link rel="stylesheet" href="./index.css" /> -->|
||<style>|
||.heading {|
||width: 100%;|
||height: 40px;|
||background-color: coral;|
||padding-left: 10px;|
||font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;|
||}|
|||
||.normal-form {|
||text-align: center;|
||margin-top: 5%;|
||}|
|||
||#submit-but {|
||border-radius: 0;|
||width: 250px;|
||height: 25px;|
|||
||}|
|||
||#name {|
||width: 250px;|
||height: 25px;|
||background-color: rgb(241, 226, 206);|
||}|
|||
||#sub-heading {|
||color: brown;|
||}|
||</style>|
||</head>|
|||
||<body>|
|||
||<h1 class="heading">PicoCTF</h1>|
||<p></p>|
|||
||<div class="normal-form">|
||<h2 id="sub-heading">Valid Input</h2>|
||<form action="#" onsubmit="return send_request()">|
||<input type="text" id="name" name="input" placeholder="Input text">|
||<br>|
||<br>|
||<button id="submit-but" type="submit" id="submit-button">SUBMIT</button>|
||</form>|
||</div>|
||</body>|
||<script>|
||function send_request() {|
||let val = document.getElementById("name").value;|
||// ^p.....F!?|
||fetch(`/flag?input=${val}`)|
||.then(res => res.text())|
||.then(res => {|
||const res_json = JSON.parse(res);|
||alert(res_json.flag)|
||return false;|
||})|
||return false;|
||}|
|||
||</script>|
|||
||</html>|
```

Ahí podemos ver que la contraseña tiene el formato: '^p.....F!?|', por lo que ingresamos una contraseña con este formato y nos regresa la bandera.
## Respuesta
picoCTF{succ3ssfully_matchtheregex_0694f25b}