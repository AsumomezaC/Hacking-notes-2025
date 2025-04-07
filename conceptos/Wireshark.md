#Redes #Comunicación #Computación 
# Wireshark

## Definición
Herramienta de **análisis de protocolos de red** de código abierto, utilizada para capturar y examinar tráfico en tiempo real o desde archivos `.pcap/.pcapng`.

## Casos de Uso
- Troubleshooting de redes.
- Detección de anomalías/ataques (DoS, escaneos).
- Reversing de comunicaciones (APIs, malware).
- Educación sobre protocolos.

---

## Instalación
- **Linux**: 
  ```bash
  sudo apt install wireshark  # Debian/Ubuntu
  sudo dnf install wireshark  # Fedora
  ```
- **Windows/macOS**: Descargar desde [wireshark.org](https://www.wireshark.org/).

> ⚠️ En Linux, agregar tu usuario al grupo `wireshark` para capturar sin root:
> ```bash
> sudo usermod -aG wireshark $USER
> ```

---

## Interfaz Gráfica
![Wireshark UI](wireshark-ui.png) *(Reemplaza con captura real)*

1. **Barra de filtros**: Sintaxis tipo `tcp.port == 443 && ip.src == 192.168.1.1`.
2. **Lista de paquetes**: Muestra número, timestamp, direcciones, protocolo, longitud.
3. **Detalles del paquete**: Jerarquía de capas (Ethernet → IP → TCP → HTTP).
4. **Bytes crudos**: Vista hexadecimal/ASCII.

---

## Filtros Básicos
| Filtro                     | Descripción                          |
|----------------------------|--------------------------------------|
| `http.request.method==GET` | Solicitudes HTTP GET.                |
| `dns.qry.name contains "google"` | Consultas DNS a Google.       |
| `tcp.flags.syn==1 && tcp.flags.ack==0` | Paquetes SYN (inicio TCP). |
| `ip.addr==192.168.1.1`     | Tráfico desde/hacia una IP.         |

---

## Comandos Útiles en Tshark (CLI)
```bash
# Capturar tráfico en interfaz eth0
tshark -i eth0 -w salida.pcap

# Leer un .pcap y filtrar HTTP
tshark -r captura.pcap -Y "http"

# Extraer URLs visitadas
tshark -r captura.pcap -Y "http.request" -T fields -e http.host -e http.request.uri
```

---

## Flujos de Trabajo Avanzados
1. **Reensamblar archivos transmitidos**:  
   *File → Export Objects → HTTP* (para imágenes, ZIPs, etc.).

2. **Mapa de conversaciones**:  
   *Statistics → Conversations* (identifica hosts "ruidosos").

3. **Seguir flujos TCP/HTTP**:  
   Clic derecho → *Follow → TCP Stream* (reconstruye sesiones).

4. **Análisis de rendimiento**:  
   *Statistics → IO Graphs* (visualiza throughput/latencia).

---

## Seguridad y Privacidad
- **Ofuscación de datos**:  
  *Edit → Preferences → Protocols → HTTP → "Uncompress data"* (evita leak de credenciales).
  
- **Filtros para evitar captura sensible**:  
  ```bash
  tshark -i eth0 -f "not port 22" -w segura.pcap  # Excluye SSH
  ```

---

## Recursos
- [Filtros Wireshark](https://wiki.wireshark.org/DisplayFilters)
- [Sample Captures](https://wiki.wireshark.org/SampleCaptures)
- `Ctrl+Shift+P`: Buscar paquetes por protcolo.