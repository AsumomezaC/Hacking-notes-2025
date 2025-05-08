#Software #Hacking #WebExplotation #Computación 
# Definición
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/14/challenge.zip)

The same files are accessible via SSH here:`ssh -p 55233 ctf-player@atlas.picoctf.net`Using the password `84b12bae`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
# Hints
- QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
- Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
- If you don't have access to a phone, you can also use zbar-tools to convert an image to text
# Solución

## Respuesta