#Software #Hacking #WebExplotation #Computación 
# Definición
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/137/disk.flag.img.gz)
# Hints
(None)
# Solución
Descargamos el [[Archivo .img]] usando [[wget]].
```bash
┌──(kali㉿kali)-[~/apr]  
└─$ wget [https://artifacts.picoctf.net/c/137/disk.flag.img.gz](https://artifacts.picoctf.net/c/137/disk.flag.img.gz)  
--2025-05-07 14:55:47--  [https://artifacts.picoctf.net/c/137/disk.flag.img.gz](https://artifacts.picoctf.net/c/137/disk.flag.img.gz)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.100, 3.161.55.61, 3.161.55.26, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.100|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 47534568 (45M) [application/octet-stream]  
Saving to: ‘disk.flag.img.gz’  
  
disk.flag.img.gz    100%[================>]  45.33M  12.4MB/s    in 3.8s      
  

2025-05-07 14:56:00 (11.9 MB/s) - ‘disk.flag.img.gz’ saved [47534568/47534568]
```

Ahora descomprimimos el archivo:
```bash
┌──(kali㉿kali)-[~/apr]  
└─$ gzip -d disk.flag.img.gz  
```
                                                                               
Usamos [[mmls]] para ver el contenido del archivo.
```bash
┌──(kali㉿kali)-[~/apr]  
└─$ mmls disk.flag.img        
DOS Partition Table  
Offset Sector: 0  
Units are in 512-byte sectors  
  
      Slot      Start        End          Length       Description  
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)  
001:  -------   0000000000   0000002047   0000002048   Unallocated  
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)  
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)  
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
```
  
Utilizamos el comando [[fls]] para ver la estructura interna del archivo descargada.
```bash
fls disk.flag.img -o 360448 -r
```

Finalmente empleamos [[icat]] para conseguir la bandera:
```bash
┌──(kali㉿kali)-[~/apr]  
└─$ icat disk.flag.img -o 360448 2371  
picoCTF{by73_5urf3r_adac6cb4}
```
## Respuesta
picoCTF{by73_5urf3r_adac6cb4}