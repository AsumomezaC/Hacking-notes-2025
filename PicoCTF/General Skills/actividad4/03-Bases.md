#Software #Hacking #Principiante
# Definición
What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.
# Hints
Submit your answer in our flag format. For example, if your answer was 'hello', you would submit 'picoCTF{hello}' as the flag.

# Solución
## Sol 1
Usando [[cyberchef]]

```cyberchef
Input: bDNhcm5fdGgzX3IwcDM1
Recipe: From Base64 
Output: l3arn_th3_r0p35
```
## Sol 2
``` linux
AsumomezaC-picoctf@webshell:~$ echo bDNhcm5fdGgzX3IwcDM1 | base64 -d
l3arn_th3_r0p35AsumomezaC-picoctf@webshell:~$ 
```
> Utiliza [[Codificación Base 64]], pues al tener caracteres imprimibles (letras, números y símbolos) es muy probable que sea eso.

## Sol3
```python
import base64
base64.b64decode('bDNhcm5fdGgzX3IwcDM1')
b'l3arn_th3_r0p35'
```
## Respuesta
picoCTF{l3arn_th3_r0p35}