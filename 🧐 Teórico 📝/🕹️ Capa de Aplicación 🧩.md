# Tabla de Contenidos

# 📊Arquitecturas de aplicaciones de red
- Qué es una arquitectura para aplicaciones de red
- Importancia de usar una arquitectura de red
## 📊Arquitectura cliente-servidor
## 📊Arquitectura compañero a compañero
- Peer to peer
#  🌍🔗 Protocolos de aplicaciones de red
##  🌍🔗 Protocolo de transferencia de archivos FTP
- Arquitectura cliente-servidor
###  🌍🔗 Sintaxis de los comandos FTP

# 🌐🕸️ Tecnologías de implementación
## 🌐🕸️ La web
- Es algo global (Accesible por todo el  mundo)
- Permite acceder a datos, información y conocimiento y acceder a ciertos servicios y a ciertas tareas.
- Funciona diferente de las aplicaciones de escritorio.
- No necesita instalar aplicaciones.
## 🌐🕸️ Páginas web
## 🌐🕸️ Navegadores web
## 🌐🕸️ Servidores web
## 🌐🕸️ Aplicaciones Web

# 🌍🔗 Protocolos para la web
## 🌍🔗 Pedidos HTTP
## 🌍🔗 Respuesta HTTP
## 🌍🔗 Manejo de estado de sesión

# 🌍🔗HTML

# 🖇️ Capa de aplicación de blockchain
 - Tener en cuenta los videos de YT, aquellos que explican "por encima" el uso de la blockchain. De todo lo que se habló hoy en clases es básicamente el contenido de los videos, i.e Capa de aplicación.
## 🖇️ Protocolos base
## 🖇️🪙 Bitcoin
### 🖇️🪙 Tipos de nodos 
- Completos
- Mineros
- Ligeros
- Supernodos
### 🖇️🪙 Claves de usuario
- Claves privada: la billetera genera un número aleatorio de 256b
- Clave pública: compartida en la red
	- Resultado de usar la fórmula matemática sobre la clave privada.

### 🖇️🪙 Funciones Hash
- Se aplican a bloques y a transacciones.
### 🖇️🪙 Minería de Bitcoin
- Agrupación de transacciones en bloque candidato.
- Se crea un **encabezado** del bloque.
	- Hash de bloque previo, marca tiempo actual, raíz de Merkle (hash de hash de hash), **nonce** (número e 32b)
	- Se cambia el número de doble hash cada 2 semanas.
### 🖇️🪙 Problema
Dos nodos mineros generan un bloque válido al mismo tiempo.
- Se agregan ambos bloques por diferentes nodos completos a su blockchain.
- La cadena que se extiende más rápido se convierte en la principal.
- Los nodos con cadena más corta la abandonan y se pasan a la cadena más larga.
### 🖇️🪙 Firma digital
Creada a partir de datos de transacción. Es única para cada transacción.
- Clave privada de usuario se usa para **firmar transacciones** y demostrar propiedad de BTC.

## 🔮🔗 Ethereum
- Es la base de la web 3.0
- dApps = contrato ingeligente + front-end
- Token nativo ETH
- Contratos inteligentes
- Máquina virtual de Ethereum
- Tiempo de transacción de 12 seg
### 🔮🔗 Conceptos básicos
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
	
### 🔮🔗 Informaciones asociadas a las cuentas
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