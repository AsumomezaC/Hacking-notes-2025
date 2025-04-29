#Comando #Linux #Transformar #Software 

# Comando `sed` en Linux

## ¿Qué es `sed`?
- **Stream Editor**: Filtro para transformar texto línea por línea.
- **No interactivo**: Edita archivos o streams mediante comandos sin abrirlos.
- **Potente**: Usa expresiones regulares para búsqueda/reemplazo avanzado.

## Sintaxis Básica
```bash
sed [opciones] 'comando(s)' archivo.txt
```

## Operaciones Comunes

### 1. Reemplazar texto
```bash
sed 's/patrón/reemplazo/' archivo.txt  # Reemplaza la primera ocurrencia por línea
sed 's/foo/bar/g' archivo.txt         # Reemplazo global (todas las ocurrencias)
sed 's/\\/\/g' archivo.txt            # Escapar caracteres (ej. barra invertida)
```

### 2. Eliminar líneas
```bash
sed '5d' archivo.txt           # Borra la línea 5
sed '/^#/d' archivo.txt        # Borra líneas que empiezan con #
sed '/pattern/d' archivo.txt   # Borra líneas que coinciden con el patrón
```

### 3. Imprimir líneas específicas
```bash
sed -n '10p' archivo.txt       # Muestra solo la línea 10
sed -n '5,10p' archivo.txt     # Muestra líneas 5 a 10
```

### 4. Edición en archivo (sobrescribir)
```bash
sed -i 's/foo/bar/g' archivo.txt      # Modifica el archivo directamente
sed -i.bak 's/foo/bar/g' archivo.txt  # Crea backup (.bak) antes de modificar
```

## Opciones Útiles
| Opción | Descripción |
|--------|-------------|
| `-e`   | Permite múltiples comandos: `sed -e 's/foo/bar/' -e 's/baz/qux/'` |
| `-n`   | Suprime salida automática (útil con `p` para imprimir selectivamente) |
| `-r`   | Usa expresiones regulares extendidas (soporta `+`, `?`, `{}` sin escaparlos) |

## Ejemplos Avanzados

### 1. Reemplazo condicional
```bash
sed '/error/s/foo/bar/' archivo.txt  # Reemplaza "foo" por "bar" solo en líneas con "error"
```

### 2. Insertar/agregar texto
```bash
sed '3i\texto' archivo.txt    # Inserta "texto" antes de la línea 3
sed '$a\texto' archivo.txt    # Agrega "texto" al final del archivo
```

### 3. Usar múltiples patrones
```bash
sed -e 's/foo/bar/' -e 's/baz/qux/' archivo.txt
```

## Expresiones Regulares en `sed`
- `^`: Inicio de línea.
- `$`: Fin de línea.
- `.`: Cualquier carácter.
- `*`: 0 o más repeticiones del anterior.
- `\1`, `\2`: Grupos de captura (ej. `sed 's/\(.*\)/\1/'`).

## Consejos
- **Prueba sin `-i` primero** para evitar modificaciones accidentales.
- **Combínalo con otros comandos**:  
  ```bash
  grep "error" log.txt | sed 's/error/CRITICAL/'
  ```

## Recursos
- [Manual oficial GNU sed](https://www.gnu.org/software/sed/manual/sed.html)
- `man sed` o `info sed` en tu terminal.