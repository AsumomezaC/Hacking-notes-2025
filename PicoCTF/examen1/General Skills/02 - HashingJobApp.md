#Software #Hacking #Computación #GeneralSkills
Hecho por: [[Estufa|Juana Estefanía Herrera Mendoza]]
# Definición
If you want to hash with the best, beat this test!`nc saturn.picoctf.net 50559`
# Hints
- You can use a commandline tool or web app to hash text
- Press Ctrl and c on your keyboard to close your connection and return to the command prompt.
# Solución
- **Al iniciar la instancia nos dan lo siguiente: `nc saturn.picoctf.net 50559`, lo copiamos y pegamos en la terminal (con ayuda de [[NET CAT]]).**

```bash
AsumomezaC-picoctf@webshell:~$ nc saturn.picoctf.net 50559
```

- **Tal y como dice el texto, tenemos que convertir la palabra entre las comillas simples a md5, y lo haremos con ayuda de [cyberchef](https://gchq.github.io/CyberChef/#recipe=MD5()), al completarlo nos dará la bandera.**

```bash

Please md5 hash the text between quotes, excluding the quotes: 'Jupiter'

Answer:

89c5c30498c2989611f9044be006197c

89c5c30498c2989611f9044be006197c

Correct.

Please md5 hash the text between quotes, excluding the quotes: 'Cindy Crawford'

Answer:

2ee8ebf845baa7f500e153417cf691fd

2ee8ebf845baa7f500e153417cf691fd

Correct.

Please md5 hash the text between quotes, excluding the quotes: 'coconuts'

Answer:

78d1999482f432e9c229269151140542

78d1999482f432e9c229269151140542

Correct.

picoCTF{4ppl1c4710n_r3c31v3d_bf2ceb02}

```
## Respuesta
picoCTF{4ppl1c4710n_r3c31v3d_bf2ceb02}