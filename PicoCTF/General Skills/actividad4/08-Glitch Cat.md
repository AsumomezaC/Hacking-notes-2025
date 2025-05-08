#Software #Hacking #Principiante
# Definición
Our flag printing service has started glitching!

Additional details will be available after launching your challenge instance.

# Hints
- ASCII is one of the most common encodings used in programming
- We know that the glitch output is valid Python, somehow!
- Press Ctrl and c on your keyboard to close your connection and return to the command prompt.

# Solución
Ingresamos con [[NET CAT (nc)]] al servidor.

```cmd
AsumomezaC-picoctf@webshell:~$ nc saturn.picoctf.net 63819
'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'
^C
AsumomezaC-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
```

Mandamos el resultado a python, para ver que significa
```python
'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'
'picoCTF{gl17ch_m3_n07_9c42a45d}'
```
## Respuesta
picoCTF{gl17ch_m3_n07_9c42a45d}