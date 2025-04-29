#Software #Hacking #WebExplotation #Computación 
# Definición
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?
# Hints
- How do operating systems know what kind of file it is? (It's not just the ending!
- Make sure to submit the flag as picoCTF{XXXXX}
# Solución
Primero descargamos el archivo con [[wget]]
```bash
┌──(kali㉿kali)-[~]  
└─$ wget [https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)      
--2025-04-07 14:46:51--  [https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 9984 (9.8K) [application/octet-stream]  
Saving to: ‘flag.txt’  
  
flag.txt            100%[================>]   9.75K  --.-KB/s    in 0s        
  
2025-04-07 14:46:59 (190 MB/s) - ‘flag.txt’ saved [9984/9984]  
```
  Pero al abrirlo vemos cosas extrañas, por lo que verificamos que sea un txt.
                                                                               
```bash
┌──(kali㉿kali)-[~]  
└─$ file flag.txt      
flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced
```
Pero vemos que los [[Magic Bytes]] no corresponde a un txt sino a un png, por lo que modificamos la extensión de archivo.

```bash
┌──(kali㉿kali)-[~]  
└─$ mv flag.txt flag.png  
```

Al entrar a la imagen encontramos la bandera.
## Respuesta
picoCTF{now_you_know_about_extensions}