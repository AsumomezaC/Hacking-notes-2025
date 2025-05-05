#Software #Hacking #WebExplotation #Computación 
# Definición
We found this [file](https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n). Recover the flag.
# Hints
- Weird that it won't display right...
# Solución
Descargamos el archivo usando [[wget]]
```bash
┌──(kali㉿kali)-[~/tun]  
└─$ wget [https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n](https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n)  
--2025-05-05 14:45:38--  [https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n](https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n)  
Resolving [mercury.picoctf.net](http://mercury.picoctf.net/) ([mercury.picoctf.net](http://mercury.picoctf.net/))... 18.189.209.142  
Connecting to [mercury.picoctf.net](http://mercury.picoctf.net/) ([mercury.picoctf.net](http://mercury.picoctf.net/))|18.189.209.142|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2893454 (2.8M) [application/octet-stream]  
Saving to: ‘tunn3l_v1s10n’  
  
tunn3l_v1s10n       100%[================>]   2.76M   320KB/s    in 8.7s      
  

2025-05-05 14:45:56 (326 KB/s) - ‘tunn3l_v1s10n’ saved [2893454/2893454]
```

  Como sabemos que el archivo esta dañado, checamos los [[Magic Bytes]] del [[Archivo .BMP]]
```bash
┌──(kali㉿kali)-[~/tun]  
└─$ xxd -l 100 tunn3l_v1s10n  
00000000: 424d 8e26 2c00 0000 0000 bad0 0000 bad0  BM.&,...........  
00000010: 0000 6e04 0000 3201 0000 0100 1800 0000  ..n...2.........  
00000020: 0000 5826 2c00 2516 0000 2516 0000 0000  ..X&,.%...%.....  
00000030: 0000 0000 0000 231a 1727 1e1b 2920 1d2a  ......#..'..) .*  
00000040: 211e 261d 1a31 2825 352c 2933 2a27 382f  !.&..1(%5,)3*'8/  
00000050: 2c2f 2623 332a 262d 2420 3b32 2e32 2925  ,/&#3*&-$ ;2.2)%  

00000060: 3027 2333                                0'#3
```

Modificamos loa magi bytes para que coincidan
```bash
┌──(kali㉿kali)-[~/tun]  
└─$ hexeditor flag.bmp  
```

>28 00  00 00 28 00

Después de eso abrimos la imagen que conseguimos:
```bash
┌──(kali㉿kali)-[~/tun]  
└─$ file flag.bmp  
flag.bmp: PC bitmap, Windows 3.x format, 1134 x 306 x 24, image size 2893400, resolution 5669 x 5669 px/m, cbSize 2893454, bits offset 40  
                                                                               
┌──(kali㉿kali)-[~/tun]  
└─$ open flag.bmp  
```

Al abrirlo no encontramos la bandera, por lo que modificamos la altura de la imagen con hexeditor, para encontrar la bandera oculta.
## Respuesta
picoCTF{qu1t3_a_v13w_2020}