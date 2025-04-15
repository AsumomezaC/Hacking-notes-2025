#Software #Hacking #Computación #GeneralSkills 
Hecho por: [[Estufa|Juana Estefanía Herrera Mendoza]]
# Definición
Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/ende.py) using [this password](https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/pw.txt) to get [the flag](https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/flag.txt.en)?
# Hints
- Get the Python script accessible in your shell by entering the following command in the Terminal prompt: `$ wget https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/ende.py`
- `$ man python`
# Solución
- **Descargamos los archivos con [[wget]], obteniendo los siguientes archivos:** 'ende.py  flag.txt.en  pw.txt'

```bash
AsumomezaC-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/ende.py
--2025-04-15 19:20:38--  https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/ende.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1328 (1.3K) [application/octet-stream]
Saving to: 'ende.py'

ende.py                                                    100%[======================================================================================================================================>]   1.30K  --.-KB/s    in 0s      

2025-04-15 19:20:38 (639 MB/s) - 'ende.py' saved [1328/1328]

AsumomezaC-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/pw.txt
--2025-04-15 19:21:21--  https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/pw.txt
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33 [application/octet-stream]
Saving to: 'pw.txt'

pw.txt                                                     100%[======================================================================================================================================>]      33  --.-KB/s    in 0s      

2025-04-15 19:21:21 (15.9 MB/s) - 'pw.txt' saved [33/33]

AsumomezaC-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/flag.txt.en
--2025-04-15 19:21:38--  https://mercury.picoctf.net/static/b351a89e0bc6745b00716849105f87c6/flag.txt.en
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 140 [application/octet-stream]
Saving to: 'flag.txt.en'

flag.txt.en                                                100%[======================================================================================================================================>]     140  --.-KB/s    in 0s      

2025-04-15 19:21:38 (49.5 MB/s) - 'flag.txt.en' saved [140/140]

AsumomezaC-picoctf@webshell:~$ ls
ende.py  flag.txt.en  pw.txt
```

- **A continuación ejecutaremos el archivo de [[Python]] junto con '-h', para obtener mas información.**
```bash
AsumomezaC-picoctf@webshell:~$ python3 ende.py -h
Usage: ende.py (-e/-d) [file]
Examples:
  To decrypt a file named 'pole.txt', do: '$ python ende.py -d pole.txt'
```
- **Antes de hacer lo del ejemplo, necesitaremos antes una contraseña, la cual la sacamos de 'pw.txt', usando un simple [[cat]], la obtendremos.**
```bash
AsumomezaC-picoctf@webshell:~$ cat pw.txt 
67c6cc9667c6cc9667c6cc9667c6cc96
```
- **La copiaremos y ahora si haremos justo como se nos menciono en el ejemplo anterior de la siguiente manera, y ademas, pegaremos la contraseña que se nos dio, obteniendo la bandera**
```bash
AsumomezaC-picoctf@webshell:~$ python3 ende.py -d flag.txt.en
Please enter the password:67c6cc9667c6cc9667c6cc9667c6cc96
picoCTF{4p0110_1n_7h3_h0us3_67c6cc96}
```
## Respuesta
picoCTF{4p0110_1n_7h3_h0us3_67c6cc96}