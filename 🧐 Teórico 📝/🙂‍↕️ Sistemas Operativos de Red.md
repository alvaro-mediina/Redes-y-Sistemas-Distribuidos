
- La idea de los sistemas operativos de red es que son **necesarios** para resolver problemas en cuanto al desempeño de las redes. Además es el estudio de los **SOR**para la correcta comunicación de las máquinas a través de protocolos.
- Los SOR están construidos de a **capas**. Cada red tiene cierto tipo de capas en los cuales a veces difieren entre unas y otras.

# Tabla de Contenidos
- [[#🙂‍↕️ Jerarquía de protocolos]]
	- [[#📚 Capas]]
	- [[#🙂‍↕️ Protocolo]]
	- [[#📞 Comunicación]]
- [[#🧩 Arquitectura de red]]
- [[#⚠️ Problemas de las redes de computadoras]]
- [[#📚 Capas de un SO de **redes de computadoras**]]
- [[#☁️ Sistema operativo de la **nube**]]
- [[#🚀Sistema operativo para **IoT**]]
- [[#🖇️ Sistema operativo para **Blockchain**]]
# 🙂‍↕️ Jerarquía de protocolos

- Se utilizan **pilas de capas** para reducir la complejidad de los **SOR**.

## 📚 Capas

- Las capas se encargan de proporcionar servicios a las capas superiores.
- Abstracción de cada capa.
- Ofrecen interfaces entre cada capa.
- **La capa n de una máquina sólo se puede comunicar con la capa n de otra máquina.**
- El cómo es la comunicación lo describen los **protocolos.**

## 🙂‍↕️ Protocolo

- Reglas y convenciones usadas en la conversación entre la capa n de una máquina y la capa n de otra máquina.

## 📞 Comunicación

- **Durante el envío de mensaje**: cada capa pasa los datos y la información de control a la **capa inmediatamente inferior**, hasta que se alcanza **la capa más baja**.
- **Durante la recepción de mensaje:** cada capa pasa cierta información conteniendo los datos a la capa inmediatamente superior hasta que alcanza la capa más alta.
- Luego de la capa más baja se encuentra el **medio físico**.
- La capa más alta representa a la **capa de aplicación.**

# 🧩 Arquitectura de red

1. **Capa física - 1** Se envía el mensaje a través de las máquinas en cuanto al mensaje, va perdiendo encabezado a encabezado a medida que sube por las capas.
2. **Capa de enlace de datos - 2** Agrega un terminador y un header a cada pieza. Pasa la unidad resultante a la capa 1 para su transmisión.
3. **Capa de red - 3**:
   - Hay limitaciones en el tamaño de los mensajes en esta capa.
   - Divide en **paquetes** los mensajes que llegan.
   - A cada paquete se le coloca un encabezado.
   - Decide cuál de las líneas que salen usar.
   - Pasa los paquetes a la capa 2.
4. **Capa de transporte - 4**:
   - Pone un encabezado en el mensaje para identificarlo y pasa el resultado a la capa 3.
   - El encabezado contiene **números de secuencia** para que la capa 4 en la máquina de destino entregue los mensajes en órden correcto.
5. **Capa de aplicación - 5** Produce un mensaje y lo pasa a la capa 4 para su **transmisión**, por ejemplo browser, e-mail, chat.

# ⚠️ Problemas de las redes de computadoras

- Hay un tamaño máximo de mensajes en cada tipo de red.
- Un problema es si llega un mensaje demasiado grande a una red, en ese caso el paquete debería **fragmentarse**

## Fragmentación

Hay dos tipos de fragmentación:

- **Transparente**: Inicialmente se realiza una fragmentación por el tamaño grande del mensaje. Luego al final del recorrido se ensamblan los fragmentos para formar un paquete.
- **No transparente**: Si se fragmenta, se refragmenta, luego no se ensamblan los paquetes fragmentados.
## Congestión

- Cuando una red no puede manejar la carga de paquetes que recibe de manera aceptable (esperas inaceptables o pérdida de paquetes)

---

# 📚 Capas de un SO de **redes de computadoras**

## **📚Modelo de referencia TCP/IP**

- **Para la arquitectura de capas que utilizamos las capas 5, 4 y 3 utilizarán el modelo de referencia TCP/IP.**
- **El que utiliza la Internet.**
  **![alt text](/imgs/image.png)**
## **📚 Capa de aplicación**
- **Contiene aplicaciones de red.**
- **Cada aplicación de red ofrece un servicio específico con su propia forma de interfaz con el usuario.**
- **La capa de aplicación en TCP/IP contiene varios protocolos de nivel alto:**
	- **Transferencia de archivos: FTP**
	- **Resolución de nombres de host en sus direcciones de red: DNS**
	- **Para la Web: HTTP**
	- **Etc.**

- **En la web están los sitios web.**
- **También las aplicaciones web, las cuales se acceden por medio de un browser, realizan funciones similiares a las aplicaciones de escritorio.**

## **📚Capa de transporte**
- **Tenemos que la capa de red provee comunicación entre hosts, los paquetes siguen una ruta elegida por la capa de red. Pero con esto no alcanza ya que en la práctica la comunicación ocurre entre procesos.**
- **La capa de transporte provee comunicación entre procesos.**
- **La capa de transporte mejora los servicios de la capa de red.**
- **Se ejecuta por medio de hosts.**
- **Entidad de transporte(ET): sw/hw de la capa de transporte.**

### **Problemas que resuelve**
- **Uso de temporizadores y las retransmisiones de paquetes.** 
- **Uso de búferes y control de flujo.** 
- **Evitar congestionar la red poniendo demasiados paquetes en ella.**
- **Cuando la CR pierde paquetes, la CT puede solucionarlo.**
- **==Si consideramos que hay procesos cliente y procesos servidor , surgen los problemas:==**
	- **El direccionamiento explícito de los destinos.**
## **📚Capa de transporte de INTERNET**
- **PROTOCOLOS**
	- **TCP: Divide el flujo de bytes entrantes en mensajes discretos y pasa cada uno de ellos a la capa de interred.**
		- **TCP proporciona entrega confiable y en orden de los mensajes.**
	- **UDP: Proporciona entrega de mensajes no confiable y desordenada.**
		- **Esto significa que un mensaje puede entregarse con errores, o no entregarse, o varios mensajes pueden entregarse en forma desordenada.**
- **COSAS QUE ==TIENE== TCP ==QUE NO== UDP**
	- **Uso de confirmaciones de recepción para los mensajes.** 
	- **Control de flujo, control de congestión, retransmisiones cuando se recibe mensaje erróneo.**
- **UDP se usa para los siguientes tipos de aplicaciones**
	- **Aplicaciones que no usan el control de flujo ni la secuenciación de mensajes.**
	- **Aplicaciones que involucran consultas de solicitud-respuesta.** 
	- **Aplicaciones de transmisión de voz y video.**
## **📚 Capa de red**
- **Objetivos:**
	- **Algoritmos de almacenamiento y reenvío**
	- **Control de congestión.**
	- **Resolver problemas que surgen cuando un mensaje tiene que viajar por redes de distinta tecnología para llegar a destino.**
	- **Enrutamiento**
- **La capa de red en TCP/IP:**
	- **Capa de interred, permite que los hosts inyecten paquetes dentro de cualquiera de las redes en la interred. Los paquetes diferentes entre dos host viajan a su destino de manera independiente.**
	- **Se utilizan las direcciones IPv4 (32 bits) y IPv6 (128 bits) para la distinción de las máquinas a las cuales se enviarán paquetes**
	- **Se envían paquetes IPv4  o paquetes IPv6, también paquetes IP**
	- **Para el enrutamiento se utilizan algoritmos de enrutamiento.**

## **📚 Capa de enlace de datos**
**Objetivo: transformar un medio de transmisión puro en una línea de comunicación que aparezca libre de errores de transmisión.**
- **Problemas de diseño que se consideran:** 
	- **Fragmentación de paquetes en tramas.**
	- **Tramas de confirmación de recepción.**
	- **Control de flujo.**
	- **Control de acceso a un canal compartido.**
	- **Control de errores.**
## **📚 Capa física**
**Objetivo: transportar un stream de datos de una máquina otra usando medios físicos.** 
- **La CF no consiste solo de medios físicos o los medios físicos se conectan entre sí usando dispositivos como codecs, modems, multiplexores, demultiplexores, etc.**

# ☁️ Sistema operativo de la **nube**

### ☁️ Virtualización
- Provee un servicio de sistemas operativos con un manejo virtualizado abstrayendo de los componentes que corren al SO.
- Permite manejar un sistema operativo completo.
### ☁️ Containerización
- Provee una aplicación abstrayendo al SO.
- Ocupa menos recursos que las máquinas virtuales.
- Están mas limitados a tareas específicas dependiendo la aplicación.
### ☁️ Capa de red
- **Protocolos utilizados**: IP y BGP
- **Protocolos para redes privadas:** VPN, MPLS, Túneles VPN, Conexiones dedicadas.
### ☁️ Capa de infraestructura

- **Protocolos típicos de Internet**: TCP/IP, DNS, HTTPS, etc.
* **Protocolos de capa de transporte:** TCP, UDP.
### ☁️ Capa de almacenamiento

- Distintos tipos de almacenamiento, con distintos protocolos para cada almacenamiento.
- Algunos tipos son:
  - En bloque. TCP/IP
  - De archivos. NFS
  - De objetos. HTTP/HTTPS, REST API.

### ☁️ Capa de plataforma

- Provee las herramientas y servicios de entornos para construir y ejecutar apps.
- Uso de APIs.
- Proporciona a los **programadores**:
	- Facilidades para escribir código, probarlas y desplegarlas.
	- Utilidad: Desligar responsabilidad de configuraciones, gestión de redes, etc.
	- Protocolos: REST - gRPC
### ☁️ Capa de funciones sin servidor

- **Propósito:** Si ocurren eventos, ejecutar funciones.
- No se necesita infraestructura. Es proporcionada por la nube.

### ☁️ Capa de contenedores
- Proporcionar servicios dentro de containers.
- Gestión y orquestación de aplicaciones en la nube.
---
# 🚀Sistema operativo para **IoT**

## 🚀 Diferencia de los protocolos de IoT con Internet
- Muchos dispositivos IoT son de **baja potencia** y tienen **recursos limitados**. Por lo tanto los protocolos para IoT están diseñados para ser **ligeros y eficientes en el uso de energía y recursos.**
- La IoT se enfoca en la comunicación entre **dispositivos IoT heterogéneos en entornos específicos** (p.ej. Hogares inteligentes, fábricas automatizadas, ciudades inteligentes, etc.)
- La internet está diseñada para la **comunicación entre computadoras y servidores**.
- Se necesitan protocolos para escalar a una gran cantidad de dispositivos IoT, gestionando transmisiones de datos frecuentes y a menudo en tiempo real.
- Los protocolos de internet permiten escalar a muchas máquinas y gestionar grandes volúmenes de tráfico de datos, pero **solo para computadoras y servidores, y no para dispositivos IoT.**
- Para las redes **IoT** utilizamos un **modelo de capas de referencia** con las mismas que las redes de computadoras, sólo que con **dos capas más**.
- Las capas **con los mismos nombres** además resuelven problemas adicionales para las **redes IoT**.

### 🚀 Arquitectura
1. Capa de aplicación
2. Capa de procesamiento y almacenamiento | Capa de gestión y orquestación.
3. Capa de transporte.
4. Capa de red.
5. Capa de enlace de datos.
6. Capa física.

### 🚀 Capa física
- Se encarga de la transmisión de bits a partir de medios físicos.
- Sensores y actuadores suelen tener capa física.
- **Problemas que considera
	-  **De conectividad**
	- **Consumo energético**
	- **Interferencias y ruido**
	- **Conectividad**

- **Protocolos**
	- Zigbee
	- LoRaWAN
	- NB-IoT
### 🚀 Capa de enlace de datos
- Responsable de la transmisión entre dispositivos dentro de una misma red local.
- **Problemas considerados:**
	- **Control de errores**.
	- **Control de acceso al medio.**
	- **Retrasos y variaciones en el tiempo de transmisión.**
	- **Desconexiones frecuentes.**
	- **Seguridad de la comunicación**

- **Protocolos**
	- Wi-Fi, Ethernet, Bluethooth
	- Bluethooth Low Energy
	- 6LoWPAN
### 🚀 Capa de red
Gestiona el direccionamiento y el enrutamiento de los datos de diferentes redes.
- **Problemas considerados:
	- **enrutamiento**
	- **escalabilidad**
	- **movilidad en redes inalámbricas**

- **Protocolos:**
	- **De internet: IPv4 e IPv6**
	- 6LoWPAN
	- RPL
### 🚀 Capa de transporte
Asegura la transmisión de datos confiable y ordenada en dispositivos.
- **Problemas considerados:**
	- **Fiabilidad de la transmisión**
	- **Compatibilidad de protocolo**
	- **Control de flujo y control de congestión**

- **Protocolos**
	-  **De internet**: **TCP, UDP**
	- MQTT
	- **CoAP**

### 🚀 Capa de procesamiento y almacenamiento
Es responsable de procesar, almacenar y analizar los datos recopilados por los dispositivos IoT.
- **Problemas considerados:**
	- **Procesamiento en tiempo real**
	- **Almacenamiento masivo**

### 🚀 Capa de gestión y orquestación
Se encarga de la gestión y orquestación de los recursos en la red IoT
- Proporciona herramientas para la configuración, monitoreo, actualización y administración de dispositivos y aplicaciones IoT.
- **Problemas considerados:**
	- **Configuración y monitoreo**
	- **Actualización de firmware**

- **Protocolos:**
	-  LwM2M

### 🚀 Capa de aplicación
Define los protocolos de comunicación usados por las aplicaciones de IoT. Facilita el UX.

- **Problemas considerados:**
	-  **Interoperatibilidad**
	- **Seguridad y privacidad**
	- **Gestión de dispositivos**
	- **Eficiencia energética**
	- **Fiabilidad y calidad de servicio**
	- **Escalabilidad y ancho de banda**
	- **Simplicidad**
	- **Complejidad**

- **Protocolos:**
	- **De la web**: HTTPS, HTTP
	- **MQTT**
	- **CoAP**
	- **WebSockets**
	- **DDS**
	- **XMPP**


---
# 🖇️ Sistema operativo para **Blockchain**
Para este tipo de red se utilizará un **modelo de referencia**.

## 🖇️ Capa de infraestructura base
- Proporciona infraestructura subyacente para la creación y operación de las blockchains.
- Incluye componentes físicos y de red.
- Pej: Internet (TCP/IP, HTTP, SSL, etc)
- Pej: enrutadores.
## 🖇️ Capa de protocolo base
- Es la **blockchain** en sí misma.
- Tiene su propia **cadena de bloques** con un diseño en específico, con su propio token nativo.
- Responsable de la **seguridad y el funcionamiento operativo** de la red blockchain.
- Establece **reglas fundamentales de consenso** y la estructura de datos principal.
	- Los nodos llegan a un acuerdo a través de las reglas de **consenso** sobre el estado del libro mayor.
	- Usar **reglas de consenso** proviene el **doble gasto**. Garantiza que sólo una versión del libro mayor sea aceptada por todos los nodos.
	- Aumenta la **resistencia a ataques maliciosos**.
- Facilita la comunicación entre los nodos y el envío entre las **transacciones**.

### 🖇️ Protocolos
- Bitcoin (PoW)
- Ethereum (PoS)
- Cardano (PoS)
- Solano (Combina PoS y PoH)
### 🖇️ Ejemplos de mecanismos de consenso
- Prueba de participación (PoS)
- Prueba de trabajo (PoW)
- Prueba de historia (PoH)

### 🖇️ Limitaciones
- Capacidad de procesar muchas transacciones por segundo.
- Esto resulta en tiempos de espera prolongados y tarifas elevadas.
- Para ello... **soluciones de escalabilidad.**
## 🖇️ Capa de comunicación entre blockchains

Aborda problemas de **interoperabilidad** y **escalabilidad**.

### 🖇️ Protocolos
- Se usan protocolos que facilitan la **interoperabilidad** y la **comunicación** entre diferentes redes blockchain.
### 🖇️ Ejemplos
- Polkadot.
- Cosmos
- Avalanche
- LayerZero
- Wormhole

## 🖇️ Capa de soluciones de escalabilidad
- Mejora el rendimiento y la capacidad de procesamiento de transacciones al construirse sobre una blockchain existente.
- **Permiten realizar un mayor número de transacciones** fuera de la cadena principal.
	- Esto reduce la carga sobre la blockchain y disminuye los costos asociados.
	- Se procura no comprometer la seguridad proporcionada por la blockchain.

### 🖇️ Protocolos
- Rollups
- Cadenas laterales
- Canales de estado.

### 🖇️ Ejemplos
- Lighting Network (Bitcoin): canales de estado 
- Polygon: cadenas laterales y rollups
- Arbitrum (Para Ethereum): usa rollups


## 🖇️ Capa de aplicaciones
- Resuelve problemas adicionales típicos de una blockchain.
- Permite la ejecución y acceso a las aplicaciones que interactúan con la blockchain.
- Aquí actuan tanto aplicaciones descentralizadas como no descentralizadas.
- Actúan los **contratos inteligentes**
	- Son **inmutables** y **transparentes**.
	- Minimizan el riesgo de error humano
	- Gestionan transacciones complejas.

### 🖇️ Ejemplos
- Finanzas descentralizadas - DeFi
	- Lido, Aave, Curve Finance, Compound.
- Gestión de cadenas de suministro: rastrean productos a lo largo de  una cadena de suministro.
- Redes sociales: CyberConnect, Lens Protocol
- Votación
## 🖇️ Capa de desarrollo
- Proporciona las herramientas necesarias para desarrollar y desplegar aplicaciones sobre blockchain.

### 🖇️ Tecnologías a usar
- APIs: APIs RESTFUL
- Librerías: Web3.js, Ether.js
- Plataformas de desarrollo: Ethereum, EOS, NEO
- Frameworks: Embark.

### 🖇️ Lenguajes de programación
- C++
- Go
- Python
- JavaScript
- Solidity

# ✋🏽Convenciones a respetar
