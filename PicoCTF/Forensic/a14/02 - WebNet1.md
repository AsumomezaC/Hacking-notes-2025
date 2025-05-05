#Software #Hacking #WebExplotation #Computación 
# Definición
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.
# Hints
- Try using a tool like Wireshark.
- How can you decrypt the TLS stream?
# Solución
>Se resuelve igual que [[01 - WebNet0]].

Descargamos la llave y los paquetes interceptados usando [[wget]].
```bash
┌──(kali㉿kali)-[~/web1]  
└─$ wget [https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap)  
--2025-05-05 14:26:51--  [https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 92525 (90K) [application/octet-stream]  
Saving to: ‘capture.pcap’  
  
capture.pcap        100%[================>]  90.36K   239KB/s    in 0.4s      
  
2025-05-05 14:27:00 (239 KB/s) - ‘capture.pcap’ saved [92525/92525]  
  
                                                                               
┌──(kali㉿kali)-[~/web1]  
└─$ wget [https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key)  
--2025-05-05 14:28:06--  [https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key)  
Resolving [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))... 3.131.60.8  
Connecting to [jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/) ([jupiter.challenges.picoctf.org](http://jupiter.challenges.picoctf.org/))|3.131.60.8|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1704 (1.7K) [application/octet-stream]  
Saving to: ‘picopico.key’  
  
picopico.key        100%[================>]   1.66K  --.-KB/s    in 0s        
  
2025-05-05 14:28:15 (60.7 MB/s) - ‘picopico.key’ saved [1704/1704]  
```
  
 Usamos la llave y [[Wireshark]] para obtenerle la bandera escondida.                                                                    
```bash
┌──(kali㉿kali)-[~/web1]  
└─$ wireshark capture.pcap    
 ** (wireshark:17087) 14:32:53.510512 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette  
 ** (wireshark:17087) 14:32:53.511535 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ToolButtonPalette  
 ** (wireshark:17087) 14:32:53.511580 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ButtonPalette  
 ** (wireshark:17087) 14:32:53.511596 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::CheckBoxPalette  
 ** (wireshark:17087) 14:32:53.511611 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::RadioButtonPalette  
 ** (wireshark:17087) 14:32:53.511626 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::HeaderPalette  
 ** (wireshark:17087) 14:32:53.511643 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ItemViewPalette  
 ** (wireshark:17087) 14:32:53.511666 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MessageBoxLabelPelette  
 ** (wireshark:17087) 14:32:53.511695 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TabBarPalette  
 ** (wireshark:17087) 14:32:53.511713 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::LabelPalette  
 ** (wireshark:17087) 14:32:53.511736 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::GroupBoxPalette  
 ** (wireshark:17087) 14:32:53.511752 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MenuPalette  
 ** (wireshark:17087) 14:32:53.511767 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::MenuBarPalette  
 ** (wireshark:17087) 14:32:53.511782 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextEditPalette  
 ** (wireshark:17087) 14:32:53.511797 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextEditPalette  
 ** (wireshark:17087) 14:32:53.511812 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::TextLineEditPalette  
 ** (wireshark:17087) 14:32:53.511827 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::ToolTipPalette  
 ** (wireshark:17087) 14:32:53.511869 [GUI ECHO] -- virtual QVariant Qt6CTPlatformTheme::themeHint(QPlatformTheme::ThemeHint) const  
 ** (wireshark:17087) 14:32:53.512565 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette  
 ** (wireshark:17087) 14:32:53.685030 [GUI ECHO] -- virtual QVariant Qt6CTPlatformTheme::themeHint(QPlatformTheme::ThemeHint) const  
 ** (wireshark:17087) 14:32:53.748450 [GUI ECHO] -- virtual const QPalette* Qt6CTPlatformTheme::palette(QPlatformTheme::Palette) const QPlatformTheme::SystemPalette
```
## Respuesta
picoCTF{honey.roasted.peanuts}