---
tags:
  - CTF
  - Criptografía
  - Hacking
  - Software
  - Programación
  - Computación
---
>Problema de la rama de [[Crypto]]
# Descripción
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 43522`.
# Pistas
- Flag is not in the usual flag format
# Solución
Primero iniciamos conectándonos usando [[NET CAT (nc)]].
```bash
AsumomezaC-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 43522
-------------------------------------------------------------------------------
rkafmlow znmn hw ukpm yblf - ymnqpnaru_hw_r_kgnm_blciel_kfyclpamly
-------------------------------------------------------------------------------
lbnxnu yukekmkghorz dlmlclskg tlw ozn ozhme wka ky yukekm jlgbkghorz dlmlclskg, l blae ktanm tnbb dakta ha kpm ehwomhro ha zhw kta elu, lae wohbb mncncinmne lckaf pw kthaf ok zhw fbkkcu lae omlfhr enloz, tzhrz zljjnane ozhmonna unlmw lfk, lae tzhrz h wzlbb enwrmhin ha how jmkjnm jblrn. ykm ozn jmnwnao h thbb kabu wlu ozlo ozhw blaektanmykm wk tn pwne ok rlbb zhc, lbozkpfz zn zlmebu wjnao l elu ky zhw bhyn ka zhw kta nwolontlw l womlafn oujn, uno kan jmnoou ymnqpnaobu ok in cno thoz, l oujn livnro lae ghrhkpw lae lo ozn wlcn ohcn wnawnbnww. ipo zn tlw kan ky ozkwn wnawnbnww jnmwkaw tzk lmn gnmu tnbb rljlibn ky bkkdhaf lyonm oznhm tkmbebu lyylhmw, lae, ljjlmnaobu, lyonm akozhaf nbwn. yukekm jlgbkghorz, ykm hawolarn, infla thoz anxo ok akozhaf; zhw nwolon tlw ky ozn wclbbnwo; zn mla ok ehan lo koznm cna'w olibnw, lae ylwonane ka oznc lw l okleu, uno lo zhw enloz ho ljjnlmne ozlo zn zle l zpaemne ozkpwlae mkpibnw ha zlme rlwz. lo ozn wlcn ohcn, zn tlw lbb zhw bhyn kan ky ozn ckwo wnawnbnww, ylaolwohrlb ynbbktw ha ozn tzkbn ehwomhro. h mnjnlo, ho tlw ako wopjhehouozn clvkmhou ky oznwn ylaolwohrlb ynbbktw lmn wzmnte lae haonbbhfnao nakpfzipo vpwo wnawnbnwwanww, lae l jnrpbhlm alohkalb ykmc ky ho.
```
Al entrar vemos un texto bastante extraño, y como sugería la pista, la bandera no esta en la forma habitual. Sin embargo pare todo con una longitud y estructura muy similar a un idioma, lo que nos hace creer que es un [[Cifrado de sustitución]] (y que en el título tenemos el contenido de la bandera: ymnqpnaru_hw_r_kgnm_blciel_kfyclpamly). Usamos una [herramienta online](https://www.guballa.de/substitution-solver) para decodificarlo:

```
-------------------------------------------------------------------------------
congrats here is your flag - frequency_is_c_over_lambda_ogfmaunraf
-------------------------------------------------------------------------------
alexey fyodorovitch karamazov was the third son of fyodor pavlovitch karamazov, a land owner well known in our district in his own day, and still remembered among us owing to his gloomy and tragic death, which happened thirteen years ago, and which i shall describe in its proper place. for the present i will only say that this landownerfor so we used to call him, although he hardly spent a day of his life on his own estatewas a strange type, yet one pretty frequently to be met with, a type abject and vicious and at the same time senseless. but he was one of those senseless persons who are very well capable of looking after their worldly affairs, and, apparently, after nothing else. fyodor pavlovitch, for instance, began with next to nothing; his estate was of the smallest; he ran to dine at other men's tables, and fastened on them as a toady, yet at his death it appeared that he had a hundred thousand roubles in hard cash. at the same time, he was all his life one of the most senseless, fantastical fellows in the whole district. i repeat, it was not stupiditythe majority of these fantastical fellows are shrewd and intelligent enoughbut just senselessness, and a peculiar national form of it.
```
Y obtenemos la bandera.
## Respuesta
picoCTF{frequency_is_c_over_lambda_ogfmaunraf}