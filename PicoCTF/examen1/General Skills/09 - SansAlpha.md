#Software #Hacking #Computación #GeneralSkills
Hecho por: [[Yo|Adrián Fernando Cuevas Solís]]
# Definición
The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.`ssh -p 58095 ctf-player@mimas.picoctf.net`Use password: `1db87a14`
# Hints
- Where can you get some letters?
# Solución
Iniciamos ingresando al servidor [[SSH]]:

```bash
AsumomezaC-picoctf@webshell:~$ ssh -p 58095 ctf-player@mimas.picoctf.net
The authenticity of host '[mimas.picoctf.net]:58095 ([52.15.88.75]:58095)' can't be established.
ED25519 key fingerprint is SHA256:n/hDgUtuTTF85Id7k2fxmHvb6rrLrACHNM6xLZ46AqQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[mimas.picoctf.net]:58095' (ED25519) to the list of known hosts.
ctf-player@mimas.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1016-aws x86_64)

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

Intentamos usar [[ls]] para ver que contiene, pero vemos que por alguna razón no detecta los comandos:
```bash
SansAlpha$ ls -la
SansAlpha: Unknown character detected
```

Por la pista, deducimos que la única forma de usar la terminal es usando [[Wildcards]] y números:
```bash
SansAlpha$ */*
bash: blargh/flag.txt: Permission denied

SansAlpha$ /*
bash: /bin: Is a directory

SansAlpha$ /*/???
E: Invalid operation /bin/awk

SansAlpha$ /*/??????
/bin/base32: extra operand ‘/bin/base64’
Try '/bin/base32 --help' for more information.

SansAlpha$ /*/????64 */*
/bin/base64: extra operand ‘/bin/x86_64’
Try '/bin/base64 --help' for more information.

SansAlpha$ /*/???[!_]64 */*
/bin/base64: extra operand ‘blargh/flag.txt’
Try '/bin/base64 --help' for more information.

SansAlpha$ /*/???[!_]64 */????.*
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV80OTQ1NjMwYX0=
```
>Para esto debemos de saber con anterioridad los siguientes conceptos: [[ls]], [[cat]] y [[Codificación Base 64]]

Una vez, terminado, obtenemos la bandera en base 64, nos podemos apoyar de [[echo]] o de [cyberchef](https://cyberchef.org/) para conseguir la bandera:
```bash
AsumomezaC-picoctf@webshell:~$ echo cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV80OTQ1NjMwYX0= | base64 -d
return 0 picoCTF{7h15_mu171v3r53_15_m4dn355_4945630a}
```
## Respuesta
picoCTF{7h15_mu171v3r53_15_m4dn355_4945630a}