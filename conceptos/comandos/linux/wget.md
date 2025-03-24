#Software #Comando #SistemaOperativo #Linux #Conexión #Redes 
# Comando `wget` en Linux

## 1. ¿Qué es `wget`?

`wget` es una herramienta de línea de comandos en Linux que permite descargar archivos desde la web a través de los protocolos HTTP, HTTPS y FTP.

## 2. Sintaxis básica

```bash
wget [opciones] [URL]
```

Ejemplo simple:

```bash
wget https://ejemplo.com/archivo.zip
```

Este comando descarga `archivo.zip` en el directorio actual.

## 3. Opciones principales

### a) Descargar en segundo plano

```bash
wget -b [URL]
```

Ejemplo:

```bash
wget -b https://ejemplo.com/archivo.zip
```

Esto ejecuta la descarga en segundo plano y guarda el progreso en `wget-log`.

### b) Cambiar el nombre del archivo descargado

```bash
wget -O nuevo_nombre.ext [URL]
```

Ejemplo:

```bash
wget -O mi_archivo.zip https://ejemplo.com/archivo.zip
```

### c) Descargar múltiples archivos

Se pueden descargar varias URLs desde un archivo de texto:

```bash
wget -i lista.txt
```

Donde `lista.txt` contiene:

```
https://ejemplo.com/archivo1.zip
https://ejemplo.com/archivo2.zip
```

### d) Reanudar descargas interrumpidas

```bash
wget -c [URL]
```

Ejemplo:

```bash
wget -c https://ejemplo.com/archivo.zip
```

Si la descarga fue interrumpida, se reanudará desde donde quedó.

### e) Limitar la velocidad de descarga

```bash
wget --limit-rate=200k [URL]
```

Ejemplo:

```bash
wget --limit-rate=500k https://ejemplo.com/archivo.zip
```

Esto limita la descarga a 500 KB/s.

### f) Descargar un sitio web completo

```bash
wget -r [URL]
```

Ejemplo:

```bash
wget -r https://ejemplo.com
```

Este comando descarga todo el sitio con su estructura de enlaces.

### g) Descargar solo archivos específicos

```bash
wget -r -A "*.jpg,*.png" [URL]
```

Ejemplo:

```bash
wget -r -A "*.pdf" https://ejemplo.com
```

Descargará solo archivos PDF del sitio.

### h) Iniciar sesión con usuario y contraseña

```bash
wget --user=usuario --password=contraseña [URL]
```

Ejemplo:

```bash
wget --user=admin --password=secreto https://ejemplo.com/archivo.zip
```

⚠️ **Nota**: No es seguro escribir contraseñas en la línea de comandos.

## 4. Combinaciones útiles

### Descargar y extraer en un solo comando:

```bash
wget -O - https://ejemplo.com/archivo.tar.gz | tar xz
```

### Descargar con intervalos entre peticiones para evitar bloqueos:

```bash
wget --wait=10 --random-wait -r [URL]
```

Esto añade una espera aleatoria entre descargas.

### Descargar con un agente de usuario personalizado:

```bash
wget --user-agent="Mozilla/5.0" [URL]
```

## 5. Ver el progreso de la descarga

Para mostrar el progreso de manera más amigable:

```bash
wget --progress=bar [URL]
```

## 6. Descargar con autenticación mediante cookies

Si el sitio web requiere inicio de sesión, puedes usar cookies:

```bash
wget --load-cookies cookies.txt [URL]
```

Para obtener `cookies.txt`, puedes usar extensiones de navegador como **EditThisCookie**.