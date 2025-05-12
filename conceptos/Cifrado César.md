# Cifrado César
>También llamado caesar
## Definición
El **Cifrado César** es uno de los algoritmos de cifrado por sustitución más antiguos, utilizado por Julio César para comunicaciones militares. Consiste en desplazar cada letra del alfabeto un número fijo de posiciones (`N`).

## Características Clave
- **Tipo**: Cifrado de sustitución monoalfabética.
- **Desplazamiento típico**: Originalmente 3 posiciones (ROT3), pero puede ser cualquier número (ROT1 a ROT25).
- **Alfabeto afectado**: Solo letras (mayúsculas y minúsculas). No modifica números, espacios o símbolos.
- **Seguridad**: Extremadamente débil (fácil de descifrar por fuerza bruta o análisis de frecuencia).

## Fórmula Matemática
Para una letra en posición `x` (A=0, B=1, ..., Z=25):
```
Cifrado:  (x + N) mod 26  
Descifrado: (x - N) mod 26
```

## Ejemplo (Desplazamiento N=3)
Texto original:  
`HELLO`  
Texto cifrado:  
`KHOOR` (H→K, E→H, L→O, etc.)  

## Variantes Relacionadas
1. **ROT13**: Caso especial con N=13 (auto-inverso).
2. **ROT5**: Para cifrar dígitos (0-9).
3. **ROT47**: Usa 47 posiciones (incluye símbolos ASCII).

## Debilidades y Ataques
1. **Fuerza bruta**: Solo 25 posibles desplazamientos en inglés.
2. **Análisis de frecuencia**: Comparar la frecuencia de letras en el texto cifrado con el idioma original.
   - En inglés: `E` (12.7%), `T` (9.1%), `A` (8.2%) son las más comunes.

## Herramientas para Descifrar
- **Python**:
  ```python
  def caesar_decrypt(text, shift):
      result = ""
      for char in text:
          if char.isalpha():
              offset = 65 if char.isupper() else 97
              result += chr((ord(char) - offset - shift) % 26 + offset)
          else:
              result += char
      return result
  print(caesar_decrypt("KHOOR", 3))  # Output: HELLO
  ```
- **CyberChef**: Usar la operación "ROT13" y ajustar el desplazamiento.

## Usos en CTFs
- **Banderas básicas**: Ej. `picoCTF{cvpbPGS}` (ROT13).
- **Mensajes ocultos**: En archivos, metadatos o capturas de red.

## Ejemplo Práctico (CTF)
**Texto cifrado**:  
`Ymj vznhp gwtbs Ktc ozruji`  
**Solución**:
1. Probamos desplazamientos (N=5 funciona):  
   ```python
   caesar_decrypt("Ymj vznhp gwtbs Ktc ozruji", 5)
   ```
2. **Texto claro**:  
   `The quick brown Fox jumps`