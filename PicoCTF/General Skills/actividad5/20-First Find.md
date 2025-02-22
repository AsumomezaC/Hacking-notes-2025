# Definición
Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/502/files.zip)

# Hints
(None)
# Solución
Descargamos el archivo usando wget

Realizamos un unzip al archivo descargado

```bash
AsumomezaC-picoctf@webshell:~$ find . -name uber-secret.txt
./files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt

AsumomezaC-picoctf@webshell:~$ cat ./files/adequate_books/more_books/.secret/deeper_se
crets/deepest_secrets/uber-secret.txt
picoCTF{f1nd_15_f457_ab443fd1}
```

>Buscamos el archivo usando el comando [[find]], y de ahí le hacemos un cat al archivo.
## Respuesta
picoCTF{f1nd_15_f457_ab443fd1}