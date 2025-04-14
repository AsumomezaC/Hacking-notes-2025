#Software #Computación #Internet #Web 
# Métodos HTTP (Solicitudes al Servidor)

## Introducción
Los métodos HTTP (o verbos HTTP) definen la acción que se desea realizar sobre un recurso identificado por una URL. Son la base de las APIs RESTful y la comunicación web.

## Métodos Principales

### 1. `GET`
- **Descripción**: Solicita datos de un recurso específico (solo lectura).
- **Características**:
  - No modifica el recurso.
  - Puede ser cacheado.
  - Parámetros visibles en la URL.
- **Uso típico**: Obtener información de una página web o API.
- **Ejemplo**:
```http
GET /api/usuarios/123 HTTP/1.1
```
### 2. `POST`
- **Descripción**: Envía datos para crear o procesar un recurso.
- **Características**:
  - Puede modificar el servidor.
  - Los datos van en el cuerpo (body) de la solicitud.
  - No es idempotente (múltiples llamadas pueden tener efectos diferentes).
- **Uso típico**: Enviar formularios, crear recursos.
- **Ejemplo**:
```http
  POST /api/usuarios HTTP/1.1
  Content-Type: application/json
  {"nombre": "Juan", "email": "juan@example.com"}
```

### 3. `PUT`
- **Descripción**: Reemplaza completamente un recurso o lo crea si no existe.
- **Características**:
  - Idempotente (múltiples llamadas tienen el mismo efecto).
  - Requiere enviar el recurso completo.
- **Uso típico**: Actualizar un recurso existente.
- **Ejemplo**:
```http
  PUT /api/usuarios/123 HTTP/1.1
  Content-Type: application/json
  {"nombre": "Juan Pérez", "email": "juan@example.com"}
```

### 4. `DELETE`
- **Descripción**: Elimina un recurso específico.
- **Características**:
  - Idempotente.
  - Puede devolver estado `204` (éxito sin contenido) o `200` con detalles.
- **Uso típico**: Borrar registros en una base de datos.
- **Ejemplo**:
```http
  DELETE /api/usuarios/123 HTTP/1.1
```

### 5. `PATCH`
- **Descripción**: Aplica modificaciones parciales a un recurso.
- **Características**:
  - No es idempotente (depende de la implementación).
  - Solo envía los campos a modificar.
- **Uso típico**: Actualizar parcialmente un recurso (ej: cambiar solo el email).
- **Ejemplo**:
```http
PATCH /api/usuarios/123 HTTP/1.1
  Content-Type: application/json
  {"email": "nuevo-email@example.com"}  
```

## Métodos Adicionales
- **`HEAD`**: Como `GET`, pero solo devuelve encabezados (sin cuerpo).
- **`OPTIONS`**: Describe las opciones de comunicación para el recurso.
- **`TRACE`**: Realiza un test de bucle de mensaje (usado para diagnóstico).

## Códigos de Estado Relacionados
| Método   | Éxito (2xx)          | Error (4xx/5xx)        |
|----------|----------------------|------------------------|
| `GET`    | `200 OK`             | `404 Not Found`        |
| `POST`   | `201 Created`        | `400 Bad Request`      |
| `PUT`    | `200 OK`/`204 No Content` | `409 Conflict`     |
| `DELETE` | `204 No Content`     | `403 Forbidden`        |

## Buenas Prácticas
- Usar `GET` solo para operaciones seguras (sin efectos secundarios).
- Preferir `PUT` sobre `POST` para actualizaciones idempotentes.
- Usar `PATCH` para actualizaciones parciales eficientes.

## Ejemplo en Curl
```bash
# GET
curl -X GET https://api.example.com/recursos/1

# POST
curl -X POST -H "Content-Type: application/json" -d '{"clave":"valor"}' https://api.example.com/recursos

# DELETE
curl -X DELETE https://api.example.com/recursos/1
```