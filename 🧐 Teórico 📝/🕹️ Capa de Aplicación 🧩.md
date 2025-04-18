# Tabla de Contenidos


# Definiciones importantes
## MIME: Extensiones Multipropósito de Correo Internet
- Formato de los mensajes de correo en internet.
- Utilizado para los mensajes de correo que se envían a través de internet, así como para describir contenido para otras aplicaciones, como la navegación web.
- Utiliza formato **RFC 822** agregando una estructura al cuerpo de mensaje y definiendo reglas de codificación para mensajes que no son del tipo ASCII.
- Desde imágenes, videos, binarios, mensajes con caracteres no ASCII hasta archivos.
- Los mensajes que en su encabezado no contenga **MIME-Version** es sólo un texto plano en inglés.

## Codificación a base64
- Codificación ASCII de datos binarios.
- En este esquema se dividen grupos de 24 bits en cuatro unidades de 6 bits, y cada unidad se envía como un carácter ASCII legal. La codificación es “A” para 0, “B” para 1, etc., seguidas por las 26 letras minúsculas, los 10 dígitos y, por último, 1 y / para el 62 y 63, respectivamente. Las secuencias 55 e 5 se usan para indicar que el último grupo contenía sólo 8 o 16 bits, respectivamente
- La codificación a base64 es algo ineficiente si se trata de mensajes completamente ASCII y con algunos No ASCII
---
# 📊Arquitecturas de aplicaciones de red
- Qué es una arquitectura para aplicaciones de red
- Importancia de usar una arquitectura de red

---
## 📊Arquitectura cliente-servidor

- **Dos procesos que se comunican**: uno en la máquina cliente y otro en la máquina servidor.
- **Forma de la comunicación**:
	1. El proceso cliente manda **solicitud** al proceso servidor.
	2. El proceso cliente **espera un mensaje de respuesta**.
	3. El proceso servidor recibe y procesa la solicitud.
	4. El proceso servidor manda mensaje de **respuesta** al proceso cliente.
### Características de los servidores
- Siempre están en un host con dirección IP **permanente**.
- Se pueden usar centros de datos para escalabilidad.

### Características de los servidores
- Pueden estar conectados **intermitentemente** usando direcciones IP dinámicas.
- Los clientes no se comunican directamente entre sí.

### Pasos de una aplicación cliente-servidor usando UDP
1. Cliente crea datagrama con IP y puerto del servidor y envía datagrama.
	- Datagrama puede perderse.
2. Si llega, el servidor lee el datagrama.
3. Servidor envía respuesta especificando dirección y puerto del cliente.
	- Datagrama puede perderse.
4. Si llega, cliente lee datagrama.
5. Cliente finaliza.
- **Evaluación**:
	- No se dice qué se hace si respuesta no llega al cliente.
	- Es responsabilidad de la aplicación de red manejar esto.
### Pasos de una aplicación cliente-servidor usando UDP
1. Se ejecuta proceso servidor.
2. Servidor espera por pedido de conexión entrante.
3. El cliente requiere pedido de conexión al servidor.
4. El servidor acepta la conexión con el cliente.
5. El cliente envía pedido al servidor.
6. El servidor lee el pedido.
7. El servidor envía la respuesta.
8. El cliente lee la respuesta.
	- TCP provee transferencia de stream de bytes ordenada.
9. EI hay más pedidos al servidor: GOTO 5
10. El cliente cierra la conexión.
11. El servidor cierra la conexión.

>[!Note] Cliente-Servidor VS P2P
> ¿Cuánto tiempo se requiere para distrubuir un archivo **(de tamaño F)** de un servidor a N compañeros?
> 
> Se deben considerar los siguientes parámetros:
> - Tasa de subida del **enlace de acceso al compañero **
> - Tasa de subida del **enlace de acceso al servidor**
> - Tasa de descarga del **enlace de acceso al compañero** 
> - Tamaño del **archivo a ser distribuido**
> - Número de **compañeros que quieren adquirir una copia del archivo**
> 
> 
> El **tiempo de distribución** es el tiempo que toma obtener una copia del archivo por los N compañeros.
> 	Asumiendo que la internet **tiene abundante ancho de banda** y todos los cuellos de botella suceden en ISP de acceso.
> 	Asumimos que los servidores y clientes **no participan** de otras aplicaciones red.
> 

