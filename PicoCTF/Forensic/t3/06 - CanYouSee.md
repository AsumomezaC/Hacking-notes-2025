kali#Software #Hacking #WebExplotation #Computación 
# Definición
How about some hide and seek?Download this file [here](https://artifacts.picoctf.net/c_titan/4/unknown.zip).
# Hints
- How can you view the information about the picture?
- If something isn't in the expected form, maybe it deserves attention?
# Solución
```bash
Primero descargamos el archivo con [[wget]].
┌──(kali㉿kali)-[~/can]  
└─$ wget [https://artifacts.picoctf.net/c_titan/4/unknown.zip](https://artifacts.picoctf.net/c_titan/4/unknown.zip)    
--2025-05-10 18:39:13--  [https://artifacts.picoctf.net/c_titan/4/unknown.zip](https://artifacts.picoctf.net/c_titan/4/unknown.zip)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.61, 3.161.55.64, 3.161.55.100, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.61|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2252173 (2.1M) [application/octet-stream]  
Saving to: ‘unknown.zip’  
  
unknown.zip         100%[================>]   2.15M  7.01MB/s    in 0.3s      
  
2025-05-10 18:39:19 (7.01 MB/s) - ‘unknown.zip’ saved [2252173/2252173]  

┌──(kali㉿kali)-[~/can]  
└─$ ls  
unknown.zip  
```
  
 Luego [[Descompresión de archivos|descomprimimos el archivo]].                                                                                                                                                            
```bash
┌──(kali㉿kali)-[~/can]  
└─$ unzip unknown.zip    
Archive:  unknown.zip  
  inflating: ukn_reality.jpg          
```
                                                                               
Usamos [[exiftool]] para ver los [[Metadatos]] del archivo.
```bash
┌──(kali㉿kali)-[~/can]  
└─$ exiftool ukn_reality.jpg  
ExifTool Version Number         : 13.10  
File Name                       : ukn_reality.jpg  
Directory                       : .  
File Size                       : 2.3 MB  
File Modification Date/Time     : 2024:02:15 17:40:14-05:00  
File Access Date/Time           : 2024:02:15 17:40:14-05:00  
File Inode Change Date/Time     : 2025:05:10 18:39:26-04:00  
File Permissions                : -rw-r--r--  
File Type                       : JPEG  
File Type Extension             : jpg  
MIME Type                       : image/jpeg  
JFIF Version                    : 1.01  
Resolution Unit                 : inches  
X Resolution                    : 72  
Y Resolution                    : 72  
XMP Toolkit                     : Image::ExifTool 11.88  
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==  
Image Width                     : 4308  
Image Height                    : 2875  
Encoding Process                : Baseline DCT, Huffman coding  
Bits Per Sample                 : 8  
Color Components                : 3  
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)  
Image Size                      : 4308x2875  

Megapixels                      : 12.4
```

Observamos una url muy extraña (similar a la [[Codificación Base 64]]), por lo que usamos [cyberchef](https://cyberchef.org/) para [[Decodificador|decodificarla]], y obtenemos la bandera.
## Respuesta
picoCTF{ME74D47A_HIDD3N_deca06fb}