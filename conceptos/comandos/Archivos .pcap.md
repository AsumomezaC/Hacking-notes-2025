#Software #Redes #Computación 
# Archivos .pcap

## Definición
Extensión de archivo que almacena **datos de tráfico de red capturados** (paquetes). Usado comúnmente por herramientas como:
- [[Wireshark]]
- Tcpdump
- Tshark

## Características
- Formato binario estándar (también existe `.pcapng`, su evolución).
- Contiene **cabeceras de paquetes** y **payloads** (datos crudos).
- Metadatos como: timestamp, protocolo, direcciones IP/MAC, puertos.

## Usos principales
1. **Análisis forense**: Detección de intrusos o malware.
2. **Depuración de red**: Diagnóstico de errores en comunicaciones.
3. **Investigación de seguridad**: Reversing de exploits.

---

## Herramientas clave

### 1. Wireshark
- GUI para visualizar `.pcap`.
- Filtros útiles:
  - `ip.src == 192.168.1.1`
  - `tcp.port == 80`
  - `http.request.method == "GET"`

### 2. Tcpdump (CLI)
```bash
# Capturar tráfico en interfaz eth0 y guardar a .pcap
tcpdump -i eth0 -w captura.pcap

# Leer un .pcap existente
tcpdump -r captura.pcap
```

### 3. Tshark (CLI de Wireshark)
```bash
# Extraer URLs HTTP de un .pcap
tshark -r captura.pcap -Y "http.request" -T fields -e http.host -e http.request.uri
```

---

## Metadatos en .pcap
Pueden extraerse con:
- **Capinfos** (incluido en Wireshark):
  ```bash
  capinfos captura.pcap
  ```
  Muestra: duración, paquetes totales, tamaño, interfaces.

- **Ejemplo de salida**:
  ```
  File name:           captura.pcap
  File type:           Wireshark/tcpdump/... - pcap
  Packet size limit:   file hdr: 65535 bytes
  Number of packets:   1240
  File size:           2.5 MB
  ```

---

## Análisis básico con Wireshark
1. **Estadísticas → Jerarquía de protocolos**: Ver distribución de protocolos.
2. **Filtro `tcp.stream eq 0`**: Aislar una conversación TCP.
3. **Seguir flujo TCP/HTTP**: (Clic derecho → Follow → Stream).

---

## Precaución
- Archivos `.pcap` pueden contener **datos sensibles** (credenciales, datos de usuarios).
- Usar filtros para capturar solo tráfico relevante y minimizar tamaño:
  ```bash
  tcpdump -i eth0 -w filtrado.pcap 'port 80 or port 443'
  ```