# Definición
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 4427`.
# Hints
1. Remember the flag format is picoCTF{XXXX}
2. What's a pipe? No not that kind of pipe... This [kind](http://www.linfo.org/pipes.html)
# Solución
1. te conectas con [[NET CAT]]
## Sol 1

1. Mande la salida a un archivo
2. Busque la bandera
```cmd
AsumomezaC-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 4427 > salida.txt
AsumomezaC-picoctf@webshell:~$ cat salida.txt | grep pico picoCTF{digital_plumb3r_5ea1fbd7}
```
## Sol 2
2. Redirigí la bandera

```cmd
AsumomezaC-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 4427 | grep pico
picoCTF{digital_plumb3r_5ea1fbd7}
```
## Respuesta
picoCTF{digital_plumb3r_5ea1fbd7}