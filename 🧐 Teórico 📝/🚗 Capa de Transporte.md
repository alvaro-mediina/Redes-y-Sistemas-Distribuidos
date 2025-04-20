Provee comunicación lógica entre **procesos de aplicación** que ejecutan diferentes sistemas finales. Se implementa sólo en host/sistemas finales.
Su **comunicación lógica** es como si los host ejecutando los procesos estuvieran directamente conectados.
Sirven para **mejorar la calidad** de los servicios de la **Capa de Red**
	* Retransmisión de paquetes perdidos en redes no orientadas a la conexión.
	* Cuando hay congestión en la red, regulando la variación de la tasa de transmisión de paquetes de los hosts.

# Problemas que soluciona la capa de transporte
- Uso de temporizadores y retransmisiones de paquete
- Direccionamiento explícito de los destinos
- Uso de búferes para lograr comunicación confiable **eficiente**
- Control de flujo
- Evitar congestión de la red poniendo demasiados paquetes en ella.
	- Cuando la **capa de red** pierde paquetes, la **capa de transporte** puede solucionarlo.
- Entrega de paquetes al host destino de forma ordenada

# Unidad de dato del protocolo
Segmentos


---
# Problema: Entrega ordenada al host destino
- El emisor numera los segmentos enviados (usando **números de secuencia**) respetando el órden del flujo de datos recibido de la capa de aplicación.
- Para cada número de segmentos enviados, **el emisor** se dispara un **temporizador de retransmisiones**
- El **receptor** manda **confirmaciones de recepción(ACK)** para segmentos recibidos correctamente
- Si **expira el temporizador** de un segmento sin recibir el **ACK**(**ack**nowledgment) el emisor retransmite el segmento correspondiente
- El receptor **re-ensambla en orden** los segmentos recibidos y los entrega a la capa de aplicación
---

# TCP (Transferer Control Protocol)
Protocolo de control de transmisión

Proporciona un flujo **(stream)** de bytes confiable de extremo a extremo a través de una inter-red no confiable.


- TCP se adapta dinámicamente a las propiedades de la inter-red y **se sobrepone a muchos tipos de fallas**
- Entidad de transporte TCP  -> ETCP
- Usaremos la palabra TCP para referirnos a veces a la ETCP y a veces al protocolo TCP


## ETCP
Una ETCP acepta **flujos de datos** a transmitir de procesos locales donde cada flujo de datos *divide* en **fragmentos** llamados segmentos que no exceden los 64KB y se envía cada segmento dentro de un datagrama IP


El **servicio TCP** se obtiene al hacer que tanto **el servidor** como **el cliente** creen **sockets**
	* *Dirección de un socket:* IP + PUERTO
	* Para obtener el servicio se debe *establecer una conexión* explícitamente entre el socket de *la máquina emisora* y uno en *la máquina receptora*.

>[!note] Un socket puede usarse para *múltiples conexiones* al mismo tiempo
> Las conexiones se identifican mediante los identificadores de sockets de los dos extremos (socket1, socket2)


**IMPORTANTE**: Cada **byte** de un flujo de datos a enviar en una conexión TCP tiene su propio número de secuencia de 32 bits. Esto impone el límite de un flujo de datos.

*Son importantes los números de secuencia para confirmaciones de recepción*

- La **ETPC** emisora y receptora intercambian datos en forma de segmentos.
		

## Segmentos
*Segmento: Encabezado TCP + (0 o más)bytes de datos*
El software de TCP decide qué tan grandes deben ser los segmentos.


*Formados por*:
	- *Encabezado fijo* de 20 bytes
	- *Opciones de encabezado* en palabras de 32 bits
	- *Datos personales*

Los límites que restringen el tamaño de un segmento:
- Cada segmento, debe caber en la carga útil de 65.515 bytes del IP. 
- Cada red tiene una *unidad máxima de transferencia* (MTU) y cada segmento debe caber en la MTU. 
- En la práctica la MTU es usualmente de *1500 bytes* (el tamaño de la carga útil de Ethernet).
- Los segmentos **sin datos** se usan para *ACKs* y *mensajes de control*

### Algunas partes del segmento

- *Puerto de origen y puerto destino*:
	- Son de 16 bits cada uno.
	- La dirección de un puerto + la dirección IP del host de destino forman un **punto terminal único** de 48b.
	- Los puntos terminales de origen y de destino en conjuntos identifican la conexión.

