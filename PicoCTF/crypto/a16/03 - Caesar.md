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
Decrypt this [message](https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext).
# Pistas
caesar cipher [tutorial](https://learncryptography.com/classical-encryption/caesar-cipher)
# Solución
Inicialmente podemos suponer que el mensaje se encuentra encriptado en [[Cifrado César]].

Comenzamos descargando el archivo con [[wget]].
```bash
AsumomezaC-picoctf@webshell:~/cesar$ wget https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext
--2025-05-12 17:11:12--  https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35 [application/octet-stream]
Saving to: 'ciphertext'

ciphertext                                   100%[============================================================================================>]      35  --.-KB/s    in 0s      

2025-05-12 17:11:12 (29.2 MB/s) - 'ciphertext' saved [35/35]
```

Después usamos [[file]] para ver que tipo de archivo estamos trabajando.
```bash
AsumomezaC-picoctf@webshell:~/cesar$ file ciphertext
ciphertext: ASCII text, with no line terminators
```

Parece ser un simple archivo en formato [[ASCII]], por lo que usamos [[Strings]] para ver su contenido.
```bash
AsumomezaC-picoctf@webshell:~/cesar$ strings ciphertext 
picoCTF{gvswwmrkxlivyfmgsrhnrisegl}
```
Vemos que contiene la bandera [[Encriptación|encriptada]], por lo que usamos una[herramienta online](https://calculado.net/cifrado-cesar-codificador-decodificador-en-linea) para desencriptarla.
Probamos suerte con los números de encriptación, hasta que de sentido -este proceso se puede automatizar-:
1. furvvlqjwkhuxelfrqgmqhrdfk
2. etquukpivjgtwdkeqpflpgqcej
3. dspttjohuifsvcjdpoekofpbdi
4. crossingtherubicondjneoach
>Esta tiene forma de palabras en [[inglés]], por lo que la usamos, y es la bandera.
## Respuesta
picoCTF{crossingtherubicondjneoach}