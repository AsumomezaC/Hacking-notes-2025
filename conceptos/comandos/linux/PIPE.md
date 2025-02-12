# Uso de `|` (_Pipe_) en Linux

## ¿Qué es un _pipe_ (`|`)?

Un _pipe_ (`|`) en Linux es un operador que permite redirigir la salida de un comando como entrada de otro. Esto permite encadenar comandos para procesar datos de manera más eficiente.

## Sintaxis

```sh
comando1 | comando2
```

Donde `comando1` genera una salida que se pasa directamente a `comando2`.

## Ejemplos Comunes

### 1. Contar el número de líneas de un archivo

```sh
cat archivo.txt | wc -l
```

`cat` muestra el contenido del archivo, y `wc -l` cuenta las líneas.

### 2. Filtrar contenido de un archivo

```sh
cat archivo.txt | grep "error"
```

Muestra solo las líneas que contienen la palabra "error".

### 3. Ordenar una lista y eliminar duplicados

```sh
cat lista.txt | sort | uniq
```

Ordena `lista.txt` y elimina elementos repetidos.

### 4. Mostrar procesos en ejecución y filtrar por nombre

```sh
ps aux | grep firefox
```

Muestra solo los procesos que contienen "firefox".

### 5. Ver archivos abiertos por un proceso

```sh
lsof | grep nombre_proceso
```

Muestra los archivos abiertos por un proceso específico.

## Uso con Múltiples _Pipes_

Se pueden encadenar múltiples comandos:

```sh
cat archivo.txt | grep "error" | sort | uniq | wc -l
```

Este comando:

1. Filtra las líneas con "error".
2. Ordena la salida.
3. Elimina duplicados.
4. Cuenta el número de líneas resultantes.

## Diferencia entre `|` y Redirección `>`

|Operador|Descripción|
|---|---|
|`>`|Redirige la salida a un archivo (sobrescribe el contenido).|
|`>>`|Redirige la salida a un archivo (sin sobrescribir, añade al final).|
|`|`|

Ejemplo de redirección a un archivo en lugar de usar `|`:

```sh
ls > archivos.txt
cat archivos.txt | wc -l  # Contar líneas desde el archivo
```

## Consideraciones

- `|` solo funciona con comandos que generan salida estándar.
- Para comandos sin salida estándar, se puede usar `2>&1` para redirigir errores.
- Si necesitas ejecutar comandos con privilegios, usa `sudo`:

```sh
   ps aux | grep apache | sudo tee procesos.txt
```
