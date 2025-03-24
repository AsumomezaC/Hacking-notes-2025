#Software #Comando #SistemaOperativo #Linux #Dirección #Archivos 
# Comando `pwd` en Linux

## 1. ¿Qué es `pwd`?

El comando `pwd` (**Print Working Directory**) muestra la ruta absoluta del directorio en el que te encuentras actualmente en la terminal.

## 2. Uso básico

```bash
pwd
```

Salida de ejemplo:

```plaintext
/home/usuario/proyectos
```

Esto indica que el usuario está en el directorio `/home/usuario/proyectos`.

## 3. Opciones útiles

- **`pwd -L`** → Muestra la ruta lógica (considerando enlaces simbólicos).
- **`pwd -P`** → Muestra la ruta física real, resolviendo enlaces simbólicos.

Ejemplo:

```bash
cd /home/usuario/enlace_simbolico
pwd -L  # Muestra /home/usuario/enlace_simbolico
pwd -P  # Muestra /home/usuario/real/directorio
```

## 4. ¿Para qué sirve `pwd`?

✅ Confirmar en qué directorio estás trabajando.  
✅ Evitar confusión cuando usas enlaces simbólicos.  
✅ Usar la ruta en scripts o comandos que requieren rutas absolutas.