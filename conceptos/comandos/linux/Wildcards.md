#Hacking #Software #Computación #Codificación
# Wildcards (Comodines) en Linux: Guía Completa

## 📌 Introducción
Los wildcards o comodines son caracteres especiales que permiten **seleccionar múltiples archivos o directorios** basados en patrones. Son esenciales para:
- Automatizar tareas repetitivas.
- Filtrar resultados en comandos como `ls`, `cp`, `mv`, `rm`, `find`, etc.
- Optimizar la gestión de archivos en la terminal .

---

## 🔍 Tipos de Wildcards y Sintaxis

### 1. Asterisco (`*`)
- **Función**: Coincide con **cualquier número de caracteres** (incluyendo cero).
- **Ejemplos**:
  ```bash
  ls *.txt       # Lista todos los archivos .txt
  cp image* ~/backup/   # Copia archivos que empiezan con "image"
  ```

### 2. Signo de Interrogación (`?`)
- **Función**: Coincide con **exactamente un carácter**.
- **Ejemplos**:
  ```bash
  ls file?.txt   # Lista file1.txt, fileA.txt, pero no file10.txt
  rm data_?.csv  # Elimina data_1.csv, data_X.csv, etc.
  ```

### 3. Corchetes (`[]`)
- **Función**: Coincide con **un único carácter** dentro de un rango o conjunto.
- **Ejemplos**:
  ```bash
  ls report_[0-9].pdf   # Lista report_1.pdf, report_2.pdf, etc.
  mv [A-Z]*.log /logs   # Mueve archivos .log que empiezan con mayúscula
  ```

### 4. Llaves (`{}`)
- **Función**: Permite **combinar múltiples patrones** (no es un wildcard clásico, pero útil en expansión).
- **Ejemplos**:
  ```bash
  cp {*.txt,*.md} ~/docs/   # Copia archivos .txt y .md
  ```

### 5. Negación (`[!]` o `[^]`)
- **Función**: Excluye caracteres específicos.
- **Ejemplos**:
  ```bash
  ls [!a-z]*.txt   # Lista archivos .txt que NO empiezan con minúscula
  ```

---

## 🛠️ Uso Avanzado con Comandos

### Con `find` 
```bash
find /ruta -name "*.log"          # Busca archivos .log recursivamente
find . -type f -name "data_[0-9]*"  # Archivos que empiezan con "data_" + dígito
```

### Con `grep` y redirección
```bash
grep "error" *.log > errors.txt   # Busca "error" en todos los .log
```

### Con `rm` y precaución 
```bash
rm -i *.tmp   # Elimina archivos .tmp con confirmación interactiva
```

---

## 📂 Casos Prácticos

### 1. Organizar archivos
```bash
mkdir -p {images,documents,backup}
mv *.jpg *.png images/
mv *.pdf *.docx documents/
```

### 2. Limpieza de logs
```bash
rm /var/log/*.log.old   # Elimina logs antiguos
```

### 3. Búsqueda recursiva 
```bash
find ~/projects -name "*test*.py"   # Busca scripts Python con "test"
```

---

## ⚠️ Precauciones
1. **Verifica antes de eliminar**: Usa `ls` con el patrón antes de `rm` para evitar borrar archivos incorrectos.
2. **Evita espacios en nombres**: Usa comillas para nombres con espacios: `mv "file name.txt" ~/`.
3. **No uses `*` en rutas críticas**: Ejemplo peligroso: `rm -rf /tmp/*` (podría borrar todo si hay un error de sintaxis) .

---

## 🔗 Recursos Adicionales
- [Guía detallada de wildcards en Warp Terminal](https://www.warp.dev/terminus/linux-wildcards) .
- [Tutorial avanzado con `find` y comodines en LabEx](https://labex.io/es/tutorials/linux-how-to-use-wildcards-with-the-find-command-in-linux-415191) .