# Protocolos
## Transporte de datos
- TCP: Servicio de stream
	- Se establece una conexión y se leen/escriben datos en flujo contínuo de bytes.
	- Similar a escribir un archivo.
- UDP: Servicio datagrama.
	- Se envían paquetes discretos (o mensajes)
	- Cada paquete contiene una colección de bytes independientes y autónomo.

# Datos
- HTTP utiliza el protocolo de transporte de datos TCP
- Normalmente los streams de video o las comunicaciones por voz utilizan servicios datagrama **UDP** por la no importancia de pérdida de paquetes para así priorizar velocidad.
# Puertos 
- Puertos para servicios conocidos son reservados y fijos $2^{10}=1024$:
	- 21 **FTP**
	- 22 **SSH**
	- 23 **Telnet**
	- 25 **SMTP**
	- 80 **HTTP**
	- 443 **HTTPS**
- Puertos **registrados** pueden reservarse (**1024** a **49151**)
- Puertos **dinámicos privados** que no pueden reservarse (**49152** a **65535**)
# Socket
Es una API abstracta. Es un endpoint para programación de red. Endpoint para conexiones en **ambas direcciones**.

## Address Family
- INET -> Protocolo de Internet (IPV4)
- INET6 -> Protocolo de Internet (IPV6)

## Type
- Stream (TPC)
- Datagram (UDP)