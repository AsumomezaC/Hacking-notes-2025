# Comando `cat` en [[Linux]]

## ¿Qué es `cat`?

El comando `cat` (abreviatura de _concatenate_) es una utilidad en sistemas Unix/Linux que permite visualizar, combinar y manipular archivos de texto. Es uno de los comandos más utilizados para la gestión de archivos en la terminal.

## Sintaxis

```sh
cat [opciones] [archivo1] [archivo2] ...
```

Si no se proporciona un archivo, `cat` lee desde la entrada estándar (`stdin`).

## Uso Básico

### 1. Mostrar el contenido de un archivo

```sh
cat archivo.txt
```

Muestra el contenido del archivo en la terminal.

### 2. Concatenar varios archivos

```sh
cat archivo1.txt archivo2.txt > combinado.txt
```

Une el contenido de `archivo1.txt` y `archivo2.txt` y lo guarda en `combinado.txt`.

### 3. Crear un archivo nuevo

```sh
cat > nuevo_archivo.txt
```

Permite escribir texto en un nuevo archivo. Finaliza con `Ctrl + D`.

### 4. Agregar contenido a un archivo existente

```sh
cat >> archivo.txt
```

Añade contenido al final del archivo sin sobrescribirlo.

## Opciones Comunes

|Opción|Descripción|
|---|---|
|`-n`|Muestra los números de línea.|
|`-b`|Numera solo las líneas no vacías.|
|`-s`|Suprime líneas vacías repetidas.|
|`-T`|Muestra los tabuladores como `^I`.|
|`-E`|Muestra los saltos de línea con `$`.|

Ejemplo con numeración de líneas:

```sh
cat -n archivo.txt
```

## Redirección de Salida

El comando `cat` se puede combinar con operadores de redirección para guardar o modificar archivos.

### Escribir en un archivo (sobrescribe el contenido)

```sh
cat archivo1.txt > archivo2.txt
```

### Añadir contenido sin sobrescribir

```sh
cat archivo1.txt >> archivo2.txt
```

## Uso con `|` (Pipelines)

### Mostrar con paginación (`less` o `more`)

```sh
cat archivo.txt | less
```

### Contar líneas, palabras y caracteres (`wc`)

```sh
cat archivo.txt | wc -l
```

Cuenta las líneas del archivo.

### Buscar texto dentro de un archivo (`grep`)

```sh
cat archivo.txt | grep "palabra"
```

Busca la palabra en el archivo.

## Consideraciones

- Para archivos grandes, es mejor usar `less` en lugar de `cat` (`less archivo.txt`).
- Si el archivo contiene datos binarios, `cat` puede mostrar caracteres ilegibles.
- `cat` es útil pero puede ser ineficiente para archivos muy grandes.