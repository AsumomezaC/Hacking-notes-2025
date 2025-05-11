#Software #Hacking #WebExplotation #Computación 
# Definición
Every file gets a flag.The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/257/flag.png).
# Hints
(None)
# Solución
Primero descargamos el archivo con [[wget]].
```bash
┌──(kali㉿kali)-[~/hideme]  
└─$ wget [https://artifacts.picoctf.net/c/257/flag.png](https://artifacts.picoctf.net/c/257/flag.png)  
--2025-05-10 14:47:53--  [https://artifacts.picoctf.net/c/257/flag.png](https://artifacts.picoctf.net/c/257/flag.png)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.26, 3.161.55.64, 3.161.55.100, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.26|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 43020 (42K) [application/octet-stream]  
Saving to: ‘flag.png’  
  
flag.png            100%[================>]  42.01K  --.-KB/s    in 0.04s    
  
2025-05-10 14:47:59 (1001 KB/s) - ‘flag.png’ saved [43020/43020]  
```
  
 Después buscamos información relevante con [[Strings]].                                                                        
```bash
┌──(kali㉿kali)-[~/hideme]  
└─$ strings flag.png                          
IHDR  
IDATx^  
;/"@  
M<g@H  
wHBH  
RPZ(Ee  
RPX`  
RRV$  
`()  
        }o9  
#@Ie  
hD`B  
WM_}  
cqsM  
U AvH  
^^'%  
kx8j  
1#=u  
Yza>  
Y+fZj  
B Y`%  
YY'u  
A8!\c  
E<@Z  
-U(0  
m PPI@  
JkJd  
9`n!@  
{_H5  
4NC=7  
8`      @JfA  
>]#'  
`SIe  
:),)0K  
bEC4|  
.(.D  
N_WT  
VZU"  
^~IU  
X,&sW  
@6||9  
& 9L  
GX{Q  
_V]"  
~-PT  
$j$4  
k3o@  
_5f%!  
+O\3  
ewnF  
 ^D h  
=RZS"k  
-nkL  
K7KX  
Y]'+  
4_&(  
 T-E  
?"}P  
e       -],  
HkNz  
@NcA!  
=yRx  
pLc<  
_       C:j  
1ILKz  
pfR=  
&g~     k  
R!c]  
s[&!  
=R2c)  
[U<XK  
1C *  
(MeoR  
B+      jm  
CO~9  
?bH2u.9n  
x<+@  
DaU)  
IDAT  
WoD0  
vr1&\  
@z;{}  
~1Qw  
Z,H+  
3!\R  
4%Q     J  
P--z  
1/B~  
$ O-  
^&@)  
ZV8M  
>gre  
fkwK  
`)`W  
kV8Y&>  
mZ-g  
Z@d?  
Q7 M  
#WJ^w  
[?)s  
4cA-  
Z%EeE  
`BBe  
RPT+  
y JJ  
RTY'Ug  
UOZ.U  
fSh8  
4H~e  
V02i  
vKGC  
pXch    \\Q$+  
v\,,+  
DV?i  
+@bJX   0S  
HHIW<$  
B[bU  
3 \R$  
V6<s  
<pXb  
k"0U  
 `&]  
