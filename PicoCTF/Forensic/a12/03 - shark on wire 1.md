#Software #Hacking #WebExplotation #Computación 
# Definición
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.
# Hints
- Try using a tool like Wireshark
- What are streams?
# Solución
Primero descargamos el archivo con [[wget]].
```bash
┌──(kali㉿kali)-[~]  
└─$ wget [https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap)  
--2025-04-07 14:30:48--  [https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 239455 (234K) [application/octet-stream]  
Saving to: ‘capture.pcap’  
  
capture.pcap        100%[================>] 233.84K   253KB/s    in 0.9s      
  
2025-04-07 14:30:58 (253 KB/s) - ‘capture.pcap’ saved [239455/239455]  
```
  
 Y vemos que descargamos un [[Archivo .pcap]]
                                                                               
```bash
┌──(kali㉿kali)-[~]  
└─$ file capture.pcap  
capture.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144) 

┌──(kali㉿kali)-[~]  
└─$ sudo apt install wireshark  
[sudo] password for kali:  
wireshark is already the newest version (4.4.5-1).  
wireshark set to manually installed.  
The following packages were automatically installed and are no longer required:  
  libflac12t64   libglapi-mesa         ruby-zeitwerk  
  libgeos3.13.0  python3-setproctitle  
Use 'sudo apt autoremove' to remove them.  
  
Summary:  
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
```

Entramos a [[wireshark]]-antes nos cercioramos que este instalado-, y de ahí seguimos los archivos udp, encontramos la bandera en el stream 6.
## Respuesta
picoCTF{StaT31355_636f6e6e}