#Hacking #Software #Computación 
# Itsdangerous Signing
Librería [[Python]] para firmas seguras. Usada por [[Flask Sessions Cookies|Flask]] para cookies.

Características:
- Firma HMAC-SHA1 por defecto
- Previene manipulación de datos
- Inclye timestamp opcional

Ejemplo de firma:
```python
from itsdangerous import URLSafeSerializer
s = URLSafeSerializer("secret-key")
s.dumps({"user": "admin"})  # Retorna string firmado
```
