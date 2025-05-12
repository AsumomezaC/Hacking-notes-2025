---
tags:
  - CTF
  - Criptografía
  - Hacking
  - Software
  - Programación
  - Computación
---
>Problema de la rama de [[Crypto]]
# Descripción
Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 9422`.
# Pistas
- What kind of encoding uses dashes and dots?
- The flag is in the format PICOCTF{}
# Solución
Comenzamos siguiendo la primera pista, y nos encontramos con el [[código morse]].

Nos conectamos usando [[NET CAT (nc)]], y vemos lo siguiente:
```bash
AsumomezaC-picoctf@webshell:~/cif$ nc jupiter.challenges.picoctf.org 9422
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. ..--- -.... ---.. ...-- ---.. ..--- ....- -.... .---- ----- }
```

Nos apoyamos de deepseek y decodificamos el mensaje:
PICOCTF{M0RS3C0D31SFUN2683824610}
Y obtenemos la bandera
## Respuesta
PICOCTF{M0RS3C0D31SFUN2683824610}