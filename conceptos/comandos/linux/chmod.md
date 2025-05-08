#Comando #Permisos #Software #Linux #Hacking 
# **Comando `chmod`: Guía Completa para Gestionar Permisos en Linux**

## 🔐 **¿Qué es `chmod`?**
`chmod` (*Change Mode*) es el comando fundamental en Linux/Unix para **cambiar [[Permisos]]** de archivos y directorios. Controla tres tipos de acceso:
- **Lectura** (r)
- **Escritura** (w)
- **Ejecución** (x)

Para tres categorías de usuarios:
- **Usuario propietario** (u)
- **Grupo asignado** (g)
- **Otros usuarios** (o)

## 📌 **Sintaxis Básica**
```bash
chmod [opciones] permisos archivo(s)
```

## 🎯 **Modos de Especificar Permisos**

### 1. **Modo Simbólico** (Letras)
```bash
chmod [ugoa][+-=][rwx] archivo
```
- **Operadores**:
  - `+` Añade permiso
  - `-` Quita permiso
  - `=` Establece exactamente

**Ejemplos**:
```bash
chmod u+x script.sh      # Añade ejecución al dueño
chmod g-w documento.txt  # Quita escritura al grupo
chmod o=r archivo.conf   # Otros solo lectura
```

### 2. **Modo Numérico** (Octal)
```bash
chmod NNN archivo
```
- **Valores**:
  - 4 = Lectura (r)
  - 2 = Escritura (w)
  - 1 = Ejecución (x)

**Combinaciones comunes**:
| Valor | Permiso |
|-------|---------|
| 7     | rwx     |
| 6     | rw-     |
| 5     | r-x     |
| 4     | r--     |
| 0     | ---     |

**Ejemplo**:
```bash
chmod 750 script.sh  # Dueño:rwx, Grupo:r-x, Otros:---
```

## 🛠 **Opciones Útiles**
| Opción | Descripción |
|--------|-------------|
| `-R`   | Recursivo (aplica a directorios y su contenido) |
| `-v`   | Modo verbose (muestra cambios) |
| `-c`   | Solo muestra cambios |
| `--reference=archivo` | Copia permisos de otro archivo |

## 📂 **Permisos Especiales**
| Permiso | Número | Letra | Efecto |
|---------|--------|-------|--------|
| **Sticky Bit** | 1000 | t | Solo dueño puede borrar (ej: /tmp) |
| **SGID** | 2000 | s | Ejecución con permisos del grupo |
| **SUID** | 4000 | s | Ejecución con permisos del dueño |

**Ejemplo**:
```bash
chmod 1777 /tmp      # Sticky bit
chmod 4755 /usr/bin/programa  # SUID
```

## 🔍 **Visualizar Permisos**
```bash
ls -l
```
Salida ejemplo:
```
-rwxr-xr-- 1 usuario grupo 4096 Jun 10 10:00 archivo
```
Donde:
- `-rwxr-xr--` = Tipo (d) y permisos
- `usuario` = Dueño
- `grupo` = Grupo asignado

## 💡 **Casos Prácticos**

### 1. **Hacer un script ejecutable**
```bash
chmod +x mi_script.sh
```

### 2. **Proteger archivo confidencial**
```bash
chmod 600 ~/.ssh/id_rsa  # Solo lectura/escritura para dueño
```

### 3. **Permisos para directorio web**
```bash
chmod 755 /var/www/html  # Dueño:rwx, Grupo/otros:r-x
```

### 4. **Cambio recursivo**
```bash
chmod -R 644 directorio/  # Todos los archivos (no ejecutables)
```

## ⚠️ **Precauciones Importantes**
1. **No usar `777`** (da todos los permisos a todos)
2. **Cuidado con `-R`** (podría hacer archivos ejecutables por error)
3. **SUID/SGID mal usados** son riesgos de seguridad
4. **Verificar cambios** con `ls -l` después de modificar

## 🔄 **Relación con Otros Comandos**
- **`chown`**: Cambia dueño/grupo
- **`umask`**: Define permisos por defecto
- **`install`**: Copia archivos estableciendo permisos

## 📊 **Tabla de Referencia Rápida**
| Permiso | Símbolo | Número |
|---------|---------|--------|
| Lectura | r | 4 |
| Escritura | w | 2 |
| Ejecución | x | 1 |
| Ninguno | - | 0 |

**Combinaciones útiles**:
- `755` = Ejecutables/directorios
- `644` = Archivos normales
- `700` = Privado absoluto

El dominio de `chmod` es esencial para la administración de sistemas y la seguridad. Unos permisos correctamente configurados previenen accesos no autorizados y garantizan el funcionamiento adecuado de aplicaciones y servicios.