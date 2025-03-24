#Software #Comando #SistemaOperativo #Linux #Eliminar #Archivos 
# Borrar todos los archivos
```bash
rm -rf *
```
# **Comando `rm` - Eliminar archivos o directorios**

El comando `rm` (del inglés _remove_) se utiliza en sistemas Linux y Unix para eliminar archivos y directorios. Es una herramienta muy poderosa, y su uso incorrecto puede llevar a la pérdida permanente de datos, ya que no mueve los archivos a la papelera, sino que los elimina directamente.

#### **Sintaxis Básica**:

```bash
rm [opciones] archivo(s)
```

#### **Opciones Comunes**:

- `-r` o `--recursive`: Elimina directorios y su contenido de manera recursiva.
- `-f` o `--force`: Elimina archivos sin pedir confirmación, incluso si son archivos de solo lectura.
- `-i`: Solicita confirmación antes de eliminar cada archivo.
- `-v` o `--verbose`: Muestra información detallada sobre qué archivos se están eliminando.

#### **Ejemplos de uso**:

1. **Eliminar un archivo**:
    
    ```bash
    rm archivo.txt
    ```
    
2. **Eliminar varios archivos**:
    
    ```bash
    rm archivo1.txt archivo2.txt archivo3.txt
    ```
    
3. **Eliminar un directorio vacío**:
    
    ```bash
    rmdir directorio/
    ```
    
4. **Eliminar un directorio y su contenido** (recurre a todos los archivos y subdirectorios):
    
    ```bash
    rm -r directorio/
    ```
    
5. **Eliminar sin pedir confirmación** (forzando el comando):
    
    ```bash
    rm -f archivo.txt
    ```
    
6. **Eliminar todos los archivos dentro de un directorio (sin eliminar el directorio en sí)**:
    
    ```bash
    rm -r directorio/*
    ```
    
7. **Eliminar archivos con confirmación antes de cada uno**:
    
    ```bash
    rm -i archivo1.txt archivo2.txt
    ```
    
8. **Eliminar archivos mostrando el detalle de lo que se está eliminando**:
    
    ```bash
    rm -v archivo.txt
    ```

#### **Advertencia**:

El comando `rm` elimina archivos permanentemente, sin posibilidad de recuperación (a menos que se cuente con herramientas especializadas para la recuperación de datos). Usa con precaución.