#Programación #Software #Hacking 

# Definición
Patrones para buscar/manipular texto.
# Expresiones Regulares (Regex) en [[Programación]] y [[Hacking]]

## 📌 Conceptos Básicos
```regex
- `.`       → Cualquier carácter (excepto salto de línea).
- `\d`      → Dígito (0-9).
- `\w`      → Carácter alfanumérico (a-Z, 0-9, _).
- `*`       → 0 o más repeticiones.
- `+`       → 1 o más repeticiones.
- `[]`      → Rango (ej: `[A-Za-z]`).
- `()`      → Grupo de captura.
- `^`       → Inicio de línea.
- `$`       → Fin de línea.
- `\b`      → Límite de palabra.
```

**Ejemplo (Email)**:
```regex
\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}\b
```

---

## 🔍 Casos de Uso en Hacking
### 1. Extracción de Datos Sensibles
- **IPs**: `\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}`
- **Emails**: `\b[\w.%+-]+@[\w.-]+\.[a-zA-Z]{2,}\b`
- **URLs**: `https?://[^\s]+`

### 2. Fuzzing/SQL Injection
```regex
-- Buscar posibles inyecciones:
'.*?(SELECT|INSERT|UPDATE|DELETE).*?--
```

### 3. Web Scraping
```regex
-- Extraer enlaces HTML:
href="(.*?)"
```

---

## 🛠 Herramientas con Regex
### 1. Comandos Útiles
```bash
# Grep (Linux):
grep -E "pattern" archivo.txt

# Extraer IPs de un log:
grep -oE "\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}" access.log
```

### 2. Python (`re` module)
```python
import re
# Buscar todos los números en un texto:
re.findall(r'\d+', 'abc123def')  # Output: ['123']
```

---

## 📋 Cheatsheet Rápido
| Patrón   | Descripción                  |
|----------|------------------------------|
| `\s`     | Espacio en blanco.           |
| `\S`     | Cualquier cosa que no sea espacio. |
| `(?=.*X)`| Lookahead (debe contener X). |
| `\n`     | Salto de línea.              |

---

## 📂 Ejemplo Práctico (Log Analysis)
**Log**:
```
2023-10-01 12:00:00 [IP: 192.168.1.1] Request: /login?user=admin
```

**Regex para extraer IP y usuario**:
```regex
IP: (\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}).*user=(\w+)
```

**Resultado**:
- Grupo 1: `192.168.1.1`
- Grupo 2: `admin`