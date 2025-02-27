#Software #Hacking #Principiante
# Definición
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)

- Start your instance to see connection details.`ssh -p 52494 ctf-player@saturn.picoctf.net`The password is `8a707622`
# Hints
- Experiment with different shell syntax
# Solución
Primero ingresamos al servidor usando [[NET CAT]].

```bash
AsumomezaC-picoctf@webshell:~$ ssh -p 52494 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:52494 ([13.59.203.175]:52494)' can't be established.
ED25519 key fingerprint is SHA256:tJ0wuU5yBvNO/FrkHmR9iY36VJClMhKV+Hq2sxqKFmg.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:52494' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

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

Al entrar al servidor intentamos realizar un [[ls]] para ver que contiene.

```bash
Special$ ls
Is
sh: 1: Is: not found
```

Vemos que los comandos no funcionan como deberían:
```bash
Cat 
sh: 1: Cat: not found
Special$ help
Help 
sh: 1: Help: not found
```

Nos damos cuenta que esto tiene que ver con la sintaxis de [Bourne Shell(sh)](https://www.ibm.com/docs/es/aix/7.2?topic=shells-bourne-shell)(que es como tener una terminal dentro de otra terminal), por lo que utilizamos la sintaxis para ejecutar los comandos que antes podríamos ejecutar directamente.

```bash
Special$ ${paramter?ls}
${paramter?ls} 
sh: 1: paramter: ls
```
>Parece que si funciona, por lo que empezamos a buscar la bandera.

```bash
Special$ ${paramter=ls}
${paramter=ls} 
blargh
Special$ ${parameter=cat blargh}
${parameter=cat blargh} 
cat: blargh: Is a directory
Special$ ${parameter=cd blargh}
${parameter=cd blargh}
Special$ ${parameter=ls blargh}
${parameter=ls blargh} 
flag.txt
Special$ ${parameter=cat < blargh/flag.txt}
${parameter=cat < blargh/flag.txt} 
cat: '<': No such file or directory
picoCTF{5p311ch3ck_15_7h3_w0r57_a60bdf40}
```
Finalmente conseguimos la bandera, empleando como apoyo [[CAT]], [[ls]] y cd.
## Respuesta
picoCTF{5p311ch3ck_15_7h3_w0r57_a60bdf40}