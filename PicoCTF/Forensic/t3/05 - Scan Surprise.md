#Software #Hacking #WebExplotation #Computación 
# Definición
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/14/challenge.zip)

The same files are accessible via SSH here:`ssh -p 55233 ctf-player@atlas.picoctf.net`Using the password `84b12bae`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
# Hints
- QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
- Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
- If you don't have access to a phone, you can also use zbar-tools to convert an image to text
# Solución
Primero descargamos el archivo con [[wget]].
```bash
┌──(kali㉿kali)-[~]  
└─$ wget [https://artifacts.picoctf.net/c_atlas/14/challenge.zip](https://artifacts.picoctf.net/c_atlas/14/challenge.zip)  
--2025-05-10 15:06:51--  [https://artifacts.picoctf.net/c_atlas/14/challenge.zip](https://artifacts.picoctf.net/c_atlas/14/challenge.zip)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.100, 3.161.55.61, 3.161.55.26, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.100|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 742 [application/octet-stream]  
Saving to: ‘challenge.zip’  
  
challenge.zip       100%[================>]     742  --.-KB/s    in 0s        
  
2025-05-10 15:06:57 (5.79 MB/s) - ‘challenge.zip’ saved [742/742]  
```
  
Al estar comprimido, lo [[Descompresión de archivos|descomprimimos]].                                                                               
```bash
┌──(kali㉿kali)-[~]  
└─$ unzip challenge.zip  
Archive:  challenge.zip  
   creating: home/ctf-player/drop-in/  
 extracting: home/ctf-player/drop-in/flag.png    
```
                                                                               
Nos movemos a la carpeta donde se descomprimió y lo abrimos.                                                                            
```bash
┌──(kali㉿kali)-[~]  
└─$ cd home/ctf-player/drop-in/        
                                                                               
┌──(kali㉿kali)-[~/home/ctf-player/drop-in]  
└─$ open flag.png
```
Al abrirlo nos muestra un [[código qr]]. Y al escanearlo vemos la bandera.
## Respuesta
picoCTF{p33k_@_b00_0194a007}