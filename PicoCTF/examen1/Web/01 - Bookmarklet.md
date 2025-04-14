#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Yo|Adrián Fernando Cuevas Solís]]
# Definición
Why search for the flag when I can make a bookmarklet to print it for me?Browse [here](http://titan.picoctf.net:51338/), and find the flag!
# Hints
- A bookmarklet is a bookmark that runs JavaScript instead of loading a webpage.
- What happens when you click a bookmarklet?
- Web browsers have other ways to run JavaScript too.
# Solución
Primero ingresamos a la pagina web y encontramos un código de [[Javascript]]

```javascript
        javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓ¡ÒÅ¤í";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();
    
```

Este código, como nos sugería la pista, lo ejecutamos en la consola de la pagina web:
```javascript
allow pasting
        javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£Ö�ÓÚåÛÑ¢ÕÓ�¡��ÒÅ¤�í";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();
```
Esto nos genera una alerta, que nos regresa la bandera.
## Respuesta
picoCTF{p@g3_turn3r_0148cb05}