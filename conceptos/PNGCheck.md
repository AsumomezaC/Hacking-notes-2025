#Software #Imágenes #Seguridad 
# Herramienta `pngcheck` para análisis de archivos PNG

## ¿Qué es pngcheck?
- **Verificador de integridad**: Utilidad para examinar la estructura de archivos PNG, JNG y MNG.
- **Detector de errores**: Identifica problemas de corrupción, chunks inválidos y metadatos malformados.
- **Informador técnico**: Muestra información detallada sobre la estructura interna del archivo.

## Instalación
```bash
# En distribuciones basadas en Debian/Ubuntu:
sudo apt install pngcheck

# En sistemas basados en RedHat:
sudo yum install pngcheck

# Desde fuentes (Linux/macOS):
wget http://www.libpng.org/pub/png/apps/pngcheck.tar.gz
tar -xzvf pngcheck.tar.gz
cd pngcheck
make && sudo make install
```

## Uso básico
```bash
pngcheck archivo.png
```
Salida típica:
```
archivo.png: OK: 800x600 (24-bit RGB, non-interlaced, 95.6% compression)
```

## Opciones principales

| Opción | Descripción |
|--------|-------------|
| `-v`   | Modo verboso (muestra todos los chunks) |
| `-c`   | Verifica checksums (por defecto activado) |
| `-t`   | Muestra tiempos de creación/modificación |
| `-f`   | Fuerza verificación incluso con errores |
| `-q`   | Modo silencioso (solo muestra errores) |
| `-7`   | Verifica solo chunks críticos (IHDR, PLTE, IDAT, IEND) |

## Ejemplos avanzados

### 1. Análisis detallado
```bash
pngcheck -vpt archivo.png
```
Muestra:
- Todos los chunks
- Tiempos de modificación
- Información de compresión

### 2. Verificar múltiples archivos
```bash
pngcheck *.png
pngcheck -q /ruta/a/directorio/*.png  # Solo reporta errores
```

### 3. Buscar chunks específicos
```bash
pngcheck -v archivo.png | grep -i "exif"  # Busca metadatos EXIF
```

### 4. Exportar información estructurada
```bash
pngcheck -l 0 archivo.png > analisis.txt  # Lista chunks con offsets
```

## Casos de uso comunes

### Detección de malware
```bash
pngcheck -v sospechoso.png | grep -A 5 "IDAT"  # Busca datos inusuales en chunks
```

### Recuperación de archivos
```bash
pngcheck -vf corrupto.png  # Intenta leer a pesar de errores
```

### Auditoría de metadatos
```bash
pngcheck -v imagen.png | grep -E "(tEXt|zTXt|iTXt)"  # Extrae texto incrustado
```

## Interpretación de chunks comunes

| Chunk   | Descripción |
|---------|-------------|
| IHDR    | Cabecera (dimensiones, tipo de color) |
| PLTE    | Paleta de colores |
| IDAT    | Datos de imagen (comprimidos) |
| IEND    | Marcador de final |
| tEXt    | Texto sin comprimir |
| zTXt    | Texto comprimido |
| eXIf    | Metadatos EXIF |

## Integración con otros comandos

### Extraer imagen de PDF corrupto
```bash
pdfimages -png documento.pdf temp
pngcheck -v temp-*.png
```

### Buscar PNGs modificados
```bash
find . -name "*.png" -exec pngcheck -t {} \; | grep "2024-"
```

## Solución de problemas

### Error común: "invalid chunk name"
- Causa: Corrupción de archivo o encabezado inválido
- Solución: Intentar recuperar con `-f` o herramientas como `pngcrush`

### Error: "CRC error"
- Causa: Datos alterados
- Verificar con: `pngcheck -c -v archivo.png`

> **Documentación oficial**: http://www.libpng.org/pub/png/apps/pngcheck.html