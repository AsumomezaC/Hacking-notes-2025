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
Can you get the real meaning from this file.Download the file [here](https://artifacts.picoctf.net/c_titan/1/enc_flag).
# Pistas
Engaging in various decoding processes is of utmost importance
# Solución
Comenzamos viendo que el problema tiene dos conceptos clave: [[Codificación Base 64]] y [[Cifrado César]]. Suponemos que combinarlos dará la solución.

Descargamos el archivo con [[wget]].
```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/1/enc_flag
--2025-05-12 18:24:06--  https://artifacts.picoctf.net/c_titan/1/enc_flag
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.43, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 73 [application/octet-stream]
Saving to: 'enc_flag'

enc_flag                                     100%[============================================================================================>]      73  --.-KB/s    in 0s      

2025-05-12 18:24:06 (19.8 MB/s) - 'enc_flag' saved [73/73]
```

Vemos su contenido con [[Strings]].
```bash
AsumomezaC-picoctf@webshell:~$ strings enc_flag 
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyeG9OakJzTURCcGZRPT0nCg==
```
Su contenido parece estar en [[Codificación Base 64]], por lo que nos apoyamos de [cyberchef](<https://cyberchef.org/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)>) para [[Decodificador|decodificarlo]].

b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2xoNjBsMDBpfQ\=='

Parece que nos dio otro texto en [[Codificación Base 64]] -por la b' y los caractéres-, por lo que repetimos el proceso.

wpjvJAM{jhlzhy_k3jy9wa3k_lh60l00i}

Ahora obtenemos algo mucho más parecido a la bandera, por lo que ahora probamos suerte con el [[Cifrado César]] usando una [herramienta online](https://www.dcode.fr/cifrado-cesar). Y obtenemos la bandera.
## Respuesta
picoCTF{caesar_d3cr9pt3d_ea60e00b}