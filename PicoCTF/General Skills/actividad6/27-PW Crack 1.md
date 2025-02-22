# Definición
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/12/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/12/level1.flag.txt.enc) in the same directory too.
# Hints
- To view the file in the webshell, do: `$ nano level1.py`
- To exit `nano`, press Ctrl and x and follow the on-screen prompts.
- The `str_xor` function does not need to be reverse engineered for this challenge.
# Solución
Descargamos ambos archivos con [[wget]].

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/12/level1.py
--2025-02-21 22:46:08--  https://artifacts.picoctf.net/c/12/level1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.18, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 876 [application/octet-stream]
Saving to: 'level1.py'

level1.py          100%[=============>]     876  --.-KB/s    in 0s      

2025-02-21 22:46:08 (602 MB/s) - 'level1.py' saved [876/876]

AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/12/level1.flag.txt.enc
--2025-02-21 22:46:39--  https://artifacts.picoctf.net/c/12/level1.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.42, 3.160.5.18, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30 [application/octet-stream]
Saving to: 'level1.flag.txt.enc'

level1.flag.txt.en 100%[=============>]      30  --.-KB/s    in 0s      

2025-02-21 22:46:40 (11.8 MB/s) - 'level1.flag.txt.enc' saved [30/30]
```

Buscamos la contraseña usando el comando [[nano]] para inspeccionar el archivo de código.
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


flag_enc = open('level1.flag.txt.enc', 'rb').read()



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "8713"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_1_pw_check()
```
>Nos damos cuenta que la contraseña es "8713"

Ejecutamos el programa de [[Python#Corre un programa desde la terminal de Linux]] e ingresamos la contraseña.

```bash
AsumomezaC-picoctf@webshell:~$ python3 level1.py
Please enter correct password for flag: 8713
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_1b2fd683}
```
## Respuesta
picoCTF{545h_r1ng1ng_1b2fd683}