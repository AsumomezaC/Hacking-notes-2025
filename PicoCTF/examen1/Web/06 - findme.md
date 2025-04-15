#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Estufa|Juana Estefanía Herrera Mendoza]]
# Definición
Help us test the form by submiting the username as `test` and password as `test!`The website running [here](http://saturn.picoctf.net:52486/).
# Hints
any redirections?
# Solución
- **Nos dirigimos a la pagina web que nos dan al inicial la instancia, ingresaremos con 'test' como username y 'test!' como contraseña.**
- **Al darle al boton de test o enter, nos dirigimos al historial del navegador, del cual nos veremos que hay 2 paginas de nombre "flag", copiamos ambas direcciones:**

```bash
http://saturn.picoctf.net:52486/next-page/id=cGljb0NURntwcm94aWVzX2Fs
http://saturn.picoctf.net:52486/next-page/id=bF90aGVfd2F5X2RmNDRjOTRjfQ==
```
- **De ambas direcciones copiamos la parte delantera del 'id=', es decir lo siguiente:**
```bash
cGljb0NURntwcm94aWVzX2Fs
bF90aGVfd2F5X2RmNDRjOTRjfQ==
```
- **Y las decodificaremos en [cyberchef](https://cyberchef.org/) (o desde la terminal), de [[Codificación Base 64]], obteniendo la bandera en dos partes.**
## Respuesta
picoCTF{proxies_all_the_way_df44c94c}