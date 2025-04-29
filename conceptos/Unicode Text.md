#Software #Comunicación #Lenguaje
# Unicode Text

## ¿Qué es Unicode?
- **Estándar universal** para la codificación de caracteres de casi todos los sistemas de escritura del mundo.
- **Objetivo**: Reemplazar esquemas de codificación inconsistentes (como ASCII extendido, ISO-8859, etc.) con un sistema unificado.
- **Versión actual**: Unicode 15.1 (2023), con más de **149,000 caracteres** (incluyendo emojis, símbolos técnicos, y escrituras antiguas).

## Conceptos Clave
1. **Puntos de Código (Code Points)**:
   - Números únicos asignados a cada carácter (ej. `U+0041` = `A`).
   - Rango: `U+0000` a `U+10FFFF`.
2. **Planes Unicode**:
   - **Básico Multilingual Plane (BMP)**: `U+0000` a `U+FFFF` (incluye la mayoría de idiomas modernos).
   - **Planos suplementarios**: Emojis, ideográficos, etc. (ej. `U+1F600` = 😀).
3. **Codificación**:
   - **UTF-8**: Compatible con ASCII, variable (1 a 4 bytes). Dominante en la web.
   - **UTF-16**: Usado en sistemas como Windows y Java (2 o 4 bytes).
   - **UTF-32**: Fijo (4 bytes), poco eficiente para almacenamiento.

## Ejemplos Prácticos
- **Caracteres especiales**: `©` (`U+00A9`), `π` (`U+03C0`), `★` (`U+2605`).
- **Emojis**: `😂` (`U+1F602`), `🚀` (`U+1F680`).
- **Escrituras**: `あ` (Hiragana japonés, `U+3042`), `α` (Griego, `U+03B1`).

## Herramientas y Recursos
1. **Búsqueda de caracteres**:
   - [Unicode Table](https://unicode-table.com) (tabla interactiva).
   - [FileFormat.Info](https://www.fileformat.info/info/unicode/) (búsqueda avanzada).
2. **Conversión**:
   - Usar `\uXXXX` (UTF-16) o `\UXXXXXXXX` (UTF-32) en lenguajes de programación.
   ```python
   print("\u03A9")  # Imprime: Ω
   ```
3. **Editores**:
   - **VS Code**: Soporte nativo con visualización de puntos de código.
   - **BabelMap** (Windows): Mapa completo de caracteres Unicode.

## Problemas Comunes
- **Compatibilidad**: No todas las fuentes soportan todos los caracteres (ej. símbolos matemáticos raros).
- **Normalización**: Diferentes secuencias pueden representar el mismo carácter (ej. `ñ` = `U+00F1` vs. `n\u0303`).
  - Usar **Normalización Unicode** (formas NFC, NFD, NFKC, NFKD).

## Enlaces Útiles
- [Página oficial Unicode](https://unicode.org)
- [UTF-8 Everywhere](https://utf8everywhere.org) (guía de buenas prácticas).