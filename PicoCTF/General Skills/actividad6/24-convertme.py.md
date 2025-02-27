#Software #Hacking #Principiante
# Definición
Run the Python script and convert the given number from decimal to binary to get the flag.[Download Python script](https://artifacts.picoctf.net/c/22/convertme.py)
# Hints
- Look up a decimal to binary number conversion app on the web or use your computer's calculator!
- The `str_xor` function does not need to be reverse engineered for this challenge.
- If you have Python on your computer, you can download the script normally and run it. Otherwise, use the `wget` command in the webshell.
- To use `wget` in the webshell, first right click on the download link and select 'Copy Link' or 'Copy Link Address'
- Type everything after the dollar sign in the webshell: `$ wget` , then paste the link after the space after `wget` and press enter. This will download the script for you in the webshell so you can run it!
- Type everything after the dollar sign in the webshell: `$ wget` , then paste the link after the space after `wget` and press enter. This will download the script for you in the webshell so you can run it!
- Finally, to run the script, type everything after the dollar sign and then press enter: `$ python3 convertme.py`
# Solución

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/22/convertme.py
--2025-02-20 23:33:31--  https://artifacts.picoctf.net/c/22/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.71, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: 'convertme.py'

convertme.py          100%[======================>]   1.16K  --.-KB/s    in 0s      

2025-02-20 23:33:31 (301 MB/s) - 'convertme.py' saved [1189/1189]

AsumomezaC-picoctf@webshell:~$ python3 convertme.py
If 95 is in decimal base, what is it in binary base?
Answer: 1011111
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_762f748e}
```

>Primero descargamos el archivo usando [[wget]]
>Ejecutamos el archivo con [[Python#Corre un programa desde la terminal de Linux]]
>Usamos [cyberchef](<https://cyberchef.org/#recipe=From_Decimal('Space',false)To_Binary('None',8)>) para conseguir el número, y lo ingresamos en la terminal.
## Respuesta
picoCTF{4ll_y0ur_b4535_762f748e}