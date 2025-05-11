#Comando #Forenscic #Datos #Seguridad #Hacking #Software #Computación 

# **Steganografía con `stepic` - Guía Completa**  
## **1. ¿Qué es `stepic`?**  
`stepic` es una **biblioteca de Python** para realizar **esteganografía**, la técnica de ocultar información (como texto o imágenes) dentro de otras imágenes sin alterar su apariencia visible.  

### **1.1. Características Principales**  
✔ **Ocultar texto en imágenes PNG/JPG**.  
✔ **Bajo impacto visual** (cambios imperceptibles al ojo humano).  
✔ **Uso simple** con funciones básicas de codificación/decodificación.  

---

## **2. Instalación**  
```bash
pip install stepic
```
*Requisito:* Necesita las bibliotecas `Pillow` (fork moderno de PIL) para manejo de imágenes.  
```bash
pip install Pillow
```

---

## **3. Uso Básico**  

### **3.1. Codificar Texto en una Imagen**  
```python
from PIL import Image
import stepic

# 1. Abrir imagen portadora
imagen = Image.open("original.png")

# 2. Texto a ocultar (en bytes)
texto_secreto = b"Este es un mensaje secreto!"

# 3. Codificar y guardar
imagen_codificada = stepic.encode(imagen, texto_secreto)
imagen_codificada.save("secreta.png")
```

### **3.2. Decodificar Texto desde una Imagen**  
```python
from PIL import Image
import stepic

# 1. Abrir imagen con datos ocultos
imagen = Image.open("secreta.png")

# 2. Decodificar mensaje
texto_decodificado = stepic.decode(imagen)
print(texto_decodificado)  # b'Este es un mensaje secreto!'
```

---

## **4. Detalles Técnicos**  

### **4.1. ¿Cómo Funciona?**  
- **Modifica los bits menos significativos (LSB)** de los píxeles de la imagen.  
- **Ejemplo**: Cambiar el último bit de un valor RGB `(255, 255, 255)` a `(254, 255, 254)` no es perceptible visualmente.  

### **4.2. Limitaciones**  
- **Capacidad**: Depende del tamaño de la imagen (típicamente ~1/3 del tamaño en bytes).  
- **Formato**: Funciona mejor con **PNG** (sin pérdida de calidad). En JPG puede haber distorsión debido a compresión.  

---

## **5. Ejemplo Avanzado: Ocultar una Imagen en Otra**  

### **5.1. Codificación**  
```python
from PIL import Image
import stepic

# Convertir imagen secreta a bytes
with open("imagen_secreta.png", "rb") as f:
    datos_imagen = f.read()

# Ocultar en imagen portadora
portadora = Image.open("portadora.png")
codificada = stepic.encode(portadora, datos_imagen)
codificada.save("portadora_con_secreto.png")
```

### **5.2. Decodificación**  
```python
from PIL import Image
import stepic

# Extraer datos ocultos
portadora = Image.open("portadora_con_secreto.png")
datos_ocultos = stepic.decode(portadora)

# Guardar como imagen
with open("imagen_recuperada.png", "wb") as f:
    f.write(datos_ocultos)
```

---

## **6. Aplicaciones Prácticas**  
- **Seguridad**: Envío de mensajes confidenciales camuflados.  
- **Marcado de agua digital**: Ocultar firma del autor en imágenes.  
- **Retos CTF (Capture The Flag)**: Desafíos de hacking ético.  

---

## **7. Alternativas a `stepic`**  
| **Herramienta**       | **Ventaja**                          |  
|----------------------|-------------------------------------|  
| **OpenStego**        | GUI amigable, soporte múltiple.     |  
| **Steghide**         | Soporte para cifrado AES.           |  
| **LSB-Steganography**| Enfoque en LSB con Python puro.     |  

---

## **8. Recursos para Aprender Más**  
📚 **Libros**:  
- "Information Hiding: Steganography and Watermarking" por Katzenbeisser.  
- "The Art of Deception" por Kevin Mitnick (incluye técnicas de esteganografía).  

🌐 **Herramientas Online**:  
- [Steganography Online](https://stylesuxx.github.io/steganography/) (codificación web).  
- [AperiSolve](https://www.aperisolve.com/) (análisis forense de imágenes).  

---
## **Enlaces Relacionados en Obsidian**  
- [[Esteganografía]]  
- [[Seguridad]]  
- [[Python]]  