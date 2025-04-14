#Comando #Hacking #Software #Computación #Linux 

# Comando `ln` en Linux
## Descripción
El comando `ln` se utiliza para crear **enlaces** (links) entre archivos en sistemas Unix/Linux. Existen dos tipos de enlaces:
1. **Enlaces simbólicos** (symbolic links): similares a accesos directos.
2. **Enlaces duros** (hard links): apuntan directamente al inodo del archivo original.

## Sintaxis básica
```bash
ln [OPCIONES] ORIGEN DESTINO
```

## Opciones comunes
- `-s`: Crea un **enlace simbólico** (recomendado para la mayoría de casos).
- `-v`: Modo verbose (muestra detalles de la operación).
- `-f`: Fuerza la creación, sobrescribiendo si el destino existe.
- `-i`: Pregunta antes de sobrescribir.

## Ejemplos

### 1. Enlace simbólico (recomendado)
```bash
ln -s /ruta/al/archivo/origen /ruta/al/enlace
```
- Útil para acceder a archivos en otras ubicaciones sin duplicar datos.
- Si se elimina el original, el enlace queda "roto" (dangling link).

### 2. Enlace duro
```bash
ln archivo_origen enlace_duro
```
- Ambos archivos comparten el mismo inodo.
- Si se elimina el original, los datos persisten a través del enlace duro.
- Solo funciona dentro del mismo sistema de archivos.

### 3. Enlace a directorio
```bash
ln -s /directorio/origen /directorio/destino
```
- Los enlaces simbólicos pueden apuntar a directorios completos.

## Diferencias clave
| Característica          | Enlace simbólico         | Enlace duro             |
|-------------------------|-------------------------|-------------------------|
| Inodo                   | Diferente               | Mismo que el original   |
| Sistemas de archivos    | Puede cruzar dispositivos | Solo mismo sistema     |
| Directorios             | Compatible              | No compatible           |
| Archivo original eliminado | Enlace roto         | Datos preservados       |

## Buenas prácticas
1. Usa rutas **absolutas** para enlaces simbólicos si van a ser accedidos desde diferentes ubicaciones.
2. Evita enlaces circulares (A → B → A).
3. Verifica enlaces con `ls -l` (muestra `->` para simbólicos).

## Comandos relacionados
- [[ls]] -i: Muestra números de inodo.
- `readlink`: Muestra la ruta de un enlace simbólico.
- `unlink`: Elimina enlaces.