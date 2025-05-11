#Software #Hacking #WebExplotation #Computación 
# Definición
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap) and try to get the flag.
# Hints
- Filter your packets to narrow down your search.
- Attacks were done in timely manner.
- Time is essential
# Solución
Primero descargamos el archivo usando [[wget]].
```
┌──(kali㉿kali)-[~/ph4]  
└─$ wget [https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap](https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap)  
--2025-05-10 18:52:42--  [https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap](https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap)  
Resolving [challenge-files.picoctf.net](http://challenge-files.picoctf.net/) ([challenge-files.picoctf.net](http://challenge-files.picoctf.net/))... 65.9.149.95, 65.9.149.59, 65.9.149.85, ...  
Connecting to [challenge-files.picoctf.net](http://challenge-files.picoctf.net/) ([challenge-files.picoctf.net](http://challenge-files.picoctf.net/))|65.9.149.95|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1452 (1.4K) [application/octet-stream]  
Saving to: ‘myNetworkTraffic.pcap’  
  
myNetworkTraffic.pc 100%[================>]   1.42K  --.-KB/s    in 0s        
  
2025-05-10 18:52:44 (33.7 MB/s) - ‘myNetworkTraffic.pcap’ saved [1452/1452]  
```
                                                                               
Al ser un [[Archivo .pcap]] nos apoyamos de [[Wireshark]] para ver su contenido.
```
┌──(kali㉿kali)-[~/ph4]  
└─$ wireshark myNetworkTraffic.pcap  
 ** (wireshark:11220) 18:53:17.947254 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette  
 ** (wireshark:11220) 18:53:17.948452 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ToolButtonPalette  
 ** (wireshark:11220) 18:53:17.948493 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ButtonPalette  
 ** (wireshark:11220) 18:53:17.948508 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::CheckBoxPalette  
 ** (wireshark:11220) 18:53:17.948522 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::RadioButtonPalette  
 ** (wireshark:11220) 18:53:17.948541 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::HeaderPalette  
 ** (wireshark:11220) 18:53:17.948569 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ItemViewPalette  
 ** (wireshark:11220) 18:53:17.948616 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MessageBoxLabelPelette  
 ** (wireshark:11220) 18:53:17.948669 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TabBarPalette  
 ** (wireshark:11220) 18:53:17.948693 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::LabelPalette  
 ** (wireshark:11220) 18:53:17.948713 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::GroupBoxPalette  
 ** (wireshark:11220) 18:53:17.948756 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MenuPalette  
 ** (wireshark:11220) 18:53:17.948783 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MenuBarPalette  
 ** (wireshark:11220) 18:53:17.948802 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextEditPalette  
 ** (wireshark:11220) 18:53:17.948833 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextEditPalette  
 ** (wireshark:11220) 18:53:17.948853 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextLineEditPalette  
 ** (wireshark:11220) 18:53:17.948879 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ToolTipPalette  
 ** (wireshark:11220) 18:53:17.948940 [GUI ECHO] -- virtual QVariant Qt6CTPlatformTheme::themeHint(QPlatformTheme::ThemeHint) const  
 ** (wireshark:11220) 18:53:17.949553 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette  
 ** (wireshark:11220) 18:53:18.407472 [GUI ECHO] -- virtual QVariant Qt6CTPlatformTheme::themeHint(QPlatformTheme::ThemeHint) const  

 ** (wireshark:11220) 18:53:18.473934 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette
```

Empezamos siguiendo las pistas, filtrando los paquetes.
Filtramos paquetes:
>tcp.len\==12||tcp.len==4

Las ordenamos por tiempo -por la pista-.

cGljb0NURg==

Vemos que parece [[Codificación Base 64]], por lo que lo transformamos

1. picoCTF
Nos damos cuenta que parece ser el inicio de la bandera, por lo que hacemos el mismo con el resto.
2. {1t_w4s
3. nt_th4t
4. 34sy_t
5. bh_4r_9
6. 59f50d3
7. }
Finalmente unimos todos los mensajes, y obtenemos la bandera.
## Respuesta
picoCTF{1t_w4snt_th4t_34sy_tbh_4r_959f50d3}