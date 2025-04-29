#Software #Hacking #WebExplotation #Computación 
# Definición
Find the flag in this [picture](https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png).
# Hints
- What does meta mean in the context of files?
- Ever heard of metadata?
# Solución
Primero obtenemos el archivo usando [[wget]]
```bash
┌──(kali㉿kali)-[~]  
└─$ wget [https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png](https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png)  
--2025-04-07 14:20:04--  [https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png](https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 108795 (106K) [application/octet-stream]  
Saving to: ‘pico_img.png’  
  
pico_img.png        100%[================>] 106.25K   429KB/s    in 0.2s      
  
2025-04-07 14:20:13 (429 KB/s) - ‘pico_img.png’ saved [108795/108795]  
```
  
### Solución 1
Usando [[Strings]] obtenemos la bandera.
```bash
┌──(kali㉿kali)-[~]  
└─$ strings -n18 pico_img.png  
"iTXtXML:com.adobe.xmp  
" id="W5M0MpCehiHzreSzNTczkc9d"?> <x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27        "> <rdf:RDF xmlns:rdf="[http://www.w3.org/1999/02/22-rdf-syntax-ns#](http://www.w3.org/1999/02/22-rdf-syntax-ns#)"> <rdf:Description rdf:about="" xmlns:xmp="[http://ns.adobe.com/xap/1.0/](http://ns.adobe.com/xap/1.0/)" xmlns:xmpMM="[http://ns.adobe.com/xap/1.0/mm/](http://ns.adobe.com/xap/1.0/mm/)" xmlns:stRef="[http://ns.adobe.com/xap/1.0/sType/ResourceRef#](http://ns.adobe.com/xap/1.0/sType/ResourceRef#)" xmp:CreatorTool="Adobe Photoshop CS6 (Windows)" xmpMM:InstanceID="xmp.iid:A5566E73B2B811E8BC7F9A4303DF1F9B" xmpMM:DocumentID="xmp.did:A5566E74B2B811E8BC7F9A4303DF1F9B"> <xmpMM:DerivedFrom stRef:instanceID="xmp.iid:A5566E71B2B811E8BC7F9A4303DF1F9B" stRef:documentID="xmp.did:A5566E72B2B811E8BC7F9A4303DF1F9B"/> </rdf:Description> </rdf:RDF> </x:xmpmeta> <?xpacket end="r"?>  
picoCTF{s0_m3ta_d8944929}K
```

### Solución 2
Obtenemos los [[ic/comunes/Objetos/Metadatos]] usando [[exiftool]]
```bash
┌──(kali㉿kali)-[~]  
└─$ exiftool pico_img.png  
ExifTool Version Number         : 13.10  
File Name                       : pico_img.png  
Directory                       : .  
File Size                       : 109 kB  
File Modification Date/Time     : 2020:10:26 14:38:23-04:00  
File Access Date/Time           : 2025:04:07 14:21:00-04:00  
File Inode Change Date/Time     : 2025:04:07 14:20:13-04:00  
File Permissions                : -rw-rw-r--  
File Type                       : PNG  
File Type Extension             : png  
MIME Type                       : image/png  
Image Width                     : 600  
Image Height                    : 600  
Bit Depth                       : 8  
Color Type                      : RGB  
Compression                     : Deflate/Inflate  
Filter                          : Adaptive  
Interlace                       : Noninterlaced  
Software                        : Adobe ImageReady  
XMP Toolkit                     : Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27  
Creator Tool                    : Adobe Photoshop CS6 (Windows)  
Instance ID                     : xmp.iid:A5566E73B2B811E8BC7F9A4303DF1F9B  
Document ID                     : xmp.did:A5566E74B2B811E8BC7F9A4303DF1F9B  
Derived From Instance ID        : xmp.iid:A5566E71B2B811E8BC7F9A4303DF1F9B  
Derived From Document ID        : xmp.did:A5566E72B2B811E8BC7F9A4303DF1F9B  
Warning                         : [minor] Text/EXIF chunk(s) found after PNG IDAT (may be ignored by some readers)  
Artist                          : picoCTF{s0_m3ta_d8944929}  
Image Size                      : 600x600  
Megapixels                      : 0.360
```
## Respuesta
picoCTF{s0_m3ta_d8944929}