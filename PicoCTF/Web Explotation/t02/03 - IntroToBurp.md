#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Try [here](http://titan.picoctf.net:65282/) to find the flag
# Hints
- Try using burpsuite to intercept request to capture the flag.
- Try mangling the request, maybe their server-side code doesn't handle malformed requests very well.
# Solución
Primero entramos a la página que nos da el reto. Y vemos una página de autenticación, por la que la llenamos con datos aleatorios, pero de ahí nos pide una autenticación. Pero esto falla y nos indica:
>Invalid [[OTP]]

Antes que nada para este problema ocuparemos instalar [[BURP]] (Actuando como [[Men_in_the_Middle]]).

Una ves que lo tenemos lo utilizamos para interceptar el mensaje y eliminamos el OTP, y esto nos da la bandera.

>Welcome, a you sucessfully bypassed the OTP request. Your Flag: picoCTF{#0TP_Bypvss_SuCc3$S_6bffad21}
## Respuesta
picoCTF{#0TP_Bypvss_SuCc3$S_6bffad21}