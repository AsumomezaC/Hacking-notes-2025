#Software #Hacking #Principiante
# Definición
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/19/challenge.zip)

`ssh -p 52029 ctf-player@atlas.picoctf.net`Using the password `1db87a14`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
# Hints
- Have you ever played hot or cold? [[busqueda binaria|Binary search]] is a bit like that.
- You have a very limited number of guesses. Try larger jumps between numbers!
- The program will randomly choose a new number each time you connect. You can always try again, but you should start your binary search over from the beginning - try around 500. Can you think of why?
# Solución
Primero [[wget|descargamos el archivo]], lo descomprimimos y nos dirigimos a la carpeta de nuestro interés. Donde [[ls|vemos su contenido]].
```bash
AsumomezaC-picoctf@webshell:~$ rm -rf *
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_atlas/19/challenge.zip
--2025-03-01 01:09:06--  https://artifacts.picoctf.net/c_atlas/19/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.128, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1041 (1.0K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                 100%[=================================================>]   1.02K  --.-KB/s    in 0s      

2025-03-01 01:09:06 (328 MB/s) - 'challenge.zip' saved [1041/1041]

AsumomezaC-picoctf@webshell:~$ unzip challenge.zip 
Archive:  challenge.zip
   creating: home/ctf-player/drop-in/
  inflating: home/ctf-player/drop-in/guessing_game.sh  
AsumomezaC-picoctf@webshell:~$ cd home/ctf-player/drop-in/
AsumomezaC-picoctf@webshell:~/home/ctf-player/drop-in$ ls -la
total 4
drwxr-xr-x 2 AsumomezaC-picoctf AsumomezaC-picoctf   30 Mar 12  2024 .
drwxrwxr-x 3 AsumomezaC-picoctf AsumomezaC-picoctf   21 Mar  1 01:09 ..
-rwxr-xr-x 1 AsumomezaC-picoctf AsumomezaC-picoctf 1579 Mar 12  2024 guessing_game.sh
```

Nos [[SSH|conectamos al servidor]], y vemos que nos espera.

```bash
AsumomezaC-picoctf@webshell:~/home/ctf-player/drop-in$ ssh -p 52029 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:52029 ([18.217.83.136]:52029)' can't be established.
ED25519 key fingerprint is SHA256:M8hXanE8l/Yzfs8iuxNsuFL4vCzCKEIlM/3hpO13tfQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:52029' (ED25519) to the list of known hosts.
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Higher! Try again.
Enter your guess: 750
Lower! Try again.
Enter your guess: 625
Higher! Try again.
Enter your guess: 690
Higher! Try again.
Enter your guess: 720
Lower! Try again.
Enter your guess: 700
Higher! Try again.
Enter your guess: 710
Congratulations! You guessed the correct number: 710
Here's your flag: picoCTF{g00d_gu355_1597707f}
```
## Respuesta
picoCTF{g00d_gu355_1597707f}