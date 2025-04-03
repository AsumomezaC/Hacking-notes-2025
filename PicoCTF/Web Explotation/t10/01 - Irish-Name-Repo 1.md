#Software #Hacking #WebExplotation #Web #Internet 
# Definición
There is a website running at `https://jupiter.challenges.picoctf.org/problem/50009/` ([link](https://jupiter.challenges.picoctf.org/problem/50009/)) or http://jupiter.challenges.picoctf.org:50009. Do you think you can log us in? Try to see if you can login!
# Hints
- There doesn't seem to be many ways to interact with this. I wonder if the users are kept in a database?
- Try to think about how the website verifies your login.
# Solución
Para hacerlo nos apoyaremos de la [[Inyección SQL]].

Intentamos ingresar en el login, pero no logramos ingresar.

Al inspeccionar nos damos cuenta que tiene un elemento 'hidden' y lo mostramos.
```html
<input type="password" id="password" name="password" class="form-control">
```

Así que con ello vemos que nos regresa.

```bash

```

Y al ingresar una [[inyección SQL]], obtenemos la bander.
Login: admin'--
Login: juan' or 1=1
Y al cumplirse al menos una condición, nos retorna la bandera.

Your flag is: picoCTF{s0m3_SQL_fb3fe2ad}
## Respuesta
picoCTF{s0m3_SQL_fb3fe2ad}