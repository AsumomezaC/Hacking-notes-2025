#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Estufa|Juana Estefanía Herrera Mendoza]]
# Definición
Connect to this PostgreSQL server and find the flag!`psql -h saturn.picoctf.net -p 58267 -U postgres pico`Password is `postgres`
# Hints
What does a SQL database contain?
# Solución
- **Nos conectamos al servidor SQL, con la dirección que se nos dio y la contraseña.**

```bash
AsumomezaC-picoctf@webshell:~$ psql -h saturn.picoctf.net -p 58267 -U postgres pico
Password for user postgres: 
psql (14.17 (Ubuntu 14.17-0ubuntu0.22.04.1), server 15.2 (Debian 15.2-1.pgdg110+1))
WARNING: psql major version 14, server major version 15.
         Some psql features might not work.
Type "help" for help.
```

  

- **Utilizamos el comando '\l' para listar todas las bases de datos.**

```bash
pico=# \l
                                 List of databases
   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges   
-----------+----------+----------+------------+------------+-----------------------
 pico      | postgres | UTF8     | en_US.utf8 | en_US.utf8 | 
 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 | 
 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
(4 rows)
```
- **Nos reconectamos a la base de datos pico (solo para reafirmar la conexión).**

```bash
pico=# \c pico
psql (14.17 (Ubuntu 14.17-0ubuntu0.22.04.1), server 15.2 (Debian 15.2-1.pgdg110+1))
WARNING: psql major version 14, server major version 15.
         Some psql features might not work.
You are now connected to database "pico" as user "postgres".
```
- **El comando '\dt' mostrara todas las tablas del esquema actual.**

```bash
pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner   
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)
```

  

- **Observamos que en la tabla anterior hay una tabla de nombre 'flags', por lo tanto, con nuestros vastos conocimientos en SQL, haremos un SELECT a aquella tabla, y obtendremos la bandera.**

```bash
pico=# select * from flags;
 id | firstname | lastname  |                address                 
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_21c94904}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)
```
>Además vemos unas bonitas referencias a STAR WARS jajaja
## Respuesta
picoCTF{L3arN_S0m3_5qL_t0d4Y_21c94904}