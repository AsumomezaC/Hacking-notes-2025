#Software #Hacking #WebExplotation #Computación 
# Definición
There's something in the [building](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png). Can you retrieve the flag?
# Hints
- There is data encoded somewhere... there might be an online decoder.
# Solución
Primero descargamos el archivo con [[wget]]
```bash
┌──(kali㉿kali)-[~]  
└─$ wget [https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png)  
--2025-04-07 14:57:38--  [https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 625219 (611K) [application/octet-stream]  
Saving to: ‘buildings.png’  
  
buildings.png       100%[================>] 610.57K   279KB/s    in 2.2s      
  
2025-04-07 14:57:49 (279 KB/s) - ‘buildings.png’ saved [625219/625219]  
```
  
Iniciamos probando suerte con [[Strings]] pero no encontramos nada de valor.                                                                               
```bash
┌──(kali㉿kali)-[~]  
└─$ strings -n18 buildings.png  
FDDDDDDDDDDDDUUUUUUUM  
TUUUUUDTETDDDDDD<""""  
GDDDDDDDDTEUUEUUUU  
UUUUUUUUUUS333333333333  
LUUUUUUUUUDTDDDDDDD  
FDDDDDDDDDDDTUEUUUU  
SUUUUUU55US3U3353335S3SSUUUUUu  
```

Entonces lo intentamos con[[exiftool]]
```bash
┌──(kali㉿kali)-[~]  
└─$ exiftool buildings.png  
ExifTool Version Number         : 13.10  
File Name                       : buildings.png  
Directory                       : .  
File Size                       : 625 kB  
File Modification Date/Time     : 2020:10:26 14:30:20-04:00  
File Access Date/Time           : 2025:04:07 14:58:04-04:00  
File Inode Change Date/Time     : 2025:04:07 14:57:49-04:00  
File Permissions                : -rw-rw-r--  
File Type                       : PNG  
File Type Extension             : png  
MIME Type                       : image/png  
Image Width                     : 657  
Image Height                    : 438  
Bit Depth                       : 8  
Color Type                      : RGB with Alpha  
Compression                     : Deflate/Inflate  
Filter                          : Adaptive  
Interlace                       : Noninterlaced  
Image Size                      : 657x438  
Megapixels                      : 0.288
```

  
Como esta codificado (usando [[Esteganografía]]), usamos un decodificador online para conseguir la contraseña: [https://stylesuxx.github.io/steganography/](https://stylesuxx.github.io/steganography/)
## Respuesta
picoCTF{h1d1ng_1n_th3_b1t5}