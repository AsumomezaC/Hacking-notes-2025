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
The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?
# Pistas
- The flag is in the format PICOCTF{}
# Solución
Comenzamos descargando el archivo con [[wget]].
```bash
AsumomezaC-picoctf@webshell:~/num$ wget https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
--2025-05-12 17:21:47--  https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100721 (98K) [application/octet-stream]
Saving to: 'the_numbers.png'

the_numbers.png                              100%[============================================================================================>]  98.36K  --.-KB/s    in 0.04s   

2025-05-12 17:21:47 (2.20 MB/s) - 'the_numbers.png' saved [100721/100721]
```

Al tratarse de una imagen, la abrimos. Y vemos que contiene una serie de números:
19 9 3 15 3 20 6 { 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14}.
Parece tener la forma de la bandera, además la pista sugiere que todo esta en mayúsculas. Y no vemos ningún número grande. Parece que hacen referencia a su orden alfabético, nos apoyamos de [deepseek](https://chat.deepseek.com/) y vemos que obtenemos al [[Desencriptación|desencriptar]].


> [!quote] Prompt
> Se que al desencriptarlo, esto empieza así PICOCTF{...}, parece que hace referencia a las letras del albábeto -seguramente en [[inglés]]-. Cuál es la bandera: 19 9 3 15 3 20 6 { 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14}

Y obtenemos la bandera.
## Respuesta
**PICOCTF{THENUMBERSMASON}**