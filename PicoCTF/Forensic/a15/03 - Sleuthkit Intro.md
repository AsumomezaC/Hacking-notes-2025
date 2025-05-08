#Software #Hacking #WebExplotation #Computación 
# Definición
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.[Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)Access checker program: `nc saturn.picoctf.net 64128`
# Hints
- (None)
# Solución
Comenzamos descargando el archivo con [[wget]].
```bash
┌──(kali㉿kali)-[~/sleu]  
└─$ wget [https://artifacts.picoctf.net/c/164/disk.img.gz](https://artifacts.picoctf.net/c/164/disk.img.gz)  
--2025-05-07 14:47:48--  [https://artifacts.picoctf.net/c/164/disk.img.gz](https://artifacts.picoctf.net/c/164/disk.img.gz)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.64, 3.161.55.26, 3.161.55.100, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.64|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 29714372 (28M) [application/octet-stream]  
Saving to: ‘disk.img.gz’  
  
disk.img.gz         100%[================>]  28.34M  12.1MB/s    in 2.4s      
  
2025-05-07 14:48:09 (12.1 MB/s) - ‘disk.img.gz’ saved [29714372/29714372]  
```
  
 Descomprimimos el archivo:                                                                              
```bash
┌──(kali㉿kali)-[~/sleu]  
└─$ gzip -d disk.img.gz              
```
                                                                               
Usamos [[mmls]] para observar la información sobre la imagen que descomprimimos.

```bash
┌──(kali㉿kali)-[~/sleu]  
└─$ mmls disk.img              
DOS Partition Table  
Offset Sector: 0  
Units are in 512-byte sectors  
  
      Slot      Start        End          Length       Description  
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)  
001:  -------   0000000000   0000002047   0000002048   Unallocated  
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```

Nos conectamos usando [[NET CAT (nc)]]  al [[Servidor]], usando los datos obtenidos por el paso anterior.
```bash
┌──(kali㉿kali)-[~]  
└─$ nc [saturn.picoctf.net](http://saturn.picoctf.net/) 56692  
What is the size of the Linux partition in the given disk image?  
Length in sectors: 202752  
202752  
Great work!  
picoCTF{mm15_f7w!}
```
## Respuesta
picoCTF{mm15_f7w!}