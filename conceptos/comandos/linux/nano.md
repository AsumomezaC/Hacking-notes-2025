# Comando `nano` en Linux

## 1. ¿Qué es `nano`?

`nano` es un editor de texto en la terminal de Linux que permite editar archivos de manera sencilla y rápida. Es una alternativa más fácil de usar que `vim` o `emacs`.

## 2. Sintaxis básica

```bash
nano [opciones] [archivo]
```

Si el archivo no existe, `nano` lo creará automáticamente.

Ejemplo:

```bash
nano documento.txt
```

## 3. Navegación y edición

### a) Moverse dentro del archivo

- **← / →** → Moverse entre caracteres
- **↑ / ↓** → Moverse entre líneas
- **Ctrl + A** → Ir al inicio de la línea
- **Ctrl + E** → Ir al final de la línea
- **Ctrl + Y** → Desplazarse una página arriba
- **Ctrl + V** → Desplazarse una página abajo

### b) Buscar y reemplazar

- **Ctrl + W** → Buscar texto
- **Ctrl + R** → Reemplazar texto
- **Alt + W** → Buscar la siguiente coincidencia

## 4. Guardar y salir

- **Ctrl + O** → Guardar cambios (presiona Enter para confirmar)
- **Ctrl + X** → Salir de `nano` (pregunta si deseas guardar si hay cambios)
- **Ctrl + S** → Guardar sin salir

## 5. Selección y manipulación de texto

- **Ctrl + K** → Cortar línea
- **Ctrl + U** → Pegar línea
- **Ctrl + 6** → Iniciar selección (usa flechas para seleccionar)
- **Alt + 6** → Copiar la selección
- **Ctrl + J** → Justificar el párrafo actual

## 6. Mostrar números de línea

Para ver números de línea dentro de `nano`, usa:

```bash
nano -c archivo.txt
```

También puedes activarlo dentro del editor presionando **Alt + Shift + #**.

## 7. Abrir `nano` en modo solo lectura

Si solo quieres ver un archivo sin modificarlo:

```bash
nano -v archivo.txt
```

## 8. Configuración personalizada

Puedes modificar el comportamiento de `nano` editando su archivo de configuración en `~/.nanorc`. Algunas opciones útiles son:

```bash
set linenumbers   # Mostrar números de línea  
set tabsize 4     # Tamaño de tabulación en 4 espacios  
set mouse         # Habilitar el uso del mouse  
```

## 9. Salida rápida sin guardar

Si hiciste cambios y quieres salir sin guardar, usa:

```bash
Ctrl + X → N
```