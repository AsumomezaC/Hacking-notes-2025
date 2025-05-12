#Encriptación #Software #Lenguaje #Hacking #Criptografía #Seguridad 

# ROT Cipher (Caesar Cipher Variant)

## Definición
- **ROT** (Rotate) es un tipo de cifrado por sustitución que desplaza cada letra del alfabeto un número fijo de posiciones (`N`).
- Es un caso particular del **[[Cifrado César]]** (que usa desplazamiento de 3 por defecto).
- **ROT13** es el más común, donde `N = 13`.

## Características
- **Simetría**: En ROT13, aplicar el cifrado dos veces devuelve el texto original (porque `13 + 13 = 26` letras en el alfabeto inglés).
  - Ejemplo: `ROT13("pico") = "cvpb"` y `ROT13("cvpb") = "pico"`.
- **Solo afecta letras**: No modifica números, símbolos o espacios.
- **Inseguro**: Fácil de descifrar manualmente o con herramientas automáticas.

## Fórmula Matemática
Para una letra `L` en posición `x` (A=0, B=1, ..., Z=25):
```
Cifrado: (x + N) mod 26  
Descifrado: (x - N) mod 26

## Ejemplo (ROT13)
Texto plano:  
`picoCTF{flag}`  
Texto cifrado:  
`cvpbPGS{synt}`  

## Herramientas para Descifrar
1. **Python**:
   ```python
   import codecs
   texto_cifrado = "cvpbPGS{abg_gbb_onq_bs_n_ceboyrz}"
   texto_plano = codecs.decode(texto_cifrado, 'rot13')
   print(texto_plano)  # Output: picoCTF{not_too_bad_of_a_crypto}
   ```
2. **Consola Linux**:
   ```bash
   echo "cvpbPGS{abg_gbb_onq_bs_n_ceboyrz}" | rot13
   ```
3. **Online**: [CyberChef](https://gchq.github.io/CyberChef/) (usando la operación "ROT13").

## Usos en CTFs
- **Banderas ofuscadas**: Común en desafíos fáciles (ej. `picoCTF`).
- **Mensajes escondidos**: En metadatos o archivos de texto.

## Variantes
- **ROT5**: Para dígitos numéricos (0-9).
- **ROT47**: Incluye símbolos ASCII (desplazamiento de 47 posiciones).