#Software #Hacking #Principiante
# Definición
How well can you perfom basic binary operations?
Start searching for the flag here `nc titan.picoctf.net 63761`
# Hints
(None)
# Solución

Ingresamos al [[NET CAT (nc)|servidor]] y realizamos las [[Operaciones Básicas en Binario]] que se nos pidan para obtener la bandera.

```bash
AsumomezaC-picoctf@webshell:~$ nc titan.picoctf.net 63761

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 11111101
Binary Number 2: 11101010


Question 1/6:
Operation 1: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11111111
Correct!

Question 2/6:
Operation 2: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 01110101
Correct!

Question 3/6:
Operation 3: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 111101111
Incorrect. Try again
Enter the binary result: 111100111
Correct!

Question 4/6:
Operation 4: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 111111010
Correct!

Question 5/6:
Operation 5: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11101000
Correct!

Question 6/6:
Operation 6: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 1110011101000010
Correct!

Enter the results of the last operation in hexadecimal: E742

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_aeaf4b09}
```
## Respuesta
picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_aeaf4b09}