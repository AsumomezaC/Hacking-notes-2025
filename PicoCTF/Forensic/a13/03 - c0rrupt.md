#Software #Hacking #WebExplotation #Computación 
# Definición
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.
# Hints
- Try fixing the file header
# Solución
Descargamos el archivo con [[wget]]:  
```bash
┌──(kali㉿kali)-[~]  
└─$ wget [https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery)        
--2025-04-28 14:46:15--  [https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 202940 (198K) [application/octet-stream]  
Saving to: ‘mystery’  
  
mystery             100%[================>] 198.18K   182KB/s    in 1.1s      
  
2025-04-28 14:46:25 (182 KB/s) - ‘mystery’ saved [202940/202940]

```
>Con experiencia podemos saber que se trata de una imagen, por lo que hacemos una copia de seguridad y modificamos el archivo con hexeditor, haciendo que los [[Magic Bytes]] coincidan:

```bash
┌──(kali㉿kali)-[~]  
└─$ cp mystery flag.png

┌──(kali㉿kali)-[~]  
└─$ hexeditor flag.png                    
                                                                               
┌──(kali㉿kali)-[~]  
└─$ xxd -l flag.png    

┌──(kali㉿kali)-[~]  
└─$ xxd -l 100 flag.png  
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4322 4452  .PNG........C"DR  
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..  
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......  
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...  
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I  
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?  
00000060: 8e64 cd71                                .d.q  
                                                                               
┌──(kali㉿kali)-[~]  
└─$ file flag.png  
flag.png: data
```

Sigue fallando por lo que nos apoyamos de la herramienta [[PNGCheck]] para solucionar todos los problemas que tenga la imagen:
```

```
Y finalmente obtenemos la bandera.
## Respuesta
picoCTF{c0rrupt1on_1847995}