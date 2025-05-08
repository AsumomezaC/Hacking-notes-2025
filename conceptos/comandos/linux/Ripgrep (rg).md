#Comando #Programación #Búsqueda #Hacking #Selección #Mejora
# Ripgrep (rg): La Alternativa Moderna a Grep

**Ripgrep** (comando `rg`) es un buscador de líneas extremadamente rápido que combina la funcionalidad de herramientas clásicas como [[grep]], [[ack]] y [[Ag (The Silver Searcher)]], pero con mejoras significativas en rendimiento y usabilidad.
## 🔥 Características Principales

1. **Velocidad excepcional** - Más rápido que grep/ag/ack en la mayoría de casos
2. **Ignora archivos .gitignore automáticamente**
3. **Búsqueda recursiva por defecto**
4. **Soporte para Unicode**
5. **Salida colorizada y bien formateada**
6. **Multiplataforma** (Linux, macOS, Windows)

## 🛠️ Instalación

### Linux (Debian/Ubuntu):
```bash
sudo apt install ripgrep
```

### macOS (Homebrew):
```bash
brew install ripgrep
```

### Windows (Chocolatey):
```bash
choco install ripgrep
```

## 📖 Uso Básico

### Búsqueda simple:
```bash
rg "patrón"
```

### Búsqueda en directorio específico:
```bash
rg "función" src/
```

### Buscar palabra exacta:
```bash
rg -w "palabra"
```

### Ignorar mayúsculas/minúsculas:
```bash
rg -i "patrón"
```

## 🎯 Características Avanzadas

### 1. Tipos de archivos
Buscar solo en archivos Python:
```bash
rg -t py "import"
```

Excluir archivos JSON:
```bash
rg -T json "config"
```

### 2. Contexto
Mostrar 2 líneas antes y después:
```bash
rg -C 2 "error"
```

### 3. Búsqueda con expresiones regulares
```bash
rg "user\d+"  # Encuentra user1, user2, etc.
```

### 4. Buscar en archivos ocultos
```bash
rg -u "config"  # -u = --unrestricted
```

### 5. Estadísticas de búsqueda
```bash
rg --stats "patrón"
```

## ⚡ Comparación de Velocidad

| Comando | Tiempo (ejemplo) |
|---------|-----------------|
| `rg`    | 0.8s            |
| `ag`    | 2.1s            |
| `ack`   | 3.4s            |
| `grep`  | 4.2s            |

## 🧠 Trucos Útiles

1. **Buscar en todos los archivos excepto node_modules:**
```bash
rg "patrón" -g '!node_modules/'
```

2. **Mostrar solo nombres de archivos con coincidencias:**
```bash
rg -l "función"
```

3. **Contar coincidencias por archivo:**
```bash
rg -c "error"
```

4. **Buscar en archivos zip/gz:**
```bash
rg -z "texto" archive.zip
```

5. **Búsqueda interactiva con fzf:**
```bash
rg "patrón" | fzf
```

## 🛑 Limitaciones

1. No tiene todas las opciones avanzadas de regex de GNU grep
2. Menor disponibilidad en sistemas antiguos
3. Menor soporte para algunos formatos binarios

## 🌟 Casos de Uso Ideales

1. **Búsqueda en proyectos de código**
2. **Análisis rápido de logs**
3. **Integración con editores (VSCode, Vim, etc.)**
4. **Scripting de productividad**

## 🔄 Migración desde Grep

| Grep              | Ripgrep          |
|-------------------|------------------|
| `grep -r`         | `rg`             |
| `grep -i`         | `rg -i`          |
| `grep -v`         | `rg -v`          |
| `grep -l`         | `rg -l`          |
| `grep -n`         | `rg -n`          |
| `grep -w`         | `rg -w`          |
| `grep -C 3`       | `rg -C 3`        |

Ripgrep se ha convertido en la herramienta preferida para muchos desarrolladores gracias a su velocidad y conveniencia. Su integración con sistemas de control de versiones y su salida bien formateada lo hacen ideal para el flujo de trabajo moderno de desarrollo.