---
## 📊Arquitectura Peer to Peer
- Compañero a compañero
### Ejemplos de aplicaciones P2P
- **Distribución de archivos**: BitTorrent
- **Bases** **de** **datos** **distrubuídas**.
- **Streaming**: KanKan
- **VoIP**: Skype

### Distribución de archivos
- Al comienzo de la distribución: 
	- **sólo el servidor tiene el archivo.**
- Para que la comunidad de compañeros reciba este archivo:
	- **el servidor debe enviar cada bit del archivo al menos una vez en su enlace de acceso.**
- En P2P cada compañero puede redistribuir cualquier porción del archivo que ha recibido a cualesquiera otros compañeros.
	- **Así los compañeros asisten al servidor en el proceso de distribución.
	- **Cuando un compañero recibe algo de datos de un archivo, puede usar su capacidad de subida para redistribuir los datos a otros compañeros.**
- La capacidad total de subida del sistema es:$$U_{total} = U_s + \sum{U_i}$$
- Por lo tanto el **tiempo mínimo de distribución es:** $NF/U_{total}$ 
	- Donde 
		- $N:=$ Número de **compañeros que quieren adquirir una copia del archivo**
		- $F:=$ Tamaño del archivo a ser distribuido
		- $U_{total}:=$ suma entre $U_s$ y la tasa de subida del enlace de acceso al peer.
		- $U_s:=$ Tasa de subida del enlace de acceso al servidor

---
## 📊Arquitectura Orientada a servicios
-  Se clasifican en **requisitos funcionales** y **no funcionales**
- Organiza las aplicaciones en **servicios reutilizables** que se comunican entre sí a través de un bus de servicios.
	- Cada servicio realiza una función específica y puede ser usado por diferentes aplicaciones.
- **Los servicios se comunican entre sí** usando patrones como: solicitud-respuesta, publicar-suscribir o enviar-olvidar.
- **Los servicios son modulares** y pueden actuar tanto como clientes como servidores dependiendo del contexto.

- **Nodos(roles):
	- **Servicios independientes
	- **Bus de servicios empresarial (ESB)**
	- **Clientes**
- **Mensajes de comunicación:**
	- Clientes a ESB
	- ESB a servicios
	- Servicios a ESB
	- Servicios entre sí

## 📊Microservicios
-  Se clasifican en **requisitos funcionales** y **no funcionales**
- Utilizada para proporcionar funciones únicas y bien definidas, complejas y eficientes.
- Su clasificación **no funcional** es similar a la de servicios comprendida por: **escalabilidad, resiliencia, flexibilidad, independencia, autonomía y mantenibilidad**


---
#  🌍🔗 Protocolos de aplicaciones de red
## 🌍🔗 Detalles de los protocolos de aplicaciones de red
##  🌍🔗 Protocolo de transferencia de archivos FTP
- Arquitectura cliente-servidor
- Utilizado para transferir archivos desde/hacia host remoto.
- Cada archivo tiene restricciones de acceso y posesión.
- FTP permite inspeccionar carpetas.
- FTP permite mensajes de control textuales.
- Maneja el puerto 21
- Se realizan dos conexiones de un cliente con el servidor.
- Utiliza **tres tipos de mensaje al intercambio**:
	- Comandos
	- Mensajes de respuesta -> A los comandos recibidos
	- Mensajes de datos enviados -> Archivo
###  🌍🔗 Sintaxis de los comandos FTP

