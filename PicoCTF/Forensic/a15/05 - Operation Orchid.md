#Software #Hacking #WebExplotation #Computación 
# Definición
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/212/disk.flag.img.gz)
# Hints
(None)
# Solución
Descargamos el archivo con [[wget]].
```bash
┌──(kali㉿kali)-[~/orch]  
└─$ wget [https://artifacts.picoctf.net/c/212/disk.flag.img.gz](https://artifacts.picoctf.net/c/212/disk.flag.img.gz)  
--2025-05-07 15:07:00--  [https://artifacts.picoctf.net/c/212/disk.flag.img.gz](https://artifacts.picoctf.net/c/212/disk.flag.img.gz)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.61, 3.161.55.64, 3.161.55.100, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.61|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 44360923 (42M) [application/octet-stream]  
Saving to: ‘disk.flag.img.gz’  
  
disk.flag.img.gz    100%[================>]  42.31M  7.70MB/s    in 5.5s      
  
2025-05-07 15:07:14 (7.72 MB/s) - ‘disk.flag.img.gz’ saved [44360923/44360923]  
```
                                                                               
[[Descompresión de archivos|Descomprimos el archivo]]:
```bash
┌──(kali㉿kali)-[~/orch]  
└─$ gzip -d disk.flag.img.gz  
```
                                                                             
Vemos sus particiones internas con [[mmls]].
```bash
┌──(kali㉿kali)-[~/orch]  
└─$ mmls disk.flag.img  
DOS Partition Table  
Offset Sector: 0  
Units are in 512-byte sectors  
  
      Slot      Start        End          Length       Description  
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)  
001:  -------   0000000000   0000002047   0000002048   Unallocated  
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)  
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)  

004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
```
  
Vemos su acomodo con [[fls]], buscando la bandera.
```bash
┌──(kali㉿kali)-[~/orch]  
└─$ fls disk.flag.img -o 411648      
d/d 460:        home  
d/d 11: lost+found  
d/d 12: boot  
d/d 13: etc  
d/d 81: proc  
d/d 82: dev  
d/d 83: tmp  
d/d 84: lib  
d/d 87: var  
d/d 96: usr  
d/d 106:        bin  
d/d 120:        sbin  
d/d 466:        media  
d/d 470:        mnt  
d/d 471:        opt  
d/d 472:        root  
d/d 473:        run  
d/d 475:        srv  
d/d 476:        sys  
d/d 2041:       swap  
V/V 51001:      $OrphanFiles

┌──(kali㉿kali)-[~/orch]  
└─$ fls disk.flag.img -o 411648 472  
r/r 1875:       .ash_history  
r/r * 1876(realloc):    flag.txt  
r/r 1782:       flag.txt.enc
```

Vemos la bandera con [[icat]] pero vemos que esta [[Encriptación|encriptada]]
```bash
┌──(kali㉿kali)-[~/orch]  
└─$ icat disk.flag.img -o 411648 1782  
Salted__0��!�-6V����0��U��l��&�:�pj_1�0�|�h  
                                           �Ȥ7� ���؎$�'%                         
```

Por lo que la [[Desencriptación|desencriptamos]] usando [[openssl]]:
```bash
┌──(kali㉿kali)-[~/orch]  
└─$ icat disk.flag.img -o 411648 1782 > flag.txt.enc  
                                                                               
┌──(kali㉿kali)-[~/orch]  
└─$ file flag.txt.enc            
flag.txt.enc: openssl enc'd data with salted password  
                                                                               
┌──(kali㉿kali)-[~/orch]  
└─$ icat disk.flag.img -o 411648 1875                
touch flag.txt  
nano flag.txt  
apk get nano  
apk --help  
apk add nano  
nano flag.txt  
openssl  
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567  
shred -u flag.txt  
ls -al  
halt

┌──(kali㉿kali)-[~/orch]  
└─$ openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567  
*** WARNING : deprecated key derivation used.  
Using -iter or -pbkdf2 would be better.  
bad decrypt  
409761449E7F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:107:  
```
                                                                               
Finalmente con un simple [[CAT]] obtenemos la bandera.
```bash
┌──(kali㉿kali)-[~/orch]  
└─$ cat flag.txt  
picoCTF{h4un71ng_p457_0a710765}
```
## Respuesta
picoCTF{h4un71ng_p457_0a710765}