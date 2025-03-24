#Software #Hacking #WebExplotation #Web 
# Definición
Can you find the robots? `https://jupiter.challenges.picoctf.org/problem/36474/` ([link](https://jupiter.challenges.picoctf.org/problem/36474/)) or http://jupiter.challenges.picoctf.org:36474
# Hints
- What part of the website could tell you where the creator doesn't want you to look?
# Solución
Al inspeccionar la pagina no encontramos nada, por lo que decidimos ver que es lo que nos esta escondiendo usando [[robots.txt]]:

User-agent: *
Disallow: /477ce.html

Ingresamos a la parte en la que no quiere que entremos (https://jupiter.challenges.picoctf.org/problem/36474/477ce.html). Y vemos esto:
Guess you found the robots  
picoCTF{ca1cu1at1ng_Mach1n3s_477ce}

## Respuesta
picoCTF{ca1cu1at1ng_Mach1n3s_477ce}