- *Número de secuencia:* Es un número de byte en el flujo de bytes transmitido y corresponde al primer byte en el segmento.
	- 32 bits de longitud.
- *Número de confirmación de recepción:* Indica el siguiente byte esperado del flujo de bytes a transmitir.
	- 32 bits de longitud
- *ACK:* 1 para indicar que el número de confirmación de recepción es válido.
	- 0 si el segmento no contiene una confirmación de recepción
	- Sólo 1 bit.
- *Longitud del encabezado:* 32 bits
- *Campo de opciones:* de longitud variable



---
# Problema: La capa de red(que incluye IP)
No proporciona ninguna garantía garantía de que los datagramas se entregarán de manera apropiada, tampoco que se entregarán.

## Solución de TCP
**Si** un datagrama se recibe correctamente se confirma su recepción.
**Si no** se confirma la recepción de un datagrama luego de un intervalo de tiempo entonces se debe retransmitir.
**Corresponde a TCP** terminar los temporizadores y retransmitir los datagramas conforme sea necesario.

# Problema: Los datagramas que llegan pueden no estar en órden
Normal cuando se trabaja con redes de **datagramas**

## Solución de TCP
TCP es el responsable de **reensamblar** los mensajes en la secuencia apropiada.

---

Cuando un **transmisor** envía un segmento, también inicia un temporizador. 

Cuando llega el segmento a destino, la *ETCP receptora* devuelve un segmento (con datos si existen, sino sin ellos) que contiene un número de confirmación de recepción igual al siguiente número de secuencia que espera recibir.

Si el temporizador expira antes de llegar el **ACK**, el emisor envía de nuevo el segmento.

## Problemas a manejar por TCP
- Pueden llegar segmentos fuera de órden.
- Pueden retardarse segmentos en tránsito durante tanto tiempo que el temporizador del emisor expira y los segmentos se retransmiten.

---
# Entrega de datos confiable
Hace falta definir un protocolo para la entrega de datos confiable

Porque sino pasan desapercibidas preguntas como:
- ¿Qué se confirma exactamente en un ACK?
- ¿cuántos paquetes se envían antes de recibir un ACK?
- ¿Qué hace el receptor cuando se pierde o daña un paquete?

La **capa de transporte** debe soportar al menos un protocolo de entrega de datos confiable

>[!note] El mismo paquete llega dos o más veces al receptor y la capa de transporte la pasa a la capa de aplicación más de una vez.
> -  Esto es inaceptable
> - ¿Cómo evitar entregar a la capa de aplicación paquetes repetidos?
> 
> *Se deben asignar números de secuencia a los paquetes que salen*
> 	La idea es que dado un número de secuencia de un segmento que acaba de llegar, el receptor pueda usar ese número de secuencia para decidir si el segmento es un duplicado y en ese caso descartarlo

## 🚗 Protocolo de parada y espera
*Situación: Latencia baja*
El RTT es bajo comparado con el tiempo de copiar un paquete
Por lo tanto sólo se puede mandar un paquete antes que llegue el ACK

**Situación**: El canal de comunicación subyacente puede perder paquetes(de datos, ACKs)
1. Los paquetes tienen N° de secuencia *(1 bit es suficiente)*
2. Se trabaja con ACKs. El receptor debe especificar el N° de secuencia del paquete siendo confirmado
3. Se usan retransmisiones de paquetes. Para ello se utilizan temporizadores

**Comportamiento del emisor**
1. El emisor envía el paquete *P* y **PARA** de enviar.
2. **Espera**: El emisor espera una cantidad "razonable" de tiempo para el *ACK*.
3. Si llega el ACK a tiempo, se envía el paquete y se lanza el temporizador. *GOTO 2*
4. Si el temporizador se acaba se retransmite el paquete *P*. *GOTO 2*
	- Si hay paquete o ACK demorado pero no perdido *->* La retransmisión va a ser un duplicado con igual número de secuencia, luego se descarta en el receptor

**Casos que se pueden dar en el protocolo:**
- No hay pérdida.
- Pérdida de un paquete.
	- *Como no llega ACK del receptor se vuelve a enviar*
- Se pierde un ACK.
	- *El temporizador del emisor se termina, vuelve a transmitir el paquete y el emisor recibe duplicado, lo descarta y envía ack*
