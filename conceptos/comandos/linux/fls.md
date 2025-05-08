#Comando #Linux #Contenido #Hacking #Software 
# **Comando `fls`: Guía Completa para Análisis Forense de Sistemas de Archivos**

## 🔍 **¿Qué es `fls`?**
`fls` (File Listing) es una herramienta del **Sleuth Kit (TSK)** que lista archivos y directorios en sistemas de archivos, incluyendo:
- Archivos existentes
- **Archivos eliminados** (crucial en [[Forensic]])
- [[Metadatos]] del sistema de archivos
## 🛠 **Uso Básico**
```bash
fls [opciones] -o offset imagen_disco
```

### 📌 **Parámetros Clave**
| Parámetro | Descripción |
|-----------|-------------|
| `-o offset` | Sector de inicio de la partición (obligatorio) |
| `-r` | Muestra recursivamente |
| `-p` | Muestra rutas completas |
| `-l` | Formato largo (como `ls -l`) |
| `-u` | Muestra archivos eliminados (unallocated) |
| `-m prefijo` | Prefijo para rutas (ej: /C/) |

## 📂 **Ejemplos Prácticos**

### 1. **Listar contenido de una partición NTFS**
```bash
fls -o 2048 -r -l imagen.dd
```
*(Offset 2048 es común en particiones modernas)*

### 2. **Encontrar archivos eliminados**
```bash
fls -o 63 -u /dev/sdb1
```

### 3. **Exportar lista completa a archivo**
```bash
fls -o 2048 -r -p imagen.E01 > lista_archivos.txt
```

## 🔎 **Interpretación de Resultados**
La salida muestra:
```
d/d 46:    Documents    # Directorio activo (inodo 46)
r/r 188:   report.pdf   # Archivo regular
* r/r 192:  secret.txt  # Archivo eliminado (*)
```

- **Primera columna**:
  - `d/d`: Directorio
  - `r/r`: Archivo regular
  - `l/l`: Enlace simbólico
  - `*`: Entrada eliminada

## 🕵️ **Casos de Uso Forenses**

### 1. **Recuperar estructura de directorios eliminados**
```bash
fls -o 63 -u -r imagen.dd | grep "^\* d/d"
```

### 2. **Buscar archivos específicos eliminados**
```bash
fls -o 2048 -u imagen.img | grep -i "\.docx"
```

### 3. **Integración con `icat` para extraer archivos**
Primero encontrar inodos:
```bash
fls -o 2048 imagen.dd | grep "important.docx"
```
Luego extraer:
```bash
icat -o 2048 imagen.dd 192 > recovered.docx
```

## ⚙️ **Opciones Avanzadas**

| Opción | Descripción |
|--------|-------------|
| `-s` | Mostrar sólo archivos de sistema |
| `-z zona` | Zona horaria para timestamps |
| `-f tipo_fs` | Forzar tipo de sistema de archivos |
| `-i img_type` | Tipo de imagen (raw, ewf, etc) |

## 📊 **Formatos de Salida**
```bash
fls -l -m "/" -o 2048 imagen.dd  # Formato largo con prefijo
```
Salida ejemplo:
```
/r/r 256 /home/user/file.txt 2023-01-01 12:00:00 (EST)
```

## 🔗 **Integración con Otras Herramientas TSK**

1. **Generar línea de tiempo con `mactime`**:
```bash
fls -o 2048 -r -m "/" imagen.dd > timeline.body
mactime -b timeline.body -d > timeline.csv
```

2. **Buscar metadatos con `istat`**:
```bash
fls -o 2048 imagen.dd | awk '{print $2}' | xargs -I {} istat -o 2048 imagen.dd {}
```

## ⚠️ **Errores Comunes**

1. **Offset incorrecto**:
   - Usar `mmls` primero para encontrar el offset correcto
   ```bash
   mmls imagen.dd
   ```

2. **Sistema de archivos no soportado**:
   - Verificar con `fsstat`:
   ```bash
   fsstat -o 2048 imagen.dd
   ```

## 📌 **Tips para Análisis Eficiente**

1. **Filtrar por fechas**:
```bash
fls -l -o 2048 imagen.dd | grep "2023-06"
```

2. **Buscar archivos ocultos**:
```bash
fls -s -o 2048 imagen.dd
```

3. **Combina con `grep`**:
```bash
fls -r -o 2048 imagen.dd | grep -i "backup"
```

`fls` es una herramienta indispensable en análisis forense digital, permitiendo reconstruir estructuras de archivos incluso después de eliminaciones o daños en el sistema de archivos. Su combinación con otras herramientas de TSK forma el núcleo de muchas investigaciones digitales.