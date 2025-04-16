#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Yolanda Alejandra Sifuentes Flores]]
# Definición
Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:57968/) and good luck
# Hints
- Sometimes, the most important information is hidden in plain sight. Have you checked all parts of the webpage?
- Cookies aren't just for eating - they're also used in web technologies!
- Web browsers often have tools that can help you inspect various aspects of a webpage, including things you can't see directly.
# Solución
1. Ingresamos a la página web y nos registramos, y nos dice lo siguiente:
Cookie Monster says: 'Me no need password. Me just need cookies!'

Hint: Have you checked your cookies lately?

[Go back](http://verbal-sleep.picoctf.net:57968/)

2. Inspeccionamos la página, y guardamos el valor de la cookie:
cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzXzZFODFGQzFFfQ%3D%3D

3. Usamos [cyberchef](<https://cyberchef.org/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=Y0dsamIwTlVSbnRqTURCck1XVmZiVEJ1YzNSbGNsOXNNSFpsYzE5ak1EQnJhV1Z6WHpaRk9ERkdRekZGZlElM0QlM0Q>) o la terminal y lo decodificamos de [[Codificación Base 64]].
picoCTF{c00k1e_m0nster_l0ves_c00kies_6E81FC1E}
ÃÜ
## Respuesta
picoCTF{c00k1e_m0nster_l0ves_c00kies_6E81FC1E}
## Referencia
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=Y0dsamIwTlVSbnRqTURCck1XVmZiVEJ1YzNSbGNsOXNNSFpsYzE5ak1EQnJhV1Z6WDBGRE9FWkRSRGMxZlElM0QlM0Q&oeol=CR