- Timeout prematuro y ACK demorado.
	- *El temporizador del emisor se termina, vuelve a transmitir el paquete y el emisor recibe duplicado, lo descarta y envía ack*
	- *En este caso se desfaza la comunicación y se empiezan a recibir paquetes duplicados*

 *La situación de esta técnica es cuando *


## 🚗 Protocolo de tubería
*Situación: Latencia alta*
El RTT es muy alto comparado con el tiempo de copiar un paquete
Por lo tanto, se pueden mandar varios paquetes antes que llegue el ACK del primer paquete enviado

*Protocolos de tubería:*
	- Retroceso - N
	- Repetición Selectiva


- El emisor puede enviar múltiples paquetes al vuelo a ser confirmados.
- Hay que usar búferes en el emisor
	- *Puede hacer falta retransmitir los paquetes*
	- *El emisor almacena en búfer todos los segmentos hasta que se confirme su recepción*
**Idea Gruesa**: Mando una ráfaga de paquetes hasta que me lleguen los sucesivos ACK.

### 🛢️ Retroceso - N
*Situación: Latencia alta*
*Proporción de errores o pérdida de paquetes baja*
*Rara vez se demoran los paquetes*

---
# Problema
*Si un paquete T a la mitad de una serie larga se daña o se pierde*
- La CT receptora debe entregar paquetes a la capa de aplicación en secuencia.
- Por lo que no se pueden entregar a la capa de aplicación los paquetes que llegaron bien después de T.

*¿Qué debe hacerse con los paquetes correctos que le siguen a un paquete que se perdió?*

**Solución:** Utilizar Retroceso N. El receptor descarta todos los paquetes subsecuentes al paquete perdido, sin enviar ACK para los paquetes descartados.

---

⬅️**Comportamiento del receptor**
*Receptor envía ack acumulativo: mayor número de secuencia tal que todos los segmentos anteriores se recibieron bien.*
Asumir que el receptor recibió un paquete n:
	Si n está en orden (todos los paquetes anteriores llegaron) y está correcto (sin errores):
	Manda ack para n y entrega parte de datos de paquete n a capa superior.
	Sino: el receptor descarta el paquete n y manda ACK del paquete más reciente recibido en orden.

➡️**Comportamiento del emisor**
*El emisor tiene un solo temporizador para el paquete más viejo no confirmado.* 
Al expirar el temporizador (del segmento más viejo no confirmado), o retransmite todos los segmentos no confirmados.
	Si llega ACK nuevo y hay segmentos enviados no confirmados, o el temporizador es reiniciado.
	Si llega ACK nuevo y no hay segmentos sin confirmar, o el temporizador es detenido.

*Asumir en el emisor*
- Todos los búferes son del mismo tamaño
- Cantidad de búferes fija en el emisor
	- Asumiendo que el RTT es fijo esta cantidad representaría, la cantidad de segmentos a enviar por ráfaga para aprovechar el canal al máximo. 
- Para referirnos a los números de secuencia de esos búferes usamos el concepto de **ventana del emisor**.

>[!Note] Ventana en el emisor
> *Permite hasta N paquetes consecutivos sin confirmar*
> 
> *Ventana emisora*: tramas enviadas sin ACK positivo o tramas listas para ser enviadas


*Si se manda un paquete de confirmación solamente*
¿Qué número de secuencia debe tener?

- Enviar ACK con N° de secuencia más alto tal que los N° de secuencia anteriores fueron recibidos.
	- *A esto se le llama ACK acumulativo.* 
- Si se pierde un segmento llegan bien varios de los siguientes, para estos se generan *ACKs duplicados.
- Para los números de secuencia, el receptor maneja variable *expectedSeqnum* que es el número de secuencia más chico que no llegó aun.


> [!Note] Ventana emisora
> *El tamaño de la ventana emisora* no puede superar MAX_SEQ cuando hay MAX_SEQ + 1 números de secuencia.

**Problema de Retroceso N**
Uso ineficiente del canal frente a segmentos perdidos o demorados


## 🚗 Protocolo de Repetición Selectiva

---
# Problema
*Si un paquete T a la mitad de una serie larga se daña o se pierde*
- La CT receptora debe entregar paquetes a la capa de aplicación en secuencia.
- Por lo que no se pueden entregar a la capa de aplicación los paquetes que llegaron bien después de T.

