#Software #Hacking #Principiante
# Definición
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/70/challenge.zip)
# Hints
- `git branch -a` will let you see available branches
- How can file 'diffs' be brought to the main branch? Don't forget to `git config`!
- Merge conflicts can be tricky! Try a text editor like nano, emacs, or vim.
# Solución

Descargamos el archivo ([[wget]]), lo descomprimimos, nos movemos a la carpeta y observamos su contenido ([[ls]]).

```bash
AsumomezaC-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/70/challenge.zip
--2025-03-01 00:21:53--  https://artifacts.picoctf.net/c_titan/70/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24662 (24K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip              100%[========================================>]  24.08K  --.-KB/s    in 0.01s   

2025-03-01 00:21:53 (2.28 MB/s) - 'challenge.zip' saved [24662/24662]

AsumomezaC-picoctf@webshell:~$ unzip challenge.zip 
Archive:  challenge.zip
   creating: drop-in/
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
 extracting: drop-in/.git/refs/heads/main  
   creating: drop-in/.git/refs/heads/feature/
 extracting: drop-in/.git/refs/heads/feature/part-1  
  inflating: drop-in/.git/refs/heads/feature/part-2  
 extracting: drop-in/.git/refs/heads/feature/part-3  
   creating: drop-in/.git/refs/tags/
 extracting: drop-in/.git/HEAD       
  inflating: drop-in/.git/config     
   creating: drop-in/.git/objects/
   creating: drop-in/.git/objects/pack/
   creating: drop-in/.git/objects/info/
   creating: drop-in/.git/objects/77/
 extracting: drop-in/.git/objects/77/d6ceca6fe23b57d88cf16f20003e10d6715690  
   creating: drop-in/.git/objects/b9/
 extracting: drop-in/.git/objects/b9/32e8c048154a46d224cd7691c99dc8cb88164a  
   creating: drop-in/.git/objects/54/
 extracting: drop-in/.git/objects/54/c7842e34d03976ddc080a9dd76742751024358  
   creating: drop-in/.git/objects/6e/
 extracting: drop-in/.git/objects/6e/17fb3a35364b4f9bb8bef8b5e6a5af2d3e7dfa  
   creating: drop-in/.git/objects/43/
 extracting: drop-in/.git/objects/43/e44dd37ba0c0adc3d78d0b85d699859ec8d75c  
   creating: drop-in/.git/objects/f6/
 extracting: drop-in/.git/objects/f6/5544e4f1511fe1d1dfff03c4d65869da039b8e  
   creating: drop-in/.git/objects/7a/
 extracting: drop-in/.git/objects/7a/b4e25c0cd108374b2275fdb1fcdf635e591833  
   creating: drop-in/.git/objects/d1/
 extracting: drop-in/.git/objects/d1/f3407cee4479c075997b497fa290ca636fe258  
   creating: drop-in/.git/objects/d3/
 extracting: drop-in/.git/objects/d3/563a2c62ab2c95c5c13f3377cc6d79b2411c22  
   creating: drop-in/.git/objects/45/
 extracting: drop-in/.git/objects/45/6656eef7d5d6b8b7d49dc4f7fe6ff456c0bb91  
   creating: drop-in/.git/objects/0a/
 extracting: drop-in/.git/objects/0a/e601af6790d90cf89319f9a6520b4e2f15db35  
   creating: drop-in/.git/objects/5c/
 extracting: drop-in/.git/objects/5c/00b43f48516d7cc81ea1f497b4d43ae6a84c4c  
  inflating: drop-in/.git/index      
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/main  
   creating: drop-in/.git/logs/refs/heads/feature/
  inflating: drop-in/.git/logs/refs/heads/feature/part-1  
  inflating: drop-in/.git/logs/refs/heads/feature/part-2  
  inflating: drop-in/.git/logs/refs/heads/feature/part-3  
  inflating: drop-in/flag.py         
AsumomezaC-picoctf@webshell:~$ cd drop-in/
AsumomezaC-picoctf@webshell:~/drop-in$ ls -la
total 8
drwxr-xr-x 3 AsumomezaC-picoctf AsumomezaC-picoctf   45 Mar  9  2024 .
drwxr-xr-x 3 AsumomezaC-picoctf AsumomezaC-picoctf   95 Mar  1 00:21 ..
drwxr-xr-x 8 AsumomezaC-picoctf AsumomezaC-picoctf 4096 Mar  9  2024 .git
-rw-r--r-- 1 AsumomezaC-picoctf AsumomezaC-picoctf   30 Mar  9  2024 flag.py
```

