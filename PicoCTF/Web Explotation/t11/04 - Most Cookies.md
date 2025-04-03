#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/c135543530f7dc24c3a6ecaeb44a81b8/server.py) [http://mercury.picoctf.net:65344/](http://mercury.picoctf.net:65344/)
# Hints
- How secure is a flask cookie?
# Solución
Primero descargamos pipx, para tener compatibilidad entre diferentes veriones de [[Python]] y Flask Unsign.

```bash
┌──(kali㉿kali)-[~]  
└─$ sudo apt install pipx      
[sudo] password for kali:  
pipx is already the newest version (1.7.1-1).  
pipx set to manually installed.  
The following packages were automatically installed and are no longer required:  
  libflac12t64   libglapi-mesa         ruby-zeitwerk  
  libgeos3.13.0  python3-setproctitle  
Use 'sudo apt autoremove' to remove them.  
  
Summary:  
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0  
                                                                               
┌──(kali㉿kali)-[~]  
└─$ pipx ensurepath  
/home/kali/.local/bin is already in PATH.  
  
![⚠](https://fonts.gstatic.com/s/e/notoemoji/16.0/26a0/72.png)  All pipx binary directories have been appended to PATH. If you are sure  
you want to proceed, try again with the '--force' flag.  
  
Otherwise pipx is ready to go! ![✨](https://fonts.gstatic.com/s/e/notoemoji/16.0/2728/72.png) ![🌟](https://fonts.gstatic.com/s/e/notoemoji/16.0/1f31f/72.png) ![✨](https://fonts.gstatic.com/s/e/notoemoji/16.0/2728/72.png)  
                                                                               
┌──(kali㉿kali)-[~]  
└─$ pipx install flask/unsign  
Unable to parse package spec: flask/unsign
```

Separamos las posibles galletas.

```txt
snickerdoodle
chocolatechip
oatmealraisin
gingersnap
shortbread
peanutbutter
whoopiepie
sugar
molasses
kiss
biscotti
butter
spritz
snowball
drop
thumbprint
pinwheel
wafer
macaroon
fortune
crinkle
icebox
gingerbread
tassie
lebkuchen
macaron
blackandwhite
whitechocolatemacadamia
```
## Respuesta