# 🌐🕸️ Tecnologías de implementación
## 🌐🕸️ La web
- Es algo global (Accesible por todo el  mundo)
- Permite acceder a datos, información y conocimiento y acceder a ciertos servicios y a ciertas tareas.
- Funciona diferente de las aplicaciones de escritorio.
- No necesita instalar aplicaciones.
## 🌐🕸️ Páginas web
## 🌐🕸️ Navegadores web
- No todas las páginas contienen HTML.
- Cuando un navegador recibe una página no necesariamente es de este tipo. Para ello, el navegador sabe de qué tipo se trata a través de lo que viene con la consulta al servidor, el **tipo MIME de la página**.
- Las páginas del tipo `text\html` se despliegan al toque.
- Si el **tipo MIME** no está integrado en el **browser** entonces:
	1. Se consulta a la tabla de tipos MIME que asocia al mensaje con un **visor**.
	2. Los visores pueden ser **plugins** o **aplicaciones auxiliares ****

### 🌐🕸️ Plugins
- Módulo de código que extienden funcionalidades.
- Se ejecutan dentro del browser.
- Los plugins tienen acceso a la página actual y pueden modificar su apariencia.
- Una vez que el plugin ha completado su trabajo se lo elimina de la memoria del browser.

- **INTERFAZ DEL NAVEGADOR**: Conjunto de procedimientos del navegador que el plugin puede llamar. **Ej:** Asignar memoria, Liberar memoria, desplegar un mensaje, etc.
- **INTERFAZ DEL PLUGIN**: Conjunto de procedimientos del plugin que el navegador puede llamar. **Ej:** Utilidad que sea necesaria para cierta particularidad que necesite el browser.
### 🌐🕸️ Aplicaciones auxiliares
- Se ejecutan en un proceso separado del browser.
- No ofrecen interfaz al navegador ni usan servicios de este.
- Suelen aceptar el nombre de un archivo, lo abren y lo despliegan.
- **Ejemplo:** El browser no tiene visor de PowerPoint y acude a una aplicación auxiliar (en particular al mismo Power Point) PowerPoint process inicia, consume el nombre del archivo y lo despliega.

## 🌐🕸️ Servidores web
- Se lo puede ver como una computadora que almacena **software del servidor web y archivos** como documentos HTML, imágenes, videos, scripts, etc.
- Cada solicitud de página estática requiere un acceso al disco para obtener el archivo.
	- Ineficiente si es que se llegase a pedir innumerables veces el archivo.
	- Se utiliza una **cache** de páginas estáticas en la memoria.

- Se utiliza **multi-threading** para el manejo de múltiples solicitudes a un archivo/distintos archivos realizadas por múltiples clientes.

## 🌐🍪 Cookies
 - El problema de persistir en sesiones de una página web se solucionan con **cookies**. Es como una especie de IP para localizar tu información entre sesiones web.
 - Puede contener **5 campos**:
	 -  **Dominio**: De dónde viene la cookie
	 - **Ruta**: es una trayectoria en la estructura del directorio del servidor que identifica qué partes del árbol de archivos del servidor pueden utilizar la cookie.
	 - **Contenido**: toma la forma nombre = valor. Tanto nombre como valor pueden ser lo que el servidor desee. Este campo es donde se almacena el contenido de la cookie.
	 - **Expiración**: especifica cuándo caduca la cookie. Si este campo está ausente, el navegador la descarta al salir. Tal cookie se conoce como **cookie no persistente**. Si se proporciona una hora y una fecha, se dice que la cookie es persistente y se mantiene hasta que expira.
	 - **Seguro**: indica que el navegador sólo puede regresar la cookie a un servidor mediante un transporte seguro, es decir, SSL/TLS
- Uso:
	- Justo antes de que un navegador solicite una página a un sitio web, verifica su directorio de cookies para ver si el dominio al que está solicitando la página ya colocó alguna cookie. De ser así, todas las cookies colocadas por ese dominio, y sólo ese dominio, se incluyen en el mensaje de solicitud. Cuando el servidor las obtiene, puede interpretarlas de la forma que desee.
	- **Con solo recibir cookies no alcanza**, es necesario almacenarlas. Por ello se utiliza un directorio de cookies en el disco duro de la máquina del cliente.

