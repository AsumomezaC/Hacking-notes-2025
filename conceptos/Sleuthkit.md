#Software #Hacking #Computación #Forenscic 
# SleuthKit (TSK)
**SleuthKit** es un conjunto de herramientas de código abierto para análisis forense digital. Se usa junto con **Autopsy** (su interfaz gráfica) para investigar sistemas de archivos, recuperar datos y analizar evidencias en discos duros, imágenes forenses (`.dd`, `.E01`, etc.) y dispositivos de almacenamiento.

## 📌 Conceptos Clave
- **Análisis forense**: Proceso de examinar medios digitales para hallar evidencias.
- **Sistemas de archivos soportados**: NTFS, FAT, EXT, HFS+, APFS, entre otros.
- **Imágenes forenses**: Archivos bit-a-bit (ej: `.raw`, `.E01`, `.aff`) que replican un disco.

---

## 🔧 Herramientas Principales (CLI)
### 1. `fsstat`
Muestra información del sistema de archivos (tipo, tamaño, clusters, etc.).
```bash
fsstat -o 63 /dev/sdb1  # Analiza partición con offset 63
```

### 2. `mmls`
Lista las particiones de un disco/imagen.
```bash
mmls imagen.dd
```

### 3. `fls`
Lista archivos y directorios (incluye eliminados).
```bash
fls -r -p /dev/sda1  # -r: recursivo, -p: muestra paths completos
```

### 4. `icat`
Extrae el contenido de un archivo por su inodo.
```bash
icat -o 2048 imagen.E01 368  > archivo_recuperado.txt  # Extrae inodo 368
```

### 5. `blkcalc`
Calcula la ubicación física de un bloque lógico (útil para recuperación).

### 6. `tsk_recover`
Recupera archivos completos de una imagen/disk.
```bash
tsk_recover -e imagen.dd output_dir/  # -e: incluye eliminados
```

---

## 🔍 Casos de Uso en Hacking/Forense
### 1. **Recuperar archivos eliminados**
```bash
fls -rd /dev/sdb1 | grep "*.pdf"  # Busca PDFs eliminados
icat /dev/sdb1 <inodo> > recovered.pdf
```

### 2. **Analizar metadatos**
```bash
istat imagen.dd 1456  # Muestra metadatos del inodo 1456
```

### 3. **Investigar timelines**
Genera una línea de tiempo de actividad del sistema:
```bash
fls -m "/" -r imagen.dd > timeline.body
mactime -b timeline.body -d > timeline.csv
```

### 4. **Extraer evidencias de imágenes forenses**
- Usar `autopsy` para análisis gráfico (corre sobre SleuthKit).