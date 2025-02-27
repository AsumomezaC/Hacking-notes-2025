#Software #Hacking #Principiante
# Lets Warm Up
## Descripcion

If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?

## Hints
Submit your answer in our flag format. For example, if your answer was 'hello', you would submit 'picoCTF{hello}' as the flag.

## Sol
### 1- con [[Python]]
```python
python #ingresamos a py desde la terminal
chr(0x70)
```

==Sol. 'picoCTF(p)'==
### Con la tabla [[ASCII]]
0x70 es equivalente al número 112(te puedes apoyar en [cyberChef](https://cyberchef.org/)), que en el código ASCII corresponde al char 'p'.