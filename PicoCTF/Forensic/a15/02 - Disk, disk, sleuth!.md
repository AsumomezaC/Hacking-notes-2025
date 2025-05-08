#Software #Hacking #WebExplotation #Computación 
# Definición
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz)
# Hints
- Have you ever used `file` to determine what a file was?
- Relevant terminal-fu in picoGym: https://play.picoctf.org/practice/challenge/85
- Mastering this terminal-fu would enable you to find the flag in a single command: https://play.picoctf.org/practice/challenge/48
- Using your own computer, you could use qemu to boot from this disk!

# Solución
Primero nos aseguramos que tengamos ya instalado [[sleuthkit]].
```bash
┌──(kali㉿kali)-[~]  
└─$ sudo apt install sleuthkit  
[sudo] password for kali:  
sleuthkit is already the newest version (4.12.1+dfsg-0kali6).  
sleuthkit set to manually installed.  
The following packages were automatically installed and are no longer required:  
  libflac12t64   libglapi-mesa         ruby-zeitwerk  
  libgeos3.13.0  python3-setproctitle  
Use 'sudo apt autoremove' to remove them.  
  
Summary:  

  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
```

Descargamos el archivo con [[wget]], y lo descomprimimos:
```bash
┌──(kali㉿kali)-[~]  
└─$ wget [https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz)  
--2025-05-07 14:40:08--  [https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz)  
Resolving [mercury.picoctf.net](http://mercury.picoctf.net/) ([mercury.picoctf.net](http://mercury.picoctf.net/))... 18.189.209.142  
Connecting to [mercury.picoctf.net](http://mercury.picoctf.net/) ([mercury.picoctf.net](http://mercury.picoctf.net/))|18.189.209.142|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 29768911 (28M) [application/octet-stream]  
Saving to: ‘dds1-alpine.flag.img.gz’  
  
[dds1-alpine.flag.im](http://dds1-alpine.flag.im/) 100%[================>]  28.39M  3.60MB/s    in 8.7s      
  
2025-05-07 14:40:25 (3.26 MB/s) - ‘dds1-alpine.flag.img.gz’ saved [29768911/29768911]  
                                                                               
┌──(kali㉿kali)-[~]  
└─$ gzip -d dds1-alpine.flag.img.gz
```

Obtenemos un [[Archivo .img]], y lo extraemos usando el comando [[mmls]]

```bash
┌──(kali㉿kali)-[~]  
└─$ mmls dds1-alpine.flag.img                                                
DOS Partition Table  
Offset Sector: 0  
Units are in 512-byte sectors  
  
      Slot      Start        End          Length       Description  
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)  
001:  -------   0000000000   0000002047   0000002048   Unallocated  
002:  000:000   0000002048   0000262143   0000260096   Linux (0x83)
```
  
Finalmente usamos [[srch_strings]] y [[grep]] para obtener la bandera.
```bash
┌──(kali㉿kali)-[~]  
└─$ srch_strings dds1-alpine.flag.img | grep pico  
ffffffff81399ccf t pirq_pico_get  
ffffffff81399cee t pirq_pico_set  
ffffffff820adb46 t pico_router_probe  
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_267e38f6}
```

> Funciona tambièn con un [[Strings]]
## Respuesta
picoCTF{f0r3ns1c4t0r_n30phyt3_267e38f6}