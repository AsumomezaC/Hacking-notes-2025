#Software #Hacking #WebExplotation #Computación 
# Definición
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/9/flag2of2-final.pdf).
# Hints
- This problem can be solved by just opening the file in different ways
# Solución
Primero descargamos el archivo y lo abrimos, obserbando lo que parece ser el final de la bandera.
pdf:  
1n_pn9_&_pdf_7f9bccd1}

Siguiendo la pista, guardamos el archivo como png (si no funciona, probaremos con jpg -yendo de los que más hemos usado en esta clase de retos-). Y obtenemos el inicio de la bandera.
png:
picoCTF{f1u3n7_

Funcionamos ambas partes y tenemos la bandera.
## Respuesta
picoCTF{f1u3n7_1n_pn9_&_pdf_7f9bccd1}