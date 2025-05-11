#Software #Hacking #WebExplotation #Computación 
# Definición
Now you DON’T see me.This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?
# Hints
- How can you be sure of the redaction?
# Solución
Primero descargamos el archivo con [[wget]].
```bash
┌──(kali㉿kali)-[~/red]  
└─$ wget [https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf)  
--2025-05-10 14:39:19--  [https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.64, 3.161.55.61, 3.161.55.100, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.64|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 34915 (34K) [application/octet-stream]  
Saving to: ‘Financial_Report_for_ABC_Labs.pdf’  
  
Financial_Report_fo 100%[================>]  34.10K  --.-KB/s    in 0.07s    
  

2025-05-10 14:39:19 (516 KB/s) - ‘Financial_Report_for_ABC_Labs.pdf’ saved [34915/34915]
```

Al abrir el documento este parece tener partes ocultas, pero simplemente con copiar el contenido a obsidian, vemos lo que ocultaban. Que incluye la bandera.
```txt
Financial Report for ABC Labs, Kigali, Rwanda for the year 2021.  
Breakdown - Just painted over in MS word.  
Cost Benefit Analysis  
Credit Debit  
This is not the flag, keep looking  
Expenses from the  
picoCTF{C4n_Y0u_S33_m3_fully}  
Redacted document.
```
## Respuesta
picoCTF{C4n_Y0u_S33_m3_fully} 