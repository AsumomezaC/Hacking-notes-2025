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
- **Conectarse a un puerto especifico**:
```bash
ssh user@host -p numberPort
```

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
    

---

Aquí tienes la información para agregar a tus apuntes en Obsidian sobre el uso de `-vvv` al conectarte a un servidor SSH:

---

# Uso de `-vvv` en SSH

## 1. ¿Qué es `-vvv` en SSH?

El argumento `-vvv` en el comando `ssh` aumenta el nivel de verbosidad de la conexión SSH, permitiendo diagnosticar problemas de conexión y depuración.

## 2. Niveles de verbosidad en SSH

SSH permite tres niveles de verbosidad para obtener más información sobre la conexión:

- `-v` → Muestra información básica de depuración.
- `-vv` → Muestra más detalles, incluyendo autenticación.
- `-vvv` → Muestra información extremadamente detallada, útil para depuración avanzada.

## 3. Ejemplo de uso

```bash
ssh -vvv usuario@servidor
```

Esto mostrará mensajes detallados sobre cada paso de la conexión, incluyendo:

- Negociación de claves.
- Métodos de autenticación intentados.
- Algoritmos de cifrado usados.
- Intentos de autenticación con clave pública y contraseña.

## 4. ¿Cuándo usar `-vvv`?

Usa `ssh -vvv` cuando:

- No puedes conectarte y quieres ver el motivo exacto del error.
- Necesitas verificar qué método de autenticación está fallando.
- Quieres saber qué claves SSH se están usando.
- Sospechas que hay problemas con el servidor SSH o el firewall.

## 5. Ejemplo de salida

```plaintext
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Connecting to servidor [192.168.1.100] port 22.
debug2: Local version string SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: KEX algorithms: curve25519-sha256,ecdh-sha2-nistp256,diffie-hellman-group-exchange-sha256
debug1: Host 'servidor' is known and matches the ECDSA key.
debug1: Found key in /home/usuario/.ssh/known_hosts:5
debug1: Authentications that can continue: publickey,password
debug2: Trying private key: /home/usuario/.ssh/id_rsa
debug2: Enabling compatibility mode for protocol 2.0
debug1: Next authentication method: password
```

Esta información permite entender qué está ocurriendo en cada paso de la conexión SSH.
## Conclusión

SSH es una herramienta esencial para la administración de servidores de manera segura. Ofrece una amplia variedad de opciones que permiten interactuar con servidores remotos de forma eficiente y segura.