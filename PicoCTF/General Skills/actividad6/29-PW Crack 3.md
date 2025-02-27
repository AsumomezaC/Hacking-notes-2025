#Software #Hacking #Principiante
# Definición
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/18/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/18/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/18/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.
# Hints
- To view the level3.hash.bin file in the webshell, do: `$ bvi level3.hash.bin`
- To exit `bvi` type `:q` and press enter.
- The `str_xor` function does not need to be reverse engineered for this challenge.
# Solución
Primero descargamos los tres archivos con [[wget]].

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/18/level3.py
--2025-02-21 23:08:38--  https://artifacts.picoctf.net/c/18/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.42, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: 'level3.py'

level3.py          100%[=============>]   1.31K  --.-KB/s    in 0s      

2025-02-21 23:08:38 (969 MB/s) - 'level3.py' saved [1337/1337]

AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/18/level3.flag.txt.enc
--2025-02-21 23:08:52--  https://artifacts.picoctf.net/c/18/level3.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.42, 3.160.5.18, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level3.flag.txt.enc'

level3.flag.txt.en 100%[=============>]      31  --.-KB/s    in 0s      

2025-02-21 23:08:52 (2.03 MB/s) - 'level3.flag.txt.enc' saved [31/31]

AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/18/level3.hash.bin
--2025-02-21 23:09:05--  https://artifacts.picoctf.net/c/18/level3.hash.bin
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.93, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: 'level3.hash.bin'

level3.hash.bin    100%[=============>]      16  --.-KB/s    in 0s      

2025-02-21 23:09:05 (604 KB/s) - 'level3.hash.bin' saved [16/16]
```

Empezamos ejecutando la pista usando el comando [[bvi]], y obtenemos el siguiente resultado:
```
00000000  16 02 6D 60 FF 9B 54 41 0B 34 35 B4 03 AF D2 26 ..m`..TA.45....&
00000010
```
Además empleamos [[nano]] para analizar el archivo de python.
```python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ######################>
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key>
#############################################################################>

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_3_pw_check()


# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["8799", "d3ab", "1ea2", "acaf", "2295", "a9de", "6f3d"]
```
Por lo que podemos notar que aquí tenemos las posibles contraseñas.

>Como no encontré una pista clara, y no se como solucionarlo, podemos modificar el archivo para que pruebe todas las combinaciones y nos regrese la bandera(no olvidemos mover la lista para que se cree antes de llamar la función):

```python
def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    for item in pos_pw_list:
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), item)
        print(decryption)
    return
    print("That password is incorrect")
```
Al ejecutarlo, vemos todas las "soluciones":
```bash
AsumomezaC-picoctf@webshell:~$ python level3.py
Please enter correct password for flag: l
Welcome back... your flag, user:
zlccIQFwg15dUcl=db1bmZ6j3=a83c}
Welcome back... your flag, user:
&h;8U,;5m?      g4f8fi91^n1o99cog%
Welcome back... your flag, user:
s>;h@|ncmo\146m0iina:o93:1%
Welcome back... your flag, user:
#8;<(>em;
         74b=6i=4n5ji9gj7%
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_6f98a49f}
Welcome back... your flag, user:
#b>?_?h8
        m1a=ll>4Tk6j3<djm 
Welcome back... your flag, user:
t=i>GL*i`?9[2f`j3;?c
                    <7=lke=2w
```
## Respuesta
picoCTF{m45h_fl1ng1ng_6f98a49f}