Observamos el contenido del archivo flag usando [[Strings]].
```bash
AsumomezaC-picoctf@webshell:~/drop-in$ strings flag.py
print("Printing the flag...")
```
>Alternativamente también puedes usar [[nano]].

Seguimos la pista y observamos que branch existen ([[Git]]).

```bash
AsumomezaC-picoctf@webshell:~/drop-in$ git branch -a

  feature/part-1
  feature/part-2
  feature/part-3
* main
```

Observamos que ramas ya han sido unidas.
```bash
AsumomezaC-picoctf@webshell:~/drop-in$ git branch --no-merged

  feature/part-1
  feature/part-2
  feature/part-3
```

Seguimos las recomendaciones y checamos las configuraciones del git.
```shell
AsumomezaC-picoctf@webshell:~/drop-in$ git config --list

core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
```

Con esto hacemos merge de las otras ramas([[Git#1️⃣ **Usando `git merge` (Fusión de ramas)**|Fusión de ramas]]).
```bash
AsumomezaC-picoctf@webshell:~/drop-in$ git merge feature/part-1
Updating 54c7842..f65544e
Fast-forward
 flag.py | 1 +
 1 file changed, 1 insertion(+)
AsumomezaC-picoctf@webshell:~/drop-in$ strings flag.py 
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')
```

>Al intentar realizar el próximo merge, nos marca un error, por lo que nos [[Git#local|Registramos localmente]].

```bash
AsumomezaC-picoctf@webshell:~/drop-in$ git merge feature/part-2
Committer identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'AsumomezaC-picoctf@webshell.(none)')

AsumomezaC-picoctf@webshell:~/drop-in$ git config --local user.email "cuevassolisadrian@gmail.com"  
AsumomezaC-picoctf@webshell:~/drop-in$ git config --local user.name "AsumomezaC"
AsumomezaC-picoctf@webshell:~/drop-in$ git merge feature/part-2
Auto-merging flag.py
CONFLICT (content): Merge conflict in flag.py
Automatic merge failed; fix conflicts and then commit the result.
AsumomezaC-picoctf@webshell:~/drop-in$ strings flag.py 
print("Printing the flag...")
<<<<<<< HEAD
print("picoCTF{t3@mw0rk_", end='')
=======
print("m@k3s_th3_dr3@m_", end='')
>>>>>>> feature/part-2
```

De ahí, si intentamos hacer el último merge, no podemos pq hay un [[Git#Resolver conflictos en un merge de Git|conflicto que debemos de resolver]]. 

```bash
nano flag.py 

print("Printing the flag...")
print("picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_", end='')

AsumomezaC-picoctf@webshell:~/drop-in$ git add .
AsumomezaC-picoctf@webshell:~/drop-in$ git commit -m "resolver conflicto"
[main 78f7b89] resolver conflicto
```

Y ahora realizamos el último merge.

```bash
AsumomezaC-picoctf@webshell:~/drop-in$ git merge feature/part-3
Auto-merging flag.py
CONFLICT (content): Merge conflict in flag.py
Automatic merge failed; fix conflicts and then commit the result.
AsumomezaC-picoctf@webshell:~/drop-in$ strings flag.py 
print("Printing the flag...")
<<<<<<< HEAD
print("picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_", end='')
=======
print("w0rk_7ffa0077}")
>>>>>>> feature/part-3
```
Fusionamos ambos y obtenemos la bandera
## Respuesta
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_7ffa0077}