*¿Qué debe hacerse con los paquetes correctos que le siguen a un paquete que se perdió?*

**Solución:** Usar Repetición Selectiva
Los paquetes en buen estado recibidos después de un *paquete dañado* E se *almacenan en búfer*
Cuando llega el paquete E, el receptor entrega a capa de aplicación, en secuencia, todos los paquetes posibles que ha almacenado en búfer

*Mecanismo común de retransmisiones:*
El temporizador de E termina y el emisor lo manda de nuevo.

**Una solución mejor**: Uso de una *ack negativa (NAK)* por el receptor.
	Así se estimula la retransmisión de paquetes antes que los temporizadores terminen y así se mejora el rendimiento.

---

- *El receptor* confirma individualmente todos los paquetes recibidos correctamente
	- Hay búferes para paquetes según se necesiten para su entrega eventual en orden a la capa de aplicación
- *El emisor* solo reenvía paquetes para los cuales el ACK no fué recibido o se recibió un NAK.
	- Hay un temporizador del emisor por cada paquete no confirmado

### Ventana del emisor
Contiene N N°de secuencias consecutivos
Limita N°de sequencias a enviar a paquetes no confirmados.

- **Tipos de paquetes que puede haber en la ventana del emisor:**
	- Paquetes enviados y confirmados porque antes hay paquetes no confirmados
	- Paquetes enviados y no confirmados
	- Paquetes listos para enviarse en búfer

---
**Situación** Es necesario almacenar en búfer paquetes porque puede perderse un paquete y llegar a otros a continuación del mismo y en repetición selectiva estos se almacenan.

# Problema
¿Cómo representar el conjunto de paquetes que puede almacenar en búfer el receptor?

**SOLUCIÓN** Usar *intervalos de números de secuencia* dentro del *espacio de números de secuencia* -> *ventana corrediza*

---

### Ventana del receptor
Puede tener los tipos de paquete:
- Paquetes esperados y no recibidos.
- Paquetes recibidos fuera de orden
- Paquetes aceptables en la ventana que no han llegado aún
*Se mantiene en bufer un paquete aceptado  por la ventana receptora*
Hasta que todos los que le preceden hayan sido pasados a capa de aplicación


### Detalles de la repetición selectiva
- El tamaño de ventana emisora comienza en 0 y crece hasta su MAX_SEQ
- El receptor tiene un búfer para cada N° de secuencia en su ventana.
*¿Qué se hace cuando llega un paquete?*
Cuando llega un paquete, su número de secuencia es revisado para ver si cae dentro de la ventana. De ser así, y no ha sido recibido aun, **se acepta y almacena**.
- *Regla para el tamaño de la ventana receptora:* $\frac{MAXSEQ + 1}{2}$
	- Con tamaños superiores la ventana receptora no funciona.

---
# Problema
*Situación:* En el encabezado de paquete hay N° de secuencia de k bits.
¿Cómo transmitir datos en ambas direcciones eficientemente?

**Solución:** Llevar  a caballito (piggybacking)
Cuando llega un segmento S con datos, el receptor se aguanta y espera hasta que la capa de aplicación le pasa el siguiente paquete P.
La confirmación de recepción de S se anexa a P en un segmento de salida (usando el campo ack en el encabezado del segmento de salida).

**Solución:** La capa de transporte para mandar un ACK, debe esperar por un paquete al cual superponer un ACK.

---
# Problema
¿Cómo evitar retrasar demasiado envío de confirmaciones de recepción por no tener tráfico de regreso?

**Solución** Método que utiliza un timer auxilar
Tras llegar un paquete de datos en secuencia, se arranca un temporizador auxiliar mediante start_ack_timer.
Si no se ha presentado tráfico de regreso antes de que termine este temporizador, se envía un paquete de ACK independiente.

*tiempo de temporizador auxiliar << tiempo de temporizador de retransimisión*

**Utilizamos esto para:**
para asegurarse que la ack de un paquete correctamente recibido llegue antes que el emisor termine su temporización y retransmita el paquete.

---






# 🫗Control de flujo en la capa de transporte
*Situación:* Evitar que un host emisor rápido desborde a un host receptor lento