BEDO`M  
tObJ  
zRV]  
j*%R  
,u/x  
xj!@[  
pQ%R  
53-8  
vHWS  
k0q^  
rK &  
N~cN.C/p  
r3!2tg  
Wk@Hs  
@. @  
H-Ip  
@}|?  
R#Cn_  
93"0q  
/|GS  
NJ\;I  
9H6 `  
r&D }  
b}(nT  
C[[Z  
B5IW  
t/tz  
$\T4  
D[:d  
^&BgK  
}w~60KO  
z/2`  
"7\!rp  
f,F  
Ka1H@&2  
.       80@  
#GDn  
R@`h  
\UJG  
w4v!  
^7,     @  
IDAT  
'UDd  
%t3,  
9Q0)  
u       xE  
50_-  
`       HXf  
)^8O  
GO:9  
(+>y  
JO{_  
5Mp!  
9f      Hh  
f       H&  
Yl      H  
$\Y&  
ds?:  
JW.q  
6eMvP  
pv!@  
04e3  
|.}z  
$h>nW  
wJ^Y  
t[|@  
`r("0Q  
`gc7,  
"f      @  
 D`R  
-RP     K  
"{wK  
_[Kc  
yI      R  
O##f_P  
B~"h  
@v @  
8K"@  
pr0"@  
~&yy  
A0^@"  
8?_C  
ByXc  
C$\T$e  
H@H5ES\h  
2X!E  
        )       t  
wuIAm  
?2|e  
Qq/yE  
oBo,  
(,-.  
4-3P  
b:4v#  
;^?,  
,}2]  
HKV/  
_)q/  
aHp`  
w}Dz  
xiA&s  
ZV6l  
//5a  
N9h/e  
84Va  
l;w|  
]o8-  
\8{?p  
[BEN  
7`:n  
:_=K  
wW0jD  
B \GUO<W  
_[5h  
#\QfM  
g,A8  
+`S,l  
#L{d  
(Y;t  
.U2=  
zi "b\f  
[?Cj  
 L6/  
VpCq  
AH[W  
vEkD  
}&HU  
G`Yu  
?")V  
kOv-  
Bp*A;  
        4oQ  
xXXA#k  
@NF{  
40%>  
+[34T  
0>gW  
wt?6Cb  
K>`q  
(,^g  
/uuT>  
1#h4  
j-P"  
IDAT  
hx#C  
w}W*  
]VJ4d  
0V7@  
+AXps%  
VFt,  
h~cW't  
V(1J  
q       b2  
"@#X  
N}n|  
(b>|  
rkbbZ  
4Umx  
+7"?  
7,35  
~#-  
xC@M  
Cc2.  
bMYF  
Zb5a  
-5-!x&|  
4o@*  
nc*D  
g^$g  
iq"u  
wjD}  
V9/$  
J6zQ!o  
+<5h  
heAm  
>+MA  
-=$!  
YFwy  
dT~9  
0S~x  
xqOd  
An~f  
&Xd^b  
q)''g  
b%R^  
{.*-  
eJ{O  
+S`^  
B8Ro>u  
*$kA  
m!:7  
<GJ]#  
EH`Yt*  
*YTg  
Y]Y_)  
(r<p  
$|+.  
-G@P  
vic;  
uJ4~  
jF?v  
E7W[  
Z|oK&@  
5- H  
|}i=  
^VZ\  
E  J  
 2ao@  
EC>?  
+NWk  
H'@gnu  
>zEZ"G%  
g>z     M  
Z>7j  
"1fkG  
=it4  
x#T*  
xgbv  
AqgL9  
]J%g  
o^Y&k'T  
P#B2D  
$?Cy  
SN%@  
<hyrJ  
IDAT,  
(*xm"  
A$"6yX  
7  P  
H:.F  
Bx}x  
5X7c  
r6eig,  
zJ,qcM  
8. r  
        iAwyb!k  
#^"`  
]**.  
E@d}iX^g  
p]H_  
_f:#  
jWeo  
059P  
I.B2  
mmI2I  
3eG>^  
Iw@p  
]Y+XAd  
?e7T  
lS?w  
a)v'm  
CjlT  
ck$@  
l|.pKN  
@ tCO  
7Vq#  
lFB`  
cOk1  
bFRiR-  
lXjV  
C%l5  
eIBQ0'0  
'bk%6  
BEr-  
j <kznk  
72A:  
!Y-r  
Eu*eW  
%m02  
-y]:  
a/~q;  
\OTzZK  
|3.8g3MyO  
?<a&  
.6Umj2-  
q]=6  
IEND  
secret/UT  
secret/flag.pngUT  
L5"E  
{b.I1  
x^>/  
#$!(  
.|      tHu  
/A{/  
!0xz  
s`i,  
        =E|  
O$e&QK  
kk%%  
JHEEV  
gXC:  
(A![  
DqKE  
HK1n  
XmjwZ  
3^:-|  
XupF  
kI-%  
PjK-?  
@$=_  
QceM  
SAoE  
fa\}P4  
}36R  
*&=Oox3  
Rr`R  
dE)I  
+KV4  
^;)q  
0{GMM?  
B%U-  
Nnnn#  
VL{K  
ihAI  
DA@R  
 Sz}  
$/ZQ#  
ZjZZZ!  
\9n:  
z.gJ  
%[65f  
7b:|iH/k+  
?41Y^  
1#!!n  
QTWmY}  
%&&z  
t>[@  
07RZ  
8aB `8-  
s[*R  
'aaix  
secret/UT  
secret/flag.pngUT  
```
                                                                               
Observamos que se esconde algo en la dirección secret, y usamos [[Binwalk]] para buscar más información
```bash
┌──(kali㉿kali)-[~/hideme]  
└─$ binwalk flag.png      
  
DECIMAL       HEXADECIMAL     DESCRIPTION  
--------------------------------------------------------------------------------  
0             0x0             PNG image, 512 x 504, 8-bit/color RGBA, non-interlaced  
41            0x29            Zlib compressed data, compressed  
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/  
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2959, uncompressed size: 3108, name: secret/flag.png  
42998         0xA7F6          End of Zip archive, footer length: 22  
```  

Observamos que hay un archivo zip escondido, por lo que lo [[Descompresión de archivos|descomprimimos]] usando [[Binwalk#2. **Extracción de Archivos**]].
```bash                                                                               
┌──(kali㉿kali)-[~/hideme]  
└─$ binwalk -e flag.png  
  
DECIMAL       HEXADECIMAL     DESCRIPTION  
--------------------------------------------------------------------------------  
41            0x29            Zlib compressed data, compressed  
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/  
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2959, uncompressed size: 3108, name: secret/flag.png  
  
WARNING: One or more files failed to extract: either no utility was found or it's unimplemented  
```
  
Nos movemos a la dirección donde esta la bandera.                                                                               
```bash
┌──(kali㉿kali)-[~/hideme]  
└─$ ls                      
flag.png  _flag.png.extracted  
                                                                               
┌──(kali㉿kali)-[~/hideme]  
└─$ cd _flag.png.extracted  
                                                                               
┌──(kali㉿kali)-[~/hideme/_flag.png.extracted]  
└─$ ls  
29  29.zlib  9B3B.zip  secret  
                                                                               
┌──(kali㉿kali)-[~/hideme/_flag.png.extracted]  
└─$ cd secret              
                                                                               
┌──(kali㉿kali)-[~/hideme/_flag.png.extracted/secret]  
└─$ ls  
flag.png
```

La abrimos, y vemos la bandera. 
## Respuesta
picoCTF{Hiddinng_An_imag3_within_@n_ima9e_dc2ab58f}