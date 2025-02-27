#Software #Hacking #Principiante
# Definición
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/bc72945175d643626d6ea9a689672dbd/static)? This [BASH script](https://mercury.picoctf.net/static/bc72945175d643626d6ea9a689672dbd/ltdis.sh) might help!
# Hints
(none)
# Solución

```cmd
AsumomezaC-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/bc72945175d643626d6ea9a689672dbd/static
--2025-02-17 17:40:39--  https://mercury.picoctf.net/static/bc72945175d643626d6ea9a689672dbd/static
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8376 (8.2K) [application/octet-stream]
Saving to: 'static'

static                100%[=======================>]   8.18K  --.-KB/s    in 0s      

2025-02-17 17:40:39 (267 MB/s) - 'static' saved [8376/8376]

AsumomezaC-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/bc72945175d643626d6ea9a689672dbd/ltdis.sh
--2025-02-17 17:40:59--  https://mercury.picoctf.net/static/bc72945175d643626d6ea9a689672dbd/ltdis.sh
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 785 [application/octet-stream]
Saving to: 'ltdis.sh'

ltdis.sh              100%[=======================>]     785  --.-KB/s    in 0s      

2025-02-17 17:40:59 (473 MB/s) - 'ltdis.sh' saved [785/785]

AsumomezaC-picoctf@webshell:~$ ./ltdis.sh static
Attempting disassembly of static ...
Disassembly successful! Available at: static.ltdis.x86_64.txt
Ripping strings from binary with file offsets...
Any strings found in static have been written to static.ltdis.strings.txt with file offset

AsumomezaC-picoctf@webshell:~$ grep "picoCTF" static.ltdis.strings.txt
   1020 picoCTF{d15a5m_t34s3r_1e6a7731}
```

>Primero descargamos ambos archivos usando wget
>Después damos permisos de ejecución y ejecutamos el script.
>Y finalmente con grep buscamos en el archivo de strings la flag.

## Solución fácil
```bash
strings static | grep pico
```
## Respuesta
picoCTF{d15a5m_t34s3r_1e6a7731}