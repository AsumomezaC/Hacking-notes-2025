# Definición
Fix the syntax error in this Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/26/fixme1.py)
# Hints
- Indentation is very meaningful in Python
- To view the file in the webshell, do: `$ nano fixme1.py`
- To exit `nano`, press Ctrl and x and follow the on-screen prompts.
- The `str_xor` function does not need to be reverse engineered for this challenge.
# Solución
>Primero descargamos el archivo usando [[wget]]

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/26/fixme1.py
--2025-02-20 23:43:04--  https://artifacts.picoctf.net/c/26/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.18, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: 'fixme1.py'

fixme1.py             100%[======================>]     837  --.-KB/s    in 0s      

2025-02-20 23:43:04 (239 MB/s) - 'fixme1.py' saved [837/837]

AsumomezaC-picoctf@webshell:~$ nano fixme1.py
```

>Después vemos el programa usando [[nano]]
```python
import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in >


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + c>

  
flag = str_xor(flag_enc, 'enkidu')
  print('That is correct! Here\'s your flag: ' + flag)
```
>Nos damos cuenta que la Identación es incorrecta en el *print* y corregimos el error, guardando los cambios con *ctrl + x -> yes*

```bash
AsumomezaC-picoctf@webshell:~$ python3 fixme1.py
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_09ee727a}
```
>Finalmente ejecutamos el archivo y obtenemos la bandera
## Respuesta
picoCTF{1nd3nt1ty_cr1515_09ee727a}