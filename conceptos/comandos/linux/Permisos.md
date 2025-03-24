#Software #Comando #SistemaOperativo #Linux #Permisos #Derechos
# Permisos de Archivos en Linux

## 1. ¿Qué son los permisos en Linux?

Los permisos en Linux definen quién puede leer, escribir o ejecutar un archivo o directorio. Se asignan a tres tipos de usuarios:

- **Propietario (Owner)**: El usuario que posee el archivo.
- **Grupo (Group)**: Los usuarios que pertenecen al mismo grupo que el propietario.
- **Otros (Others)**: Todos los demás usuarios.

## 2. Tipos de Permisos

### a) Permiso de lectura (r)

- **Descripción**: Permite ver el contenido de un archivo.
- **Número**: 4

### b) Permiso de escritura (w)

- **Descripción**: Permite modificar el contenido de un archivo.
- **Número**: 2

### c) Permiso de ejecución (x)

- **Descripción**: Permite ejecutar un archivo como un programa o script.
- **Número**: 1

## 3. Comandos Principales

### a) **ls -l**

Muestra los permisos de los archivos en el directorio actual.

```bash
ls -l
```

Ejemplo de salida:

```bash
-rwxr-xr-- 1 usuario grupo 1234 feb 17 12:34 archivo.txt
```

### b) **chmod** (Cambiar permisos)

Usado para modificar los permisos de un archivo o directorio.

```bash
chmod [permisos] [archivo]
```

- **Modo simbólico**:
    
    ```bash
    chmod u+x archivo.txt   # Agregar permiso de ejecución al propietario
    chmod g-w archivo.txt   # Quitar permiso de escritura al grupo
    chmod o+r archivo.txt   # Agregar permiso de lectura a otros
    ```
    
- **Modo octal**:
    
    ```bash
    chmod 755 archivo.txt   # Propietario: lectura, escritura, ejecución; Grupo/Otros: lectura, ejecución
    chmod 644 archivo.txt   # Propietario: lectura, escritura; Grupo/Otros: lectura
    ```
    

### c) **chown** (Cambiar propietario y grupo)

Permite cambiar el propietario y grupo de un archivo o directorio.

```bash
chown usuario:grupo archivo.txt
```

## 4. Representación de Permisos

### a) **Permisos en formato simbólico**

Ejemplo:

```bash
rwxr-xr--
```

- **r**: Lectura
- **w**: Escritura
- **x**: Ejecución
- **-**: Sin permiso

### b) **Permisos en formato octal**

Cada tipo de permiso tiene un valor numérico:

- Lectura (r) = 4
- Escritura (w) = 2
- Ejecución (x) = 1

Entonces, un archivo con permisos `rwxr-xr--` (dueño: rwx, grupo: r-x, otros: r--) sería representado como `755`.

## 5. Permisos de Directorios

- **r**: Permite listar los archivos en el directorio.
- **w**: Permite crear, eliminar y renombrar archivos dentro del directorio.
- **x**: Permite acceder al contenido de los archivos en el directorio.

## 6. Combinación de Permisos

- **777**: Todos los permisos (lectura, escritura, ejecución) para todos.
- **755**: El propietario tiene todos los permisos, el grupo y otros tienen solo lectura y ejecución.
- **644**: El propietario tiene lectura y escritura, el grupo y otros solo lectura.