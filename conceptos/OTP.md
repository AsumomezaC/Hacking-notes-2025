#Seguridad #Hacking #Computación #Software 

# One-Time Password (OTP)
Contraseña de un solo uso. Tipos comunes:

1. **TOTP** (Time-based): 
   - Generado localmente (ej: Google Authenticator)
   - Basado en tiempo + secreto compartido

2. **HOTP** (HMAC-based):
   - Incrementa contador con cada uso
   - Ej: Yubikey

Vulnerabilidades típicas:
- Implementación incorrecta de validación
- Reutilización de OTPs
- Generación predecible