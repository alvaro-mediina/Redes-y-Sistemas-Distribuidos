# Tabla de Contenidos

- [[#🎯 Objetivos de la Introducción]]
- [[#🌐Redes de Dispositivos📲]]
- [[#🤔¿Por qué se enseña la materia?😝]]
- [[#🌐La internet 🌐]]
- [[#☁️ La nube]]
- [[#🚀 Internet de las cosas]]
- [[#🖇️ Redes Blockchain]]
- [[🙂‍↕️ Sistemas Operativos de Red]]

# 🎯 Objetivos de la Introducción

- **Comprender los distintos tipos de redes de dispositivos.**
- **Entender** **cómo** están **organizados** los distintos tipos de redes (i.e Internet, la nube, IoT y las Blockchains)
- **Entender** la arquitectura de los **sistemas operativos de red** (SOR) para los distintos tipos de redes.
- **Entender** convenciones.

# 🌐Redes de Dispositivos

### Definición

- **red de dispositivos** es una estructura compuesta por dispositivos (o nodos) interconectados.
  - Dos **nodos** están **interconectados** si pueden intercambiar información.
  - Los **nodos** pueden compartir recursos como almacenamiento, servicios o aplicaciones, facilitando así el funcionamiento en conjunto de ellos.

### Conexión y comunicación

- **conexión de** **redes de dispositivos** puede hacerse por **medios de transmisión** que utilizan medios **físicos** (cable de cobre, fibra óptica) o inalámbricos (bluetooth, microondas)
- **comunicación** se realiza mediante **protocolos** específicos que aseguran la correcta y eficiente transmisión de datos.

### Ejemplos de dispositivos

- Computadoras
- Celulares
- Impresoras
- Dispositivos IoT (La internet de las cosas) y otros.

### Ejemplos de red de dispositivos

- **La** **internet**: conecta a las computadoras entre sí por medio de **proovedores de servicios de internet**
- **La nube**: por medio de una **red de servidores** interconectados se proveen servicios como almacenamiento o ejecución de aplicaciones.
- **La internet de las cosas (IoT)**: dispositivos físicos que se conectan a internet, comparten datos entre sí y con la nube.
- **Red blockchain**: conjunto de nodos interconectados usados para mantener y validar un registro digital descentralizado de transacciones.

### Lo que necesitás saber para entender **un tipo de red**

1. Su **propósito**.
2. Su **organización**: tipos de nodos y cómo se interconectan entre sí.
3. **Entender** el tipo de sistema operativo de la red: un SO de la red se utiliza para gestionar el uso de los recursos de la red y la comunicación entre los nodos.
4. **Entender** los **protocolos** más importantes que componen al SO de la red:
   - Formatos de mensajes.
   - Reglas de comunicación entre los nodos.
   - **Cada protocolo resuelve** un conjunto de problemas.

---

### 🤔¿Por qué se enseña la materia?😝

- Comprensión de las redes.
- Comprensión del funcionamiento de las redes y de los dispositivos que la soportan.
- Organización y funcionamiento de los SO de redes, en sus diversas partes y qué problemas resuelven.
- Desarrollo de aplicaciones de red.

---

# 🌐La internet 🌐

- Red que cubre a todo el mundo y consiste de varias **redes de área local (LAN)**: están conectadas entre sí por medio de **proveedores de servicio de internet (PSI)**.

## LAN

- Cada **LAN** sirve como una red localizada que conecta dispositivos dentro de un área física específica.
- **Dispositivos en una LAN**: computadoras, televisores, impresoras, puentes, etc.

## PSI

- Los **PSI** proveen los servicios e infraestructura para que los usuarios conecten sus LAN a la Internet más amplia.
- Los **PSI** utilizan dispositivos como **enrutadores** y **puertas de enlace**.
- Manejan el tráfico de datos entre usuario y la red global.
- Facilitan la conexión a través de varios medios incluyendo **cable, DSL, fibra óptica, tecnologías inalámbricas**.

## Aplicaciones de Red

- En internet hay **aplicaciones de Red** que permiten:
  - **Compartir recursos:** por ejemplo, recursos de hardware, compartir información.
  - **Comunicación entre las personas:** pej. vía mail, chat, mensajería, telefonía IP.
  - \*_Socializar:_
  - **Trabajo colaborativo**.
  - **E-Commerce.**
  - **Entretenimiento**.
- Distintas redes de computadoras (**LANs y PSI**) se pueden interconectar entre sí.

  > [!Note] Sistema Operativo de Red
  > Para poder aprovechar y gestionar los distintos tipos de redes se define el **sistema operativo de red** de la internet.

- En la internet para proveer servicios se crean **aplicaciones de red**.
  - Para programarlas se usan **APIs, sockets, middlewares** como la web y las llamadas a procedimientos remotos (Estos últimos están basados en sistemas operativos de red)
  - El **sistema operativo de red** se apoya en el **hardware de red** que forman las **LAN y los ISP.**

## Estructura de la Internet

- Está formada por billones de dispositivos de computación conectados entre sí.
- Se ejecutan **aplicaciones de red**.
- La internet es una red de redes que interconecta varias redes entre sí
- Para envío y recepción de mensajes entre computadoras se usan **protocolos**.

### Host

un **host** se refiere a cualquier dispositivo o computadora conectada a una red que tiene la capacidad de comunicarse con otros dispositivos en la misma red. **(Tanembaum)**

### Tipos de ISPs de acceso

Hosts acceden a la internet a través de ISPs de acceso.

- **ISP residenciales**: compañias de cable, telefónicas, fibra a la casa
- **ISP empresarial**: da acceso a sus empleados
- **ISP universitaria**: acceso a docentes, estudiantes y personal
- **ISP que proveen acceso a WiFi**: aeropuertos, hoteles, restaurantes

> [!NOTE] ### ¿Cómo hacer que dos host que están en distintos ISPs de acceso puedan enviarse paquetes entre sí?
>
> - Los ISPs de acceso deben estar interconectados.

> [!DANGER] ### Dados miles de ISP de acceso, cómo conectarlos entre sí?
>
> #### **Idea 1:** Conectar cada ISP de acceso a otro ISP de acceso, esto se conoce como una **malla**.
>
> - Conectar cada ISP de acceso con cada uno de los otros directamente **no es escalable**, se deben hacer O(N²) conexiones.
>
> #### **Idea 2:** Conectar cada ISP de acceso a un ISP global de tránsito.
>
> - Las ISP **cliente** y **provedora** tienen acuerdo económico.
>
> ### **Idea 3**: Es más conveniente tener **ISPs globales de tránsito** que conectan los ISP de acceso.
>
> - Es más conveniente por la simplicidad de la estructura, reduce la cantidad de nodos conectados entre sí (la malla entre nodos desaparece).
> - Existe un **peering link**, que es un link compañero que conecta a distintos tipos de **ISPs globales de tránsito**

- Las ISP de acceso son interconectadas a través de redes ISP nacionales e internacionales de más alto nivel llamados **ISPs de capa superior** o **ISPs globales de tránsito**.
  - Consiste de **enrutadores de alta velocidad** interconectados con **enlaces de fibra óptica** de alta velocidad.
  - Proveen **servicios de tránsito**
  - Pueden competir entre sí.
  - Cada red ISP es manejada de manera **independiente**.

> [!DANGER] ### **Problema: No todas las ISP globales de tránsito tienen presencia en todas las ciudades/regiones del mundo**
>
> - Por ende cada región/ciudad puede tener un **ISP regional** al cual se conectan los ISP de acceso en la región.
>
> #### Consecuencias
>
> - Cada ISP regional se conecta con ISPs globales de tránsito.
> - Los ISP de acceso pagan al ISP regional al cual se conectan, y cada ISP regional paga al ISP global de tránsito al cual se conecta.
> - En algunos lugares un ISP regional puede cubrir un país entero y ese ISP regional puede conectarse con otros ISP regionales.

### Redes proveedoras de contenido

- Google, Facebook, Microsoft, Apple, etc.
- \*\*Estas redes se utilizan para:
  - Reducir pagos a redes de tránsito global.
  - Tener control sobre cómo sus servicios son entregados a los usuarios finales.
- \*\*Las redes proveedoras de contenido se conectan a:
  - ISP regionales e ISP de acceso.
  - Podrían llegar a usar un ISP de tránsito si no le queda otra.

### Otra forma de ver la estructura de internet

- Es como un conjunto de redes de distintos tamaños interconectadas entre sí.
  - Así las redes pueden venir en diferentes tamaños, formas y cumplír distintos propósitos.
  - Varias redes pueden interconectarse entre sí para formar redes más grandes.
  - La **internet** es el ejemplo de red de redes más grande.

> [!NOTE] ### Si pensáramos a la internet como una red formada por niveles que forman una jerarquía.
>
> 1. Tier-1: ISPs comerciales: Redes globales de tránsito - Cobertura nacional e internacional.
> 2. Redes proveedoras de contenido.
> 3. ISP regionales.
> 4. ISPs de acceso.

![[🧐 Teórico 📝/imgs/1.png]]

### Tipos de redes

- Ver filmina N 39 donde explica las distintas distancias en relación a las locaciones para distintas redes.

## Redes de área amplia (WANs)

- Una WAN cubre un área geográfica grande, tipicamente un país o hasta un continente.

### Organización de una WAN

- **Subred**: Varios **enrutadores** conectados entre sí forman un grafo.
- **Arco**: representa un cable que une 2 enrutadores.
- A una **subred** pueden estar conectadas computadoras o lan enteras.
- Para ir de una máquina a otra hay distintas **rutas alternativas**

> [!NOTE] ### ¿Cómo enviar mensajes en una WAN?
>
> - Si tenemos que enviar desde una computadora **L bits por paquete.**
> - Además tenemos **R bits por segundo**.
> - Toma L/R segundos transmitir paquete de L-bit en un enlace de R bps.

> [!DANGER] ### A esto nace
>
> - **Encolado y pérdida de paquetes**
> - Los paquetes se van a encolar, y esperarán a ser transmitidos en el enlace.
> - Los paquetes pueden ser **perdidos** si el **buffer** se llena.

- Algoritmos de enrutamiento: Hay varios caminos que conectan dos enrutadores, el algoritmo de enrutamiento decide cuál de ellos tomar.

> [!NOTE] ### ¿Cuánto demora el almacenamiento y reenvío?
> $d_{nodal}=d_{proc}+d_{queue}+d_{trans}+d_{prop}$
>
> - $d_{proc}$ : Procesamiento del nodo
> - $d_{queue}$ : Demora por encolado
> - $d_{trans}$ : Transmisión
> - $d_{prop}$ : Propagación

### Sistemas Telefónicos fijos: DSL

- Los datos sobre la línea DSL van a la internet.
- La voz sobre la línea DSL va a la red telefónica la cual está conectado por un cable de cobre en una **oficina central**.

### Arquitectura de red celular

- MSC: Conecta células a red telefónica.
  - Maneja seteo de llamadas.
  - Maneja movilidad.
- Célula: Cubre una región geográfica.
  - Cuenta con una estación base (BS)
  - Usuarios móviles se enlazan a la red a través de la BS.

### Área de red Metropolitana (MAN)

- Una red de área metropolitana (MAN) cubre una ciudad.
- Hay **dos tipos**:
  - **Redes de cable:** se basan en la red de TV por cable.
    - Cable coaxial sirve para unir varias casas.
    - Elementos de commutación
    - Los elementos de commutación se unen por cables de fibra óptica.
  - **WiMAX:** son redes inalámbricas de alta velocidad.
  - Hay estación base que permite enviar paquetes por el aire en lugar de usar cable o redes telefónicas.
  - La estación base se conecta a internet.

### Redes de Área local

- LAN inalámbricas
- La Ethernet.

### Redes de Área local

- Difusión - Canales de difusión
- Colisiones
- Manejo de Colisiones(enfoques)

### Redes hogareñas

- Constan de dispositivos inalámbricos que se conectan a una caja en la cual suele estar el router, punto de acceso inalámbrico, ethernet.

### Redes de acceso empresarial

---

# ☁️ La nube

- Permite el acceso remoto a un conjunto de **recursos informáticos** incluyendo almacenamiento, procesamiento de datos y aplicaciones, a través de una **red de servicidores** interconectados.
  - Los **servidores** utilizan protocolos para comunicarse entre sí con los usuarios.
  - Los **recursos** se utilizan dinámicamente según las necesidades de los servicios ofrecidos. Los usuarios pueden acceder a dichos recursos desde cualquier lugar y momento utilizando dispositivos conectados a internet.

## ☁️Clasificación de las nubes

- **Pública:** Infraestructura compartida proporcionada por proveedores como AWS, Google Cloud. Los recursos compartidos son utilizados entre múltiples usuarios.
- **Privada:** Infraestructura dedicada a una sola organización.
- **Híbrida:** Combina nubes públicas y privadas.

## ☁️Estructura de la nube (Ver gráfico en las filminas)

- **Regiones**:
- **Zona de disponibilidad**:
- **Nube privada virtual**:
- **Subred**
- **Tipos de nodos en la nube**
  - Servidores web
  - Servidores de aplicaciones
  - Almacenamiento de objetos
  - Balanceadores de carga
  - Balanceadores de carga externos
  - Balanceadores de carga internos

---

# 🚀 Internet de las cosas

- Sistema Físico que permite que dispositivos físicos (Dispositivos IoT) se conecten a internet y compartan datos entre sí y con sistemas en la nube.
- Se conectan a internet a través de tecnologías como Wifi, Bluetooth, redes de celulares, etc.
- Los datos recopilados por los dispositivos IoT pueden enviarse a plataformas de nube.
- Las **computadoras tradicionales** se usan para gestionar redes IoT

## Ejemplos

- Sensores: Sensor de temperatura, de riego.
- Actuadores: Motores eléctricos, actuadores para abrir y cerrar puertas.
- Wearables: Electrodomésticos inteligentes, cámaras de seguridad.

## Propósito

- **Crear una red** de objetos conectados que recopilen, compartan y actúen con información para mejorar la vida cotidiana y eficiencia en diferentes contextos.

## Metas de la IoT

- Automatización
- Monitoreo
- Optimización de recursos
- Mejora de la vida cotidiana
- Sostenibilidad ambiental
- Análisis de datos
- Mejorar la seguridad física

## 🚀 Estructura de la IoT

- Pueden ser **redes de sensores o sistemas ciberfísicos (CPS).**

---

# 🖇️ Redes Blockchain

- Conjunto de nodos interconectados que operan en un sistema descentralizado que permite la creación de un registro digital de transacciones seguro.
- Las **transacciones** se agrupan en bloques que se encadenan unos con otros. Esta cadena es accesible y verificable por participantes de la red.
- **Permite** la validación del registro de transacciones, usando mecanismos de consenso para asegurar la integridad y seguridad de los datos.
- **Puede** proporcionar funcionalidades avanzadas como contratos inteligentes que automatizan procesos mediante condiciones predefinidas.

## 🖇️Tipos de dispositivos

- Nodos completos: **contienen copias de los registros**, y participan en la validación de transacciones.
- Dispositivos mineros: **utilizados** para validar transacciones y **crear** nuevos bloques en redes blockchain una vez que resolvieron un problema matemático complejo.
- Nodos ligeros: **pueden** verificar y procesar transacciones
- Billeteras digitales.

## 🖇️Objetivos

- **Transparencia**: Permitir a los usuarios verificar las transacciones en tiempo real.
- **Inmutabilidad**: Garantizar que una vez que los datos son registrados, no puedan ser alterados ni eliminados sin el consenso de la red.
- **Descentralización**: Eliminar la dependencia de un único punto de control, lo que reduce el riesgo de fraude y mejora la resiliencia del sistema.
- **Interoperatibilidad**: Facilitar la comunicación y el intercambio de datos entre diferentes blockchains.

## 🖇️Conexiones

- Las redes blockchain se basan y se conectan con tecnologías anteriores como:
  - **Internet**: Proporciona la infraestructura necesaria para la comunicación entre nodos distribuidos. La blockchain opera sobre Internet, utilizando sus protocolos para transmitir datos y permitir el acceso global.
  - **Nubes**: A veces se integra con servicios en la nube para almacenamiento adicional y procesamiento.
  - **Bases de datos**: La blockchain actúa como una base de datos distribuida donde hay nodos que mantienen una copia del registro, lo que mejora la seguridad y la transparencia.

## 🖇️ Estructura de las redes blockchain

- **Tipos de nodos**:
  - Completos
  - Ligeros
  - Mineros
  - Billeteras
  - Validadores
  - Super Nodos
  - Autoridades de certificación

---