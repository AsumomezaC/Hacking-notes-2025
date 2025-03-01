#Software #Hacking #Principiante
# Definición
What was I last working on? I remember writing a note to help me remember...You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/163/challenge.zip)
# Hints
- The `cat` command will let you read a file, but that won't help you here!
- Read the chapter on [[Git]] from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
- When committing a file with git, a message can (and should) be included.
# Solución

Primero descargamos el archivo(con [[NET CAT]]) y lo descomprimimos.
```bash
AsumomezaC-picoctf@webshell:~/drop-in$ wget https://artifacts.picoctf.net/c_titan/163/challenge.zip
--2025-02-28 01:31:29--  https://artifacts.picoctf.net/c_titan/163/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.43, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17741 (17K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip              100%[=======================================>]  17.33K  --.-KB/s    in 0.005s  

2025-02-28 01:31:29 (3.62 MB/s) - 'challenge.zip' saved [17741/17741]

AsumomezaC-picoctf@webshell:~/drop-in$ unzip challenge.zip 
Archive:  challenge.zip
   creating: drop-in/
  inflating: drop-in/message.txt     
   creating: drop-in/.git/
   creating: drop-in/.git/branches/
  inflating: drop-in/.git/description  
   creating: drop-in/.git/hooks/
  inflating: drop-in/.git/hooks/applypatch-msg.sample  
  inflating: drop-in/.git/hooks/commit-msg.sample  
  inflating: drop-in/.git/hooks/fsmonitor-watchman.sample  
  inflating: drop-in/.git/hooks/post-update.sample  
  inflating: drop-in/.git/hooks/pre-applypatch.sample  
  inflating: drop-in/.git/hooks/pre-commit.sample  
  inflating: drop-in/.git/hooks/pre-merge-commit.sample  
  inflating: drop-in/.git/hooks/pre-push.sample  
  inflating: drop-in/.git/hooks/pre-rebase.sample  
  inflating: drop-in/.git/hooks/pre-receive.sample  
  inflating: drop-in/.git/hooks/prepare-commit-msg.sample  
  inflating: drop-in/.git/hooks/update.sample  
   creating: drop-in/.git/info/
  inflating: drop-in/.git/info/exclude  
   creating: drop-in/.git/refs/
   creating: drop-in/.git/refs/heads/
 extracting: drop-in/.git/refs/heads/master  
   creating: drop-in/.git/refs/tags/
 extracting: drop-in/.git/HEAD       
  inflating: drop-in/.git/config     
   creating: drop-in/.git/objects/
   creating: drop-in/.git/objects/pack/
   creating: drop-in/.git/objects/info/
   creating: drop-in/.git/objects/43/
 extracting: drop-in/.git/objects/43/246218ab4fc7b30e9a9dff073e012316851469  
   creating: drop-in/.git/objects/25/
 extracting: drop-in/.git/objects/25/16effb8d70e33bdd0023629b164a77225e1ec2  
   creating: drop-in/.git/objects/e6/
 extracting: drop-in/.git/objects/e6/5fedb3a72a16c577f4b17023b63997134b307d  
  inflating: drop-in/.git/index      
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master  
```

Nos desplazamos ahora a la carpeta en la que estaremos trabajando y vemos su contenido
```bash
AsumomezaC-picoctf@webshell:~/drop-in$ ls
challenge.zip  drop-in  message.txt
AsumomezaC-picoctf@webshell:~/drop-in$ cd drop-in/
AsumomezaC-picoctf@webshell:~/drop-in/drop-in$ ls -la
total 4
drwxr-xr-x 3 AsumomezaC-picoctf AsumomezaC-picoctf  37 Mar 12  2024 .
drwxr-xr-x 4 AsumomezaC-picoctf AsumomezaC-picoctf  73 Feb 28 01:31 ..
drwxr-xr-x 8 AsumomezaC-picoctf AsumomezaC-picoctf 166 Mar 12  2024 .git
-rw-r--r-- 1 AsumomezaC-picoctf AsumomezaC-picoctf  87 Mar 12  2024 message.txt
```

Como las [[#Hints]] nos dicen que no usemos [[CAT]] y que la respuesta esta en [[Git]], por lo cual eso es lo que hacemos.

```bash
AsumomezaC-picoctf@webshell:~/drop-in/drop-in$ git log

commit e65fedb3a72a16c577f4b17023b63997134b307d (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:29 2024 +0000

    picoCTF{t1m3m@ch1n3_88c35e3b}
```

Y en cuanto checamos los commits pasados, encontramos la bandera.
## Respuesta
picoCTF{t1m3m@ch1n3_88c35e3b}