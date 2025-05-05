#Software #Hacking #WebExplotation #Computación 
# Definición
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/2978e1270538613cd8181c7b0dabe9bd/dolls.jpg)
# Hints
- Wait, you can hide files inside files? But how do you find them?
- Make sure to submit the flag as picoCTF{XXXXX}
# Solución
Descargamos la imagen usando [[wget]]
```bash
┌──(kali㉿kali)-[~/mat]  
└─$ wget [https://mercury.picoctf.net/static/2978e1270538613cd8181c7b0dabe9bd/dolls.jpg](https://mercury.picoctf.net/static/2978e1270538613cd8181c7b0dabe9bd/dolls.jpg)                
--2025-05-05 14:37:46--  [https://mercury.picoctf.net/static/2978e1270538613cd8181c7b0dabe9bd/dolls.jpg](https://mercury.picoctf.net/static/2978e1270538613cd8181c7b0dabe9bd/dolls.jpg)  
Resolving [mercury.picoctf.net](http://mercury.picoctf.net/) ([mercury.picoctf.net](http://mercury.picoctf.net/))... 18.189.209.142  
Connecting to [mercury.picoctf.net](http://mercury.picoctf.net/) ([mercury.picoctf.net](http://mercury.picoctf.net/))|18.189.209.142|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 651622 (636K) [application/octet-stream]  
Saving to: ‘dolls.jpg’  
  
dolls.jpg           100%[================>] 636.35K  1.03MB/s    in 0.6s      
  
2025-05-05 14:37:55 (1.03 MB/s) - ‘dolls.jpg’ saved [651622/651622]  
```
  
 Utilizamos [[Binwalk]] para detectar si hay archivos escondidos dentro de la imagen.                                                                             
```bash
┌──(kali㉿kali)-[~/mat]  
└─$ binwalk dolls.jpg      
  
DECIMAL       HEXADECIMAL     DESCRIPTION  
--------------------------------------------------------------------------------  
0             0x0             PNG image, 594 x 1104, 8-bit/color RGBA, non-interlaced  
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8  
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378942, uncompressed size: 383937, name: base_images/2_c.jpg  
651600        0x9F150         End of Zip archive, footer length: 22  
```
  
 Utilizamos 'unzip', una vez que detectamos que se trata de paquetes empaquetados entre sí, hasta encontrar la bandera.                                                                          
```bash
┌──(kali㉿kali)-[~/mat]  
└─$ unzip dolls.jpg  
Archive:  dolls.jpg  
warning [dolls.jpg]:  272492 extra bytes at beginning or within zipfile  
  (attempting to process anyway)  
  inflating: base_images/2_c.jpg      
                                                                               
┌──(kali㉿kali)-[~/mat]  
└─$ cd base_images  
                                                                               
┌──(kali㉿kali)-[~/mat/base_images]  
└─$ ls                      
2_c.jpg  
                                                                               
┌──(kali㉿kali)-[~/mat/base_images]  
└─$ unzip 2_c.jpg    
Archive:  2_c.jpg  
warning [2_c.jpg]:  187707 extra bytes at beginning or within zipfile  
  (attempting to process anyway)  
  inflating: base_images/3_c.jpg      
                                                                               
┌──(kali㉿kali)-[~/mat/base_images]  
└─$ cd base_images  
                                                                               
┌──(kali㉿kali)-[~/mat/base_images/base_images]  
└─$ unzip 3_c.jpg  
Archive:  3_c.jpg  
warning [3_c.jpg]:  123606 extra bytes at beginning or within zipfile  
  (attempting to process anyway)  
  inflating: base_images/4_c.jpg      
                                                                               
┌──(kali㉿kali)-[~/mat/base_images/base_images]  
└─$ cd base_images  
                                                                               
┌──(kali㉿kali)-[~/mat/base_images/base_images/base_images]  
└─$ unzip 4_c.jpg  
Archive:  4_c.jpg  
warning [4_c.jpg]:  79578 extra bytes at beginning or within zipfile  
  (attempting to process anyway)  
  inflating: flag.txt                 
                                                                               
┌──(kali㉿kali)-[~/mat/base_images/base_images/base_images]  
└─$ ls  
4_c.jpg  flag.txt  
                                                                               
┌──(kali㉿kali)-[~/mat/base_images/base_images/base_images]  
└─$ cat flag.txt          
picoCTF{4cf7ac000c3fb0fa96fb92722ffb2a32}
```
## Respuesta
picoCTF{4cf7ac000c3fb0fa96fb92722ffb2a32}