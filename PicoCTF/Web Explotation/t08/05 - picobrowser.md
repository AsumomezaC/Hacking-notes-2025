#Software #Hacking #WebExplotation #Web #Internet 
# Definición
This website can be rendered only by **picobrowser**, go and catch the flag! `https://jupiter.challenges.picoctf.org/problem/50522/` ([link](https://jupiter.challenges.picoctf.org/problem/50522/)) or http://jupiter.challenges.picoctf.org:50522
# Hints
- You don't need to download a new web browser
# Solución
Inspeccionamos la página [[HTML]] y seguimos un paso similar a [[03 - logon]].
>Como no tenemos firefox, lo hacemos desde la consola (usando [[CURL]]).

```bash
C:\Users\52492>curl -s https://jupiter.challenges.picoctf.org/problem/50522/flag -H "User-Agent: picobrowser"
```
## Respuesta
picoCTF{p1c0_s3cr3t_ag3nt_51414fa7}