## 🌐🕸️ Aplicaciones Web

# 🌍🔗 Protocolos para la web

## 🌍🔗 Cosas que se necesita que soporte un protocolo para la web

- Pedido de páginas, de objetos, o de ejecución de programas que generan páginas.
- Manejo del estado de sesión.
- Poder mantener el sistema de archivos del servidor web.
- Recepción de páginas por un browser.
- Seguridad.
- Feedback adecuado cuando no se puede responder a los pedidos.
- Comunicación confiable.

## 🌍🔗 HTTP
- **Hyper Text Transfer Protocol**
- Generalmente opera sobre TCP en el puerto 80.
- Los encabezados de solicitud-respuesta se proporcionan en ASCII 
- Transfiere páginas de servidores web a navegadores y manda pedidos de navegadores a servidores web.
- Tipos de mensajes soportados por HTTP:
	- HTTP-Request (de browser a servidor)
	- HTTP-Response (de servidor a browser)
## 🌍🔗 Conexiones HTTP
- **RTT**: Tiempo necesario para que un paquete pequeño viaje del cliente al servidor y dé de regreso.
> [!Note] Tiempo de respuesta de HTTP no persistente para recibir un archivo
> - Un RTT para iniciar la conexión TCP.
> - Un RTT para el pedido HTTP y el regreso de los primeros bytes de la respuesta HTTP.
> - Tiempo de transmisión de un archivo.
> - Tiempo de respuesta de HTTP no persistente = 2RTT + Tiempo de transmisión del archivo.
		
## 🌍🔗 Pedidos HTTP
- Información que debería tener un mensaje de pedido:
	- En caso de que se requiera pedir una página:
		- **URL** del documento.
		- **Especificación de programa que genera una página web**.
		- **Tipo de acción** (Meter páginas, borrar páginas, etc)
		- Enviar **información sobre la máquina/software del cliente** para que el servidor web pueda retornar páginas adecuadas al cliente.
		- Mandar **información de estado de sesión** para que el servidor se entere. 
		- **Restricciones sobre el tipo de páginas** que el cliente puede aceptar.

- El **tipo de acción** para un pedido HTTP viene de la mano de métodos HTTP como (PUT, DELETE, POST, GET, TRANCE, CONNECT, OPTIONS)

- Se necesita enviar información diversa a un cliente, por ende se debe indicar el tipo de información de que se trata y luego la información en sí. **Se utilizan headers de pedidos**.
## 🌍🔗 Respuesta HTTP
- Un mensaje de respuesta es aquel que devuelve el servidor tras la solicitud de un cliente.
- La información que debería tener un mensaje de respuesta es:
	- Feedback adecuado sobre el pedido realizado.
	- Documento solicitado.
	- Información sobre el tipo de documento enviado.
	- Información de estado de sesión.
- Para especificar la respuesta HTTP se utiliza **un código**(de tres dígitos)  seguido de **un mensaje**
- Para mandar además de la página solicitada/datos solicitados información adicional en una respuesta HTTP se usan **encabezados de respuesta** que son pares: (nombre de encabezado, valor)

- Los **encabezados** pueden ser de pedido, de respuesta o ambos tipos.
- Se usan para:
	- **Proveer información**.
	- **Fijar restricciones**.
	- **Proveer información de eventos**.
	- **Proveer datos de la sesión**.

Algunos encabezados:
- **User-Agent** permite que el cliente informe al servidor sobre la implementación de su navegador (por ejemplo, Mozilla/5.0 y Chrome/5.0.375.125). Esta información es útil para que los servidores puedan ajustar sus respuestas para el navegador.
- **Accept**, los cuatro encabezados indican al servidor lo que el cliente está dispuesto a aceptar en caso de que tenga un repertorio limitado de lo que es aceptable.
- **Host** da nombre al servidor. Se utiliza porque algunas direcciones IP pueden proporcionar varios nombres DNS y el servidor necesita una forma para saber a qué host debe entregar la solicitud.
- **Authorization** es necesario para páginas que están protegidas. En este caso, tal vez el cliente debe probar que tiene permiso para ver la página solicitada
- **Set-Cookie** es la forma en que los servidores envían cookies a los clientes. Debe guardar la cookie y regresarla en las solicitudes posteriores al servidor, mediante el uso del encabezado **Cookie**.

