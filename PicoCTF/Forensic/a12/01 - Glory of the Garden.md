#Software #Hacking #WebExplotation #Computación 
# Definición
This [garden](https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg) contains more than it seems.
# Hints
- What is a hex editor?
# Solución
Descargamos el archivo que nos dan con [[wget]]  

```bash
┌──(kali㉿kali)-[~]  
└─$ wget [https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg](https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg)  
--2025-04-07 14:11:45--  [https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg](https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2295192 (2.2M) [application/octet-stream]  
Saving to: ‘garden.jpg’  
  
garden.jpg          100%[================>]   2.19M  1.54MB/s    in 1.4s      
  
2025-04-07 14:11:55 (1.54 MB/s) - ‘garden.jpg’ saved [2295192/2295192]
```

Luego usamos [[Strings]] para ver que contiene, y obtenemos la bandera:

```bash
┌──(kali㉿kali)-[~]  
└─$ strings -n18 garden.jpg                
Copyright (c) 1998 Hewlett-Packard Company  
IEC [http://www.iec.ch](http://www.iec.ch/)  
IEC [http://www.iec.ch](http://www.iec.ch/)  
.IEC 61966-2.1 Default RGB colour space - sRGB  
.IEC 61966-2.1 Default RGB colour space - sRGB  
,Reference Viewing Condition in IEC61966-2.1  
,Reference Viewing Condition in IEC61966-2.1  
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz  
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz  
Here is a flag "picoCTF{more_than_m33ts_the_3y3eBdBd2cc}"
```
## Respuesta
picoCTF{more_than_m33ts_the_3y3eBdBd2cc}