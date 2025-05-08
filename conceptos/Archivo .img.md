#Hacking #Software #Programación #Archivos #Computación #Forenscic 
# **Archivos .img: Guía Completa**

Los archivos con extensión **.img** son imágenes de disco que contienen una representación exacta bit a bit de un medio de almacenamiento. Son ampliamente utilizados en computación forense, virtualización y recuperación de datos.

## 🔍 **¿Qué es un archivo .img?**
Un archivo **.img** es:
- Una copia exacta (bit-a-bit) de un dispositivo de almacenamiento
- Puede contener particiones, sistemas de archivos y datos
- Equivalente a archivos **.iso** pero más genérico (no solo para CDs/DVDs)

## 📌 **Tipos de archivos .img**

| Tipo | Descripción | Uso común |
|------|-------------|-----------|
| **Raw image** | Copia exacta sin compresión | Forense, recuperación |
| **Sparse image** | Solo ocupa espacio de datos existentes | Virtualización |
| **Compressed image** | Comprimido (ej: .img.gz) | Almacenamiento |
| **Hybrid image** | Combinación de varios formatos | Arranque USB |

## 🛠 **Herramientas para trabajar con .img**

### 1. **Creación de imágenes**
```bash
# Crear imagen de un dispositivo completo
sudo dd if=/dev/sdX of=disco.img bs=4M status=progress

# Crear imagen comprimida
sudo dd if=/dev/sdX | gzip > disco.img.gz
```

### 2. **Montar imágenes**
```bash
# Montar imagen completa (detectar particiones)
sudo losetup -Pf disco.img
sudo mount /dev/loop0p1 /mnt

# Montar partición específica
sudo mount -o loop,offset=$((512*2048)) disco.img /mnt
```

### 3. **Análisis forense**
```bash
# Ver tabla de particiones
mmls disco.img

# Analizar sistema de archivos
fsstat disco.img

# Extraer archivos
fls -r -o 2048 disco.img  # Offset de partición
```

## ⚙️ **Usos comunes**

1. **Forense digital**: Preservar evidencia digital intacta
2. **Backup de discos**: Crear copias exactas de sistemas
3. **Virtualización**: Imágenes para máquinas virtuales
4. **Desarrollo embebido**: Imágenes para Raspberry Pi, etc.
5. **Recuperación de datos**: Trabajar con copias en lugar del original

## 🔄 **Conversión entre formatos**

### A VMDK (VMware):
```bash
qemu-img convert -f raw -O vmdk disco.img disco.vmdk
```

### A QCOW2 (QEMU):
```bash
qemu-img convert -f raw -O qcow2 disco.img disco.qcow2
```

### Descomprimir imagen:
```bash
gunzip disco.img.gz
```

## 📊 **Comparación con formatos similares**

| Formato | Compresión | Checksum | Soporte |
|---------|------------|----------|---------|
| **.img** | No (raw) | No | Universal |
| **.E01** | Sí | Sí | Forense |
| **.qcow2** | Sí | No | Virtualización |
| **.vmdk** | Sí | No | VMware |
| **.iso** | No | Opcional | CD/DVD |

## ⚠️ **Precauciones importantes**

1. **Tamaño**: Las imágenes raw son del tamaño completo del disco
2. **Permisos**: Requieren acceso root para creación/montaje
3. **Integridad**: Verificar con hashes (sha256sum)
4. **Espacio**: Asegurar suficiente espacio en disco

## 🚀 **Ejemplo práctico: Crear imagen de Raspberry Pi**

1. Insertar tarjeta SD en lector
2. Identificar dispositivo con `lsblk`
3. Crear imagen:
```bash
sudo dd if=/dev/sdX of=raspberry.img bs=4M status=progress
```
4. Comprimir:
```bash
gzip raspberry.img
```

Los archivos .img son fundamentales en administración de sistemas, forense y virtualización. Su manejo adecuado permite trabajar con medios de almacenamiento de manera segura y eficiente.