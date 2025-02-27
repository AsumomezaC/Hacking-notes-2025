# Comando `ls` en Linux

## 1. ¿Qué es `ls`?

El comando `ls` en Linux se usa para listar archivos y directorios en el terminal. Es uno de los comandos más usados para explorar el sistema de archivos.

## 2. Sintaxis básica

```bash
ls [opciones] [ruta]
```

Si se ejecuta sin opciones ni ruta, muestra el contenido del directorio actual:

```bash
ls
```

## 3. Opciones principales

### a) Mostrar detalles de los archivos (`-l`)

```bash
ls -l
```

Ejemplo de salida:

```
-rw-r--r--  1 usuario grupo  1234 feb 20 10:15 archivo.txt
```

Donde:

- `-rw-r--r--` → Permisos del archivo
- `1` → Número de enlaces
- `usuario` → Propietario
- `grupo` → Grupo
- `1234` → Tamaño en bytes
- `feb 20 10:15` → Fecha de modificación
- `archivo.txt` → Nombre del archivo

### b) Mostrar archivos ocultos (`-a`)

```bash
ls -a
```

Muestra archivos y directorios ocultos (los que empiezan con `.`), como `.bashrc`.

### c) Mostrar archivos ocultos excepto `.` y `..` (`-A`)

```bash
ls -A
```

Similar a `-a` pero no muestra `.` (directorio actual) ni `..` (directorio padre).

### d) Listar con formato legible para humanos (`-lh`)

```bash
ls -lh
```

Muestra los tamaños en KB, MB o GB en lugar de bytes.

### e) Ordenar por tamaño (`-S`)

```bash
ls -lS
```

Lista los archivos ordenados por tamaño, de mayor a menor.

### f) Ordenar por fecha de modificación (`-t`)

```bash
ls -lt
```

Lista los archivos ordenados por la fecha de modificación más reciente.

### g) Ordenar de forma inversa (`-r`)

```bash
ls -lr
```

Invierte el orden de la lista.

### h) Mostrar solo directorios (`-d */`)

```bash
ls -d */
```

Muestra solo los directorios en el directorio actual.

### i) Mostrar el número de inodo (`-i`)

```bash
ls -i
```

Muestra el número de inodo de cada archivo.

### j) Usar colores en la salida (`--color`)

```bash
ls --color=auto
```

Muestra los archivos con colores para diferenciar tipos (archivos normales, directorios, ejecutables, etc.).

### k) Mostrar UID y GID (`-n`)

```bash
ls -ln
```

Muestra el ID numérico del usuario y del grupo en lugar de sus nombres.

## 4. Combinaciones útiles

- **Listar todos los archivos con detalles:**
    
    ```bash
    ls -lah
    ```
    
- **Ordenar por tamaño y mostrar en formato legible:**
    
    ```bash
    ls -lhS
    ```
    
- **Listar archivos en orden cronológico inverso:**
    
    ```bash
    ls -ltr
    ```
    

## 5. Alias recomendados

Para hacer más fácil el uso de `ls`, puedes definir alias en tu archivo `~/.bashrc` o `~/.zshrc`:

```bash
alias ll='ls -lh'
alias la='ls -lha'
alias l='ls -CF'
```

Luego, recarga la configuración con:

```bash
source ~/.bashrc
```

---

# Comando `ls -lath` en Linux

## 1. ¿Qué es `ls -lath`?

El comando `ls -lath` muestra el listado detallado de archivos en un directorio con varias opciones combinadas para visualizar información de manera más útil.

## 2. Desglose de opciones

- **`-l`** → Muestra los detalles en formato de lista (permisos, propietario, tamaño, fecha, etc.).
- **`-a`** → Muestra todos los archivos, incluyendo los ocultos (los que empiezan con `.`).
- **`-t`** → Ordena por fecha de modificación, mostrando primero los archivos más recientes.
- **`-h`** → Muestra los tamaños de los archivos en un formato legible (KB, MB, GB en lugar de bytes).

## 3. Ejemplo de uso

```bash
ls -lath
```

### Salida de ejemplo

```plaintext
total 2.3M
drwxr-xr-x  4 usuario usuario 4.0K Feb 20 10:30 .
drwxr-xr-x 20 usuario usuario 4.0K Feb 19 14:00 ..
-rw-r--r--  1 usuario usuario 1.2M Feb 20 10:29 archivo_grande.log
-rw-r--r--  1 usuario usuario 512K Feb 20 10:28 otro_archivo.txt
drwxr-xr-x  2 usuario usuario 4.0K Feb 20 10:27 .config
-rw-r--r--  1 usuario usuario  64K Feb 20 10:25 .archivo_oculto
```

## 4. ¿Para qué sirve `ls -lath`?

Este comando es útil para:  
✅ Ver detalles de archivos con permisos, propietario y tamaño.  
✅ Incluir archivos ocultos en el listado.  
✅ Ordenar los archivos según la última modificación.  
✅ Mostrar tamaños en un formato fácil de entender.

## 5. Alternativas útiles

- **`ls -latr`** → Igual, pero ordena del más antiguo al más reciente.
- **`ls -lah`** → Muestra todos los archivos sin ordenar por fecha.
- **`ls -lt`** → Solo ordena por fecha sin incluir ocultos.