En la comunicación request-response de browser al servidor, cuando se utilizan cookies, normalmente se tienen los encabezados:
- **HOST**
- **USER-AGENT**
- **ACCEPT**
- **CONNECTION**

# 🌍🔗HTML

---
# 🖇️ 📦Capa de aplicación de blockchain
 - Tener en cuenta los videos de YT, aquellos que explican "por encima" el uso de la blockchain. De todo lo que se habló hoy en clases es básicamente el contenido de los videos, i.e Capa de aplicación.
## 🖇️ Protocolos base (Requisitos)
-  **Registro de transacciones**: Capacidad de almacenar transacciones. 
- **Consistencia del estado del sistema**: Todos los participantes poseen el estado actual del sistema.
- **Descentralización**: Operación sin autoridad central que controle el sistema.
- **Inmutabilidad**: Una vez que las transacciones se agregan al registro, no pueden ser modificados ni eliminados.
- **Seguridad**: Protección ante alteraciones y accesos no autorizados.
- **Transparencia**: Todos los participantes deben poder ver y verificar las transacciones y los datos.
- **Consenso**: Los nodos de la red deben acordar la validez de grupos de transacciones antes de agregarlas al registro.
- **Escalabilidad - Privacidad - Rendimiento - Resiliencia  - Blockchain**

## 🖇️📦 Cadenas de bloques
- Un bloque está estructurado por:
	- *Encabezado*: Contiene metadatos, hash del bloque anterior, Nonce y Timestamp
	- *Cuerpo del bloque*: Almacena las transacciones realizadas.
- **Nonce**: Número aleatorio usado durante la minería para encontrar un hash válido.
- **Timestamp**: Marca temporal indicando la creación del bloque. Proporciona un orden cronológico.

## 🖇️ Mecanismos de consenso
- **Proof of Work**: Nodos mineros que compiten por resolver problemas criptográficos complejos. El primero en resolverlo valida un bloque y recibe recomensas.
- **Proof of Stack**: Nodos validadores que son elegidos según su participación en la red. Verifican si las transacciones dentro de un bloque propuesto son válidas y cumplen con las reglas de red. Luego de validar las transacciones, los nodos validadores **crean nuevos bloques** y se repite el proceso tal que otros nodos validadores validan el nuevo bloque, si todo OK entonces se agrega a la blockchain y se reciben recompensas
- **Delegated Proof of Stack**
- **Byzantine Fault Tolerance**


# 🖇️🪙 Bitcoin
## 🖇️ 🪙Características 
- **Blockchain pública**: cualquiera puede unirse a la red, ejecutar un nodo y verificar transacciones.
- **Permissionless**: No requiere permisos para participar como usuario, minero o nodo.
- **Proof of Work**: Si se quiere añadir un bloque a la blockchain, se debe resolver un problema de matemáticas complejo que conlleva mucho cómputo.
- **Oferta limitada**: Solo hay 21 millones de bitcoins.
- **Estructura de incentivos**: 
- **Tiempo de bloque**: Aproximadamente 10 minutos en promedio para minar un nuevo bloque.
- **Transferencia de valores:** Permite el envío y recepción de bitcoins de manera rápida y segura entre pares, sin intermediarios como bancos.
- **Almacenamiento de valor:** Debido a su oferta limitada y su seguridad,  Bitcoin es considerado como una reserva limitada como el oro.
- **Pagos internacionales:** Facilita el pago internacional
- **Seguridad y verificación de transacciones:** Usa un sistema público y transparente para evitar fraudes y dobles gastos.
- **Bitcoins script:** Soporta contratos inteligentes básicos a través de su lenguaje de scripting aunque con restricciones para mantener su seguridad.

