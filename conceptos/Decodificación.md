#Seguridad #Programación #Software #Datos 
# **Decodificación - Guía Completa**  
*(Para tus apuntes de Obsidian)*  

---

## **1. Introducción a la Decodificación**  
La decodificación es el proceso de **interpretar información codificada** para recuperar su forma original. Se aplica en:  
- **Comunicaciones digitales** (Wi-Fi, Bluetooth).  
- **Sistemas de almacenamiento** (discos duros, SSDs).  
- **Criptografía** (descifrado de mensajes).  
- **Procesamiento de señales** (audio, imágenes).  

---

## **2. Tipos de Decodificación**  

### **2.1. Decodificación Digital**  
| **Tipo**               | **Descripción**                                  | **Ejemplo**                     |  
|------------------------|-----------------------------------------------|--------------------------------|  
| **Binario a Texto**     | Convierte bits en caracteres (ASCII, UTF-8).  | `01001000 → "H"`              |  
| **Base64**             | Decodifica datos binarios a texto.            | `SGVsbG8= → "Hello"`          |  
| **Protocolos**         | Interpreta tramas de red (HTTP, TCP/IP).      | Decodificar paquetes Ethernet. |  

#### **Ejemplo: Base64 en Python**  
```python
import base64
codificado = "SGVsbG8gd29ybGQh"
decodificado = base64.b64decode(codificado).decode('utf-8')
print(decodificado)  # "Hello world!"
```

### **2.2. Decodificación de Señales**  
- **Modulación digital**:  
  - **ASK** (Amplitude-Shift Keying).  
  - **FSK** (Frequency-Shift Keying).  
  - **PSK** (Phase-Shift Keying).  

#### **Proceso típico**:  
```
Señal analógica → Muestreo → Cuantización → Decodificación a bits.  
```

---

## **3. Técnicas de Decodificación**  

### **3.1. Algoritmos Clásicos**  
| **Algoritmo**          | **Uso**                                |  
|-----------------------|---------------------------------------|  
| **Hamming**           | Corrección de errores en transmisión. |  
| **Viterbi**           | Decodificación de señales convolucionales. |  
| **Reed-Solomon**      | Usado en CDs y QR codes.              |  

### **3.2. Herramientas Comunes**  
- **FFmpeg**: Decodificación de audio/video.  
  ```bash
  ffmpeg -i video.mp4 -c:v libx264 output.avi
  ```
- **Wireshark**: Decodificador de protocolos de red.  

---

## **4. Decodificación en Criptografía**  

### **4.1. Métodos**  
| **Tipo**               | **Clave**      | **Ejemplo**                     |  
|------------------------|--------------|--------------------------------|  
| **Simétrica** (AES)    | Misma clave   | `openssl aes-256-cbc -d -in file.enc` |  
| **Asimétrica** (RSA)   | Clave privada | `openssl rsautl -decrypt -inkey priv.pem` |  

#### **Ejemplo: AES en Python**  
```python
from Crypto.Cipher import AES
import base64

clave = b'mi_clave_secreta_32'
datos_cifrados = base64.b64decode("U2FsdGVkX1+...")
cipher = AES.new(clave, AES.MODE_EAX)
datos = cipher.decrypt(datos_cifrados)
```

### **4.2. Retos Comunes**  
- **Fuerza bruta**: Ataques por diccionario.  
- **Side-channel attacks**: Analizar consumo de energía o tiempo.  

---

## **5. Decodificación en Machine Learning**  

### **5.1. Autoencoders**  
Redes neuronales que aprenden a reconstruir datos:  
1. **Encoder**: Compresión a espacio latente.  
2. **Decoder**: Reconstrucción.  

#### **Ejemplo en Keras**  
```python
from keras.layers import Input, Dense
from keras.models import Model

# Encoder
input_img = Input(shape=(784,))
encoded = Dense(32, activation='relu')(input_img)

# Decoder
decoded = Dense(784, activation='sigmoid')(encoded)

autoencoder = Model(input_img, decoded)
autoencoder.compile(optimizer='adam', loss='binary_crossentropy')
```

---

## **6. Herramientas de Decodificación**  

### **6.1. Para Desarrollo**  
| **Herramienta**       | **Lenguaje**  | **Uso**                     |  
|----------------------|-------------|----------------------------|  
| **CyberChef**        | Web         | Operaciones de codificación/decodificación. |  
| **iconv**           | Bash        | Conversión de caracteres.   |  
| **binwalk**         | Python      | Extracción de datos embebidos. |  

### **6.2. Para Análisis Forense**  
- **Audacity**: Decodificación de tonos DTMF.  
- **Ghidra**: Ingeniería inversa de binarios.  

---

## **7. Ejemplo Práctico: Decodificar QR**  
```python
from pyzbar.pyzbar import decode
from PIL import Image

datos_qr = decode(Image.open('qr.png'))
print(datos_qr[0].data.decode('utf-8'))  # Texto decodificado
```

---

## **8. Recursos para Aprender**  
📚 **Libros**:  
- "The Code Book" - Simon Singh (historia de la criptografía).  
- "Information Theory, Inference and Learning Algorithms" - David MacKay.  

🌐 **Herramientas Online**:  
- [CyberChef](https://gchq.github.io/CyberChef/) (todo-en-uno).  
- [Base64 Decoder](https://www.base64decode.org/).  

---
## **Enlaces Relacionados en Obsidian**  
- [[Codificación]]  
- [[Criptografía]]  
- [[Machine learning (ML)]]  