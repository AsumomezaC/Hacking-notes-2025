#Hacking #Computación #Software #Herramienta
# exiftool

## Qué es
Herramienta CLI para leer, escribir y editar metadatos en archivos (imágenes, videos, PDFs, etc.).

## Instalación
- **Linux**: `sudo apt install libimage-exiftool-perl` (o usar `exiftool` en algunas distros).
- **macOS**: `brew install exiftool`.
- **Windows**: Descargar de [exiftool.org](https://exiftool.org/).

## Uso básico
```bash
# Leer todos los metadatos
exiftool archivo.jpg

# Extraer metadatos específicos (ej: fecha y modelo)
exiftool -DateTimeOriginal -Model archivo.jpg

# Eliminar metadatos (crea copia con "_original")
exiftool -all= archivo.jpg

# Editar un campo
exiftool -Artist="Tu Nombre" archivo.jpg
```

## Opciones útiles
- `-h`: Muestra ayuda.
- `-csv`: Exporta metadatos a CSV.
- `-r`: Procesa directorios recursivamente.
- `-overwrite_original`: Sobrescribe el archivo sin copia de seguridad.

## Ejemplo avanzado
Eliminar metadatos GPS de todas las imágenes en un directorio:
```bash
exiftool -r -GPS*= ./directorio
```
