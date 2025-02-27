#Software #Hacking #Principiante
# Definición
Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/503/big-zip-files.zip

# Hints
Can grep be instructed to look at every file in a directory and its subdirectories?

# Solución
>Descargamos el archivo con wget

Usamos unzip para descomprimir el archivo
Accedemos a la flag usando grep:
```bash
AsumomezaC-picoctf@webshell:~$ grep -R picoCTF
.python_history:'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'
.bash_history:grep "picoCTF" static.ltdis.x86_64.txt
.bash_history:grep "picoCTF" static.ltdis.st
.bash_history:grep "picoCTF" static.ltdis.x86_64.txt
.bash_history:grep "picoCTF" static.ltdis.strings.txt
README.txt:Welcome to the picoCTF webshell!
README.txt:picoCTF challenges.
README.txt:  Extensive brute-forcing is not necessary to solve picoCTF challenges.
README.txt:- If you change your username through the picoCTF website, you will
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```

## Respuesta
picoCTF{gr3p_15_m4g1c_ef8790dc}