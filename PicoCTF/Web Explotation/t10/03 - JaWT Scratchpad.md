#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/63090/` or http://jupiter.challenges.picoctf.org:63090
# Hints
- What is that cookie?
- Have you heard of JWT?
# Solución
Utilizamos [[JWT]] para conseguir la contraseña, utilizando la cookie.

Y utilizamos el cookie editor para convertir el token que esta en [[Codificación Base 64]] -apoyándonos de [cyberchef](https://cyberchef.org/)-.

Alteramos la cookie y nos establecemos como admin. Pero al modificar esto no coincide.

Por lo que ocupamos crackear la cookie usando la terminal, apoyándonos con [John](https://github.com/magnumripper/JohnTheRipper). Y descubrimos que la contraseña es 'ilovepico'. 

Modificando la cookie obtenemos la bandera.
## Respuesta
picoCTF{jawt_was_just_what_you_thought_1ca14548}