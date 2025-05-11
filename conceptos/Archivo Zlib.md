#Compresión #Hacking #Software #Datos 
# Archivos ZLIB

## Qué es ZLIB
ZLIB es una biblioteca de [[Compresión de archivos|compresión]] de datos ampliamente utilizada que implementa el método de compresión DEFLATE. Es un estándar de facto para la compresión de datos en muchos sistemas y formatos de archivo.

## Características principales
- **Algoritmo**: Utiliza DEFLATE (combinación de LZ77 y codificación Huffman)
- **Sin pérdidas**: Compresión perfecta (los datos originales se recuperan exactamente)
- **Rendimiento**: Buen equilibrio entre velocidad y ratio de compresión
- **Licencia**: Libre de royalties, de uso gratuito

## Formatos que usan ZLIB
- PNG (imágenes)
- ZIP/GZIP
- HTTP comprimido
- Muchos formatos de juegos y aplicaciones

## Estructura de un archivo ZLIB
1. **Cabecera**: 2 bytes
   - Método de compresión (4 bits)
   - Información de ventana (4 bits)
   - Bandera de compresión (5 bits)
   - Bandera de checksum (1 bit)

2. **Datos comprimidos**: Bloques DEFLATE

3. **Checksum**: ADLER-32 (4 bytes)

## Uso en línea de comandos
```bash
# Comprimir
zlib-flate -compress < input.txt > output.zlib

# Descomprimir
zlib-flate -uncompress < input.zlib > output.txt
```

## Implementación en varios lenguajes

### [[Python]]
```python
import zlib

# Comprimir
compressed = zlib.compress(b'datos a comprimir')

# Descomprimir
decompressed = zlib.decompress(compressed)
```

### [[JavaScript]] ([[Node.js]])
```javascript
const zlib = require('zlib');

// Comprimir
zlib.deflate('datos a comprimir', (err, buffer) => {
  if (!err) console.log(buffer);
});

// Descomprimir
zlib.inflate(buffer, (err, buffer) => {
  if (!err) console.log(buffer.toString());
});
```

## Ventajas y desventajas

### Ventajas
- Ampliamente soportado
- Buen ratio de compresión
- Rápido
- Implementaciones en muchos lenguajes

### Desventajas
- No es el mejor ratio de compresión disponible
- No soporta compresión progresiva como otros formatos
## Referencias
1. RFC 1950 - ZLIB Compressed Data Format Specification
2. Sitio oficial de ZLIB: https://zlib.net/