*Podemos asumir* que el receptor maneja búferes para los mensajes que llegan
*Esto es necesario porque*:
- Para procesar los segmentos recibidos.
- El receptor puede acumular una cantidad de segmentos suficientes antes de pasarlos a la capa de aplicación para que los procese
- Los segmentos pueden llegar desordenados


*Situación*: La *capa de aplicación* lee los mensajes que llegan, pero no necesariamente al instante en que los datos llegan.

>[!Note] Si nos quedamos solo con los protocolos de comunicación confiable anteriores, estos *no son suficientes para evitar desbordamiento de búferes en el receptor*. o Hace falta definir un protocolo especial para el control de flujo.


*Situación:* ¿Qué hace el receptor con los búferes si tiene varias conexiones?
**Solución:**
- Se usan búferes a medida que llegan segmentos.
- Se dedican conjuntos de búferes específicos a conexiones específicas.


## 🫗 Control de flujo
*Soluciona con* solicitar espacio en búfer en el otro extremo
- Para estar seguro de no sobrecargar al receptor
- Porque sabe cuánto necesita

*Cuando el receptor recibe este pedido*:
1. Sabe cuál es su situación y cuánto espacio puede otorgar. 
2. Aquí el receptor reserva una cierta cantidad de búferes al emisor.
3. *Los búferes podrían repartirse por conexión*, o no. 
4. *Si los búferes se reparten por conexión y aumenta la cantidad de conexiones abiertas*,  el receptor necesita ajustar dinámicamente sus reservas de búferes.

>[!Note] ### Funcionamiento entre host emisor y host receptor
>1. Inicialmente **el emisor** solicita una cierta cantidad de búferes, con base en sus necesidades percibidas.
>2. **El receptor** otorga entonces tantos búferes como puede
>	- **El receptor**, sabiendo su capacidad de manejo de búferes podría indicar al emisor “te he reservado X búferes”.
>1. **El emisor** lleva la cuenta de su asignación de búferes con el receptor.
>	- Cada vez que **el emisor** envía un segmento, **el receptor** debe disminuir la asignación de *búferes disponibles*
>	- Cuando la asignación de búferes(disponibles) llega a 0, **el emisor** para de enviar.

### Idea básica
- El emisor solicita búferes
- El receptor responde con la cantidad de búferes que tiene y espera la secuencia 0
- El emisor manda lo que puede recibir el receptor
- El receptor recibe y aloja en buffer, si se satura no recibe más
- El receptor procesa
- El emisor no envía más hasta que avise que tiene búferes disponibles.

## 🫗 Control de flujo en TCP
**El receptor** ya no estará avisando sobre cuántos búferes tiene para almacenar, ahora avisa la *cantidad de bytes a almacenar* (ventana)


**El receptor**
- Cuando la conexión TCP *recibe bytes* en el orden correcto y en secuencia, coloca los datos en el buffer de recepción.
- *El receptor* puede confirmar llegada de datos nuevos y anunciar nuevo tamaño de ventana al emisor.
- *Si búfer de recepción está lleno*, avisar tamaño de ventana de cero.
- Una vez que el receptor entrega a la capa de aplicación X datos de búfer de recepción lleno, puede avisar al emisor de un tamaño de ventana de X

**El emisor**
También dispone de un tamaño de ventana disponible para su buffer de salida.
- Si el tamaño de ventana anunciado es cero el emisor no podrá enviar datos. 
- El emisor envía segmentos cumpliendo la siguiente propiedad:
 $$LastByteSent−LastByteAcked ≤ TamañoDeVentana$$

---
# Problema
¿Cómo manejar pérdida de segmentos en TCP?


**Solución:** el receptor solicita segmento/s específico/s mediante segmento especial llamado *NAK*
- Tras recibir segmento/s faltante/s, el receptor puede enviar una confirmación de recepción de todos los datos que tiene en búfer. 
- Cuando el receptor nota una brecha entre el número de secuencia esperado y el número de secuencia del paquete recibido, el receptor envía un NAK en un campo de opciones.
**Solución:** *(ACK selectivos)* el receptor le dice al emisor que piezas recibió.
- El emisor puede así reenviar los datos no confirmados que ya envió. 
- Se usan dos campos de opciones:
	- **Sack permited option**: se envía en segmento SYN para indicar que se usarán acks selectivos.
	- **Sack option**: Con lista de rangos de números de secuencia recibidos.