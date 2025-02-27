# Comando `vi` en Linux

## 1. ¿Qué es `vi`?

`vi` es un editor de texto en la terminal de Linux, disponible en prácticamente todas las distribuciones. Es rápido y eficiente, aunque su curva de aprendizaje es más alta que editores como [[nano]].

## 2. Modos de `vi`

`vi` tiene tres modos principales:

- **Modo normal:** Navegación y ejecución de comandos.
- **Modo inserción:** Permite escribir y modificar texto.
- **Modo de línea de comandos:** Para guardar, salir y ejecutar comandos adicionales.

## 3. Sintaxis básica

```bash
vi [archivo]
```

Ejemplo:

```bash
vi documento.txt
```

Si el archivo no existe, `vi` lo creará.

## 4. Navegación en `vi`

- **h, j, k, l** → Moverse a la izquierda, abajo, arriba y derecha.
- **gg** → Ir al inicio del archivo.
- **G** → Ir al final del archivo.
- **Ctrl + d / Ctrl + u** → Avanzar o retroceder media pantalla.
- **Ctrl + f / Ctrl + b** → Avanzar o retroceder una pantalla completa.
- **/texto** → Buscar texto en el archivo.
- **n / N** → Ir a la siguiente o anterior coincidencia.

## 5. Modos de edición

Para entrar en **modo de inserción**, usa:

- **i** → Insertar antes del cursor.
- **a** → Insertar después del cursor.
- **o** → Insertar en una nueva línea debajo del cursor.
- **O** → Insertar en una nueva línea arriba del cursor.

Para salir del modo de inserción, presiona `Esc`.

## 6. Guardar y salir

Desde el **modo de comandos** (`Esc` para entrar):

- **`:w`** → Guardar cambios.
- **`:q`** → Salir.
- **`:wq` o `ZZ`** → Guardar y salir.
- **`:q!`** → Salir sin guardar.

## 7. Edición de texto

- **x** → Borrar un carácter.
- **dd** → Borrar una línea.
- **yy** → Copiar una línea.
- **p** → Pegar después del cursor.
- **u** → Deshacer el último cambio.
- **Ctrl + r** → Rehacer el último cambio deshecho.

## 8. Uso de `sudo vi test` en un servidor

Cuando te conectas a un servidor mediante [[SSH]] y necesitas editar un archivo que requiere permisos de `root`, puedes usarlo agregando [[sudo]]:

```bash
sudo vi test
```

Esto abre el archivo `test` con permisos elevados.

### Problema común: Error "E482: Can't open file for writing"

Si abres un archivo sin permisos y luego intentas guardar con `:w`, podrías obtener este error. Para solucionarlo, usa:

```bash
:w !sudo tee %
```

Esto guarda el archivo con permisos de `sudo` sin salir de `vi`.

### Editar archivos en `/etc/` o `/var/`

Cuando necesitas modificar archivos del sistema, usa:

```bash
sudo vi /etc/nginx/nginx.conf
```

o

```bash
sudo vi /var/log/syslog
```

Asegúrate de no modificar archivos críticos sin respaldo.

## 9. Alternativas a `vi`

Si `vi` se te hace complicado, puedes usar:

- [[vim]] (versión mejorada de `vi`).
- [[nano]] (más intuitivo).
- [[bvi]] (para edición hexadecimal).