## 🖇️🪙 Usuarios
- Cada usuario tiene un **par de claves**.
- **Clave privada**: No compartida en la red.
- **Clave pública**: Compartida en la red.

## 🖇️🪙 Tipos de nodos/bloques 
- Completos
- Mineros
- Ligeros
- Supernodos
### 📦 Completos
Validan y transmiten transacciones y bloques.
Mantienen copia completa de la blockchain.
### 📦 Mineros
Crean nuevos bloques a través de la minería.
### 📦 Ligeros
Verifican transacciones usando información resumida.
Obtienen información necesaria de los nodos completos.
Consultan, envían y reciben saldos en BTC
### 📦 Supernodos
Actúan como hubs(lobby) de alta capacidad, conectándose a muchos otros nodos y facilitando la distribución de los datos.


## 🖇️🪙 Partes de un Nodo/Bloque
### 📦  **Encabezado**:
- Contiene al **Hash del bloque**, **Metadatos**, **Hash del bloque anterior**, **Merkle Root**
-  Cada vez que hay una actualización en el bloque se cambia el hash.
- **Merkle Root**: hash que resume todas las transacciones dentro del bloque. Las *transacciones* en un bloque se organizan de a pares, la cual se aplica SHA256 a cada par, luego el conjunto de todos los pares hasheados se vuelve a hashear hasta obtener un *merkle root*.
### **📦 Cuerpo del bloque**
- Almacena las transacciones realizadas.
- **Hash del bloque**: Identificador único del bloque generado mediante un **algoritmo criptográfico**
- Cada bloque tiene:
	- **Hash del bloque anterior**
	- **Hash del bloque posterior**
- Se usan mecanismos de consenso para asegurar que los nodos acuerden validez de los nuevos bloques.

## 🖇️🪙 Funciones Hash
- Se aplican a bloques y a transacciones.
- Cada bloque y transacción en la red se **identifica** mediante un hash único. En este caso suele ser SHA-256 (Secure Hash Algoritm 256)

## 🖇️🪙 Minería de Bitcoin
1. Los mineros agrupan las transacciones pendientes dentro de un nodo candidato.
2. Se crea un encabezado para el bloque.
	- Hash del bloque anterior, Merkle root y Nonce.
3. Se aplica dos veces SHA256 al encabezado del bloque.
4. Si el hash obtenido no cumple con los requisitos de dificultad establecidos por la red, el nonce se incrementa aleatoriamente y se repite el proceso hasta encontrar un hash válido.

> [!Danger]  Se cambia el número de doble hash cada un cierto tiempo

>[!note] ### 🖇️🪙 Validez de un bloque
> - El doble hash del bloque debe tener un número específico de *ceros* iniciales.
> - La cantidad de ceros se ajusta periódicamente.
> 	- Cuantos más ceros se requieren más complejo es el minado.
> - Antes de agregar un nuevo bloque se debe validar que los mineros invirtieron cierto poder de cómputo.

5. Una vez encontrado un hash válido, el minero difunde el nuevo bloque a la red.
6. Los nodos verifican el trabajo realizado y añaden el bloque a la blockchain.
7. Los otros nodos mineros que estaban tratando de crear sus bloques válidos pierden el trabajo realizado hasta ese momento.
8. El minero recibe una recompensa en **bitcoins** por su trabajo, así como las tarifas de las transacciones incluidas en el bloque.
## 🖇️🪙 Problema
*Dos nodos mineros generan un bloque válido al mismo tiempo.*
- Se agregan ambos bloques por diferentes nodos completos a su blockchain local
- El siguiente minero en encontrar un bloque válido lo añadirá a la cadena que está usando.
- La cadena que se extiende más rápido se convierte en la principal.
- El bloque que no fue extendido se convierte en un bloque huérfano y es descartado.
- Los nodos con cadena más corta la abandonan y se pasan a la cadena más larga.
- El minero cuyo bloque se convierte en huérfano no recibe la recompensa por su trabajo.

