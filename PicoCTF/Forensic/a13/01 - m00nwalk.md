#Software #Hacking #WebExplotation #Computación 
# Definición
Decode this [message](https://jupiter.challenges.picoctf.org/static/d6fcea5e3c6433680ea4f914e24fab61/message.wav) from the moon.
# Hints
- How did pictures from the moon landing get sent back to Earth?
- What is the CMU mascot?, that might help select a RX option
# Solución
Primero descargamos el archivo con [[wget]]:
```bash
AsumomezaC-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/d6fcea5e3c6433680ea4f914e24fab61/message.wav
--2025-04-28 18:10:51--  https://jupiter.challenges.picoctf.org/static/d6fcea5e3c6433680ea4f914e24fab61/message.wav
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11066998 (11M) [application/octet-stream]
Saving to: 'message.wav.1'

message.wav.1                                              100%[======================================================================================================================================>]  10.55M  1.85MB/s    in 5.8s    

2025-04-28 18:10:57 (1.82 MB/s) - 'message.wav.1' saved [11066998/11066998]
```

Hacemos caso a la pista y nos damos cuenta que ocupamos un [[SSTV Decoder]], lo descargamos y lo usamos para conseguir la imagen.
```python
┌──(kali㉿kali)-[/opt]  
└─$ sudo git clone [https://github.com/colaclanth/sstv.git](https://github.com/colaclanth/sstv.git)  
[sudo] password for kali:  
Cloning into 'sstv'...  
remote: Enumerating objects: 221, done.  
remote: Counting objects: 100% (59/59), done.  
remote: Compressing objects: 100% (10/10), done.  
remote: Total 221 (delta 51), reused 49 (delta 49), pack-reused 162 (from 1)  
Receiving objects: 100% (221/221), 1.01 MiB | 1.15 MiB/s, done.  
Resolving deltas: 100% (139/139), done.  
                                                                             
┌──(kali㉿kali)-[/opt]  
└─$ cd /home  
                                                                               
┌──(kali㉿kali)-[/home]  
└─$ dir  
kali  
                                                                               
┌──(kali㉿kali)-[/home]  
└─$ cd kali  
                                                                               
┌──(kali㉿kali)-[~]  
└─$ sstv -d message.wav -o result.png
```

>Este imagen contiene la bandera: picoCTF{beep_boop_im_in_space}
## Respuesta
picoCTF{beep_boop_im_in_space}