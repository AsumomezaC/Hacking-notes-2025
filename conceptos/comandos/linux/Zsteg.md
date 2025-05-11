#Comando #Linux #Programación #Software #Forenscic #CTF #esteganografía #Ruby
# Zsteg
**Zsteg** es una herramienta de línea de comandos escrita en Ruby que detecta y extrae **datos ocultos** en archivos de imágenes (PNG, BMP) mediante técnicas de esteganografía. Es comúnmente usada en CTFs (*Capture The Flag*) y análisis forense digital.

## 📌 Conceptos Clave
- **Esteganografía**: Ocultar información dentro de otro archivo (ej: mensajes en imágenes).
- **LSB (Least Significant Bit)**: Técnica común para esconder datos en los bits menos significativos de los píxeles.
- **Metadata**: Información oculta en el archivo (EXIF, comentarios, chunks PNG).

---

## 🔧 Instalación
```bash
gem install zsteg  # Requiere Ruby
```

---

## 🔍 Uso Básico
### 1. **Escaneo Automático**
Busca automáticamente datos ocultos:
```bash
zsteg imagen.png
```
**Salida típica**:  
- Detecta cadenas de texto, archivos ZIP embebidos, o patrones sospechosos.

### 2. **Extraer Datos Específicos**
- **Texto en LSB** (bits menos significativos):
  ```bash
  zsteg -e "b1,rgb,lsb" imagen.png
  ```
- **Extraer un archivo ZIP oculto**:
  ```bash
  zsteg -E "b1,rgb,lsb" imagen.png > oculto.zip
  ```

### 3. **Fuerza Bruta con Métodos Conocidos**
Prueba múltiples combinaciones de canales (RGB) y bits:
```bash
zsteg -a imagen.png
```

### 4. **Analizar Metadatos**
Aunque no es su enfoque principal, puede revelar chunks PNG sospechosos:
```bash
zsteg -v imagen.png  # Modo verbose
```

---

## 🚀 Casos de Uso en CTFs/Hacking
### 1. **Encontrar Flags en CTFs**
```bash
zsteg -a desafio.png | grep "flag{"
```

### 2. **Recuperar Archivos Ocultos**
Si detecta un archivo embebido (ej: PDF, ZIP):
```bash
zsteg -E "b1,rgba,lsb" imagen.png > secreto.pdf
```

### 3. **Descifrar Mensajes en LSB**
```bash
zsteg -e "b1,r,lsb" -x imagen.png  # Extrae datos del canal rojo (r)
```

---

## 📚 Opciones Avanzadas
| Opción          | Descripción                                  |
|-----------------|--------------------------------------------|
| `-a`            | Escaneo agresivo (prueba todas las combinaciones). |
| `-e <modo>`     | Extrae datos con un modo específico (ej: `b1,rgb,lsb`). |
| `-E <modo>`     | Extrae y guarda en un archivo binario.      |
| `-v`            | Modo verbose (muestra detalles técnicos).   |

---

## 🛠️ Ejemplo Práctico
**Problema**: Una imagen (`secreta.png`) parece contener un mensaje oculto.  
**Solución**:
```bash
zsteg secreta.png -a  # Escaneo completo
# Encuentra un mensaje en LSB del canal verde:
zsteg -e "b1,g,lsb" secreta.png
```

---

## 📚 Recursos Relacionados
- [[Esteganografía]]  
- [[Steghide]] (alternativa para JPEG)  
- [[Binwalk]] (análisis de archivos binarios)  