## 🖇️🪙 Problema
*Hay que garantizar **autenticidad, integridad, no repudio, seguridad y verificación descentralizada***
### 🖇️🪙 Firma digital
Creada a partir de datos de transacción. Es única para cada transacción.
- La clave privada de usuario se usa para **firmar transacciones** y demostrar propiedad de BTC.
- La clave pública se usa para verificar la firma.

	*Visto de otro modo:* La firma digital es un hash de la transacción cifrada con la clave privada del usuario.

- **Verificación de la firma**: Si los nodos de la red utilizan la clave pública del remitente para descifrar la firma digital y coinciden con el hash de la transacción, es válido.

### 🖇️🪙Ejemplo Firma digital
1. **Alice** quiere enviar 1 Bitcoin a *Bob*. Alice crea una transacción 
2. Alice usa su clave privada para generar una firma digital de la transacción. 
3. **Alice** transmite la transacción firmada a la red Bitcoin.
4. Los nodos de la red usan la clave pública de **Alice** para verificar la firma digital y asegurarse que la transacción no ha sido alterada y que **Alice** es la legítima propietaria de los fondos.


## 🖇️ 🪙 Escenarios
### 🖇️ 🪙 Escenario 1: Envío y validación de una transacción
1. Usuario envía transacción a *nodo completo*.
2. *Nodo completo* verifica la validez de la transacción recibida (p.ej. que el remitente tiene suficientes fondos). Luego difunde la transacción a otros *nodos completos* y *supernodos*. 
3. *Supernodo* retransmite transacción recibida de nodo completo a muchos otros nodos completos y ligeros a los que está conectado. 
4. Nodo ligero recibe transacción de supernodo, la verifica usando información resumida, si la verificación es exitosa, la acepta. 
5. Nodo minero: recibe la transacción del nodo completo o supernodo. Incluye la transacción en un bloque candidato y empieza a minar. 
6. Nodo complete y supernodo: continúan propagando la transacción a otros nodos en la red hasta que todos la hayan recibido.

### 🖇️ 🪙Escenario 2: Minería y propagación de un nuevo bloque
1. **Nodo de minería**: Resuelve problema criptográfico y crea un nuevo bloque con las transacciones recientes. o Difunde el nuevo bloque a un nodo completo. 
2. **Nodo completo**: verifica la validez del bloque recibido (o sea, que el bloque sigue las reglas de consenso y no contiene transacciones inválidas.) 
	- Si el bloque es válido, lo agrega a su blockchain
	- Difunde el bloque a otros nodos completes y supernodos
3. **Supernodo**: recibe y verifica bloque que recibió del nodo completo, y si todo está bien lo añade a su copia de la blockchain.
	- Retransmite el bloque a muchos otros nodos completos y ligeros a los que está conectado. 
4. **Nodo ligero**: recibe bloque del supernodo y verifica el bloque usando la cabecera del mismo y la cadena de bloques resumida.
	- Si es válido, almacena su información resumida.

### 🖇️ 🪙Escenario 3: Respuesta a un ataque de doble gasto
1. **Usuario malicioso**: envía dos transacciones conflictivas (doble gasto) a diferentes nodos completos. 
2. **Nodo completo 1**: recibe la primera transacción y la verifica. Difunde esa transacción a otros nodos completos y supernodos. 
3. **Nodo completo 2**: recibe la segunda transacción conflictiva y la verifica. Detecta el conflicto con la primera transacción; rechaza la segunda transacción y no la difunde.
4. **Supernodo**: recibe la primera transacción válida del nodo completo 1 y le difunde a otros nodos. 
5. **Nodo de minería**: recibe la primera transacción válida y la incluye en un bloque candidato. Si la segunda transacción llega después de la primera y detecta el conflicto y la rechaza.

