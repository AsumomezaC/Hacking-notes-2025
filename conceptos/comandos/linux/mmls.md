#Comando #Linux #Análisis #Software #Hacking #Forenscic 
# **mmls: Análisis de Estructuras de Discos y Particiones en The Sleuth Kit**

El comando `mmls` (Media Management List) es una herramienta fundamental del **The Sleuth Kit (TSK)** que permite visualizar la estructura de particiones de discos duros, imágenes forenses y otros medios de almacenamiento. Es esencial en análisis forenses digitales y recuperación de datos.
## 🔍 **Funcionalidad Principal**
Muestra el diseño de particiones (tabla de particiones) de:
- Discos físicos (`/dev/sda`, `/dev/nvme0n1`)
- Imágenes forenses (`.dd`, `.E01`, `.aff`)
- Volúmenes RAID reconstruidos

## 🛠 **Instalación**
```bash
# Debian/Ubuntu
sudo apt install sleuthkit

# RHEL/CentOS
sudo yum install sleuthkit

# macOS (Homebrew)
brew install sleuthkit
```

## 💻 **Sintaxis Básica**
```bash
mmls [opciones] imagen_disco_o_dispositivo
```

## 📊 **Ejemplos Prácticos**

### 1. Mostrar particiones de una imagen forense
```bash
mmls imagen.dd
```
Salida típica:
```
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Description
000:  Meta    0000000000   0000000000   0000000001   Primary Table (#0)
001:  -----   0000000000   0000002047   0000002048   Unallocated
002:  000:00  0000002048   0020971519   0020969472   NTFS (0x07)
003:  000:01  0020971520   0041943039   0020971520   Linux Swap (0x82)
```

### 2. Analizar un disco físico (requiere root)
```bash
sudo mmls /dev/sda
```

### 3. Especificar tipo de tabla de particiones
```bash
mmls -t dos imagen.dd  # Forzar DOS/MBR
mmls -t gpt imagen.dd  # Forzar GPT
```

## 🔧 **Opciones Clave**

| Opción | Descripción |
|--------|-------------|
| `-i <tipo>` | Especificar tipo de imagen (raw, ewf, etc.) |
| `-b <tamaño>` | Tamaño de sector (ej: 512, 4096) |
| `-o <offset>` | Offset de inicio en sectores |
| `-r` | Mostrar nombres de sistema de archivos |
| `-v` | Modo verbose |

## 🕵️ **Casos de Uso Avanzados**

### 1. Analizar imágenes con offset conocido
```bash
mmls -o 2048 imagen.dd  # Offset de 2048 sectores (1MB)
```

### 2. Identificar particiones eliminadas
```bash
mmls -r /dev/sdb  # Muestra posible espacio no asignado
```

### 3. Trabajar con sistemas de archivos exóticos
```bash
mmls -t bsd disk.img  # Para tablas BSD
```

### 4. Integración con otras herramientas TSK
```bash
mmls image.E01 | grep NTFS | awk '{print $3}' | xargs -I {} fls -o {} image.E01
```
(Extrae inodos de partición NTFS para análisis con `fls`)

## 📚 **Interpretación de Resultados**

- **Slot**: Número de partición
- **Start/End**: Sectores inicial/final
- **Length**: Tamaño en sectores
- **Description**: Tipo de partición
- **Unallocated**: Espacio no asignado (potencialmente conteniendo datos eliminados)

## ⚠️ **Consideraciones Importantes**

1. **Permisos**: Requiere acceso de lectura al dispositivo
2. **Sistemas cifrados**: No puede leer particiones cifradas sin descifrar primero
3. **Discos dañados**: Usar `ddrescue` primero si hay sectores dañados
4. **Unidades**: Verificar siempre el tamaño de sector (normalmente 512 bytes)

## 🔄 **Alternativas y Herramientas Relacionadas**

- `fdisk -l`: Herramienta tradicional de Linux
- `gdisk`: Para tablas GPT
- `parted`: Herramienta de particionado
- `diskutil list`: En macOS

## 🎓 **Consejos para Análisis Forense**

1. **Documentar offsets**: Guardar offsets de particiones para usar con `icat`, `fls`
2. **Verificar checksums**: Comparar con `fsstat` para validar
3. **Buscar slack space**: Espacio entre particiones puede contener datos ocultos
4. **Multiples tablas**: Algunos discos pueden tener MBR y GPT simultáneamente

El comando `mmls` es la puerta de entrada para cualquier análisis forense serio de medios de almacenamiento, permitiendo entender la estructura del disco antes de realizar extracciones con otras herramientas del Sleuth Kit como `fls` o `icat`.