#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Can you get the flag?Go to this [website](http://saturn.picoctf.net:53286/) and see what you can discover.
# Hints
- Do you know how to modify cookies?
# Solución
Primero ingresamos a la página e ingresamos como invitado.
Al entrar nos dirá que no tienen servicio en este momento, pero al cambiar el valor de la cookie 'isAdmin' a '1'  y recargando la página obtenemos la bandera.
## Respuesta
picoCTF{gr4d3_A_c00k13_5d2505be}