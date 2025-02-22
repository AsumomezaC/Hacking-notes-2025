# Definición
Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/6/fixme2.py)
# Hints
- Are equality and assignment the same symbol?
- To view the file in the webshell, do: `$ nano fixme2.py`
- To exit `nano`, press Ctrl and x and follow the on-screen prompts.
- The `str_xor` function does not need to be reverse engineered for this challenge.
# Solución

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/6/fixme2.py
--2025-02-20 23:52:47--  https://artifacts.picoctf.net/c/6/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.18, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py             100%[======================>]   1.00K  --.-KB/s    in 0s      

2025-02-20 23:52:47 (382 MB/s) - 'fixme2.py' saved [1029/1029]

AsumomezaC-picoctf@webshell:~$ nano fixme2.py
```

>Repetimos el procedimiento de [[25-fixme1.py]]

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

# Check that flag is not empty
if flag = "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)
```
En este caso el error es que el *if* esta haciendo una asignación y no una comparación (\==). En este caso guardamos con *ctrl + o* y salimos con *ctrl + x*

```bash
AsumomezaC-picoctf@webshell:~$ python3 fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
```
Ejecutamos el nuevo archivo y obtenemos la bandera
## Respuesta
picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}