# Comando `crontab` en Linux

## 1. ¿Qué es `crontab`?

El **crontab** (cron table) es el archivo donde los usuarios pueden programar tareas automáticas en **cron**, el planificador de tareas en Linux.

## 2. Formato de una línea en `crontab`

Cada línea sigue esta estructura:

```plaintext
MINUTO HORA DÍA_DEL_MES MES DÍA_DE_LA_SEMANA COMANDO
```

### Explicación de los campos:

|Campo|Valores posibles|Ejemplo|
|---|---|---|
|**MINUTO**|0-59|`30` (minuto 30)|
|**HORA**|0-23|`14` (2 PM)|
|**DÍA_DEL_MES**|1-31|`15` (día 15)|
|**MES**|1-12 (o nombres)|`3` (marzo)|
|**DÍA_DE_LA_SEMANA**|0-7 (0 y 7 = domingo)|`1` (lunes)|
|**COMANDO**|Comando o script|`/home/usuario/backup.sh`|

### Caracteres especiales

- `*` → Significa "todos los valores posibles".
- `,` → Lista de valores (ej. `1,5,10` significa los días 1, 5 y 10).
- `-` → Rango de valores (ej. `1-5` significa del 1 al 5).
- `/` → Incremento (ej. `*/5` significa "cada 5 minutos").

---

## 3. Comandos útiles de `crontab`

|Comando|Descripción|
|---|---|
|`crontab -l`|Lista las tareas programadas del usuario.|
|`crontab -e`|Edita el crontab del usuario actual.|
|`crontab -r`|Borra todas las tareas del usuario actual.|
|`sudo crontab -e`|Edita el crontab del usuario root.|
|`sudo crontab -l`|Lista las tareas del usuario root.|

---

## 4. Ejemplos de configuraciones

### 🕘 Ejecutar un script todos los días a las 9 AM

```bash
0 9 * * * /home/usuario/mi_script.sh
```

### 🔄 Ejecutar un comando cada 10 minutos

```bash
*/10 * * * * /home/usuario/comando.sh
```

### 📅 Ejecutar un script los lunes y viernes a las 6 PM

```bash
0 18 * * 1,5 /home/usuario/tarea.sh
```

### 🖥️ Limpiar la memoria caché cada hora

```bash
0 * * * * sync; echo 3 > /proc/sys/vm/drop_caches
```

### 🛠️ Reiniciar un servicio cada noche a la medianoche

```bash
0 0 * * * systemctl restart mi-servicio
```

---

## 5. Variables en `crontab`

Puedes definir variables antes de las tareas:

```bash
MAILTO="usuario@correo.com"  # Envía la salida de cron a este correo
SHELL=/bin/bash               # Define la shell usada por cron
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin  # Define rutas
```

---

## 6. Archivos de configuración de `cron`

- **`/etc/crontab`** → Crontab del sistema.
- **`/var/spool/cron/crontabs/usuario`** → Crontab de cada usuario.
- **`/etc/cron.daily/`** → Scripts que se ejecutan diariamente.
- **`/etc/cron.hourly/`** → Scripts que se ejecutan cada hora.
- **`/etc/cron.weekly/`** → Scripts que se ejecutan semanalmente.
- **`/etc/cron.monthly/`** → Scripts que se ejecutan mensualmente.

---

Con esto tienes un resumen completo de `crontab` para tus apuntes en Obsidian. ¿Quieres agregar algo más? 🚀⏳