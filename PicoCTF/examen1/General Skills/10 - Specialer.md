#Software #Hacking #Computación #GeneralSkills
Hecho por: [[Briseida Guzmán Ramírez]]
# Definición
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.`ssh -p 55782 ctf-player@saturn.picoctf.net`. The password is `3f39b042`
# Hints
- What programs do you have access to?
# Solución
1. Conectarse usando [[ssh]]

```bash
AsumomezaC-picoctf@webshell:~$ ssh -p 55782 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:55782 ([13.59.203.175]:55782)' can't be established.
ED25519 key fingerprint is SHA256:lMXKIC17ONzyUJx7ZYBY5VSwoxCz20uq5/Nm+IhXKew.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:55782' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password: 
Specialer$ 

```

2. Realizamos: cd ../..  y tab2
```bash
Specialer$ cd ../..
```
3. Realizamos cd ../../ y tab 2 veces
```bash
Specialer$ cd ../../
bin/   home/  lib/   lib64/ 
```
4. ```
Ahora buscar este:  cd ../../home/ y tab 2 veces
```bash
Specialer$ cd ../../home/ctf-player/
.hushlogin  .profile    abra/       ala/        sim/        
```
5. Ahora se completa así después del paso   Specialer$ cd ../../home/ctf-player/  y enter
```bash
Specialer$ cd ../../home/ctf-player/
```
>Debe estar aquí -[[pwd]]
```shell
Specialer$ pwd
/home/ctf-player
```
6. Ahora: cd ctf-player/ y tab 2 veces
```bash
Specialer$ cd ctf-player/
.hushlogin  .profile    abra/       ala/        sim/    
```
>Aquí para que funcione se le debe dar tab antes de ctf
7. Entrar a cd abra/ -enter
```bash
Specialer$ cd abra/      
```
8. [[echo]] $(<cadabra.txt)
```bash
Specialer$ echo $(<cadabra.txt)
Nothing up my sleeve!
```
9. cd ../ala- Tab 2 veces
```bash
Specialer$ cd ../ala/
kazam.txt  mode.txt   
```
10. echo $(<kazam.txt)
```bash
Specialer$ echo $(<kazam.txt)
return 0 picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_811ae7e9}
Specialer$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
```
Y obtenemos la bandera

//Ayuda en [https://josephkimiri.github.io/posts/Specialer/](https://josephkimiri.github.io/posts/Specialer/)
## Respuesta
picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_811ae7e9}