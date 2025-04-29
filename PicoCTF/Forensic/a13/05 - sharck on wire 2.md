#Software #Hacking #WebExplotation #Computación #Redes 
# Definición
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.
# Hints
(None)
# Solución
Primero descargamos el archivo con [[wget]]:
```bash
┌──(kali㉿kali)-[~/sw]
└─$ wget [https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap)  
--2025-04-28 15:18:34--  [https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 112318 (110K) [application/octet-stream]  
Saving to: ‘capture.pcap’  
  
capture.pcap        100%[================>] 109.69K   636KB/s    in 0.2s      
  
2025-04-28 15:18:43 (636 KB/s) - ‘capture.pcap’ saved [112318/112318]  
```

De ahí vemos que obtenemos un [[Archivo .pcap]], por lo que usamos [[Wireshark]] para ver lo que esconde:
```bash
┌──(kali㉿kali)-[~/sw]  
└─$ wireshark capture.pcap  
 ** (wireshark:38035) 15:21:37.456756 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette  
 ** (wireshark:38035) 15:21:37.459004 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ToolButtonPalette  
 ** (wireshark:38035) 15:21:37.459087 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ButtonPalette  
 ** (wireshark:38035) 15:21:37.459141 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::CheckBoxPalette  
 ** (wireshark:38035) 15:21:37.459199 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::RadioButtonPalette  
 ** (wireshark:38035) 15:21:37.459243 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::HeaderPalette  
 ** (wireshark:38035) 15:21:37.459286 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ItemViewPalette  
 ** (wireshark:38035) 15:21:37.459412 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MessageBoxLabelPelette  
 ** (wireshark:38035) 15:21:37.459494 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TabBarPalette  
 ** (wireshark:38035) 15:21:37.459554 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::LabelPalette  
 ** (wireshark:38035) 15:21:37.459657 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::GroupBoxPalette  
 ** (wireshark:38035) 15:21:37.459698 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MenuPalette  
 ** (wireshark:38035) 15:21:37.459730 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MenuBarPalette  
 ** (wireshark:38035) 15:21:37.459762 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextEditPalette  
 ** (wireshark:38035) 15:21:37.459793 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextEditPalette  
 ** (wireshark:38035) 15:21:37.459885 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextLineEditPalette  
 ** (wireshark:38035) 15:21:37.459932 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ToolTipPalette  
 ** (wireshark:38035) 15:21:37.460015 [GUI ECHO] -- virtual QVariant Qt6CTPlatformTheme::themeHint(QPlatformTheme::ThemeHint) const  
 ** (wireshark:38035) 15:21:37.460906 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette  
 ** (wireshark:38035) 15:21:37.774835 [GUI ECHO] -- virtual QVariant Qt6CTPlatformTheme::themeHint(QPlatformTheme::ThemeHint) const  

 ** (wireshark:38035) 15:21:37.877024 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette
```
 
Filtramos los paquetes que nos interesan:
>udp.dstport\==22

Para automatizar el proceso podemos crear un script de [[Python]] que lo haga por nosotros, usando [[nano]]:
```bash
┌──(kali㉿kali)-[~]  
└─$ nano exp.py
```

```python
from scapy.all import *  
  
packets = rdpcap('capture.pcap')  
flag = ''  
  
for p in packets:  
        if UDP in p and p[UDP].dport==22:  
                if p[UDP].sport > 5000:  
                        flag += chr(p[UDP].sport-5000)  
print(flag)
```

Ejecutamos el archivo, y obtenemos la bandera:
```bash
┌──(kali㉿kali)-[~/sw]  
└─$ python exp.py      
picoCTF{p1LLf3r3d_data_v1a_st3g0}
```
## Respuesta
picoCTF{p1LLf3r3d_data_v1a_st3g0}