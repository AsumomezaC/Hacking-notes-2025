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
In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/b9ddda080c56fb421bf30409bec3460d/values)
# Pistas
- Bits are expensive, I used only a little bit over 100 to save money
# Solución
Primero descargamos el archivo con [[wget]]
```bash
AsumomezaC-picoctf@webshell:~/mind$ wget https://mercury.picoctf.net/static/b9ddda080c56fb421bf30409bec3460d/values
--2025-05-22 00:29:12--  https://mercury.picoctf.net/static/b9ddda080c56fb421bf30409bec3460d/values
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 206 [application/octet-stream]
Saving to: 'values'

values                                       100%[============================================================================================>]     206  --.-KB/s    in 0s      

2025-05-22 00:29:12 (96.0 MB/s) - 'values' saved [206/206]
```
Y vemos su contenido con [[CAT]].
```bash
AsumomezaC-picoctf@webshell:~/mind$ cat values 
Decrypt my super sick RSA:
c: 964354128913912393938480857590969826308054462950561875638492039363373779803642185
n: 1584586296183412107468474423529992275940096154074798537916936609523894209759157543
e: 65537
```

Nos percatamos que usa cifrado [[RSA]], por lo que apoyándonos de [esta página](https://www.alpertron.com.ar/ECM.HTM) factorizamos 'n'. Encontrando el Euler's totient: 1584586296183412107468474423529992275939442909666671958851095205636494743947753520.

Usamos un programa de [[Java]], y obtenemos la bandera.
```java
package Cryptography.javacodebad;

import java.math.BigInteger;
import java.util.ArrayList;
import java.util.Scanner;

public class RSA {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        BigInteger N,phiN,e,d,m,c;

        // cipertext c, plaintext m

        System.out.println("Insert N");
        N = new BigInteger (sc.nextLine());

        System.out.println("Input e");
        e = new BigInteger (sc.nextLine());

        System.out.println("Input c");
        c = new BigInteger (sc.nextLine());

        System.out.println("Input phi");
        phiN = new BigInteger (sc.nextLine());

        sc.close();

        d = e.modInverse(phiN);
        m = c.modPow(d, N);

        System.out.println("d = "+d);           
        System.out.println("m = "+m);

        System.out.println("m in base 256 = "+base256(m));
        System.out.println("Convert with ASCII \n"+ Encode256(base256(m)));
    }
    static ArrayList<BigInteger> base256 (BigInteger M) {
        BigInteger base = new BigInteger("256");
        ArrayList<BigInteger> message256 = new ArrayList<BigInteger>();
        BigInteger sisa=M;
        BigInteger k;
        double z = Double.parseDouble(M.toString());
        double p = Math.floor(Math.log(z)/Math.log(256));
        int r = (int) p;
        for (int j=0;j<=r;j++){
            k=sisa.mod(base);
            sisa=sisa.divide(base);
            message256.add(k);
        }
        return message256;
    }

    static String Encode256 (ArrayList<BigInteger> ascii) {
        String ascii256="";
        int g;
        for (int i=0;i<ascii.size();i++) {
            g = Integer.parseInt(""+ascii.get(i));
            ascii256=ascii256+( (char) g );
        }
        return ascii256;
    }
}
```

Y ejecutamos.
```bash
C:\Downloads>javac Cryptography/javacodebad/RSA.java

C:\Downloads>java Cryptography.javacodebad.RSA
Insert N
1584586296183412107468474423529992275940096154074798537916936609523894209759157543
Input e
65537
Input c
964354128913912393938480857590969826308054462950561875638492039363373779803642185
Input phi
1584586296183412107468474423529992275939442909666671958851095205636494743947753520
d = 935562844569036545560296463739101898548923569077653917264816483618391559307175713
m = 13016382529449106065927291425342535437996222135352905256639684640304028661985917
m in base 256 = [125, 50, 54, 57, 56, 49, 57, 51, 55, 95, 100, 111, 48, 103, 95, 48, 110, 95, 78, 95, 49, 49, 97, 109, 115, 123, 70, 84, 67, 111, 99, 105, 112]
Convert with ASCII
}26981937_do0g_0n_N_11ams{FTCocip
```
Nos damos cuenta que la bandera esta al revés, por lo que usando la [IA](chat.deepseek.com), la acomodamos (obteniendo la bandera).
```python
reved_string = "}26981937_do0g_0n_N_11ams{FTCocip"
flag = ""
for i in reved_string:
    flag = i + flag
print(flag)
```
## Respuesta
picoCTF{sma11_N_n0_g0od_73918962}