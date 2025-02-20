# Definición
Run the Python script `code.py` in the same directory as `codebook.txt`.
- [Download code.py](https://artifacts.picoctf.net/c/3/code.py)
- [Download codebook.txt](https://artifacts.picoctf.net/c/3/codebook.txt)
# Hints
- On the webshell, use `ls` to see if both files are in the directory you are in
- The `str_xor` function does not need to be reverse engineered for this challenge.

# Solución

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/3/code.py
--2025-02-20 23:26:51--  https://artifacts.picoctf.net/c/3/code.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.93, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: 'code.py'

code.py               100%[======================>]   1.25K  --.-KB/s    in 0s      

2025-02-20 23:26:51 (653 MB/s) - 'code.py' saved [1278/1278]

AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/3/codebook.txt
--2025-02-20 23:27:07--  https://artifacts.picoctf.net/c/3/codebook.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.71, 3.160.5.42, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: 'codebook.txt'

codebook.txt          100%[======================>]      27  --.-KB/s    in 0s      

2025-02-20 23:27:07 (7.22 MB/s) - 'codebook.txt' saved [27/27]

AsumomezaC-picoctf@webshell:~$ ls
code.py  codebook.txt
AsumomezaC-picoctf@webshell:~$ python3 code.py
picoCTF{c0d3b00k_455157_197a982c}
```

>Primero descargamos ambos archivos con [[wget]].
>Después corroboramos que se encuentren en la misma carpeta con [[ls]]
>Finalmente ejecutamos el archivo con [[Python#Corre un programa desde la terminal de Linux]]
## Respuesta
picoCTF{c0d3b00k_455157_197a982c}