d
# 🔮🔗 Ethereum
- Es la base de la web 3.0
- dApps = contrato ingeligente + front-end
- Token nativo ETH
- Contratos inteligentes
- Máquina virtual de Ethereum
- Tiempo de transacción de 12 seg
## 🔮🔗 Conceptos básicos
- El **estado de la EVM** es mantenido por varios nodos.
- **cada solicitud de transacción** = solicitud de cálculo a la EVM
- Varios participantes verifican, validan y llevan a cabo la transacción.
- La ejecución de transacción cambia el estado de la EVM.
- Las **transacciones y el estado** actual de la EVM se registran en la blockchain.
- **contrato inteligente** = programa cargado en estado de EVM.
- Usuarios **solicitan ejecución** de contratos inteligentes
- Para **hacer público un contrato** en la red, hay que pagar una tarifa.
- Para que un **usuario** invoque un contrato debe pagar una tarifa.
## 🔮🔗 Cuentas
Tiene saldo en ETH y puede enviar transacciones.
- Hay dos tipos de cuentas:
	- De propiedad externa:
		- Creación gratuita
		- Pueden iniciar transacciones
		- Transferencias de ETH
		- Usan par de clave, pública y privada.
		- Una transacción puede activar un contrato inteligente.
	- De contrato
		- Tiene un costo
		- Aquí también se pueden activar contratos inteligentes.
		- No hay claves privadas
	
## 🔮🔗 Informaciones asociadas a las cuentas
- **Nonce** de cuenta: contador de la cantidad de transacciones
	- **Nonce de cc** 
		- **Fragmentos de código**
		- **Llamada de mensajes -> Ejecuta código**
		- **Base de datos de estado** -> Contiene hash para acceso.
		- La cable privada se usa para firmar mensajes y transacciones.
			- Es de 64 caracteres hexadecimales o 128 bits
		- La cable pública se genera a partir de la clave privada utilizando un algoritmo
		- **Dirección de cuenta** = últimos 20 B del hash de la clave pública.
	- **Nonce de CPE:
		- A partir de una firma se puede **derivar la clave pública**.
		- Las cuentas de contrato tienen **dirección de 42 caracteres hexadecimales**
- **Balance de cuenta**: cantidad de wei = fracción de ETH. 1 e18
- **Billetera:** Interfaz o app para interactuar con una cuenta CPE o CC
- **Transacción**: Instrucción firmada proveniente de cuenta.
	- **Ejemplo:** Transferir ETH de una cuenta a otra.
	- Las CPE inician transacciones.
	- Una transacción se ejecuta en la EVM a pedido de un nodo.
## 🔮🔗 Máquina virtual de Ethereum
- Máquina de pila de 1024 elementos.
- Cada elemento es una palabra de 256 b
- Es un **entorno virtual descentralizado** que ejecuta código en los nodos.
- El **estado de Ethereum** contiene todas las cuentas y balances y el estado de la máquina.
- Contiene reglas para cambiar el estado del bloque.
- El **estado de Ethereum** es una estructura de datos enorme.

## 🔮🔗 Nodos
- Nodo = Instancia de software cliente de Ethereum conectado a otras máquinas.
- Cliente = **verifica los datos** según las reglas de Ethereum
	- **de consenso**: implemente el consenso PoS.
	- **de ejecución:** escucha las transacciones, las ejecuta en la EVM y mantiene el estado más reciente del estado y la BD.
- N-**Completos**:
	- Validan bloques y estados
	- Mismos conceptos que antes
- N-**Ligeros**
- N-**Archivo**
- N-**Validadores**:
	- Crean bloques
	- Proponen bloques.
	- ....
## 🔮🔗 Prueba de participación PoS
- Tiempo / Epoch = 32 ranuras
- Ranura = 12 segundos

# 🔮🔗 Parcial
- Dar un escenario para [Algo sobre Ethereum o Bitcoin] (Por ejemplo para validar un nodo)
- Averiguar info.
- Ejercicio de comparación de bitcoin
- Ejemplo de aplicación distribuída donde se pida tomar una decisión de diseño.