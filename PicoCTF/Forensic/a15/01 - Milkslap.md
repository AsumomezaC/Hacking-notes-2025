#Software #Hacking #WebExplotation #Computación 
# Definición
[🥛](http://mercury.picoctf.net:29522/)
# Hints
- Look at the problem category
# Solución
Primero entramos a la página web ([[HTML]]), e inspeccionamos su contenido.
```html
<!doctype html>

<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=400" />
  <title>![🥛](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f95b/72.png)</title>
  <link rel="stylesheet" href="style.css" />

</head>
<body>
  <div id="image" class="center"></div>
  <div id="foot" class="center">
    <h1>MilkSlap!</h1>
    Inspired by <a href="http://eelslap.com">[http://eelslap.com](http://eelslap.com/)</a> <br>
    Credit to: <a href="https://github.com/boxmein">boxmein</a> for code inspiration.
  </div>
  <script src="script.js">

</script>
</body>
</html>
```
Como no encontramos nada inspeccionamos el estilo [[CSS]]:

```css
/* source: milkslap-milkslap.scss */
body {
  margin: 0;
  padding: 0;
  overflow: hidden; }

a {
  color: inherit; }

.center {
  width: 1080px;
  height: 720px;
  margin: 0 auto; }

#image {
  height: 720px;
  margin-top: 5%;
  margin-bottom: 20px;
  background-image: url(concat_v.png);
  background-position: 0 0; }

#foot {
  margin-bottom: 5px;
  color: #999999; }
  #foot h1 {
    font-family: serif;
    font-weight: normal;
    font-size: 1rem;
    text-align: center; }  
```
 Encontramos una imagen muy curiosa, y la descargamos.

Pero antes ocuparemos descargar [[zsteg]], que trabaja con [[Ruby]]:

```
┌──(kali㉿kali)-[~/Downloads]  
└─$ sudo apt install ruby   
ruby is already the newest version (1:3.3+b1).  
ruby set to manually installed.  
The following packages were automatically installed and are no longer required:  
  libflac12t64   libglapi-mesa         ruby-zeitwerk  
  libgeos3.13.0  python3-setproctitle  
Use 'sudo apt autoremove' to remove them.  
  
Summary:  
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0  
                                                                               
┌──(kali㉿kali)-[~/Downloads]  
└─$ gem install zsteg                         
Fetching rainbow-3.1.1.gem  
Fetching iostruct-0.5.0.gem  
Fetching zpng-0.4.5.gem  
Fetching zsteg-0.2.13.gem  
Defaulting to user installation because default installation directory (/var/lib/gems/3.3.0) is not writable.  
Successfully installed rainbow-3.1.1  
Defaulting to user installation because default installation directory (/var/lib/gems/3.3.0) is not writable.  
WARNING:  You don't have /home/kali/.local/share/gem/ruby/3.3.0/bin in your PATH,  
          gem executables (zpng) will not run.  
Successfully installed zpng-0.4.5  
Defaulting to user installation because default installation directory (/var/lib/gems/3.3.0) is not writable.  
Successfully installed iostruct-0.5.0  
Defaulting to user installation because default installation directory (/var/lib/gems/3.3.0) is not writable.  
WARNING:  You don't have /home/kali/.local/share/gem/ruby/3.3.0/bin in your PATH,  
          gem executables (zsteg, zsteg-mask, zsteg-reflow) will not run.  
Successfully installed zsteg-0.2.13  
Parsing documentation for rainbow-3.1.1  
Installing ri documentation for rainbow-3.1.1  
Parsing documentation for zpng-0.4.5  
Installing ri documentation for zpng-0.4.5  
Parsing documentation for iostruct-0.5.0  
Installing ri documentation for iostruct-0.5.0  
Parsing documentation for zsteg-0.2.13  
Installing ri documentation for zsteg-0.2.13  
Done installing documentation for rainbow, zpng, iostruct, zsteg after 1 seconds  
4 gems installed 

┌──(kali㉿kali)-[~/Downloads]  
└─$ zsteg -a Untitiled.png
```

Pero al intentar extraer la bandera, el buffer se desborda, por lo que aumentamos el tamaño del buffer. Y lo volvemos a intentar. 

```bash
┌──(kali㉿kali)-[~/Downloads]  
└─$ export RUBY_THREAD_VM_STACK_SIZE=500000000

┌──(kali㉿kali)-[~/Downloads]  
└─$ zsteg -a Untitiled.png
```
Obteniendo la bandera.
## Respuesta
picoCTF{imag3_m4n1pul4t10n_sl4p5}