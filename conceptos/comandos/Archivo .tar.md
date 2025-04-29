#Archivos #Computación #Software 
# Archivos TAR en Linux

## ¿Qué es un archivo .tar?
- **Tape ARchive**: Formato de archivo contenedor que agrupa múltiples archivos en uno solo (sin compresión por defecto)
- **Propósito original**: Crear backups en cintas magnéticas (ahora usado comúnmente para empaquetar archivos)
- **Características**:
  - Conserva permisos, estructura de directorios y metadatos
  - No comprime por sí mismo (usualmente se combina con gzip/bzip2/xz)

## Comandos básicos de manejo

### 1. Crear archivo tar
```bash
tar -cvf nombre_archivo.tar directorio/  # Crear (-c) archivo (-f) con verbosidad (-v)
```

### 2. Listar contenido
```bash
tar -tvf archivo.tar       # Listar (-t) contenido detallado
tar -tf archivo.tar        # Listar solo nombres de archivos
```

### 3. Extraer archivos
```bash
tar -xvf archivo.tar                 # Extraer (-x) todo el contenido
tar -xvf archivo.tar archivo.txt     # Extraer solo un archivo específico
tar -xvf archivo.tar --wildcards '*.txt'  # Extraer por patrón
```

## Compresión combinada

| Método       | Comando creación           | Extensión | Notas                     |
|--------------|---------------------------|-----------|---------------------------|
| **Gzip**     | `tar -czvf archivo.tar.gz` | .tar.gz   | Compresión rápida         |
| **Bzip2**    | `tar -cjvf archivo.tar.bz2`| .tar.bz2  | Mejor compresión (más lento) |
| **XZ**       | `tar -cJvf archivo.tar.xz` | .tar.xz   | Alta compresión (más lento) |
| **Zstd**     | `tar -cavf archivo.tar.zst`| .tar.zst  | Balance velocidad/compresión |

## Opciones avanzadas

### 1. Excluir archivos
```bash
tar -cvf backup.tar --exclude='*.tmp' directorio/
```

### 2. Ver contenido sin extraer
```bash
tar -tvzf archivo.tar.gz | less
```

### 3. Extraer en directorio específico
```bash
tar -xzvf archivo.tar.gz -C /ruta/destino/
```

### 4. Actualizar archivo existente
```bash
tar -uvf archivo.tar nuevos_archivos/
```

### 5. Crear backup preservando atributos
```bash
tar -cpvf backup.tar --acls --selinux --xattrs /directorio
```

## Comparación de formatos

| Formato    | Velocidad | Compresión | Uso típico               |
|------------|-----------|------------|--------------------------|
| .tar       | ★★★★★     | ☆☆☆☆☆      | Empaquetado sin compresión |
| .tar.gz    | ★★★★☆     | ★★★☆☆      | Uso general              |
| .tar.bz2   | ★★☆☆☆     | ★★★★☆      | Archivos grandes         |
| .tar.xz    | ★☆☆☆☆     | ★★★★★      | Máxima compresión        |
| .tar.zst   | ★★★★☆     | ★★★★☆      | Balance moderno          |

## Consejos útiles

1. **Verificar integridad**:
   ```bash
   tar -tf archivo.tar && echo "OK" || echo "Corrupto"
   ```

2. **Tamaño antes de extraer**:
   ```bash
   tar -tzf archivo.tar.gz | awk '{sum+=$3} END {print sum/1048576 " MB"}'
   ```

3. **Crear incremental** (con `--listed-incremental`):
   ```bash
   tar --create --file=backup.tar --listed-incremental=snapshot.file directorio/
   ```

4. **Dividir en partes**:
   ```bash
   tar -cvzf - directorio/ | split -b 2G - backup.tar.gz.part
   ```

## Recuperación de archivos dañados
```bash
dd if=corrupto.tar bs=1M skip=100 | tar -xzvf -  # Saltar bloques dañados
```