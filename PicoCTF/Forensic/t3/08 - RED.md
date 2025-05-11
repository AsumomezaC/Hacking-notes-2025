#Software #Hacking #WebExplotation #Computación 
# Definición
RED, RED, RED, REDDownload the image: [red.png](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png)
# Hints
- The picture seems pure, but is it though?
- Red?Ged?Bed?Aed?
- Check whatever Facebook is called now.
# Solución
Primero descargamos el archivo con [[wget]]
```bash
┌──(kali㉿kali)-[~/red]  
└─$ wget [https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png)  
--2025-05-10 18:48:28--  [https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png)  
Resolving [challenge-files.picoctf.net](http://challenge-files.picoctf.net/) ([challenge-files.picoctf.net](http://challenge-files.picoctf.net/))... 65.9.149.59, 65.9.149.95, 65.9.149.85, ...  
Connecting to [challenge-files.picoctf.net](http://challenge-files.picoctf.net/) ([challenge-files.picoctf.net](http://challenge-files.picoctf.net/))|65.9.149.59|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 796 [application/octet-stream]  
Saving to: ‘red.png’  
  
red.png             100%[================>]     796  --.-KB/s    in 0s        
  
2025-05-10 18:48:34 (4.87 MB/s) - ‘red.png’ saved [796/796]  
```
  
Buscamos datos ocultos del archivo que descargamos usando [[Zsteg]] -siguiendo la pista-.                                                                           
```bash
┌──(kali㉿kali)-[~/red]  
└─$ zsteg red.png        
meta Poem           .. text: "Crimson heart, vibrant and bold,\nHearts flutter at your sight.\nEvenings glow softly red,\nCherries burst with sweet life.\nKisses linger with your warmth.\nLove deep as merlot.\nScarlet leaves falling softly,\nBold in every stroke."  
b1,rgba,lsb,xy      .. text: "cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ=="                      
b1,rgba,msb,xy      .. file: OpenPGP Public Key  
b2,g,lsb,xy         .. text: "ET@UETPETUUT@TUUTD@PDUDDDPE"  
b2,rgb,lsb,xy       .. file: OpenPGP Secret Key  
b2,bgr,msb,xy       .. file: OpenPGP Public Key  
b2,rgba,lsb,xy      .. file: OpenPGP Secret Key  
b2,rgba,msb,xy      .. text: "CIkiiiII"  
b2,abgr,lsb,xy      .. file: OpenPGP Secret Key  
b2,abgr,msb,xy      .. text: "iiiaakikk"  
b3,rgba,msb,xy      .. text: "#wb#wp#7p"  
b3,abgr,msb,xy      .. text: "7r'wb#7p"  

b4,b,lsb,xy         .. file: 0421 Alliant compact executable not stripped
```

Observamos una zona muy particular, similar a la [[Codificación Base 64]], por lo que nos apoyamos de [cyberchef](https://cyberchef.org/) para decodificarla:

picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}

Y obtenemos la bandera.
## Respuesta
picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}