#Software #Hacking #Principiante
# Definición
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 29221`.
# Hints
1. I hear python can convert things.
2. It might help to have multiple windows open.
# Solución

```cmd
AsumomezaC-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 29221
Let us see how data is stored
falcon
Please give the 01100110 01100001 01101100 01100011 01101111 01101110 as a word.
...
you have 45 seconds.....

Input:
falcon
Please give me the  143 157 156 164 141 151 156 145 162 as a word.
Input:
containerToo slow!

AsumomezaC-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 29221
Let us see how data is stored
chair
Please give the 01100011 01101000 01100001 01101001 01110010 as a word.
...
you have 45 seconds.....

Input:
chair
Please give me the  160 151 145 as a word.
Input:
pie
Please give me the 636f6e7461696e6572 as a word.
Input:
container
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_00a975ff}
```

Te da tres cadenas a convertir:
## Binario
```python
def binario_a_ascii(binario):
	caracteres = [binario[i:i+8] for i in range(0, len(binario), 8)]
	return ''.join(chr(int(car, 2)) for car in caracteres)
```
>Respuesta: chair
## Octal
```python
def octal_a_ascii(octal):
	caracteres = octal.split()
	return ''.join(chr(int(car, 8)) for car in caracteres)
```
>Respuesta: pie
## Hexadecimal
```python
def hexadecimal_a_ascii(hexadecimal):
	return bytes.fromhex(hexadecimal).decode('utf-8')
```
>Respuesta: container


> [!success] Contrarreloj
> Lo más complicado es que tienes un tiempo muy justo para realizarlo, lo que exige tener varias pantallas abiertas simultáneamente.
## Respuesta
picoCTF{learning_about_converting_values_00a975ff}