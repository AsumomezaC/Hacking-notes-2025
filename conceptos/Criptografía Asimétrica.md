#Criptografía #Hacking #Software #Seguridad 

## 📌 Definición
La **criptografía asimétrica** (o de clave pública) es un sistema criptográfico que utiliza un par de claves:
- **Clave pública**: Compartida abiertamente para cifrar datos o verificar firmas.
- **Clave privada**: Secreta, usada para descifrar o firmar digitalmente.

## 🔑 Componentes Clave
1. **Par de claves**: Generadas matemáticamente relacionadas (ej: RSA, ECC).
2. **Algoritmos**: 
   - **Cifrado/Descifrado**: RSA, ElGamal.
   - **Firma digital**: ECDSA, EdDSA.
   - **Intercambio de claves**: Diffie-Hellman.

## ⚙️ Funcionamiento
1. **Cifrado**: 
   - *A* usa la **clave pública de B** para cifrar un mensaje.
   - Solo *B* puede descifrarlo con su **clave privada**.
2. **Firma digital**: 
   - *A* firma con su **clave privada**.
   - *B* verifica con la **clave pública de A**.

## 📊 Comparación con Simétrica
| **Aspecto**       | **Asimétrica**                          | **Simétrica**                |
|--------------------|----------------------------------------|------------------------------|
| Número de claves   | 2 (pública + privada)                  | 1 (secreta compartida)       |
| Velocidad          | Lenta (cálculos complejos)             | Rápida                       |
| Uso típico         | Intercambio de claves, firmas          | Cifrado masivo de datos      |

## 🔐 Aplicaciones
- **SSL/TLS**: Seguridad en la web (HTTPS).
- **PGP/GPG**: Correo encriptado.
- **Blockchain**: Firmas digitales en transacciones.
- **Autenticación**: SSH, certificados digitales.

## ⚠️ Limitaciones
- **Rendimiento**: Más lenta que la simétrica (se usa híbrido: asimétrica para intercambiar clave simétrica).
- **Gestión de claves**: Requiere infraestructura (PKI) para validar identidades.

## 📚 Algoritmos Notables
- **RSA**: Basado en factorización de primos.
- **ECC (Curvas Elípticas)**: Menor longitud de clave = misma seguridad que RSA.
- **Diffie-Hellman**: Intercambio seguro de claves.

## 🌟 Ejemplo Práctico con [[Python]]
```python
# Ejemplo simplificado con RSA en Python
from Crypto.PublicKey import RSA

# Generar par de claves
key = RSA.generate(2048)
private_key = key.export_key()
public_key = key.publickey().export_key()

# Cifrar con pública, descifrar con privada
```