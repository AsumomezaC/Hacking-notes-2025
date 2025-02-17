**Conectarse por SSH**

```markdown
# Conectarse a un Servidor Remoto mediante SSH

El protocolo SSH (Secure Shell) se usa para conectarse de manera segura a un servidor remoto y ejecutar comandos. SSH cifra las comunicaciones, proporcionando un canal seguro para interactuar con sistemas remotos.

## Sintaxis básica

```bash
ssh usuario@host
````

Donde:

- `usuario`: El nombre de usuario en el servidor remoto.
- `host`: La dirección IP o el nombre del dominio del servidor.

### Ejemplo de uso

2. Para conectarte a un servidor con la dirección `192.168.1.100` como usuario `picoplayer`:

```bash
ssh picoplayer@192.168.1.100
```

3. Si el servidor escucha en un puerto diferente al predeterminado (22), puedes especificar el puerto con la opción `-p`:

```bash
ssh -p 2222 picoplayer@192.168.1.100
```

4. Para conectarte a un servidor con un archivo de clave privada (en lugar de una contraseña):

```bash
ssh -i /ruta/a/clave.pem picoplayer@192.168.1.100
```

### Autenticación

Cuando te conectas por primera vez a un servidor, se te pedirá que aceptes la clave del servidor si no está almacenada en tu archivo `known_hosts`. Esto es una medida de seguridad para evitar ataques de intermediarios.

Si el servidor requiere autenticación por contraseña, te pedirá que ingreses la contraseña después de la conexión.

### Usar SSH con puertos y redirección

- **Redirección de puertos locales**: Para redirigir un puerto local hacia un puerto en el servidor remoto:

```bash
ssh -L 8080:localhost:80 usuario@host
```

Este comando redirige el puerto local 8080 al puerto 80 en el servidor remoto.

- **Redirección de puertos remotos**: Para redirigir un puerto del servidor remoto a tu máquina local:

```bash
ssh -R 8080:localhost:80 usuario@host
```

## Copiar archivos usando `scp` (Secure Copy)

Puedes copiar archivos entre tu máquina local y el servidor remoto usando `scp`, que utiliza el mismo protocolo SSH.

- Para copiar un archivo del servidor remoto a tu máquina local:

```bash
scp usuario@host:/ruta/del/archivo /ruta/local
```

- Para copiar un archivo de tu máquina local al servidor remoto:

```bash
scp /ruta/local usuario@host:/ruta/remota
```

## Consejos adicionales

- **Autenticación sin contraseña**: Para evitar tener que escribir la contraseña cada vez, puedes configurar una autenticación basada en claves. Esto involucra generar un par de claves pública y privada, y colocar la clave pública en el archivo `~/.ssh/authorized_keys` del servidor.
    
- **Salir de una sesión SSH**: Para cerrar una sesión SSH, simplemente escribe el comando `exit` o presiona `Ctrl+D`.
    

## Conclusión

SSH es una herramienta esencial para la administración de servidores de manera segura. Ofrece una amplia variedad de opciones que permiten interactuar con servidores remotos de forma eficiente y segura.