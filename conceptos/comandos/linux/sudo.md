#Software #Comando #SistemaOperativo #Linux #Terminal #Permisos #Derechos 
# Comando `sudo` en Linux

## 1. ¿Qué es `sudo`?

`sudo` (superuser do) permite ejecutar comandos con privilegios de superusuario o de otro usuario, sin necesidad de cambiar de sesión. Es una alternativa más segura que `su`, ya que permite conceder permisos específicos a usuarios sin darles acceso total al sistema.

## 2. Sintaxis básica

```bash
sudo [opciones] [comando]
```

Ejemplo:

```bash
sudo apt update
```

Este comando actualiza la lista de paquetes en sistemas basados en Debian.

## 3. Opciones comunes

- **`-u usuario`** → Ejecutar un comando como otro usuario:
    
    ```bash
    sudo -u usuario comando
    ```
    
    Ejemplo:
    
    ```bash
    sudo -u postgres psql
    ```
    
    Inicia la consola de PostgreSQL como el usuario `postgres`.
    
- **`-s`** → Iniciar una sesión de shell con privilegios de `root`:
    
    ```bash
    sudo -s
    ```
    
- **`-i`** → Simular una sesión completa de `root` (similar a `su - root`):
    
    ```bash
    sudo -i
    ```
    
- **`-v`** → Renovar el tiempo de autenticación sin ejecutar un comando.
    
- **`-k`** → Invalidar el caché de autenticación, obligando a pedir contraseña en el siguiente `sudo`.
    
- **`-b`** → Ejecutar el comando en segundo plano.
    

## 4. Uso de `sudo -l` en un servidor SSH

Cuando te conectas a un servidor mediante SSH, puedes usar `sudo -l` para ver qué comandos puedes ejecutar con `sudo`.

Ejemplo de conexión SSH:

```bash
ssh usuario@servidor
```

Una vez dentro del servidor, ejecuta:

```bash
sudo -l
```

Esto mostrará una lista de los comandos que puedes ejecutar con `sudo` y si se requiere contraseña o no.

Salida de ejemplo:

```
User usuario may run the following commands on servidor:
    (ALL : ALL) ALL
```

Esto significa que el usuario puede ejecutar cualquier comando como cualquier usuario.

Ejemplo con restricciones:

```
User usuario may run the following commands on servidor:
    (root) NOPASSWD: /usr/bin/systemctl restart apache2
```

En este caso, el usuario puede reiniciar Apache sin necesidad de ingresar contraseña.

Si no tienes permisos para ejecutar `sudo`, el mensaje será:

```
Sorry, user usuario is not allowed to execute '/bin/bash' as root on servidor.
```

## 5. Agregar permisos con `visudo`

Para otorgar permisos de `sudo` a un usuario, usa:

```bash
sudo visudo
```

Y agrega una línea como:

```
usuario ALL=(ALL) NOPASSWD: ALL
```

Esto permite al usuario ejecutar cualquier comando sin contraseña (útil, pero inseguro en algunos casos).