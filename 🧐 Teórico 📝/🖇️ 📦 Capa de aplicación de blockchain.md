- Tener en cuenta los videos de YT, aquellos que explican "por encima" el uso de la blockchain. De todo lo que se habló hoy en clases es básicamente el contenido de los videos, i.e Capa de aplicación.
# 🖇️ Protocolos base (Requisitos)
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

---

# 🔮🔗 Ethereum

*Propósito* Diseñada para descentralizar la web, la creación de DApps y contratos inteligentes
*Objetivo* Eliminar intermediarios y proporcionar una plataforma transparente, segura y autónoma para transacciones y acuerdos digitales
*Busca* ser la base de la web 3.0

## Características salientes
1. Contratos inteligentes
2. Descentralización
3. Token nativo
4. EVM
5. Inmutabilidad y transparencia

- Tiempo de transacción de 12 seg

>[!Note] **Mecanismo de consenso** Proof of stack
es el proceso mediante el cual los usuarios bloquean una cantidad específica de Ether (ETH) para participar en la validación de transacciones y la creación de nuevos bloques en la red.


## 🔮🔗 Conceptos básicos
- El **estado de la EVM** es mantenido por todos los nodos.

- **Cada solicitud de transacción** = solicitud de cálculo a la EVM
	- Cualquier usuario puede solicitar un cálculo de la EVM.
	- *Solicitudes de cálculo* se llaman **solicitudes de transacción**
	
- Varios participantes verifican, validan y llevan a cabo la transacción.
- La *ejecución de transacción* cambia el estado de la EVM.

- Cualquier participante que *envíe una solicitud de transacción* debe ofrecer una cantidad de ETH a la red como recompensa
	-  *La red quemará una parte de esta recompensa* y otorgará el resto a quien finalmente realice el trabajo de verificar la transacción, ejecutarla, registrarla en la blockchain y transmitirla a la red. 
	- *La cantidad de ETH pagada corresponde a los recursos necesarios para hacer el cálculo*. Así, nadie puede bloquear la red con cálculos infinitos.

- Las **transacciones y el estado** actual de la EVM se registran en la blockchain.

- **Contrato inteligente** = programa cargado en estado de EVM. Es como un **script** que cuando se usa con ciertos parámetros, realiza acciones o cálculos si se cumplen determinadas *condiciones*

- *Cualquier desarrollador* puede crear un contrato inteligente y hacerlo público en la red, utilizando la blockchain como capa de datos, *a cambio de una tarifa pagada* a la red.

- Usuarios **solicitan ejecución** de contratos inteligentes
- Para **hacer público un contrato** en la red, hay que pagar una tarifa.
- Para que un **usuario** invoque un contrato debe pagar una tarifa.

## 🔮🔗 Cuentas
Tiene saldo en ETH y puede enviar transacciones.
- **Hay dos tipos de cuentas:**
	- *De propiedad externa(EOA)*: Controlada por cualquier persona con clave privada
		- Creación gratuita
		- Pueden iniciar transacciones
		- Transferencias de ETH ó tokens
		- Usan par de clave, pública y privada.
		- Una transacción puede activar un contrato inteligente.
	- *De contrato*: Script de un contrato inteligente implementado en la red
		- Tiene un costo
		- Sólo puede enviar transacciones a causa de haber recibido una
		- Aquí también se pueden activar contratos inteligentes.
		- No hay claves privadas

*Ambos:*
- Reciben, mantienen y envían ETH y tokens
- Interactúan con contratos inteligentes implementados

## 🔮🔗 Informaciones asociadas a las cuentas
- **Nonce** de cuenta: contador de la cantidad de transacciones
	- **Nonce de CC** 
		- **Fragmentos de código**
		- **Llamada de mensajes -> Ejecuta código**
		- **Base de datos de estado** -> Contiene hash para acceso.
		- **La cable privada** se usa para firmar mensajes y transacciones.
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
- El **estado de Ethereum** es una estructura de datos enorme llamado *Merkle Patricia Trie modificada*.

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
	- Distribuyen bloques creados a otros nodos en la red
	- Actualizan el estado global
	- Son recompensados con ETH por producir bloques
## 🔮🔗 Prueba de participación PoS
- Tiempo / Epoch = 32 ranuras
- Ranura = 12 segundos

# 🔮🔗 Parcial
- Dar un escenario para [Algo sobre Ethereum o Bitcoin] (Por ejemplo para validar un nodo)
- Averiguar info.
- Ejercicio de comparación de bitcoin
- Ejemplo de aplicación distribuída donde se pida tomar una decisión de diseño.