## ¿Qué es Base64?

Base64 es un método de [[codificación]] binario a texto que permite representar datos binarios en un formato de caracteres [[ASCII]]. Se utiliza comúnmente para transferir datos en entornos que solo admiten texto, como correos electrónicos, almacenamiento en bases de datos y transmisión de datos en aplicaciones web.

La codificación Base64 convierte cada grupo de 3 bytes (24 bits) en 4 caracteres ASCII de 6 bits cada uno. Si la cantidad de bytes no es múltiplo de 3, se agregan caracteres de relleno (`=`) para completar la codificación.

## ¿Dónde se usa Base64?

Algunas aplicaciones comunes de Base64 incluyen:

- **Codificación de imágenes** en [[HTML]]/[[CSS]] (`data:image/png;base64, ...`).
- **Transmisión de datos en [[JSON]] y [[XML]]** sin problemas de caracteres especiales.
- **Autenticación HTTP básica**, donde las credenciales se codifican en Base64.
- **Adjuntar archivos en correos electrónicos ([[MIME]])**.

## Ejemplo de Codificación y Decodificación

### En Python

```python
import base64

# Codificación
texto = "Hola, mundo!"
texto_codificado = base64.b64encode(texto.encode()).decode()
print("Texto codificado:", texto_codificado)

# Decodificación
texto_decodificado = base64.b64decode(texto_codificado).decode()
print("Texto decodificado:", texto_decodificado)
```

**Salida:**

```
Texto codificado: SG9sYSwgbXVuZG8h
Texto decodificado: Hola, mundo!
```

### En JavaScript

```javascript
// Codificación
const texto = "Hola, mundo!";
const textoCodificado = btoa(texto);
console.log("Texto codificado:", textoCodificado);

// Decodificación
const textoDecodificado = atob(textoCodificado);
console.log("Texto decodificado:", textoDecodificado);
```

**Salida:**

```
Texto codificado: SG9sYSwgbXVuZG8h
Texto decodificado: Hola, mundo!
```

## Variantes de Base64

Existen algunas variaciones de Base64 para diferentes aplicaciones:

- **Base64 estándar**: Usa los caracteres `A-Z`, `a-z`, `0-9`, `+`, `/` y `=` como relleno.
- **Base64 URL-Safe**: Reemplaza `+` por `-` y `/` por `_` para evitar problemas en URLs.

Ejemplo en Python:

```python
import base64

texto = "Ejemplo URL Safe"
codificado = base64.urlsafe_b64encode(texto.encode()).decode()
print("Base64 URL-Safe:", codificado)
```

## Consideraciones

- Base64 **aumenta el tamaño** de los datos en aproximadamente un 33%.
- No es un método de cifrado, solo de codificación. No protege los datos de accesos no autorizados.
- Puede ser útil para almacenar datos binarios como imágenes en bases de datos de texto, pero no es eficiente para archivos grandes.