#Hacking #Software #Programación #Computación 
# [[JSON]] Web Token (JWT)  

## 🔹 ¿Qué es un JWT?  
Un **JSON Web Token (JWT)** es un estándar abierto (**RFC 7519**) utilizado para generar tokens de autenticación y autorización de forma segura. Se usa principalmente para transmitir información entre partes de manera confiable y verificable.  

## 🔹 ¿Cómo funciona un JWT?  
Un JWT es un **token firmado**, lo que significa que su autenticidad puede ser verificada mediante una clave secreta o un par de claves pública/privada (en caso de firmas con RSA o ECDSA).  

El token JWT está compuesto por **tres partes codificadas en Base64**:  

1. **Header** (Encabezado): Contiene el tipo de token y el algoritmo de firma.  
2. **Payload** (Cuerpo): Contiene los datos o claims (información del usuario, roles, etc.).  
3. **Signature** (Firma): Se usa para verificar la integridad del token.  

Ejemplo de un JWT en su forma codificada:  
```

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjEwLCJyb2xlIjoiYWRtaW4ifQ.sD3Jp9cGAsO9w7JXwPX5F7J2vNer7H3zLoJMe2fGqZw

````

## 🔹 ¿Para qué se utilizan los JWT?  
✅ **Autenticación**: Se usa para verificar la identidad de un usuario sin necesidad de almacenar sesiones en el servidor.  
✅ **Autorización**: Un JWT puede contener los permisos del usuario y ser validado en cada solicitud.  
✅ **Comunicación entre microservicios**: Permite enviar información segura entre servicios sin necesidad de mantener sesiones.  

## 🔹 Ejemplo de un JWT decodificado  
### 1️⃣ **Header**  
```json
{
  "alg": "HS256",
  "typ": "JWT"
}
````

### 2️⃣ **Payload**

```json
{
  "userId": 10,
  "role": "admin",
  "exp": 1712345678
}
```

### 3️⃣ **Firma (Signature)**

La firma se genera con el algoritmo especificado en el `header`, combinando el `header`, el `payload` y una **clave secreta**.

## 🔹 Ventajas y desventajas de JWT

### ✅ **Ventajas**

- **Independiente del estado**: No requiere almacenamiento en el servidor.
    
- **Seguro**: Usa firmas digitales para evitar manipulación.
    
- **Rápido**: La autenticación se realiza sin consultas a la base de datos.
    

### ❌ **Desventajas**

- **No se puede invalidar fácilmente**: Si un token es comprometido, sigue siendo válido hasta que expire.
    
- **Mayor tamaño**: Un JWT puede ser más grande que un simple token de sesión.
    
- **Seguridad**: Si no se usa HTTPS, el token podría ser interceptado.
    

## 🔹 Buenas prácticas con JWT

✅ **Usar expiración (`exp`)** para evitar tokens ilimitados.  
✅ **Transmitirlo solo por HTTPS** para evitar ataques Man-in-the-Middle.  
✅ **No almacenar JWT en localStorage** si es usado en un navegador (usar cookies seguras).  
✅ **Utilizar firmas seguras** como `RS256` en lugar de `HS256` cuando sea posible.