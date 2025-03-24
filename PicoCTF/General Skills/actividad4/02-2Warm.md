#Software #Hacking #Principiante
# Descripción
Can you convert the number 42 (base 10) to binary (base 2)?

# Hint
Submit your answer in our competition's flag format. For example, if your answer was '11111', you would submit 'picoCTF{11111}' as the flag.

# Sol
## Sol 1
Usando [[Python]]
```cmd
AsumomezaC-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> bin(42)[2:]
'101010'
```

>Usamos la función bin para obtener transformar 42 a binario, pero tomamos a partir del tercer carácter (porque los primeros dos indican que es binario: "0b") 

## Sol 2
Usando [[cyberchef]]

> [!info] Decimal a binario
> input: 42
> recipe: from decimal - to binary (byte lenght:6)
> output: 101010
## Resultado
picoCTF{101010}

