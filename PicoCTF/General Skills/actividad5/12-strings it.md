#Software #Hacking #Principiante
# Definición
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings) without running it?
# Hints
[strings](https://linux.die.net/man/1/strings)
# Solución
# Sol 1

```cmd
AsumomezaC-picoctf@webshell:~$ wget -O stringIt.txt https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
--2025-02-17 17:14:08--  https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 776032 (758K) [application/octet-stream]
Saving to: 'stringIt.txt'

stringIt.txt          100%[=======================>] 757.84K  1.86MB/s    in 0.4s    

2025-02-17 17:14:09 (1.86 MB/s) - 'stringIt.txt' saved [776032/776032]

AsumomezaC-picoctf@webshell:~$ grep -a -o "picoCTF{[^}]*}" stringIt.txt
picoCTF{5tRIng5_1T_7f766a23}
```

>Primero descargamos el archvio con wget, utilizando -O para especificar el nombre de guardado del archivo

>Después buscamos en el archivo (forzando búsqueda txt) algo que coincida con la forma picoCTF{contraseña}.

## Sol 2
>Después de descargar el archivo

aplicamos el comando [[strings]] en el archivo string, y ejecutamos un grep para filtrar:
```bash
strings -n 10 strings | grep pico
```
## Respuesta
picoCTF{5tRIng5_1T_7f766a23}