#Software #Hacking #Seguridad #Internet 
# WebShell en PHP

## Definición
Una **WebShell** es un script malicioso escrito en [[PHP]] (u otros lenguajes) que permite a un atacante controlar un servidor web comprometido. Funciona como una interfaz entre el atacante y el servidor.

## Características principales
- Se ejecuta en el contexto del servidor web (usuario www-data, apache, etc.)
- Permite ejecución de comandos, navegación por directorios, subida/descarga de archivos
- Suele estar ofuscada para evitar detección

## Ejemplo básico de WebShell PHP
```php
<?php 
    if(isset($_GET['cmd'])) {
        system($_GET['cmd']); 
    }
?>
```

## Métodos comunes de infección
- Explotación de vulnerabilidades (LFI, RFI, SQLi, etc.)
- Subida de archivos maliciosos
- Backdoors en aplicaciones comprometidas

## Técnicas de ofuscación comunes
- Codificación Base64
- Función `eval()` con cadenas codificadas
- Uso de funciones como `gzinflate()` 
- Concatenación de strings

## Ejemplo ofuscado
```php
<?php $k='ev'.'al'; $k(gzinflate(base64_decode('...'))); ?>
```

## Detección y prevención
- Monitorear archivos PHP nuevos o modificados
- Buscar funciones peligrosas (`system`, `exec`, `passthru`, etc.)
- Restringir permisos de escritura en directorios web
- Usar WAF (Web Application Firewall)
- Escanear con herramientas como `Lynis` o `Rkhunter`

## Comandos peligrosos en WebShells
- `system()`, `exec()`, `shell_exec()`
- `passthru()`, `popen()`, `proc_open()`
- `eval()`, `assert()`
- `file_put_contents()` (para crear nuevos archivos maliciosos)