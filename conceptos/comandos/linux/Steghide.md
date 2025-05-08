#CTF #hacking #esteganografía #Steghide #seguridad  #Software #Programación 
# Steghide  
**Steghide** es una herramienta de esteganografía que permite **ocultar y extraer datos** en archivos de imagen (JPEG, BMP) y audio (WAV, AU). Es ampliamente usada en CTFs (*Capture The Flags*) y pruebas de seguridad para esconder información sensible dentro de archivos multimedia.  

---

## 📌 Conceptos Clave  
- **Esteganografía**: Técnica de ocultar información dentro de otro archivo (sin llamar la atención).  
- **Soporte**: Funciona mejor con **JPEG**, **BMP**, **WAV** y **AU**.  
- **Cifrado**: Usa AES-128 por defecto para proteger datos ocultos.  

---

## 🔧 Instalación  
### En Linux (Debian/Ubuntu):  
```bash
sudo apt install steghide
```  
### En macOS (Homebrew):  
```bash
brew install steghide
```  

---

## 🔍 Uso Básico  

### 1. **Ocultar datos en una imagen**  
```bash
steghide embed -cf imagen.jpg -ef archivo_secreto.txt
```  
- `-cf` (cover file): Archivo de portada (imagen/audio).  
- `-ef` (embedded file): Archivo a ocultar.  
- **Ejemplo con contraseña**:  
  ```bash
  steghide embed -cf foto.jpg -ef mensaje.txt -p "MiClaveSecreta"
  ```  

### 2. **Extraer datos ocultos**  
```bash
steghide extract -sf imagen.jpg -xf salida.txt
```  
- `-sf` (stego file): Imagen con datos ocultos.  
- `-xf` (extract file): Nombre del archivo extraído.  
- **Si tiene contraseña**: Se pedirá interactivamente.  

### 3. **Ver información de un archivo esteganográfico**  
```bash
steghide info imagen_sospechosa.jpg
```  
Muestra:  
- Método de cifrado usado.  
- Capacidad disponible para ocultar datos.  

---

## 🚀 Casos de Uso en Hacking/CTFs  

### 1. **Extraer un flag oculto en un CTF**  
```bash
steghide extract -sf challenge.jpg  
# Si pide contraseña, probar con:  
steghide extract -sf challenge.jpg -p "flag{123}"  
```  

### 2. **Fuerza bruta con contraseñas**  
Steghide no incluye fuerza bruta, pero puedes usar **stegcracker**:  
```bash
stegcracker imagen.jpg /ruta/wordlist.txt
```  

### 3. **Ocultar un archivo ZIP dentro de un JPEG**  
```bash
steghide embed -cf portada.jpg -ef malware.zip -p "hack123"
```  

---

## 📚 Opciones Avanzadas  
| Comando           | Descripción |  
|------------------|------------|  
| `steghide --help` | Muestra ayuda general |  
| `-e <algoritmo>` | Usa cifrado específico (ej: `aes128`, `rijndael-128`)|  
| `-z <nivel>`     | Compresión (1-9, 9=máxima) |  
| `-f`             | Sobrescribe archivos sin preguntar |  

---

## ⚠️ Limitaciones  
- **No funciona con PNG** (para PNG, usa **Zsteg** o **binwalk**).  
- **Sin soporte para metadatos EXIF**.  

---

## 📌 Comparación con Otras Herramientas  
| Herramienta   | Formatos       | Cifrado | Fuerza Bruta |  
|--------------|---------------|---------|-------------|  
| **Steghide** | JPEG, BMP, WAV | AES-128 | No (requiere herramientas externas) |  
| **Zsteg**    | PNG, BMP       | No      | Sí (análisis LSB) |  
| **Binwalk**  | Múltiples      | No      | Sí (extracción automática) |  

---

## 📚 Recursos Relacionados  
- [[Zsteg]]  
- [[Binwalk]]  
- [[Esteganografía]] 