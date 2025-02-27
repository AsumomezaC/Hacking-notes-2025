#Software #Hacking #Principiante
# Definición
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/13/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/13/level2.flag.txt.enc) in the same directory too.
# Hints
- Does that encoding look familiar?
- The `str_xor` function does not need to be reverse engineered for this challenge.
# Solución
Descargamos los archivos con [[wget]].

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.py
--2025-02-21 22:53:45--  https://artifacts.picoctf.net/c/13/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.18, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py          100%[=============>]     914  --.-KB/s    in 0s      

2025-02-21 22:53:45 (238 MB/s) - 'level2.py' saved [914/914]

AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
--2025-02-21 22:54:02--  https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.42, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.en 100%[=============>]      31  --.-KB/s    in 0s      

2025-02-21 22:54:02 (9.64 MB/s) - 'level2.flag.txt.enc' saved [31/31]
```

Analizamos el archivo con [[nano]].
```python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT #################>
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,ne>
########################################################################>

flag_enc = open('level2.flag.txt.enc', 'rb').read()



def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_2_pw_check()
```
Nos damos cuenta que en este caso la contraseña esta "escondida" usando [[ASCII]] + codificación [[hexadecimal]].

Para describir de que se trata nos apoyaremos de [[Python#Ejecución directa de un script en una sola línea]].

```bash
AsumomezaC-picoctf@webshell:~$ python3 -c 'print(chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36))'
de76
```
Ya con esto ingresamos la contraseña en el programa "level2.py"
```bash
AsumomezaC-picoctf@webshell:~$ python3 level2.py
Please enter correct password for flag: de76
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_489dea9a}
```
## Respuesta
picoCTF{tr45h_51ng1ng_489dea9a}