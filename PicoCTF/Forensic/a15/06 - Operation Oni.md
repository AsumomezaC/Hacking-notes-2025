#Software #Hacking #WebExplotation #Computación 
# Definición
Download this disk image, find the key and log into the remote machine.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download disk image](https://artifacts.picoctf.net/c/69/disk.img.gz)
- Remote machine: `ssh -i key_file -p 58864 ctf-player@saturn.picoctf.net`
# Hints
(None)
# Solución
Primero descargamos la imagen con [[wget]]
```bash
┌──(kali㉿kali)-[~/oni]  
└─$ wget [https://artifacts.picoctf.net/c/69/disk.img.gz](https://artifacts.picoctf.net/c/69/disk.img.gz)        
--2025-05-07 15:25:13--  [https://artifacts.picoctf.net/c/69/disk.img.gz](https://artifacts.picoctf.net/c/69/disk.img.gz)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.100, 3.161.55.26, 3.161.55.64, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.100|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 48132743 (46M) [application/octet-stream]  
Saving to: ‘disk.img.gz’  
  
disk.img.gz         100%[================>]  45.90M  13.3MB/s    in 3.7s      
  
2025-05-07 15:25:25 (12.5 MB/s) - ‘disk.img.gz’ saved [48132743/48132743]   
```
                                                                               
Después [[Descompresión de archivos|descomprimos]] el archivo.
```bash
┌──(kali㉿kali)-[~/oni]  
└─$ gzip -d disk.img.gz      
```
                                                                               
Vemos las particiones internas con [[mmls]].
```bash
┌──(kali㉿kali)-[~/oni]  
└─$ mmls disk.img      
DOS Partition Table  
Offset Sector: 0  
Units are in 512-byte sectors  
  
      Slot      Start        End          Length       Description  
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)  
001:  -------   0000000000   0000002047   0000002048   Unallocated  
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)  

003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
```

 Vemos su contenido con [[fls]].  
```bash
┌──(kali㉿kali)-[~/oni]  
└─$ fls disk.img -o 206848      
d/d 458:        home  
d/d 11: lost+found  
d/d 12: boot  
d/d 13: etc  
d/d 79: proc  
d/d 80: dev  
d/d 81: tmp  
d/d 82: lib  
d/d 85: var  
d/d 94: usr  
d/d 104:        bin  
d/d 118:        sbin  
d/d 464:        media  
d/d 468:        mnt  
d/d 469:        opt  
d/d 470:        root  
d/d 471:        run  
d/d 473:        srv  
d/d 474:        sys  
V/V 33049:      $OrphanFiles  
```
                                                                               
Usamos [[icat]] para conseguir la llave para la [[Desencriptación]].
```bash
┌──(kali㉿kali)-[~/oni]  
└─$ fls disk.img -o 206848 470  
r/r 2344:       .ash_history  
d/d 3916:       .ssh  
                                                                               
┌──(kali㉿kali)-[~/oni]  
└─$ fls disk.img -o 206848 3916  
r/r 2345:       id_ed25519  
r/r 2346:       id_ed25519.pub  
                                                                               
┌──(kali㉿kali)-[~/oni]  
└─$ icat disk.img -o 206848 2345 > key_file  
```
                                                                               
Finalmente realizamos una conexión [[SSH]] y una vez dentro obtenemos la bandera con un [[chmod]]
```bash
┌──(kali㉿kali)-[~/oni]  
└─$ ssh -i key_file -p 56059 [ctf-player@saturn.picoctf.net](mailto:ctf-player@saturn.picoctf.net)  
The authenticity of host '[[saturn.picoctf.net](http://saturn.picoctf.net/)]:56059 ([13.59.203.175]:56059)' can't be established.  
ED25519 key fingerprint is SHA256:XBSvB1lk28EctsAVdKJtsl0A7C5bonqPrvHCYH8aEy4.  
This key is not known by any other names.  
Are you sure you want to continue connecting (yes/no/[fingerprint])? y  
Please type 'yes', 'no' or the fingerprint: yes  
Warning: Permanently added '[[saturn.picoctf.net](http://saturn.picoctf.net/)]:56059' (ED25519) to the list of known hosts.  
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@  
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @  
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@  
Permissions 0664 for 'key_file' are too open.  
It is required that your private key files are NOT accessible by others.  
This private key will be ignored.  
Load key "key_file": bad permissions  
[ctf-player@saturn.picoctf.net](mailto:ctf-player@saturn.picoctf.net)'s password:  
                                                                               
┌──(kali㉿kali)-[~/oni]  
└─$ chmod 600 key_file  
                                                                               
┌──(kali㉿kali)-[~/oni]  
└─$ ssh -i key_file -p 56059 [ctf-player@saturn.picoctf.net](mailto:ctf-player@saturn.picoctf.net)  
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)  
  
 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com/)  
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com/)  
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)  
  
This system has been minimized by removing packages and content that are  
not required on a system that users do not log into.  
  
To restore this content, you can run the 'unminimize' command.  
  
The programs included with the Ubuntu system are free software;  
the exact distribution terms for each program are described in the  
individual files in /usr/share/doc/*/copyright.  
  
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by  
applicable law.  
  
ctf-player@challenge:~$ cat flag.txt  
picoCTF{k3y_5l3u7h_339601ed}ctf-player@challenge:~$ Connection to [saturn.picoctf.net](http://saturn.picoctf.net/) closed by remote host.  
Connection to [saturn.picoctf.net](http://saturn.picoctf.net/) closed.
```
## Respuesta
picoCTF{k3y_5l3u7h_339601ed}