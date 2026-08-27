# Tema 37 — Contenido Teórico

> **Título oficial**: Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión.
>
> **Bloque**: Parte II — Técnico
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha generación**: 2026-08-27
> **Fuentes**: Ver tema-37-fuentes.md · **Diagramas**: Ver tema-37-diagramas.md · **Cambios**: Ver tema-37-changelog.md
>
> *Extensión: ~20.000 palabras · 19 diagramas SVG embebidos · 4 tipos de callout transversales*

---

## Convenciones del documento

Este tema incluye cuatro tipos de **cajas callout** para facilitar el estudio:

> **[DATO CLAVE EXAMEN]** Información de alta densidad memorística, con alta probabilidad de aparecer en el test oficial: tamaños de trama, tiempos, distancias, categorías de cableado, numeración de normas IEEE y códigos del ENS.

> **[EJERCICIO RESUELTO]** Problema resuelto paso a paso: calcular una ranura de colisión, dimensionar un cableado, contar dominios de difusión, decidir un método de acceso.

> **[EJEMPLO AYTO MADRID]** Aplicación de la teoría al entorno municipal (red local de una Oficina de Atención a la Ciudadanía, centro de proceso de datos del IAM, biblioteca, colegio o instalación deportiva municipal).

> **[REFERENCIA CRUZADA]** Enlace conceptual a otros temas del temario oficial.

**Cómo leer este tema.** El enunciado oficial es una **lista de cuatro preguntas encadenadas sobre un mismo objeto**: qué es una red local y cómo se clasifica (tipología), cómo se ponen los bits en el medio (técnicas de transmisión), cómo se reparte ese medio entre quienes quieren usarlo a la vez (métodos de acceso) y con qué aparatos se une todo (dispositivos de interconexión). Las cuatro tienen distinto peso en un examen de C1. La **tipología** produce preguntas de definición y de clasificación, que son fáciles si se tiene el vocabulario. Las **técnicas de transmisión** producen preguntas de dato puro. Los **métodos de acceso** son el corazón conceptual del tema y donde se concentran las preguntas de razonamiento: **CSMA/CD y CSMA/CA se preguntan casi siempre**, y casi siempre por su diferencia. Y los **dispositivos de interconexión** son la parte más práctica: la pregunta canónica es «cuántos dominios de colisión y cuántos dominios de difusión hay en este dibujo».

**Un aviso sobre lo que aparenta ser historia y no lo es.** Buena parte de este tema describe tecnologías **retiradas**: el cable coaxial de Ethernet, el concentrador, Token Ring, Token Bus, FDDI. Es tentador saltárselas. Sería un error por dos razones. La primera, práctica: **el temario oficial las pide expresamente** —«métodos de acceso» incluye los deterministas, que hoy no se usan en redes locales— y son de las preguntas más rentables, porque son cerradas y no cambian. La segunda, conceptual: **la red local moderna se entiende por contraste con ellas**. Un conmutador no se entiende sin haber entendido antes por qué era un problema el concentrador; CSMA/CD no se entiende sin el bus de coaxial en el que nació; y la palabra «dominio de colisión» no significa nada si nunca ha habido colisiones.

**Fronteras con otros temas, declaradas de entrada.** Este tema comparte materia con cuatro temas del bloque técnico y conviene fijar el reparto antes de empezar, para que el solapamiento del temario oficial no se lea como una omisión ni como una repetición:

- El **Tema 33** cubre las **comunicaciones en general**: medios de transmisión, modos de comunicación, equipos terminales, redes de conmutación y difusión, y comunicaciones móviles. Aquí esos mismos conceptos se recorren **solo en su versión de red local**: el par trenzado tal y como lo instala un cableado estructurado, no la fibra submarina; el punto de acceso del vestíbulo de una junta de distrito, no la estación base celular.
- El **Tema 34** cubre el **modelo OSI, el modelo TCP/IP y los protocolos de la pila**. Aquí las capas se usan como **regla para clasificar dispositivos** —repetidor en la 1, conmutador en la 2, encaminador en la 3— y no se describen las capas 3 a 7.
- El **Tema 30** cubre la **administración** de la red de área local: gestión de usuarios, gestión de dispositivos, monitorización y control de tráfico. La frontera es limpia y conviene enunciarla así: **el Tema 37 describe la red y el Tema 30 la administra**. Aquí se explica qué es una VLAN y cómo viaja su etiqueta; allí, cómo se planifican, se despliegan y se supervisan.
- Los **Temas 36 y 39** cubren la **seguridad en redes** —perímetro, acceso remoto, VPN— y los **principios del ENS y del ENI**. Aquí la seguridad aparece únicamente en §6.2 y §6.3, y solo en lo que la normativa exige a la **red local** de una Administración.

**Caso de referencia usado en todo el tema** (contexto Ayuntamiento de Madrid, supuesto simplificado): la **red local de una Oficina de Atención a la Ciudadanía** de un distrito, instalada en un edificio municipal de tres plantas, con puestos de tramitación, teléfonos IP, impresoras multifunción, una sala de espera con Wi-Fi para la ciudadanía, cámaras de videovigilancia alimentadas por el propio cable de red y un armario de comunicaciones por planta. Esa oficina se conecta, a través de la red corporativa, con el **centro de proceso de datos del IAM**, donde vive el sistema de tramitación de expedientes. El mismo escenario permite instanciar todo el tema: la tipología y las topologías (§2), el cableado y la radio (§3), la contienda por el medio en la Wi-Fi de la sala de espera (§4), la electrónica de los armarios (§5) y las obligaciones normativas que pesan sobre todo ello (§6).

---

## 1. Concepto y caracterización de las redes locales

### 1.1. Definición, evolución y características principales

**Definición.** Una **red de área local** (*Local Area Network*, **LAN**) es un sistema de comunicación de datos que interconecta un conjunto de equipos informáticos dentro de un **ámbito geográfico reducido** —un edificio, un grupo de edificios próximos o un recinto—, sobre un **medio de transmisión propiedad de la organización que la explota**, con **velocidades altas**, **retardos bajos** y **tasas de error muy pequeñas** [IEEE802] [TANENBAUM].

De esa definición conviene extraer **cinco rasgos**, porque las preguntas de examen suelen consistir en presentar una red y preguntar si es o no una red local (ver **diagrama D1**):

1. **Ámbito geográfico reducido.** El orden de magnitud clásico va de unos metros a unos pocos kilómetros. No hay una cifra normativa: es una característica cualitativa, y de hecho la frontera con la red de área metropolitana es difusa.
2. **Titularidad privada del medio.** Es el rasgo **jurídicamente más significativo** y el que mejor discrimina. En una red local, **el cable es de la organización**: se instala, se mantiene y se sustituye sin intervención de un operador de telecomunicaciones ni contrato de servicio. En una red de área extensa, en cambio, el medio pertenece a un operador y se contrata. Es exactamente la diferencia entre el cable que va del puesto al armario de la oficina y el enlace que une esa oficina con el centro de proceso de datos.
3. **Velocidad de transmisión elevada.** Históricamente, órdenes de magnitud por encima de la red de área extensa disponible en el mismo momento. Hoy lo normal en el puesto es **1 Gbit/s**, en la agregación **10 Gbit/s** y en el centro de proceso de datos **25, 40, 100 Gbit/s y más** [IEEE8023DJ].
4. **Retardo bajo y tasa de error muy baja.** Al no haber travesía de redes de terceros, el retardo de propagación es de microsegundos y la tasa de error de bit del cableado bien instalado es del orden de 10 elevado a menos 10 o mejor. Esto tiene una consecuencia de diseño importante: **en una red local no hace falta un control de errores sofisticado en la capa 2**; basta con **detectar** el error y descartar la trama, dejando la recuperación a la capa de transporte. Es la razón por la que la subcapa LLC en modo con conexión nunca se usó en la práctica.
5. **Medio compartido, al menos en su origen.** Este es el rasgo del que nace la mitad del tema. Si varias estaciones cuelgan del mismo medio, hay que decidir **quién transmite y cuándo**: ese es el problema del **acceso al medio** (§4). La red local conmutada moderna ha eliminado en gran medida el medio compartido en la parte cableada, pero lo conserva íntegro en la parte inalámbrica.

**Evolución histórica**, en cinco etapas que hay que saber ordenar:

- **Origen (1973-1980).** **Robert Metcalfe** y **David Boggs** construyen en el **Xerox PARC** el prototipo de **Ethernet**, a **2,94 Mbit/s** sobre un cable coaxial, y publican en 1976 el artículo fundacional en *Communications of the ACM* [METCALFE]. Su antecedente directo es la red **ALOHA** de la Universidad de Hawái (1970), que resolvía el acceso por radio a un canal compartido mediante transmisión aleatoria y retransmisión tras colisión [ABRAMSON]. En 1980 el consorcio **DIX** —**D**EC, **I**ntel y **X**erox— publica **Ethernet II** a 10 Mbit/s.
- **Normalización (1980-1990).** El **IEEE** crea en febrero de 1980 el **comité 802** —de ahí el nombre: **año 80, mes 2**— y normaliza tres tecnologías en competencia: **802.3** (Ethernet, CSMA/CD), **802.4** (Token Bus) y **802.5** (Token Ring). Es el periodo de la «guerra de las redes locales».
- **Consolidación de Ethernet y del cableado estructurado (1990-2000).** La aparición de **10BASE-T** (1990), que lleva Ethernet al **par trenzado** y a la **topología física de estrella** con concentrador, es el punto de inflexión: el cableado deja de ser una tirada de coaxial y pasa a ser una **infraestructura estructurada y normalizada** [ISO11801]. Ethernet gana la guerra y Token Ring y FDDI desaparecen.
- **Conmutación y velocidad (1995-2010).** El **conmutador** sustituye al concentrador, el **dúplex** elimina las colisiones y llegan **Fast Ethernet** (100 Mbit/s, 1995), **Gigabit Ethernet** (1998 en fibra, 1999 en cobre) y **10 Gigabit** (2002). Aparecen las **VLAN** (802.1Q, 1998) y la **red inalámbrica** (802.11, 1997; 802.11b, 1999).
- **Convergencia y movilidad (2010 en adelante).** El cable de red transporta también **energía** (PoE, 802.3af/at/bt), **voz** (telefonía IP) y **vídeo** (videovigilancia); el acceso inalámbrico deja de ser un complemento y pasa a ser el modo de conexión mayoritario en muchos entornos; y el control de acceso a la red (802.1X) se generaliza por exigencia normativa.

> **[DATO CLAVE EXAMEN]** Tres datos de origen que se preguntan con frecuencia: **Ethernet nació en el Xerox PARC en 1973**, obra de **Metcalfe y Boggs**, a **2,94 Mbit/s**; su antecedente teórico es **ALOHA** (Universidad de Hawái, 1970); y el nombre del comité **IEEE 802** procede de su fecha de creación, **febrero de 1980**.

> **[EJEMPLO AYTO MADRID]** La red local de una Oficina de Atención a la Ciudadanía cumple los cinco rasgos de manual: ocupa **un edificio**; el cableado y los conmutadores son **propiedad del Ayuntamiento** y los mantiene el IAM o su contratista, sin que intervenga ningún operador; el puesto tiene **1 Gbit/s**; el retardo interno es despreciable frente al del enlace con el centro de proceso de datos; y en la sala de espera hay un medio **realmente compartido**, la radio, con todas las consecuencias que se verán en §4.2.2.

### 1.2. Modelo de referencia OSI y arquitectura TCP/IP en el ámbito local

Toda la materia de este tema vive en **las dos capas inferiores** del modelo OSI. Situarla bien es lo que permite después clasificar sin dudas cada dispositivo y cada norma.

**Alcance del comité IEEE 802.** El **ámbito normativo del IEEE 802** se limita a la **capa física (1)** y a la **capa de enlace de datos (2)** del modelo OSI [IEEE802]. Todo lo que hay por encima —IP, TCP, HTTP— es ajeno a la familia 802 y corresponde al IETF. Por eso una red local es, técnicamente, **una tecnología de capas 1 y 2**: proporciona a la capa 3 un servicio de entrega de tramas dentro de un mismo segmento, y nada más.

**La aportación arquitectónica del IEEE: partir la capa 2 en dos.** El modelo OSI define una única capa de enlace. El IEEE constató que, en una red local, esa capa tiene **dos responsabilidades muy distintas**: una que depende íntimamente de la tecnología del medio y otra que no depende de ella en absoluto. De ahí la **división en dos subcapas** (ver **diagrama D2**):

- **LLC** (*Logical Link Control*, **control del enlace lógico**, norma **802.2**), la **subcapa superior**. Ofrece a la capa de red un servicio **uniforme e independiente de la tecnología subyacente**: la capa 3 ve lo mismo tanto si por debajo hay Ethernet como si hay Wi-Fi o Token Ring. Se ocupa de la **multiplexación de protocolos superiores** mediante los puntos de acceso al servicio **DSAP** y **SSAP**, y opcionalmente del **control de errores y de flujo**. Define tres tipos de servicio: **tipo 1**, sin conexión y sin acuse —el único que se usa—; **tipo 2**, orientado a conexión, con numeración, acuse y control de flujo; y **tipo 3**, sin conexión pero con acuse [IEEE8022].
- **MAC** (*Medium Access Control*, **control de acceso al medio**), la **subcapa inferior**. Es **específica de cada tecnología** y resuelve exactamente el problema que da título a §4: **quién transmite y cuándo**. Además delimita la trama, inserta las **direcciones físicas** y calcula la **secuencia de comprobación de trama**.

> **[DATO CLAVE EXAMEN]** La pregunta canónica de este epígrafe: **el IEEE 802 divide la capa de enlace de OSI en dos subcapas, LLC (802.2, común a toda la familia) y MAC (específica de cada tecnología)**. Y el matiz que la acompaña: **solo la subcapa MAC toca el medio**; LLC es indiferente a él. La subcapa MAC no existe como tal en el modelo OSI puro: **es una aportación del IEEE**.

**Una nota sobre la vigencia de LLC.** En la práctica, la subcapa LLC **cayó en desuso**. La razón es histórica: la trama **Ethernet II** de DIX, anterior a la norma, resolvía la multiplexación de protocolos superiores con un campo de **tipo** (`EtherType`) de dos octetos que identifica directamente el protocolo de capa 3 —`0x0800` para IPv4, `0x0806` para ARP, `0x86DD` para IPv6—. La norma 802.3 reinterpretó ese campo como **longitud** y colocó el DSAP y el SSAP dentro de los datos. Convivieron ambas interpretaciones, y **ganó Ethernet II**: prácticamente todo el tráfico de una red local actual usa el campo como `EtherType`. La regla de desambiguación es sencilla y se pregunta: **si el valor del campo es menor o igual que 1500, es una longitud (trama 802.3); si es mayor o igual que 1536 (`0x0600`), es un tipo (trama Ethernet II)**.

**Correspondencia con el modelo TCP/IP.** El modelo de internet [RFC1122] agrupa las dos capas inferiores de OSI en un único nivel de **acceso a la red**. Por tanto, **este tema entero cabe en el nivel de acceso a la red del modelo TCP/IP**. La consecuencia práctica es la que da sentido al reloj de arena de internet: la capa de red se apoya en la red local sin conocerla, de modo que la misma IP viaja indistintamente sobre Ethernet, Wi-Fi o cualquier tecnología futura.

> **[REFERENCIA CRUZADA]** El desarrollo completo del modelo OSI —sus siete capas, el concepto de servicio, interfaz y protocolo, el encapsulamiento y las unidades de datos— y del modelo TCP/IP corresponde al **Tema 34**, que también describe los protocolos de las capas 3 a 7. Aquí solo se usan como marco de clasificación.

**El punto de contacto entre la capa 2 y la capa 3: la dirección.** Merece detenerse porque es la base de §5. La **dirección MAC** identifica un **interfaz físico** y tiene **ámbito local**: solo sirve dentro del segmento. La **dirección IP** identifica un **nodo en una red** y tiene **ámbito global**. Un dispositivo de capa 2 —conmutador— toma decisiones **por dirección MAC** y no mira la dirección IP; un dispositivo de capa 3 —encaminador— decide **por dirección IP** y reescribe las direcciones MAC en cada salto. Toda la tabla de clasificación de dispositivos de §5 se deduce de esta frase.

**La dirección MAC** [IEEE802] tiene **48 bits** (6 octetos), se escribe en hexadecimal y su estructura es la siguiente: los **24 primeros bits** son el **identificador único de organización (OUI)** que el IEEE asigna al fabricante, y los 24 restantes los asigna el fabricante a cada tarjeta. Dos bits del primer octeto tienen significado propio y se preguntan:

- El **bit I/G** (individual o de grupo), que es el **menos significativo del primer octeto**: a **0** indica dirección **individual** (unidifusión) y a **1**, dirección **de grupo** (multidifusión o difusión). La dirección de **difusión** es `FF:FF:FF:FF:FF:FF`, con todos los bits a 1.
- El **bit U/L** (universal o local), el **segundo menos significativo del primer octeto**: a **0** indica dirección **administrada universalmente** —la que grabó el fabricante— y a **1**, **administrada localmente**, es decir, asignada por software. Es el bit que se activa cuando un sistema operativo **aleatoriza** la dirección MAC de su interfaz Wi-Fi por privacidad, una práctica hoy generalizada que tiene consecuencias directas sobre el inventario y el control de acceso de una red municipal.

### 1.3. Normalización y familias de estándares IEEE 802

El **comité IEEE 802**, creado en **febrero de 1980**, organiza su trabajo en **grupos de trabajo** identificados por un número tras el punto, y dentro de cada grupo por **letras** que designan enmiendas sucesivas. Conocer el reparto es de las cosas más rentables del tema, porque produce preguntas cerradas.

**Los grupos que hay que saber** [IEEE802]:

| Norma | Materia | Estado |
|---|---|---|
| **802.1** | **Arquitectura, gestión e interconexión**. Es el grupo transversal: puentes, VLAN, árbol de expansión y control de acceso | Activo |
| **802.2** | **LLC**, control del enlace lógico. Subcapa superior del nivel 2, común a la familia | Retirado (absorbido) |
| **802.3** | **Ethernet**: CSMA/CD y todas sus variantes físicas y de velocidad | Activo |
| **802.4** | **Token Bus**: paso de testigo sobre bus físico. Entorno industrial (perfil **MAP**) | Retirado |
| **802.5** | **Token Ring**: paso de testigo en anillo. Impulsado por IBM | Retirado |
| **802.6** | **DQDB**, red de área metropolitana de doble bus con cola distribuida | Retirado |
| **802.11** | **WLAN**, red de área local **inalámbrica**. Denominación comercial **Wi-Fi** | Activo |
| **802.15** | **WPAN**, red de área personal: **802.15.1** Bluetooth, **802.15.4** base de **Zigbee** y de otras redes de sensores | Activo |
| **802.16** | **WMAN**, red de área metropolitana inalámbrica. Denominación comercial **WiMAX** | Retirado |
| **802.17** | **RPR**, anillo de paquetes con recuperación (*Resilient Packet Ring*) | Retirado |
| **802.22** | **WRAN**, red regional inalámbrica sobre espacios en blanco de televisión | Activo |

**Dentro de 802.1**, las cuatro enmiendas de cita obligada:

- **802.1D** — **puentes transparentes** y **árbol de expansión (STP)**.
- **802.1Q** — **redes de área local virtuales (VLAN)** y etiquetado de trama. Desde 2018 incorpora también el árbol de expansión y la priorización.
- **802.1p** — **priorización de tráfico** mediante los tres bits de prioridad de la etiqueta 802.1Q. Nunca fue una norma independiente: es parte de 802.1Q, aunque el nombre se ha consolidado.
- **802.1X** — **control de acceso a la red basado en puerto**.

**Dentro de 802.3**, las enmiendas que conviene ubicar: **802.3u** (Fast Ethernet, 100 Mbit/s), **802.3z** y **802.3ab** (Gigabit en fibra y en cobre), **802.3ae** y **802.3an** (10 Gigabit en fibra y en cobre), **802.3bz** (2,5 y 5 Gbit/s sobre cableado existente de Cat 5e y Cat 6, pensado precisamente para alimentar puntos de acceso Wi-Fi 6 sin recablear), **802.3x** (control de flujo), **802.3ad** (agregación de enlaces, hoy **802.1AX**) y **802.3af/at/bt** (**PoE**).

**Dentro de 802.11**, la correspondencia entre la numeración del IEEE y la **denominación comercial por generaciones** que fija la Wi-Fi Alliance [WIFI-ALLIANCE]:

| Norma IEEE | Nombre comercial | Banda | Novedad principal |
|---|---|---|---|
| **802.11** (1997) | — | 2,4 GHz | 1 y 2 Mbit/s. Norma original |
| **802.11b** (1999) | — | 2,4 GHz | 11 Mbit/s. La que popularizó la tecnología |
| **802.11a** (1999) | — | 5 GHz | 54 Mbit/s con **OFDM** |
| **802.11g** (2003) | — | 2,4 GHz | 54 Mbit/s, OFDM en 2,4 GHz, compatible con 802.11b |
| **802.11n** (2009) | **Wi-Fi 4** | 2,4 y 5 GHz | **MIMO**, agregación de tramas, canales de 40 MHz |
| **802.11ac** (2013) | **Wi-Fi 5** | 5 GHz | Canales de 80 y 160 MHz, **MU-MIMO** de bajada |
| **802.11ax** (2021) | **Wi-Fi 6** / **6E** | 2,4, 5 y **6 GHz** | **OFDMA**, **BSS Coloring**, **TWT**. La variante **6E** es la que abre la banda de 6 GHz |
| **802.11be** (2025) | **Wi-Fi 7** | 2,4, 5 y 6 GHz | Canales de **320 MHz**, **MLO** (operación multienlace), 4096-QAM |
| **802.11bn** (previsto 2028) | **Wi-Fi 8** | 2,4, 5 y 6 GHz | Objetivo declarado: **fiabilidad ultraalta**, no más velocidad de pico |

> **[DATO CLAVE EXAMEN]** Los datos de actualidad que distinguen un temario al día de uno desfasado, verificados en agosto de 2026: **802.11be (Wi-Fi 7) se publicó el 22 de julio de 2025**; **802.11bn (Wi-Fi 8) está en fase de borrador**, con aprobación prevista para **2028**, y su objetivo declarado **no es la velocidad de pico sino la fiabilidad**; y en Ethernet, **802.3df-2024** normalizó los **800 Gbit/s** y **P802.3dj**, en desarrollo, llegará a **1,6 Tbit/s**.

> **[DATO CLAVE EXAMEN]** Errores de atribución que se preguntan a menudo: **802.1Q es VLAN, no seguridad**; **802.1X es control de acceso, no cifrado inalámbrico**; **802.11i es la seguridad inalámbrica (WPA2)**; **802.15.1 es Bluetooth y 802.15.4 es la base de Zigbee**; y **802.16 es WiMAX**, una red metropolitana, no una red local.

> **[EJEMPLO AYTO MADRID]** En un pliego de contratación del suministro de electrónica de red para una junta de distrito, las normas IEEE aparecen literalmente en las prescripciones técnicas: se exige que los conmutadores soporten **IEEE 802.1Q**, **802.1D/w/s**, **802.1X**, **802.3ad** de agregación y **802.3at o 802.3bt** de alimentación, y que los puntos de acceso soporten **802.11ax** y **802.11i** con **WPA3**. Citar la norma y no la marca no es solo buena práctica técnica: el **artículo 126.6 de la Ley 9/2017** prohíbe mencionar una marca en las prescripciones técnicas salvo que resulte imprescindible, y aun entonces con la coletilla «o equivalente» [LCSP].

---

## 2. Tipología de redes locales

### 2.1. Clasificación según cobertura y alcance geográfico

La clasificación por **alcance geográfico** es la más antigua y la que abre casi todos los manuales. Su utilidad no está en las cifras, que son orientativas, sino en el **criterio que hay detrás de cada frontera** (ver **diagrama D3**).

| Tipo | Denominación | Alcance orientativo | Titularidad del medio | Ejemplo |
|---|---|---|---|---|
| **BAN / PAN** | Red de área corporal o **personal** | Centímetros a **10 m** | Del usuario | Bluetooth (802.15.1), NFC, teclado inalámbrico, auricular |
| **LAN** | Red de área **local** | Hasta **1-2 km**, un edificio o recinto | **De la organización** | Ethernet y Wi-Fi de una oficina municipal |
| **CAN** | Red de área de **campus** | **1-10 km**, varios edificios contiguos | De la organización | Conjunto de edificios de un mismo complejo administrativo |
| **MAN** | Red de área **metropolitana** | **10-100 km**, una ciudad | Mixta: propia, cedida o de operador | Red que une las sedes municipales de una ciudad |
| **WAN** | Red de área **extensa** | **Más de 100 km**, país o continente | **De operador**, contratada | Enlaces entre sedes de distintas provincias; internet |
| **GAN** | Red de área **global** | Mundial | De operadores | Interconexión de WAN. En la práctica, internet |

**Los criterios que de verdad separan una LAN de una WAN**, y que son lo que hay que saber razonar, son **cuatro** y solo uno es el alcance:

1. **Propiedad del medio.** En la LAN, propio; en la WAN, de un operador. Es el criterio decisivo.
2. **Velocidad y retardo.** La LAN opera en gigabits con retardos de microsegundos; la WAN, con velocidades contratadas y retardos de milisegundos.
3. **Tecnología de acceso.** La LAN nació con un **medio compartido** y necesita un método de acceso; la WAN usa enlaces **punto a punto** y su problema no es el acceso sino el **encaminamiento**.
4. **Régimen jurídico.** Explotar una red de área extensa que cruce el dominio público exige títulos habilitantes y sujeción a la **Ley 11/2022**; la red interior de un edificio no [LGT].

> **[DATO CLAVE EXAMEN]** Si una pregunta ofrece varias características para identificar una red local, **el criterio que discrimina es la titularidad privada del medio**, no la distancia. Una red que une dos edificios municipales separados por 800 metros mediante **fibra propia** es una red local (o de campus); si esos mismos 800 metros se cubren con un **enlace contratado a un operador**, técnicamente ya no lo es.

**Las redes de almacenamiento (SAN).** Merece una mención porque aparece en las clasificaciones y se confunde. Una **SAN** (*Storage Area Network*) es una **red especializada en el tráfico entre servidores y sistemas de almacenamiento**, con protocolos propios (**Fibre Channel**, **iSCSI**, **FCoE**, **NVMe over Fabrics**). No es una categoría de alcance sino de **función**: puede estar contenida dentro de un centro de proceso de datos y ser, en términos de alcance, una red local.

> **[REFERENCIA CRUZADA]** Las redes de almacenamiento y su virtualización —SAN frente a NAS, y los protocolos de bloque frente a los de archivo— se desarrollan en el **Tema 26**. Las redes de área extensa, las tecnologías de conmutación y las comunicaciones móviles, en el **Tema 33**.

### 2.2. Topologías físicas y lógicas de red

La **topología** de una red es la **forma en que se disponen e interconectan sus nodos**. La distinción que abre este epígrafe es la que más se pregunta de toda la sección y hay que fijarla antes de describir ninguna topología concreta:

- **Topología física**: **cómo está tendido el cable**. Es lo que se ve al levantar el falso techo.
- **Topología lógica**: **cómo circula la información** entre los nodos, es decir, qué estaciones oyen a qué otras y cómo se comparte el medio. Es lo que determina el método de acceso.

**Ambas pueden no coincidir, y de hecho casi nunca coinciden.** Los tres casos que se preguntan (ver **diagrama D5**):

| Red | Topología física | Topología lógica | Explicación |
|---|---|---|---|
| **Ethernet con concentrador** | **Estrella** | **Bus** | El concentrador **repite por todos los puertos**: eléctricamente sigue siendo un bus, con colisiones |
| **Token Ring con MAU** | **Estrella** | **Anillo** | La unidad de acceso al medio concentra el cableado, pero el testigo recorre las estaciones **una tras otra** |
| **Ethernet con conmutador** | **Estrella** | **Punto a punto conmutado** | Cada puerto es un **enlace independiente** en dúplex: ya no hay bus ni colisiones |

> **[DATO CLAVE EXAMEN]** La respuesta a «¿qué topología tiene una red Ethernet con concentrador?» es **estrella física y bus lógico**. Y la clave conceptual: **el concentrador no cambia la topología lógica, solo el cableado**. Fue precisamente el conmutador —no el concentrador— el que acabó con el bus lógico y, con él, con las colisiones.

#### 2.2.1. Topologías básicas: estrella, bus, anillo y malla

Las cuatro topologías básicas se comparan siempre por los mismos **cinco criterios**: cantidad de cable, punto único de fallo, comportamiento ante la rotura de un enlace, facilidad para añadir un nodo y método de acceso que imponen (ver **diagrama D4**).

**Bus.** Todos los nodos cuelgan de un **único medio compartido**, terminado en ambos extremos por resistencias que evitan reflexiones.

- **Ventajas**: **mínima cantidad de cable**, instalación sencilla y barata, no requiere equipo central.
- **Inconvenientes**: **una rotura del bus parte la red en dos** y la deja inoperativa; el diagnóstico de averías es difícil porque no hay punto central donde mirar; el medio es **compartido**, lo que obliga a un método de acceso y limita el rendimiento al crecer el número de nodos.
- **Realización histórica**: **10BASE5** («Ethernet grueso», coaxial de 10 mm, hasta **500 m** por segmento, conexión mediante **transceptor de vampiro**) y **10BASE2** («Ethernet fino», coaxial RG-58, hasta **185 m**, conexión mediante **conector en T** y BNC).

**Estrella.** Todos los nodos se conectan a un **equipo central** —concentrador o conmutador— mediante un enlace propio.

- **Ventajas**: la rotura de un cable **afecta solo a ese nodo**; el diagnóstico es sencillo porque todo pasa por el centro; añadir un nodo es conectar un cable; permite **gestión centralizada** y alimentación **PoE**.
- **Inconvenientes**: **mayor cantidad de cable**; y sobre todo, el equipo central es un **punto único de fallo**.
- Es la **topología física universal** de la red local moderna, y la que presupone el cableado estructurado.

**Anillo.** Cada nodo se conecta al siguiente formando un **circuito cerrado**; la información circula en **un solo sentido** y **cada estación regenera la señal**.

- **Ventajas**: la regeneración en cada nodo permite **cubrir distancias largas**; el acceso es **determinista** y el retardo máximo, **acotado**; el rendimiento **no se degrada** con la carga como en el bus.
- **Inconvenientes**: **el fallo de un nodo o de un enlace rompe el anillo**, salvo que haya doble anillo o conmutación de derivación; añadir una estación obliga a **interrumpir el servicio**; y hay latencia añadida por el paso por cada nodo.
- **Realización histórica**: **Token Ring** (802.5) y **FDDI**, que resuelve la fragilidad con un **doble anillo contrarrotante**.

**Malla.** Los nodos se conectan entre sí con **enlaces redundantes**. En la **malla completa** todos con todos, lo que exige `n × (n − 1) / 2` enlaces; en la **malla parcial**, solo los pares que interesan.

- **Ventajas**: **máxima tolerancia a fallos** y múltiples caminos alternativos; ausencia de punto único de fallo.
- **Inconvenientes**: **coste de cableado prohibitivo** y complejidad de gestión.
- **Uso real**: no se usa como topología de acceso, sino **entre los conmutadores de núcleo** de un centro de proceso de datos y en las redes malladas inalámbricas (*mesh*).

> **[EJERCICIO RESUELTO]** ¿Cuántos enlaces necesita una malla completa de 12 conmutadores, y cuántos interfaces por equipo? La fórmula del número de enlaces de una malla completa es `n × (n − 1) / 2`. Con `n = 12`: `12 × 11 / 2 = 66 enlaces`. Cada equipo necesita `n − 1 = 11 interfaces` dedicados solo a la malla, además de los puertos de acceso. Ahí está la razón por la que la malla completa no se usa en la práctica más allá de un puñado de nodos: **el número de enlaces crece con el cuadrado del número de nodos**, mientras que en una estrella crece linealmente. Comparación: la misma red en estrella necesitaría **12 enlaces** y **un interfaz por equipo**.

**Otras topologías que se citan.** El **árbol** o topología jerárquica es una extensión de la estrella en varios niveles, y es la que realmente adopta un edificio cableado: un armario por planta y un armario principal. La topología **punto a punto** es el caso degenerado de dos nodos unidos por un enlace exclusivo, que es lo que hay hoy en cada puerto de conmutador. Y la topología **celular** describe la cobertura por áreas de una red inalámbrica.

#### 2.2.2. Topologías híbridas y estructuras jerárquicas

Ninguna red real de cierto tamaño responde a una topología pura: todas son **híbridas**. Las combinaciones con nombre propio son la **estrella-bus** (varias estrellas unidas por un troncal), la **estrella-anillo** (varias estrellas cuyos concentradores forman un anillo) y, sobre todas, el **árbol**.

**El árbol o topología jerárquica** es la estructura de la red local moderna, y coincide punto por punto con la del cableado estructurado (§6.1). Se organiza en **tres niveles**:

1. **Nivel de acceso.** Los conmutadores a los que se conectan directamente los puestos, los teléfonos, las impresoras, las cámaras y los puntos de acceso. Están en el **armario de planta**. Sus rasgos: alta densidad de puertos, **PoE**, y funciones de seguridad de borde (802.1X, control de tormentas de difusión).
2. **Nivel de distribución.** Agrega los conmutadores de acceso del edificio, aplica políticas y hace el **encaminamiento entre VLAN**. Está en el **armario principal**.
3. **Nivel de núcleo.** Interconecta a alta velocidad los bloques de distribución. En una oficina pequeña se **colapsa** con el de distribución —arquitectura llamada de **núcleo colapsado** o de **dos capas**—, que es lo habitual fuera de un centro de proceso de datos.

**La ventaja de la jerarquía** no es estética: es que **acota el alcance de los problemas**. Un bucle, una tormenta de difusión o un fallo de configuración quedan contenidos en su bloque en lugar de propagarse por toda la red. Y permite dimensionar el ancho de banda por niveles: si veinticuatro puestos de 1 Gbit/s cuelgan de un conmutador de acceso, su enlace ascendente debe ser de 10 Gbit/s o llevar varios enlaces agregados, no de 1 Gbit/s.

> **[EJERCICIO RESUELTO]** Una planta de la Oficina de Atención a la Ciudadanía tiene **44 puestos de 1 Gbit/s**, **12 teléfonos IP** y **6 cámaras**. ¿Basta con un enlace ascendente de 1 Gbit/s? El planteamiento correcto **no es sumar los 62 gigabits nominales**, porque nunca transmiten todos a la vez: se trabaja con una **relación de sobresuscripción** aceptada. La práctica habitual en el nivel de acceso admite entre **20:1 y 4:1**. Con 62 puertos de 1 Gbit/s y un ascendente de 1 Gbit/s la relación es de **62:1**, muy por encima de lo aceptable; con **10 Gbit/s** baja a **6,2:1**, que sí es razonable. Conclusión: **el enlace ascendente debe ser de 10 Gbit/s**, o bien dos enlaces de 1 Gbit/s agregados (802.1AX) si el presupuesto lo impone, asumiendo 31:1. Obsérvese que el tráfico de las cámaras es **continuo y ascendente**, a diferencia del de los puestos, que es a ráfagas: en una red con mucha videovigilancia la sobresuscripción admisible es menor.

> **[EJEMPLO AYTO MADRID]** El edificio de tres plantas de la oficina de referencia adopta exactamente esa estructura: un **armario de planta** con un conmutador de acceso de 48 puertos con PoE en cada planta, un **armario principal** en la planta baja junto al recinto de instalaciones de telecomunicación, y **fibra óptica multimodo** entre cada armario de planta y el principal. Físicamente hay **tres estrellas colgando de una cuarta**: un árbol. Lógicamente, cada puerto es un enlace punto a punto y la red está partida en VLAN, de modo que la topología lógica no se parece en nada al dibujo del cableado.

### 2.3. Clasificación por medio físico y tecnología

El tercer criterio de clasificación es el **medio**, del que se derivan casi todas las propiedades operativas de la red. La división primaria es entre **redes cableadas** —medio guiado— y **redes inalámbricas** —medio no guiado—, y sobre ella se superpone la tecnología concreta.

#### 2.3.1. Redes locales cableadas

**Ethernet (IEEE 802.3) es hoy prácticamente la única tecnología de red local cableada**, tras la desaparición de sus competidoras. Su nomenclatura de variantes físicas es de las cosas que más se preguntan porque es sistemática y, una vez entendida, se deduce:

**`<velocidad>` + `BASE` o `BROAD` + `<medio o codificación>`**

- El **número inicial** es la velocidad en **megabits por segundo** (o con la letra `G`, en gigabits).
- **`BASE`** indica **banda base** y **`BROAD`**, banda ancha. Salvo la histórica y nunca implantada 10BROAD36, **toda Ethernet es de banda base**.
- El **sufijo** identifica el medio o la codificación: en las primeras normas era la longitud máxima del segmento en centenares de metros (**10BASE5** = 500 m; **10BASE2** ≈ 185 m); después pasó a designar el medio y el número de pares o de longitudes de onda: **`T`** par trenzado (*twisted*), **`F`** fibra, **`S`** fibra multimodo (*short*), **`L`** fibra monomodo (*long*), **`X`** codificación en bloque.

| Variante | Norma | Velocidad | Medio | Distancia máxima |
|---|---|---|---|---|
| **10BASE5** | 802.3 | 10 Mbit/s | Coaxial grueso | **500 m** por segmento |
| **10BASE2** | 802.3a | 10 Mbit/s | Coaxial fino RG-58 | **185 m** por segmento |
| **10BASE-T** | 802.3i | 10 Mbit/s | Par trenzado Cat 3 (2 pares) | **100 m** |
| **100BASE-TX** | 802.3u | 100 Mbit/s | Par trenzado Cat 5 (**2 pares**) | **100 m** |
| **100BASE-FX** | 802.3u | 100 Mbit/s | Fibra multimodo | 2 km (dúplex) |
| **1000BASE-T** | 802.3ab | 1 Gbit/s | Par trenzado Cat 5e (**los 4 pares**) | **100 m** |
| **1000BASE-SX** | 802.3z | 1 Gbit/s | Fibra multimodo 850 nm | 220-550 m |
| **1000BASE-LX** | 802.3z | 1 Gbit/s | Fibra monomodo 1310 nm | 5 km |
| **2.5GBASE-T / 5GBASE-T** | 802.3bz | 2,5 y 5 Gbit/s | Cat 5e y Cat 6 **existentes** | **100 m** |
| **10GBASE-T** | 802.3an | 10 Gbit/s | Cat 6A | **100 m** (Cat 6: 55 m) |
| **10GBASE-SR / LR** | 802.3ae | 10 Gbit/s | Fibra multimodo / monomodo | 300 m / 10 km |

> **[DATO CLAVE EXAMEN]** El dato de distancia que hay que llevar grabado: **100 metros es la longitud máxima del canal de par trenzado**, con independencia de la velocidad, desde 10BASE-T hasta 10GBASE-T. Y su desglose normalizado: **90 m de cable horizontal fijo más 10 m de latiguillos** [ISO11801]. Otro dato de precisión: **10BASE-T y 100BASE-TX usan solo dos pares** de los cuatro; **1000BASE-T y superiores usan los cuatro**, en ambos sentidos simultáneamente. De ahí que una avería en un par pueda dejar una red funcionando a 100 Mbit/s pero no a 1 Gbit/s: es un síntoma de diagnóstico clásico.

**Otra tecnología cableada que conviene citar**: **PLC** (*Power Line Communications*), que transmite datos por la red eléctrica del edificio. No es una red local normalizada por el IEEE 802 —su norma es **IEEE 1901**— y en entorno profesional se descarta por su baja fiabilidad y por la facilidad con que la señal se escapa fuera del recinto, con el riesgo de seguridad que ello supone. Su uso queda para el ámbito doméstico o para salvar un punto concreto sin cableado.

#### 2.3.2. Redes locales inalámbricas

Una **WLAN** (**802.11**) sustituye el medio guiado por el **espectro radioeléctrico**, lo que cambia radicalmente cinco cosas: el medio pasa a ser **realmente compartido** y además **no acotado** físicamente, el **método de acceso** debe cambiar (§4.2.2), la **seguridad** deja de apoyarse en el control físico del cable, la **calidad** varía con la distancia y las interferencias, y el **régimen jurídico** del medio es el del dominio público radioeléctrico.

**Arquitectura y vocabulario** [IEEE80211]:

- **Estación (STA)**: cualquier dispositivo con interfaz 802.11.
- **Punto de acceso (AP)**: estación que además hace de **puente** entre el medio inalámbrico y el cableado. Es un dispositivo de **capa 2**.
- **BSS** (*Basic Service Set*): conjunto de estaciones asociadas a un mismo punto de acceso. Su identificador, el **BSSID**, es normalmente **la dirección MAC de la radio del punto de acceso**.
- **ESS** (*Extended Service Set*): varios BSS unidos por un **sistema de distribución** —normalmente la red cableada— que se presentan al usuario como **una sola red**, con un mismo **SSID**. Es lo que permite el **itinerancia** (*roaming*) al moverse por el edificio.
- **IBSS** o modo **ad hoc**: estaciones que se comunican entre sí **sin punto de acceso**.

**Las tres bandas** en las que opera una red local inalámbrica, y sus compromisos:

| Banda | Anchura útil | Alcance y penetración | Interferencia | Canales sin solape |
|---|---|---|---|---|
| **2,4 GHz** | Estrecha (unos 83 MHz) | **Mejor alcance** y mejor penetración en muros | **Muy alta**: microondas, Bluetooth, mandos, sensores | **3** (canales **1, 6 y 11**) con 20 MHz |
| **5 GHz** | Amplia | Menor alcance, peor penetración | Baja | Más de 20 con 20 MHz; menos al ensanchar |
| **6 GHz** | Muy amplia (Wi-Fi 6E y 7) | El menor alcance de las tres | **Muy baja**: banda nueva | Hasta 59 con 20 MHz; **7 canales de 160 MHz** |

> **[DATO CLAVE EXAMEN]** El dato de la banda de 2,4 GHz que se pregunta siempre: **solo hay tres canales que no se solapan, el 1, el 6 y el 11**, porque cada canal ocupa 20-22 MHz y los canales están separados solo 5 MHz. Es la razón por la que en un edificio con muchos puntos de acceso la banda de 2,4 GHz se satura y se recomienda planificar la cobertura en **5 GHz**, dejando 2,4 GHz para los dispositivos que no admiten otra cosa.

> **[DATO CLAVE EXAMEN]** El régimen jurídico, que casi ningún temario recoge y es directamente examinable: el **artículo 88 de la Ley 11/2022** clasifica el uso del dominio público radioeléctrico en **común, especial y privativo**, y establece que **el uso común no precisa de ningún título habilitante** y se lleva a cabo en las bandas y con las características técnicas que se fijen. **Wi-Fi opera en régimen de uso común**: por eso el Ayuntamiento puede desplegar puntos de acceso sin licencia, pero **debe respetar las condiciones técnicas del CNAF** —potencia máxima radiada y, en determinadas subbandas de 5 GHz, **selección dinámica de frecuencia (DFS)** y **control automático de potencia (TPC)**— y **no tiene protección frente a interferencias** de otros usuarios de la misma banda [LGT] [SETSI].

**El resto de las tecnologías inalámbricas de ámbito reducido**, que se citan para completar la clasificación y no se desarrollan: **Bluetooth** (802.15.1), red de área personal de bajo consumo y corto alcance; **Zigbee** y **Thread** sobre **802.15.4**, para redes de sensores y domótica; **NFC**, de alcance centimétrico; y **WiMAX** (802.16), que es una red **metropolitana** y no local, hoy retirada.

> **[REFERENCIA CRUZADA]** Las comunicaciones móviles celulares (de 2G a 5G), la evolución de las redes inalámbricas metropolitanas y extensas y los parámetros de caracterización del espectro se desarrollan en el **Tema 33**. El sistema **TETRA** de radiocomunicación en grupo, en el **Tema 38**. La seguridad de las redes inalámbricas —WPA2, WPA3, portal cautivo, red de invitados— y su encaje en el ENS, en el **Tema 36** y, en lo que atañe a la red local, en §6.2 de este tema.

---

## 3. Técnicas de transmisión

Esta sección responde a la pregunta «cómo se ponen los bits en el medio». Es la parte más **densa en datos** del tema y la que más se beneficia de estudiarse con las tablas y los diagramas delante. Conviene abordarla con un orden mental fijo: primero **en qué sentido** circula la información (§3.1), después **qué se pone en el medio**, si la señal digital tal cual o una portadora modulada (§3.2), luego **con qué código o modulación** concretos (§3.3), después **cómo se comparte un mismo medio entre varias señales** (§3.4) y, por último, **por qué medio físico** (§3.5).

### 3.1. Modos y sentidos de transmisión de datos

Hay **tres clasificaciones independientes** que se solapan y que conviene no mezclar, porque las preguntas juegan precisamente con eso (ver **diagrama D6**).

**Primera: según el sentido de la comunicación.**

| Modo | Descripción | Ejemplo |
|---|---|---|
| **Símplex** | **Un solo sentido**, siempre el mismo. Emisor y receptor no intercambian papeles | Radiodifusión, teclado a ordenador, sensor a central |
| **Semidúplex** (*half-duplex*) | **Ambos sentidos, pero no a la vez**. Hay que alternar el turno | Walkie-talkie, **Ethernet con concentrador**, **Wi-Fi** |
| **Dúplex** (*full-duplex*) | **Ambos sentidos simultáneamente** | Telefonía, **Ethernet conmutada** |

Esta clasificación es la que **más consecuencias tiene en este tema**, y por una razón concreta: **el método de acceso al medio solo hace falta cuando la transmisión es semidúplex sobre medio compartido**. En cuanto un enlace es dúplex y punto a punto, no hay con quién colisionar y **CSMA/CD deja de tener sentido y se desactiva**. Toda la evolución de la red local cableada —del bus coaxial al conmutador— se puede resumir como el paso del semidúplex compartido al dúplex punto a punto. Y a la inversa: **la red inalámbrica sigue siendo semidúplex** —una radio no puede transmitir y recibir en la misma frecuencia al mismo tiempo— y por eso conserva íntegro el problema del acceso al medio.

**Segunda: según el número de líneas.**

- **Transmisión serie**: los bits se envían **uno tras otro** por un único canal. Necesita menos conductores, no sufre desfase entre líneas y es la única viable a distancia y a alta velocidad. **Toda red local es serie**.
- **Transmisión paralelo**: varios bits **simultáneamente** por conductores distintos. Rápida en distancias muy cortas, pero a alta frecuencia sufre **desviación de sincronismo** (*skew*) y diafonía entre líneas, lo que la ha eliminado incluso de los buses internos del ordenador.

Un matiz que se pregunta: **1000BASE-T transmite por los cuatro pares a la vez, y eso no lo convierte en transmisión paralelo**. Lo que hace es **multiplexar** un único flujo serie sobre cuatro canales físicos, cada uno de ellos serie; no envía cuatro bits del mismo símbolo por cuatro hilos distintos.

**Tercera: según el sincronismo.**

- **Transmisión asíncrona**: se transmite **carácter a carácter**, y cada carácter se delimita con un **bit de arranque** y uno o dos **bits de parada**. No hace falta un reloj común, pero el rendimiento es bajo —de 10 bits transmitidos, 8 son útiles: un **20 % de sobrecarga**—. Es la del puerto serie clásico.
- **Transmisión síncrona**: se transmiten **bloques o tramas** completos, y emisor y receptor mantienen la sincronización mediante un **reloj común** o, más habitualmente, mediante un **código de línea autosincronizante** que permite extraer el reloj de la propia señal (§3.3). Es la de **todas las redes locales**.
- **Transmisión isócrona**: variante con **retardo constante y garantizado** entre unidades, propia del tráfico de voz y vídeo en tiempo real.

> **[DATO CLAVE EXAMEN]** Tres asociaciones que hay que tener automatizadas: **Ethernet con concentrador es semidúplex y Ethernet con conmutador es dúplex**; **Wi-Fi es siempre semidúplex**, y esa es la razón última de que use CSMA/CA y no CSMA/CD; y **todas las redes locales son de transmisión serie y síncrona**.

### 3.2. Transmisión en banda base y banda ancha

La distinción es de las que más confusión generan, porque la palabra «banda ancha» tiene en el lenguaje comercial un significado distinto —«conexión rápida a internet»— del que tiene aquí.

**Transmisión en banda base.** La señal digital se transmite **tal cual**, ocupando **todo el ancho de banda del medio** y sin desplazarla en frecuencia. No hay portadora ni modulación en el sentido clásico: solo una **codificación de línea** que convierte los bits en niveles de tensión, de corriente o de luz.

- **Un solo canal** por medio: el medio no puede transportar dos comunicaciones simultáneas.
- Transmisión **bidireccional** por naturaleza en un mismo conductor (aunque en la práctica se usen pares distintos por sentido).
- Requiere **regeneración periódica** de la señal, porque la atenuación limita la distancia.
- Equipo terminal **sencillo y barato**.
- **Es el modo de toda la familia Ethernet**, y de ahí la partícula **`BASE`** de su nomenclatura: 10BASE-T, 1000BASE-T, 10GBASE-T.

**Transmisión en banda ancha.** La señal digital **modula una portadora** de alta frecuencia, de modo que ocupa solo **una banda o canal** dentro del espectro del medio. Como quedan libres las demás bandas, el mismo medio puede transportar **varias comunicaciones simultáneas** mediante multiplexación por división de frecuencia (§3.4).

- **Múltiples canales** por medio, cada uno con su portadora.
- Transmisión **unidireccional por canal**: como la amplificación es direccional, hace falta **un canal para cada sentido** —o dos cables, o una división del espectro en banda de subida y de bajada—, y una **cabecera** que traslade la frecuencia.
- Cubre **distancias mayores** que la banda base con la misma calidad.
- Equipo terminal **más complejo y caro** (módem).
- Es el modo de la **televisión por cable**, de **DOCSIS**, de **ADSL/VDSL** y, en su versión radioeléctrica, de **Wi-Fi**.

> **[DATO CLAVE EXAMEN]** Las tres diferencias que se preguntan, en su forma más compacta: **banda base = señal digital sin modular + un solo canal + bidireccional + Ethernet**; **banda ancha = señal modulada sobre portadora + varios canales por división de frecuencia + unidireccional por canal + televisión por cable y DSL**. Y la trampa recurrente: la única Ethernet de banda ancha que llegó a normalizarse fue **10BROAD36**, que **nunca se implantó**; **toda Ethernet real es de banda base**.

Una precisión conceptual que ordena la confusión anterior: **Wi-Fi es banda ancha en sentido técnico** —modula una portadora de 2,4, 5 o 6 GHz—, aunque coloquialmente se hable de la red inalámbrica como parte de la red local «de banda base». Y la fibra óptica, aun transmitiendo pulsos de luz sin modular una portadora eléctrica, admite ambos modos: **banda base** en un enlace Ethernet convencional y **banda ancha** cuando se multiplexan varias longitudes de onda (**WDM**).

### 3.3. Técnicas de modulación y codificación de señal

Aquí conviene separar dos operaciones que suelen confundirse:

- **Codificación de línea** (banda base): convertir una **secuencia de bits** en una **secuencia de niveles o símbolos** de la señal, sin desplazarla en frecuencia.
- **Modulación** (banda ancha): hacer que los bits **alteren un parámetro de una portadora** senoidal: su amplitud, su frecuencia o su fase.

**Qué se le pide a una buena codificación de línea** [STALLINGS], porque de ahí se deducen todas las que vienen después: que la señal **no tenga componente continua** —que la media de tensión sea cero, para poder acoplar el circuito con transformadores y no cargar el medio—; que permita **extraer el reloj** de la propia señal (**autosincronización**), evitando que una larga cadena de bits iguales haga perder la cuenta al receptor; que sea **eficiente en ancho de banda**, es decir, que necesite el menor número de transiciones por bit; y que facilite la **detección de errores** en la propia capa física.

**Las codificaciones de línea que hay que conocer** (ver **diagrama D8**):

| Código | Cómo funciona | Autosincroniza | Componente continua | Uso |
|---|---|---|---|---|
| **NRZ** (sin retorno a cero) | Un nivel para el 1 y otro para el 0, mantenido todo el intervalo | **No** | Sí | Enlaces cortos, base de otros códigos |
| **NRZI** (NRZ invertido) | **Hay transición** para el 1 y **no la hay** para el 0 (codificación diferencial) | Parcial | Sí | Combinado con 4B/5B en 100BASE-FX; USB |
| **Manchester** | **Transición en mitad de cada intervalo de bit**: de bajo a alto para el 1 y de alto a bajo para el 0 (o al revés según convenio) | **Sí, siempre** | **No** | **10BASE-T y 10BASE5** |
| **Manchester diferencial** | Transición central siempre (reloj); el bit se codifica por la **presencia o ausencia de transición al inicio** | **Sí** | No | **Token Ring (802.5)** |
| **4B/5B** | Cada **4 bits** se sustituyen por un símbolo de **5 bits** elegido de modo que nunca haya más de tres ceros seguidos | Habilita la sincronización | — | **100BASE-TX y FX** (con MLT-3 o NRZI) |
| **MLT-3** | **Tres niveles** (−1, 0, +1) recorridos cíclicamente: hay transición al siguiente nivel para el 1 y no la hay para el 0 | Con 4B/5B | No | **100BASE-TX** |
| **8B/10B** | Cada **8 bits** se sustituyen por **10**, con equilibrio de unos y ceros (*disparidad*) | Sí | **No** | **1000BASE-X** (fibra), Fibre Channel, PCIe |
| **4D-PAM5** | **Cinco niveles** de amplitud (**PAM-5**) transmitidos simultáneamente por **los cuatro pares** (*4 dimensiones*), con el quinto nivel usado para corrección de errores | Sí | No | **1000BASE-T** |
| **64B/66B** | Cada **64 bits** se transmiten en **66**, con solo 2 bits de sobrecarga (**3,125 %**), frente al 25 % de 8B/10B | Sí | Aleatorizado | **10GBASE-R** y superiores |
| **DSQ128 / PAM-16** | 16 niveles de amplitud por par, con cancelación de eco y ecualización digital | Sí | No | **10GBASE-T** |

> **[EJERCICIO RESUELTO]** ¿Por qué 1000BASE-T alcanza 1 Gbit/s sobre un cable de Cat 5e certificado solo hasta **100 MHz**? La respuesta encadena tres decisiones de diseño y es una pregunta clásica de razonamiento. **Primera**: usa **los cuatro pares a la vez** y en **ambos sentidos** (con cancelación de eco), de modo que cada par transporta `1000 / 4 = 250 Mbit/s`. **Segunda**: emplea **PAM-5**, cinco niveles de amplitud, lo que permite codificar **más de un bit por símbolo**: con 4 niveles útiles se llevarían 2 bits por símbolo, y `250 Mbit/s ÷ 2 = 125 Mbaudios`. **Tercera**: **125 Mbaudios caben en 100 MHz** porque la señal PAM-5, tras el filtrado y la conformación de pulso, ocupa aproximadamente la mitad del ancho de banda que ocuparía una señal binaria de la misma velocidad. La conclusión que se valora: **la velocidad de transmisión en bits por segundo y la velocidad de modulación en baudios no son lo mismo**; su relación es `Vt = Vm × log2(n)`, donde `n` es el número de niveles del símbolo. Es la fórmula que conviene llevar memorizada.

**Las modulaciones que hay que conocer**, para la parte de banda ancha y para la radio:

- **ASK** (modulación por desplazamiento de **amplitud**): se varía la amplitud de la portadora. Sencilla pero muy sensible al ruido, que es precisamente ruido de amplitud.
- **FSK** (por desplazamiento de **frecuencia**): se varía la frecuencia. Más robusta frente al ruido, menos eficiente en espectro.
- **PSK** (por desplazamiento de **fase**): se varía la fase. **BPSK** lleva 1 bit por símbolo; **QPSK**, 2; **8-PSK**, 3.
- **QAM** (modulación de **amplitud en cuadratura**): combina amplitud y fase, que es lo que permite las constelaciones densas. **16-QAM** transporta **4 bits por símbolo**; **64-QAM**, **6**; **256-QAM**, **8**; **1024-QAM** (Wi-Fi 6), **10**; y **4096-QAM** (Wi-Fi 7), **12**. La regla es directa: **una constelación de `n` puntos transporta `log2(n)` bits por símbolo**.
- **OFDM** (multiplexación por división de frecuencias **ortogonales**): reparte el flujo entre **muchas subportadoras estrechas y ortogonales** transmitidas en paralelo. Es a la vez una técnica de modulación y de multiplexación, y es **la base de 802.11a/g/n/ac/ax/be**, de LTE y de 5G. Su virtud decisiva es la **robustez frente a la propagación multitrayecto**, que es el problema dominante en interiores.

> **[DATO CLAVE EXAMEN]** La cadena de razonamiento que resume por qué una red inalámbrica es más rápida cuanto más cerca se está del punto de acceso: **a mejor relación señal/ruido, se puede usar una constelación más densa** (de QPSK a 4096-QAM), **y cada punto adicional de la constelación son más bits por símbolo**. La velocidad no baja con la distancia porque «llegue menos señal» en sentido literal, sino porque **el equipo negocia a la baja el esquema de modulación y codificación** para que los errores sigan siendo tratables.

### 3.4. Técnicas de multiplexación de canales

**Multiplexar** es **compartir un mismo medio físico entre varias comunicaciones simultáneas**. Conviene distinguirlo con precisión del método de acceso al medio de §4: la **multiplexación reparte el canal de forma planificada y estable** entre flujos conocidos, mientras que el **método de acceso arbitra la contienda** entre estaciones que compiten de forma imprevisible. Dicho de otro modo: **TDM es multiplexación; CSMA/CD es acceso**. La frontera se difumina en las técnicas de reserva de §4.4, que son precisamente multiplexación dinámica aplicada al acceso.

**Las cinco técnicas** (ver **diagrama D9**):

**1. FDM — por división de frecuencia.** El ancho de banda del medio se divide en **subbandas de frecuencia**, cada una asignada a un canal, separadas por **bandas de guarda** para evitar interferencias. Los canales son **simultáneos y continuos**. Es analógica por naturaleza y está en la radiodifusión, en la televisión por cable y, en su versión moderna, en la asignación de canales de Wi-Fi.

**2. TDM — por división de tiempo.** El medio se asigna **por completo a cada canal durante una ranura de tiempo**, rotando cíclicamente. Dos variantes que se preguntan por su diferencia:

- **TDM síncrona**: cada canal tiene su ranura **fija y reservada**, la use o no. Sencilla y con retardo determinista, pero **desperdicia capacidad** si una fuente calla. Es la de la jerarquía telefónica clásica (E1, T1).
- **TDM estadística o asíncrona**: las ranuras se asignan **solo a quien tiene datos que enviar**, lo que exige identificar en cada ranura a qué canal pertenece. **Aprovecha mucho mejor la capacidad** y es el principio de la conmutación de paquetes.

**3. WDM — por división de longitud de onda.** Es FDM aplicada a la **fibra óptica**: varias señales de **distinta longitud de onda (colores)** viajan simultáneamente por la misma fibra y se separan en el extremo con filtros ópticos. **CWDM** (*coarse*) usa pocos canales muy separados y es barata; **DWDM** (*dense*) usa decenas o centenares de canales muy juntos y multiplica por cien la capacidad de una fibra ya tendida. Es la técnica que hace que **no haya que tender fibra nueva** cuando se agota la capacidad de la existente.

**4. CDM / CDMA — por división de código.** Todas las estaciones transmiten **a la vez y en toda la banda**, pero cada una multiplica su señal por un **código de expansión ortogonal** distinto; el receptor recupera la señal deseada correlando con el código correspondiente y ve las demás como ruido. Es la base de la telefonía móvil de tercera generación y de las técnicas de espectro ensanchado.

**5. OFDM / OFDMA — por división de frecuencias ortogonales.** Ya descrita en §3.3 como modulación. Su versión de acceso múltiple, **OFDMA**, asigna **subconjuntos de subportadoras (unidades de recurso) a estaciones distintas**, de modo que varias estaciones transmiten **simultáneamente** dentro del mismo canal. Es la gran novedad de **Wi-Fi 6** y la que explica su ganancia real: no transmite mucho más rápido a un solo cliente, pero **atiende a muchos clientes pequeños a la vez** en lugar de por turnos, que es exactamente el escenario de una sala de espera llena de móviles.

> **[EJEMPLO AYTO MADRID]** Las cinco técnicas conviven en la oficina de referencia. Entre el armario principal y el centro de proceso de datos, el par de fibras contratado transporta varios servicios por **WDM**. Dentro del edificio, la Wi-Fi de la sala de espera usa **OFDM** y, si los puntos de acceso son Wi-Fi 6, **OFDMA** para atender a decenas de móviles simultáneos con tráfico pequeño. Los canales de 2,4 y 5 GHz se planifican por **FDM**, evitando que dos puntos de acceso vecinos usen el mismo canal. Y el enlace de respaldo por radio del edificio emplea **TDM** para repartir su capacidad entre voz y datos.

### 3.5. Medios de transmisión guiados y no guiados

La distinción es la clásica: en un **medio guiado** la señal se propaga **confinada** en un soporte físico —cobre o vidrio—; en un **medio no guiado** se propaga **libremente** por el espacio. De esa diferencia se derivan las cuatro propiedades que separan a ambos en la práctica: el medio guiado tiene **capacidad predecible**, **inmunidad relativa al entorno**, **alcance acotado por la atenuación** y **seguridad física** —para pinchar un cable hay que acceder a él—; el no guiado tiene **capacidad variable**, **vulnerabilidad a interferencias**, alcance dependiente del entorno y **ningún confinamiento físico**, lo que significa que **la señal se escapa del edificio** y cualquiera puede capturarla.

> **[DATO CLAVE EXAMEN]** La consecuencia de seguridad de esa última frase es la que fundamenta la exigencia del ENS: **el medio inalámbrico no se puede acotar físicamente**, y por eso **`mp.com.4.2`** ordena literalmente que, *«si se emplean comunicaciones inalámbricas, será en un segmento separado»* [ENS]. No es una recomendación de diseño: es un requisito normativo.

#### 3.5.1. Cableado de par trenzado, fibra óptica y coaxial

**Par trenzado.** Dos conductores de cobre aislados y **trenzados entre sí**. El trenzado no es decorativo: hace que las interferencias externas afecten por igual a ambos conductores y se cancelen en la recepción diferencial, y reduce la **diafonía** (*crosstalk*) entre pares del mismo cable. **A mayor número de trenzas por metro, mayor categoría y mayor frecuencia admisible.** Un cable de red típico agrupa **cuatro pares**.

Su **nomenclatura de apantallamiento**, normalizada como `XX/YZZ` donde `XX` es la pantalla global, `Y` el material y `ZZ` el elemento apantallado:

| Sigla | Nombre | Pantalla global | Pantalla por par |
|---|---|---|---|
| **U/UTP** | No apantallado | No | No |
| **F/UTP** | Apantallado con lámina | Lámina (*foil*) | No |
| **S/FTP** | Trenza global y lámina por par | Trenza (*screen*) | Lámina por par |
| **U/FTP** | Lámina por par, sin pantalla global | No | Lámina por par |
| **SF/UTP** | Trenza y lámina globales | Trenza + lámina | No |

El apantallamiento mejora la inmunidad, pero **exige una puesta a tierra correcta en ambos extremos**; mal instalado, la pantalla actúa de antena y **empeora** el comportamiento. Es una advertencia práctica que aparece en los pliegos.

Las **categorías de componente y clases de enlace** [ISO11801], que hay que saber emparejar:

| Categoría | Clase | Frecuencia | Aplicación típica |
|---|---|---|---|
| **Cat 5e** | **D** | **100 MHz** | 1000BASE-T; 2.5GBASE-T |
| **Cat 6** | **E** | **250 MHz** | 1000BASE-T; 10GBASE-T solo hasta **55 m** |
| **Cat 6A** | **EA** | **500 MHz** | **10GBASE-T a 100 m**. Es hoy el estándar de obra nueva |
| **Cat 7** | **F** | 600 MHz | Conector no RJ-45 (GG45, TERA). Poca implantación |
| **Cat 7A** | **FA** | 1.000 MHz | Íd. |
| **Cat 8.1** | **I** | **2.000 MHz** | 25 y 40 Gbit/s a **30 m**. Centro de proceso de datos |

> **[DATO CLAVE EXAMEN]** Dos parejas que se confunden y se preguntan: **la categoría se predica de los componentes** —cable, conector, latiguillo— y **la clase se predica del enlace o canal instalado**, es decir, del resultado medido; y la correspondencia **Cat 6A = Clase EA = 500 MHz = 10 Gbit/s a 100 m**, que es la especificación que debe exigir hoy cualquier obra nueva de una Administración. También: **Cat 6 llega a 10 Gbit/s, pero solo hasta 55 metros**, matiz que se pregunta como trampa.

**Los parámetros de calidad** que se miden al certificar un cableado y que hay que saber nombrar: **atenuación o pérdida de inserción**, **diafonía en el extremo cercano (NEXT)** y su versión sumada de todos los pares (**PSNEXT**), **diafonía en el extremo lejano igualada (ELFEXT / ACR-F)**, **relación entre atenuación y diafonía (ACR)**, **pérdida de retorno**, **retardo de propagación** y **diferencia de retardo entre pares (*delay skew*)**, decisiva en 1000BASE-T porque los cuatro pares deben llegar sincronizados.

**Cable coaxial.** Un conductor central rodeado de un dieléctrico, una malla conductora y una cubierta. Esa geometría concéntrica le da **gran inmunidad al ruido** y **mucho ancho de banda**, y fue el medio de la Ethernet original (**10BASE5** y **10BASE2**). **Está retirado de las redes locales**, donde el par trenzado lo desplazó por coste, manejabilidad y compatibilidad con la topología en estrella. Sobrevive en la **distribución de televisión** (RG-6, RG-59), en las **infraestructuras comunes de telecomunicación** de los edificios y en el acceso **DOCSIS**.

**Fibra óptica.** Un núcleo de vidrio rodeado de un revestimiento de índice de refracción menor, que confina la luz por **reflexión total interna**. Sus ventajas son categóricas: **ancho de banda enormemente superior**, **atenuación muy baja** —lo que permite kilómetros sin regeneración—, **inmunidad total a las interferencias electromagnéticas**, **ausencia de diafonía**, **imposibilidad práctica de provocar cortocircuitos o chispas** —lo que la hace obligatoria en atmósferas explosivas— y **dificultad de intervención no detectada**, que es un argumento de seguridad. Sus inconvenientes: **coste de instalación y de terminación**, **fragilidad a la curvatura** y necesidad de **personal y utillaje especializados** para fusionar.

Sus **dos tipos**, que hay que distinguir con precisión:

| Tipo | Diámetro del núcleo | Fuente de luz | Alcance | Uso en red local |
|---|---|---|---|---|
| **Multimodo (MMF)** | **50 o 62,5 µm** | **LED o VCSEL** (850/1300 nm) | Cientos de metros | **Troncal vertical dentro del edificio** |
| **Monomodo (SMF)** | **8-10 µm** | **Láser** (1310/1550 nm) | Decenas de km | **Enlace entre edificios y con el operador** |

En multimodo se clasifica además por grados **OM1** a **OM5** (OM3 y OM4 son las de obra nueva para 10 y 40 Gbit/s) y en monomodo por **OS1** y **OS2**. Los conectores que hay que saber nombrar: **LC** (el más habitual hoy, de formato pequeño), **SC**, **ST** y **MPO/MTP** para haces de fibras.

> **[EJERCICIO RESUELTO]** ¿Qué medio se especifica para cada tramo de la oficina de referencia? **Del puesto al armario de planta**: par trenzado **U/UTP Cat 6A**, canal de 100 m, porque garantiza 10 Gbit/s durante toda la vida útil del edificio y permite **PoE** de tipo 3 o 4 para teléfonos, cámaras y puntos de acceso. **Del armario de planta al armario principal** (vertical, unos 40 m): **fibra multimodo OM4**, dos hilos por enlace, porque la distancia excede lo razonable en cobre para 10 Gbit/s con margen y porque la fibra elimina los problemas de tierras entre plantas. **Del armario principal al centro de proceso de datos del IAM** (varios kilómetros): **fibra monomodo OS2**. **A la sala de espera**: no hay cable de usuario, hay **puntos de acceso Wi-Fi** alimentados por PoE desde el conmutador de planta. La justificación que se valora en un caso de examen es siempre la misma tríada: **distancia, velocidad objetivo y necesidad de alimentación**.

#### 3.5.2. Espectro radioeléctrico y transmisión inalámbrica

El **espectro radioeléctrico** es un **bien de dominio público** cuya administración corresponde al Estado [LGT, art. 85]. Su carácter finito y compartido es la causa de todas las particularidades de la red local inalámbrica.

**Las bandas de uso común para redes locales** y su régimen (ver **diagrama D11**):

- **2,4 GHz** (2.400-2.483,5 MHz). Banda **ICM** (industrial, científica y médica), compartida con hornos microondas, Bluetooth, mandos a distancia y multitud de sensores. Se divide en **canales de 22 MHz separados 5 MHz**, numerados del 1 al 13 en Europa, de donde resulta que **solo los canales 1, 6 y 11 no se solapan**.
- **5 GHz** (5.150-5.725 MHz en varias subbandas). Mucho más ancha y con muchos más canales sin solape. Su particularidad regulatoria: en las subbandas compartidas con radares meteorológicos y militares es **obligatorio el DFS** —el punto de acceso debe **detectar el radar y cambiar de canal**— y el **TPC**, control automático de potencia. Es la causa de un síntoma que desconcierta a los usuarios: **un punto de acceso puede cambiar de canal solo y provocar una desconexión breve** de todos los clientes.
- **6 GHz** (5.945-6.425 MHz en Europa). Abierta para **Wi-Fi 6E y Wi-Fi 7**. Es la banda más limpia porque es nueva, admite **siete canales de 160 MHz**, y su uso está restringido principalmente a **interiores y a baja potencia**.

**Los fenómenos de propagación** que hay que saber nombrar porque explican los problemas de cobertura: **atenuación con la distancia** (que en espacio libre crece con el cuadrado de la distancia, y mucho más en interiores); **absorción** por materiales —el agua y por tanto las personas absorben mucho en 2,4 GHz; el hormigón armado y los cristales metalizados son barreras muy severas—; **reflexión**, **refracción** y **difracción**; **propagación multitrayecto**, que hace que la misma señal llegue por varios caminos con desfases y se cancele parcialmente —el problema que OFDM y MIMO vinieron a resolver, y que MIMO llega incluso a aprovechar—; e **interferencia** cocanal y de canal adyacente.

> **[DATO CLAVE EXAMEN]** El régimen jurídico del espectro que se usa en una red local, en una frase: **Wi-Fi opera en bandas de uso común del dominio público radioeléctrico, que conforme al artículo 88 de la Ley 11/2022 no precisan de ningún título habilitante**, pero **quedan sujetas a las condiciones técnicas del CNAF** y **carecen de protección frente a interferencias**. Corolario práctico y examinable: si el Wi-Fi de una dependencia municipal sufre interferencias de un vecino que usa legalmente la misma banda, **no hay a quién reclamar**; la solución es técnica —cambiar de canal, subir a 5 o 6 GHz, replanificar la cobertura—, no jurídica.

> **[EJEMPLO AYTO MADRID]** La sala de espera de la oficina reúne todos los problemas del medio no guiado a la vez. La **absorción por las personas** hace que la cobertura medida con la sala vacía no se parezca a la real con cuarenta ciudadanos esperando. Los **muros de hormigón armado** del edificio obligan a un punto de acceso por zona en lugar de uno potente en el centro. La **banda de 2,4 GHz** está saturada por los móviles de los propios ciudadanos. Y la señal **se escapa a la calle**, de modo que la red de invitados debe estar en **VLAN separada** con salida directa a internet y sin ninguna visibilidad de la red corporativa, que es exactamente lo que exige `mp.com.4.2` del ENS y lo que se detalla en §6.2.

---

## 4. Métodos de acceso al medio

### 4.1. Clasificación y principios de los métodos de acceso

**El problema.** Cuando **varias estaciones comparten un mismo medio de transmisión**, dos que transmitan simultáneamente **superponen sus señales** y ambas se destruyen: eso es una **colisión**. El **método de acceso al medio** es el conjunto de reglas que decide **quién transmite y cuándo**, y reside en la **subcapa MAC** del nivel de enlace (§1.2). Es, junto con las técnicas de transmisión, la materia propia y distintiva de las redes locales: **en un enlace punto a punto no existe este problema**.

**Los cuatro criterios con que se evalúa un método de acceso**, que son los que permiten comparar y responder a las preguntas de análisis:

1. **Rendimiento** (*throughput*) útil que se obtiene del medio, y cómo evoluciona **al aumentar la carga**.
2. **Retardo de acceso**: cuánto tarda una estación en poder transmitir, y sobre todo si ese retardo está **acotado** o no.
3. **Equidad**: si todas las estaciones tienen la misma oportunidad, o si el método permite **priorizar**.
4. **Complejidad y coste** de la implantación.

**La clasificación canónica** [TANENBAUM] divide primero entre asignación **estática** y **dinámica**, y esta última en tres familias (ver **diagrama D12**):

**A. Asignación estática o determinista pura.** El canal se reparte de antemano y de forma fija entre las estaciones, por **FDM** o por **TDM síncrona**. Es sencillo y ofrece **retardo garantizado**, pero **desperdicia el canal** cuando una estación calla y **no escala**: con `n` estaciones cada una obtiene `1/n` de la capacidad aunque sea la única activa. **No se usa en redes locales de datos**, precisamente porque el tráfico de datos es a ráfagas.

**B. Asignación dinámica por contienda (métodos aleatorios).** No hay coordinación previa: **cada estación transmite cuando lo estima oportuno** y se resuelve *a posteriori* lo que salga mal. Son eficientes con carga baja y se degradan con carga alta. Aquí están **ALOHA**, **CSMA** y sus variantes **CSMA/CD** y **CSMA/CA**.

**C. Asignación dinámica sin contienda por paso de testigo (métodos deterministas).** Circula un permiso explícito para transmitir. **Nunca hay colisiones** y el **retardo máximo está acotado**. Aquí están **Token Ring**, **Token Bus** y **FDDI**.

**D. Asignación dinámica por reserva o por sondeo.** Una estación central pregunta por turno (**sondeo** o *polling*) o las estaciones **reservan** capacidad antes de transmitir. Es el esquema de las redes con maestro y de las de acceso por cable o fibra.

> **[DATO CLAVE EXAMEN]** La contraposición que vertebra toda la sección, y que hay que poder enunciar en una frase: **los métodos por contienda son eficientes con poca carga pero su retardo no está acotado y se degradan al saturarse; los métodos deterministas garantizan un retardo máximo y no se degradan, a costa de una sobrecarga constante que los hace menos eficientes con poca carga**. De ahí que Ethernet ganase en la ofimática —tráfico a ráfagas, carga media baja— y que el paso de testigo sobreviviese más tiempo en el entorno **industrial**, donde lo que importa es la garantía de plazo.

**El antecedente: ALOHA.** Conviene conocerlo porque explica de dónde viene CSMA y porque sus cifras de rendimiento se preguntan [ABRAMSON].

- **ALOHA puro** (1970): la estación **transmite en cuanto tiene datos**, sin escuchar nada; si no recibe confirmación, supone colisión y **retransmite tras un tiempo aleatorio**. Su **rendimiento máximo teórico es del 18,4 %** (`1 / 2e`) del canal.
- **ALOHA ranurado** (*slotted*): el tiempo se divide en **ranuras** y las estaciones **solo pueden empezar a transmitir al comienzo de una ranura**. Eso reduce a la mitad el periodo de vulnerabilidad y **duplica el rendimiento hasta el 36,8 %** (`1 / e`).

La lección que se extrajo y que dio origen a CSMA es sencilla: **si antes de transmitir se escucha el medio, se evitan casi todas las colisiones**.

### 4.2. Métodos aleatorios o por contienda

**CSMA** (*Carrier Sense Multiple Access*, **acceso múltiple con detección de portadora**) añade a ALOHA la escucha previa. Sus **tres variantes por política de persistencia** hay que saber distinguirlas:

- **CSMA no persistente**: si el medio está ocupado, la estación **espera un tiempo aleatorio** antes de volver a escuchar. Reduce las colisiones pero **desaprovecha el canal**, porque puede quedar libre y nadie estar escuchando.
- **CSMA 1-persistente**: si está ocupado, **sigue escuchando continuamente** y transmite **con probabilidad 1** en cuanto queda libre. Aprovecha bien el canal, pero **garantiza la colisión** si dos estaciones estaban esperando a la vez. **Es la variante de Ethernet**.
- **CSMA p-persistente**: en un medio ranurado, cuando el canal queda libre transmite **con probabilidad `p`** y espera a la siguiente ranura con probabilidad `1 − p`. Es un compromiso entre las dos anteriores.

Sobre esa base se construyen las dos variantes que **hay que dominar**, y cuya diferencia es la pregunta más repetida de todo el tema.

#### 4.2.1. Método CSMA/CD en redes Ethernet

**CSMA/CD** (*Collision Detection*, **con detección de colisión**) es el método de acceso de **IEEE 802.3** en su operación **semidúplex** [IEEE8023]. Su idea añadida es que la estación **no solo escucha antes de transmitir, sino también mientras transmite**, de modo que puede **detectar la colisión en el momento en que ocurre** y abortar, en lugar de gastar el canal transmitiendo una trama ya condenada.

**El algoritmo, paso a paso** (ver **diagrama D13**):

1. La estación con datos que enviar **escucha el medio**.
2. Si está **ocupado**, sigue escuchando hasta que quede libre (política **1-persistente**).
3. Cuando queda libre, espera el **espacio entre tramas** (*interframe gap*) de **96 tiempos de bit** —9,6 µs a 10 Mbit/s— y **transmite**.
4. **Mientras transmite, sigue escuchando.** Si detecta que el nivel de señal en el medio no se corresponde con lo que está emitiendo, hay **colisión**.
5. Ante la colisión: **aborta la transmisión** y emite una **señal de atasco (*jam*) de 32 bits**, para asegurarse de que **todas las demás estaciones detectan también la colisión** y ninguna se queda con una trama a medias que crea válida.
6. Calcula un tiempo de espera mediante el **retroceso exponencial binario truncado**: tras la colisión número `n`, elige un número aleatorio `r` en el intervalo `[0, 2^k − 1]`, donde **`k = mín(n, 10)`**, y espera **`r` ranuras de colisión**.
7. Reintenta desde el paso 1. Si llega a **16 intentos fallidos**, **descarta la trama** y notifica el error a la capa superior.

> **[DATO CLAVE EXAMEN]** Los cinco números de CSMA/CD que hay que llevar memorizados: **espacio entre tramas de 96 tiempos de bit**; **señal de atasco de 32 bits**; **retroceso exponencial binario truncado en `k = 10`** —es decir, el intervalo deja de crecer a partir de la décima colisión, con 1.024 ranuras posibles—; **límite de 16 intentos** antes de descartar la trama; y **ranura de colisión de 512 tiempos de bit**, que equivalen a **64 octetos**.

**La regla de los 64 octetos**, que es el razonamiento más elegante del tema y del que se pueden hacer preguntas de varios tipos. La detección de colisión **solo funciona si la estación sigue transmitiendo cuando la colisión le llega de vuelta**. Si terminase de transmitir antes, se iría tan tranquila creyendo que todo ha ido bien.

El peor caso es el de dos estaciones en **los extremos opuestos** del segmento: la primera transmite, su señal tarda un tiempo `T` en llegar al otro extremo, la segunda transmite justo un instante antes de que le llegue, y la señal colisionada tarda otro tiempo `T` en volver a la primera. Luego **la estación debe seguir transmitiendo durante al menos `2T`**, el **tiempo de ida y vuelta** del segmento. Ese `2T` es la **ranura de colisión** (*slot time*), y en Ethernet de 10 y 100 Mbit/s se fijó en **512 tiempos de bit**. De ahí, directamente, la **trama mínima de 64 octetos**: `512 bits ÷ 8 = 64 octetos`. Si una trama tiene menos datos, la subcapa MAC **añade relleno** (*padding*) hasta alcanzar los 46 octetos de carga útil mínima.

> **[EJERCICIO RESUELTO]** Comprobación numérica de la regla. En Ethernet a **10 Mbit/s**, la ranura de colisión de **512 tiempos de bit** dura `512 ÷ 10.000.000 = 51,2 µs`. Con una velocidad de propagación en el cable de aproximadamente `2 × 10^8 m/s` —dos tercios de la de la luz—, en la mitad de ese tiempo (`25,6 µs`, que es el tiempo de ida `T`) la señal recorre `2 × 10^8 × 25,6 × 10^-6 = 5.120 metros`. Ese es el **diámetro máximo teórico** del dominio de colisión; el presupuesto real de la norma lo reduce a unos **2.500 m** por los retardos que introducen los repetidores y la electrónica. **Segunda parte del razonamiento, que es la que se pregunta**: al pasar a 100 Mbit/s, la ranura sigue siendo de 512 tiempos de bit, pero cada bit dura diez veces menos, así que **la distancia máxima se divide por diez**, hasta unos **250 m** —de ahí que Fast Ethernet solo admita uno o dos repetidores—. Y en **Gigabit** habría bajado a 25 m, cifra inservible: por eso la norma **amplió la ranura a 4.096 tiempos de bit (512 octetos)** e introdujo la **extensión de portadora**, que rellena las tramas cortas hasta ese tamaño. **Conclusión general que hay que saber enunciar: en CSMA/CD, la velocidad, el tamaño mínimo de trama y la distancia máxima están ligados y no se pueden fijar independientemente.**

**La estructura de la trama Ethernet**, que conviene tener presente porque de ella salen varias preguntas de dato:

| Campo | Tamaño | Contenido |
|---|---|---|
| **Preámbulo** | **7 octetos** | `10101010` repetido, para sincronizar el reloj del receptor |
| **SFD** (delimitador de inicio) | **1 octeto** | `10101011`. El cambio del último bit marca el comienzo real |
| **Dirección de destino** | **6 octetos** | MAC destino (individual, de grupo o difusión) |
| **Dirección de origen** | **6 octetos** | MAC origen (siempre individual) |
| **Tipo / Longitud** | **2 octetos** | `EtherType` si ≥ 1536; longitud si ≤ 1500 |
| **Datos y relleno** | **46 a 1500 octetos** | Carga útil. Relleno si no llega a 46 |
| **FCS** | **4 octetos** | Secuencia de comprobación, **CRC-32** |

**Tamaños que se derivan y se preguntan**: **trama mínima 64 octetos** y **máxima 1518** —contando de la dirección de destino al FCS, sin preámbulo ni delimitador—; **1522 con etiqueta 802.1Q**; y **MTU de 1500 octetos**. Y una precisión: el **preámbulo y el delimitador no se cuentan** en el tamaño de la trama, aunque sí ocupan tiempo en el medio.

**El final de CSMA/CD.** Es importante decirlo con claridad porque es una pregunta frecuente: **en una red local actual, CSMA/CD no se usa**. La razón es que **la operación en dúplex sobre un enlace punto a punto lo hace innecesario**: cada puerto de conmutador está unido a un único equipo por un canal dedicado con un par para cada sentido, de modo que **no hay con quién colisionar**. La norma prevé expresamente que, cuando el enlace negocia dúplex, **CSMA/CD se deshabilite**. En **10 Gigabit y superiores, el modo semidúplex ni siquiera está definido**: solo existe dúplex. CSMA/CD sobrevive únicamente como concepto de examen y en instalaciones con concentradores, que ya no se fabrican.

> **[DATO CLAVE EXAMEN]** Formulación compacta de lo anterior, que es exactamente como suele preguntarse: **CSMA/CD solo tiene sentido en semidúplex sobre medio compartido**; con conmutador y enlace dúplex, **se desactiva**, y en 10 Gbit/s y superiores **no existe el semidúplex**. La consecuencia: **una red conmutada moderna no tiene colisiones**, y por tanto ver contadores de colisión distintos de cero en un puerto es síntoma de un problema —típicamente, una **negociación automática fallida** que ha dejado un extremo en dúplex y el otro en semidúplex, la avería clásica del *duplex mismatch*, que se manifiesta como lentitud extrema con tasas de error altas.

#### 4.2.2. Método CSMA/CA en redes Wi-Fi

**CSMA/CA** (*Collision Avoidance*, **con evitación de colisión**) es el método de acceso de **IEEE 802.11**, implementado en la **función de coordinación distribuida (DCF)** [IEEE80211]. Su punto de partida es una imposibilidad física que hay que entender antes que el algoritmo.

**Por qué no se puede detectar la colisión en radio.** Tres razones, y con saber la primera basta para responder:

1. **El emisor no puede oír mientras transmite.** La señal que emite su propia antena es de seis a nueve órdenes de magnitud más potente que la que le llegaría de otra estación: **su propia transmisión ensordece su receptor**. Detectar una colisión sería como oír un susurro al otro lado de la habitación mientras se grita.
2. **El medio no es el mismo para todos.** En un cable, todas las estaciones ven el mismo estado del medio. En radio, **cada estación oye un subconjunto distinto** de las demás, según su posición. De ahí el problema del nodo oculto.
3. **Una colisión detectada en el emisor no dice nada** sobre lo que ha ocurrido **en el receptor**, que es donde importa.

Como **detectar** es imposible, hay que **evitar**. El algoritmo (ver **diagrama D14**):

1. La estación con datos **escucha el medio**, con **dos mecanismos a la vez**: **detección física de portadora** (medir energía en el canal) y **detección virtual**, consultando su **vector de asignación de red (NAV)**, un temporizador que indica cuánto tiempo se ha anunciado que el medio estará ocupado.
2. Si el medio está libre durante un **DIFS** completo, la estación **no transmite inmediatamente**: pasa al paso 3. Este es el punto que diferencia CSMA/CA de CSMA/CD y donde fallan las respuestas.
3. **Retroceso aleatorio previo obligatorio.** Elige un número aleatorio en `[0, CW − 1]` y espera ese número de **ranuras**, **decrementando el contador solo mientras el medio siga libre** y **congelándolo** si alguien transmite. Cuando el contador llega a cero, transmite. El valor inicial de la ventana de contienda es **CWmín = 15** en OFDM, y **se duplica en cada intento fallido** hasta **CWmáx = 1023**.
4. El receptor, si recibe la trama correctamente, espera un **SIFS** —el espacio más corto, lo que le da **prioridad absoluta** sobre cualquiera que quiera empezar a transmitir— y envía un **acuse de recibo (ACK)**.
5. **Si el emisor no recibe el ACK, supone colisión**, duplica su ventana de contienda y reintenta. El acuse es **obligatorio en 802.11**, a diferencia de Ethernet: es la única forma de saber si la trama llegó.

**Los espacios entre tramas** y su jerarquía de prioridad, que es un dato clásico de examen:

| Espacio | Nombre | Duración en 5 GHz | Para qué |
|---|---|---|---|
| **SIFS** | Espacio corto | **16 µs** | **Máxima prioridad**: ACK, CTS, fragmentos siguientes |
| **PIFS** | Espacio de la función puntual | `SIFS + 1 ranura` = **25 µs** | Acceso del punto de acceso en modo PCF |
| **DIFS** | Espacio de la función distribuida | `SIFS + 2 ranuras` = **34 µs** | Acceso normal de las estaciones (DCF) |
| **Ranura** | *slot time* | **9 µs** | Unidad del retroceso aleatorio |

> **[DATO CLAVE EXAMEN]** La fórmula **`DIFS = SIFS + 2 × ranura`** y sus dos instancias: en **5 GHz y 802.11g** con ranura corta, `16 + 2 × 9 = 34 µs` (y `10 + 2 × 9 = 28 µs` en 802.11g); en **802.11b a 2,4 GHz**, con SIFS de 10 µs y ranura de 20 µs, **DIFS = 50 µs**. La razón de que existan varios espacios es **crear prioridades sin negociación**: quien puede empezar antes, gana. Por eso el ACK, que espera solo un SIFS, **nunca colisiona** con una estación que esté esperando un DIFS.

**El problema del nodo oculto y RTS/CTS.** Es el escenario que hay que saber dibujar. Tres estaciones: **A** y **C** están ambas al alcance del punto de acceso **B**, pero **A y C no se oyen entre sí** —hay un muro, o la distancia es excesiva—. A escucha el medio, lo encuentra libre (porque no oye a C, que está transmitiendo) y transmite: **colisión en B**. La escucha de portadora **ha fallado**, y no por un error del algoritmo sino porque **el medio que oye A no es el medio que ve B**.

La solución opcional es el intercambio **RTS/CTS**:

1. **A** envía un **RTS** (*Request To Send*) al punto de acceso, indicando **cuánto tiempo va a necesitar** el medio.
2. El punto de acceso responde con un **CTS** (*Clear To Send*) que **también incluye la duración**. Y aquí está la clave: **el CTS lo oyen todas las estaciones al alcance del punto de acceso**, incluida **C**, aunque C no oyese el RTS de A.
3. Todas las estaciones que oyen el RTS o el CTS **actualizan su NAV** con esa duración y **se abstienen de transmitir** durante ese tiempo. Es **detección virtual de portadora**: se abstienen no porque oigan la transmisión, sino porque **se les ha dicho que hay una**.

El coste es la **sobrecarga** de dos tramas de control por cada trama de datos, razón por la cual RTS/CTS **está desactivado por defecto** y solo se activa por encima de un umbral de tamaño de trama.

Existe también el problema simétrico, el **nodo expuesto**: una estación se abstiene de transmitir porque oye una transmisión que **no la habría afectado**, desperdiciando capacidad. Es el precio de errar por el lado conservador.

> **[EJERCICIO RESUELTO]** ¿Por qué la velocidad real de una Wi-Fi es aproximadamente **la mitad** de la velocidad nominal negociada? Hay que sumar cuatro sobrecargas y explicarlas: (a) **es semidúplex**, de modo que el mismo canal transporta ida y vuelta; (b) **cada trama de datos exige un ACK**, precedido de su SIFS; (c) **antes de cada transmisión hay un DIFS más un retroceso aleatorio** que, con CWmín = 15, promedia 7,5 ranuras, unos 67 µs; y (d) la **cabecera de la capa física (preámbulo PLCP) se transmite siempre a la velocidad más baja** para que la entiendan todas las estaciones, con lo que su coste temporal es desproporcionado. A eso se añade que **el medio es compartido entre todas las estaciones asociadas**: la velocidad nominal es la del canal, no la de cada cliente. La conclusión que se valora: **la cifra que anuncia el fabricante es la velocidad de la capa física del canal; el rendimiento útil de la capa de aplicación ronda el 50-60 % de ella en el mejor caso, y se reparte entre todos los clientes activos.**

> **[EJEMPLO AYTO MADRID]** En la sala de espera, con cuarenta ciudadanos conectados a un único punto de acceso, se manifiestan todos los efectos a la vez. El **retroceso aleatorio** crece porque hay más contienda; algunos móviles están en el límite de cobertura y **negocian una modulación lenta**, de modo que ocupan el canal mucho tiempo para enviar poco —el llamado **problema de la tasa ancla**, por el que **una sola estación lenta degrada a todas las demás**—; y quienes están detrás de la columna de hormigón son **nodos ocultos** respecto de los que están junto a la puerta. La solución no es un punto de acceso más potente: **subir la potencia agranda la celda y empeora la contienda**. Es poner **más puntos de acceso con menos potencia cada uno**, planificar canales que no se solapen y **fijar una velocidad mínima de asociación** para expulsar de la celda a los clientes demasiado lejanos, obligándolos a asociarse al punto de acceso vecino.

> **[DATO CLAVE EXAMEN]** La comparación CSMA/CD frente a CSMA/CA es **la pregunta más probable de todo el tema**. Los seis puntos de contraste: **detecta la colisión** frente a **la evita**; **cableada (802.3)** frente a **inalámbrica (802.11)**; **no hay acuse** frente a **acuse obligatorio**; **retroceso solo después de colisionar** frente a **retroceso también antes de transmitir**; **señal de atasco de 32 bits** frente a **RTS/CTS y NAV**; y **desactivada en dúplex** frente a **siempre activa, porque la radio es siempre semidúplex**.

### 4.3. Métodos deterministas o por paso de testigo

En los métodos de **paso de testigo** (*token passing*) circula por la red una **trama de control especial, el testigo**, que representa el **derecho a transmitir**. Solo la estación que **posee el testigo** puede emitir. Terminada su transmisión —o agotado su tiempo de retención—, **cede el testigo a la siguiente estación** del orden lógico.

**Las cuatro propiedades** que se derivan de ese mecanismo, y que son lo que hay que saber razonar:

1. **No hay colisiones**, por construcción: en todo momento hay como máximo un transmisor autorizado.
2. **El retardo máximo está acotado**. Con `n` estaciones, ninguna espera más que el tiempo de una vuelta completa del testigo. Esta es la propiedad **determinista** y la que lo hacía apto para el control industrial.
3. **El rendimiento no se degrada con la carga**: al saturarse, el canal sigue entregando prácticamente toda su capacidad, mientras que CSMA/CD se hunde. Con **carga baja**, en cambio, es **menos eficiente**, porque una estación con datos puede tener que esperar a que le llegue el testigo aunque nadie más esté transmitiendo.
4. Admite **prioridades** de forma natural, reservando el testigo para tráfico urgente.

Sus **inconvenientes** son los que lo condenaron: **complejidad** —hay que mantener el anillo lógico, detectar la **pérdida del testigo** o la aparición de **testigos duplicados**, y gestionar la entrada y salida de estaciones—, **coste del equipamiento** y, sobre todo, la **imbatible economía de escala de Ethernet**.

**Las tres realizaciones** que el temario exige conocer (ver **diagrama D15**):

**IEEE 802.5 — Token Ring** [IEEE8025]. Impulsada por IBM. Topología **lógica de anillo** y **física de estrella** mediante unidades de acceso al medio (**MAU**), que incorporan relés de derivación para que la caída de una estación no rompa el anillo. Velocidades de **4 y 16 Mbit/s**. El **testigo** es una trama de **3 octetos** (delimitador de inicio, control de acceso y delimitador de fin) y el campo de **control de acceso** lleva **tres bits de prioridad y tres de reserva**, que permiten a una estación de alta prioridad reservar el siguiente testigo. Una estación asume el papel de **monitor activo**: vigila que el testigo no se pierda ni se duplique, elimina las tramas que dan más de una vuelta y proporciona el reloj maestro. En la variante de **16 Mbit/s** se introdujo la **liberación temprana del testigo**, que permite emitirlo sin esperar a que la trama propia complete la vuelta.

**IEEE 802.4 — Token Bus.** Combina el **bus físico** con un **anillo lógico**: las estaciones se ordenan por dirección descendente y cada una sabe a quién debe pasar el testigo, aunque físicamente todas cuelguen del mismo cable. Su motivación fue **industrial**: el sector de la fabricación quería el determinismo del testigo sin renunciar al cableado de bus y con la robustez del coaxial de banda ancha. Fue la base del perfil **MAP** (*Manufacturing Automation Protocol*) de General Motors. Su complejidad para mantener el anillo lógico —altas, bajas y regeneración— fue su ruina.

**FDDI** [FDDI]. No es una norma IEEE sino **ANSI X3T9.5 / ISO 9314**. **100 Mbit/s sobre fibra óptica**, con **doble anillo contrarrotante**: un anillo **primario** que transporta los datos y un anillo **secundario** de respaldo que circula en sentido contrario. Ante un corte, las dos estaciones adyacentes **pliegan** ambos anillos en uno solo (*wrap*), reconstruyendo un anillo único y manteniendo el servicio: es la respuesta a la fragilidad estructural del anillo simple. Admite hasta **500 estaciones** y **200 km** de perímetro total (100 km de anillo doble). Las estaciones pueden ser de **doble conexión (DAS)**, unidas a los dos anillos, o de **simple conexión (SAS)**, unidas solo al primario a través de un concentrador. Su acceso es un **paso de testigo temporizado**: se acuerda un **tiempo objetivo de rotación del testigo (TTRT)** y cada estación mide el **tiempo real de rotación (TRT)**; si el testigo llega antes de lo previsto, la estación dispone de un **tiempo de retención (THT)** proporcional al adelanto para enviar tráfico asíncrono. Ese mecanismo permite **garantizar ancho de banda al tráfico síncrono** —voz y vídeo— y repartir el sobrante. Usa **liberación temprana del testigo** y **codificación 4B/5B con NRZI**. Su papel histórico fue el de **red troncal de campus** en los años noventa, antes de que Fast Ethernet y Gigabit la desplazaran.

> **[DATO CLAVE EXAMEN]** Datos discriminantes de las tres: **802.5 = Token Ring = 4 y 16 Mbit/s = IBM = MAU = monitor activo**; **802.4 = Token Bus = anillo lógico sobre bus físico = industrial = MAP**; **FDDI = 100 Mbit/s = fibra = doble anillo contrarrotante = 200 km = 500 estaciones = ANSI/ISO, no IEEE**. Y el dato conceptual: **el doble anillo de FDDI resuelve el punto débil estructural de la topología en anillo**, que es que el corte de un enlace deja la red inoperativa.

> **[EJERCICIO RESUELTO]** Una red de 50 estaciones se satura de tráfico continuo. ¿Qué le ocurre a un Token Ring de 16 Mbit/s y qué a una Ethernet de 10 Mbit/s con concentrador? **Token Ring**: el rendimiento **se mantiene cerca del máximo**, porque el testigo circula sin colisiones y todo el tiempo de canal se dedica a datos; el retardo de cada estación tiende al tiempo de una vuelta completa, que es **previsible y acotado**. **Ethernet**: al aumentar la carga aumenta la probabilidad de colisión, y **cada colisión gasta canal sin transmitir nada útil**; el retroceso exponencial alarga las esperas, lo que reduce las colisiones pero dispara el retardo, y el rendimiento útil **cae muy por debajo del nominal**. La conclusión que se valora es doble: **con carga alta gana el testigo; con carga baja y a ráfagas gana Ethernet**, porque una estación puede transmitir de inmediato en lugar de esperar el testigo. Y la observación decisiva: **este razonamiento describe la Ethernet de bus compartido, no la conmutada**; con conmutador y dúplex no hay colisiones y el problema desaparece, que es exactamente la razón por la que la discusión quedó zanjada a favor de Ethernet.

### 4.4. Métodos basados en reserva y sondeo

La cuarta familia agrupa los métodos en los que **una entidad coordinadora reparte el acceso**, o en los que las estaciones **piden el canal antes de usarlo**. Son el esquema natural cuando existe un elemento central con visión de toda la red.

**Sondeo (*polling*).** Una **estación primaria o maestra** pregunta **por turno** a cada secundaria si tiene algo que transmitir; la secundaria **solo transmite cuando es interrogada**. Es el esquema de las redes multipunto clásicas y de muchos buses industriales (Modbus, Profibus en su modo maestro-esclavo).

- **Ventajas**: **sin colisiones**, retardo **acotado y calculable**, control centralizado, prioridades triviales de implantar.
- **Inconvenientes**: **sobrecarga del sondeo** —se gasta canal preguntando a estaciones que no tienen nada que decir—; el retardo crece linealmente con el número de estaciones; y la primaria es un **punto único de fallo**.
- Variantes: **sondeo cíclico** (todas por igual), **por lista de prioridad** (unas más veces que otras) y **adaptativo** (se salta a las que llevan tiempo calladas).

**Selección (*selecting*).** El movimiento inverso: la primaria **avisa a la secundaria** de que va a enviarle datos y espera confirmación de que está preparada. Sondeo y selección son las dos mitades del mismo esquema maestro-esclavo.

**Reserva.** El tiempo se organiza en **ciclos** con dos partes: un **periodo de contienda o de reserva**, en el que las estaciones piden capacidad en minirranuras, y un **periodo de transmisión**, repartido según las peticiones concedidas. Es multiplexación por división de tiempo **dinámica** aplicada al acceso, y su virtud es que **la contienda se limita a las peticiones**, que son cortas, en lugar de a los datos, que son largos. Ejemplos reales:

- **DOCSIS**, el acceso por cable coaxial: el equipo de cabecera concede ranuras a los módems, que las solicitan en un periodo de contienda.
- **DQDB** (**IEEE 802.6**), red metropolitana de **doble bus con cola distribuida**, en la que cada estación lleva la cuenta de las peticiones pendientes aguas arriba para respetar un orden global de llegada.
- Las **redes ópticas pasivas (PON)**, donde el terminal de línea (OLT) asigna ventanas de transmisión a cada unidad de usuario (ONT) mediante **asignación dinámica de ancho de banda**.

**Los métodos centralizados dentro de 802.11.** El propio Wi-Fi contempla mecanismos de esta familia, aunque su uso ha sido marginal o reciente:

- **PCF** (*Point Coordination Function*): el punto de acceso **sondea** por turno a las estaciones durante un periodo libre de contienda. Nunca se implantó en la práctica.
- **HCCA**, dentro de **802.11e**, versión con calidad de servicio de la anterior.
- **La coordinación de OFDMA de Wi-Fi 6**, que sí se ha implantado y es conceptualmente un método de reserva: el punto de acceso envía una **trama de activación** (*trigger frame*) que **asigna unidades de recurso a estaciones concretas**, las cuales transmiten **simultáneamente y sin contienda** en la porción de canal que se les ha asignado. Es la reintroducción del control centralizado en una tecnología nacida distribuida, y la razón de fondo de la mejora de Wi-Fi 6 en entornos densos.

> **[DATO CLAVE EXAMEN]** La clasificación completa, tal como conviene reproducirla en un desarrollo: **acceso estático** (FDM, TDM síncrona) frente a **acceso dinámico**; y dentro del dinámico, **por contienda** (ALOHA, CSMA, **CSMA/CD**, **CSMA/CA**), **sin contienda por paso de testigo** (**802.5**, **802.4**, **FDDI**) y **sin contienda por reserva o sondeo** (*polling*, DQDB, DOCSIS, PON, PCF y el OFDMA coordinado de Wi-Fi 6).

> **[REFERENCIA CRUZADA]** Las técnicas de conmutación de circuitos, de mensajes y de paquetes, y las redes de difusión, se desarrollan en el **Tema 33**. Los mecanismos de calidad de servicio que se apoyan en la priorización de 802.1p —clasificación, marcado y encolado— corresponden al **Tema 30**.

---

## 5. Dispositivos de interconexión

**La regla que ordena toda la sección.** Los dispositivos de interconexión se clasifican por **la capa más alta del modelo OSI cuya información utilizan para tomar sus decisiones** [X200]. Un dispositivo que solo regenera señal opera en la capa 1; uno que lee direcciones MAC, en la 2; uno que lee direcciones IP, en la 3; y uno que traduce entre protocolos distintos, en las capas altas. **De esa única frase se deducen todas las propiedades de cada aparato**: qué separa, qué propaga y qué filtra.

**Los dos conceptos que hay que dominar antes de empezar**, porque son el objeto de la pregunta más repetida de esta sección:

- **Dominio de colisión**: conjunto de interfaces cuyas transmisiones **pueden colisionar entre sí**, es decir, que comparten el mismo medio. Los dispositivos de **capa 1 lo propagan** —no lo dividen—; los de **capa 2 y 3 lo dividen**.
- **Dominio de difusión**: conjunto de interfaces a los que llega una trama enviada a la dirección de **difusión** `FF:FF:FF:FF:FF:FF`. Los dispositivos de **capa 1 y 2 lo propagan**; solo los de **capa 3 —o la separación en VLAN, que es de capa 2 pero funciona como frontera lógica— lo dividen**.

> **[DATO CLAVE EXAMEN]** La tabla que resume la sección y que conviene memorizar entera: el **repetidor y el concentrador** son de **capa 1**, tienen **un dominio de colisión y uno de difusión**; el **puente, el conmutador y el punto de acceso** son de **capa 2**, crean **un dominio de colisión por puerto** y **un dominio de difusión por VLAN**; el **encaminador** es de **capa 3** y crea **un dominio de colisión y un dominio de difusión por interfaz**; y la **pasarela** opera **por encima de la capa 3**. Ver **diagrama D16**.

### 5.1. Interconexión en el nivel físico: repetidores y concentradores

**Repetidor.** Dispositivo de **dos puertos** que **recibe, regenera y retransmite** la señal. Su función es combatir la **atenuación** y la **distorsión** para extender el alcance de un segmento más allá de lo que permite el medio.

Lo esencial de su comportamiento: **no interpreta nada**. No lee direcciones, no comprueba el CRC, no filtra, no almacena. **Regenera todo, incluidos el ruido interpretable como señal, las tramas defectuosas y las colisiones**. En consecuencia, **une segmentos en un único dominio de colisión** y no mejora el rendimiento: solo la distancia.

Su versión óptica y la más común hoy es el **conversor de medio** (*media converter*), que traduce entre par trenzado y fibra manteniendo la señal en la capa 1.

**Concentrador (*hub*).** Es, literalmente, un **repetidor multipuerto**. Todo lo que entra por un puerto **sale regenerado por todos los demás**. Sus consecuencias son las que hay que saber enunciar:

1. **Un único dominio de colisión** para todos los puertos: todas las estaciones compiten por el mismo medio y necesitan **CSMA/CD**.
2. **Obliga al semidúplex.** Como la trama sale por todos los puertos, no puede haber transmisión simultánea en ambos sentidos.
3. **El ancho de banda es compartido**, no por puerto: un concentrador de 10 Mbit/s con 24 puertos ofrece **10 Mbit/s repartidos entre 24**, no 240.
4. **No hay ninguna privacidad**: toda estación recibe todas las tramas, y basta poner el interfaz en **modo promiscuo** para leer el tráfico ajeno. Es la razón de seguridad —además de la de rendimiento— por la que el concentrador es **inadmisible en una red administrativa** y por la que el ENS lo excluye de facto al exigir la separación de flujos.
5. **La topología es estrella física y bus lógico** (§2.2).

Existió una **regla de diseño** que se pregunta, la **regla 5-4-3** de la Ethernet a 10 Mbit/s: entre dos estaciones cualesquiera puede haber como máximo **5 segmentos**, unidos por **4 repetidores**, de los cuales solo **3** pueden tener estaciones conectadas (los otros dos son enlaces entre repetidores). Su fundamento no es arbitrario: es el **presupuesto de retardo** que garantiza que la ranura de colisión de 512 tiempos de bit siga siendo suficiente (§4.2.1).

> **[DATO CLAVE EXAMEN]** **El concentrador está obsoleto y no se fabrica.** Se estudia por tres razones examinables: porque explica qué es un dominio de colisión, porque es la referencia contra la que se define el conmutador, y porque la **regla 5-4-3** sigue apareciendo en los test.

### 5.2. Interconexión en el nivel de enlace de datos

#### 5.2.1. Puentes y conmutadores

**Puente (*bridge*).** Dispositivo de **capa 2** que une dos o más segmentos y **decide, trama a trama, si la reenvía o la descarta**, en función de las **direcciones MAC**. Su aportación conceptual —y la diferencia radical con el repetidor— es el **filtrado**: **una trama cuyo origen y destino están en el mismo segmento no se reenvía al otro**, con lo que **el tráfico local se queda en su segmento** y **cada segmento pasa a ser un dominio de colisión independiente**.

**Cómo funciona un puente transparente** [IEEE8021D], en tres mecanismos que hay que saber nombrar:

1. **Aprendizaje de direcciones.** El puente **mira la dirección MAC de origen** de cada trama que recibe y anota en su **tabla de reenvío** que esa dirección es alcanzable por el puerto por el que ha llegado. Aprende **solo, sin configuración**, y de ahí lo de «transparente». Las entradas tienen un **temporizador de envejecimiento** —típicamente **300 segundos**— tras el cual se borran si no se ha vuelto a ver esa dirección.
2. **Reenvío y filtrado.** Ante una trama, consulta la MAC de **destino**: si está en la tabla y corresponde a **otro puerto**, la reenvía **solo por ese puerto**; si corresponde **al mismo puerto** por el que llegó, la **descarta** (filtrado); y si **no está en la tabla**, la **inunda** por todos los puertos menos el de entrada (*flooding*). Las tramas de **difusión** y de **multidifusión** se **inundan siempre**, y esta es la razón por la que un puente **no divide el dominio de difusión**.
3. **Prevención de bucles.** Si hay dos caminos entre dos segmentos, una trama de difusión circularía indefinidamente y se multiplicaría en cada bucle: es la **tormenta de difusión**, que satura la red en segundos. Como la trama Ethernet **no tiene campo de tiempo de vida** —a diferencia del datagrama IP—, nada la detiene. La solución es el **protocolo de árbol de expansión (STP)**, que **bloquea lógicamente los enlaces redundantes** dejando una única topología sin bucles, y los **reactiva automáticamente** si el camino activo cae.

**Conmutador (*switch*).** Es, funcionalmente, un **puente multipuerto implantado en hardware**. Hace lo mismo que un puente —aprender, filtrar, reenviar, evitar bucles— pero con dos diferencias decisivas de implantación:

- **Muchos puertos** y **conmutación en circuitos específicos (ASIC)** en lugar de en software, lo que le permite operar a **velocidad de cable** (*wire speed*) en todos los puertos a la vez.
- Cada puerto es un **dominio de colisión propio** y funciona en **dúplex**, lo que **elimina las colisiones** y hace innecesario CSMA/CD (§4.2.1).

**Sus consecuencias**, que son el reverso exacto de las del concentrador: **ancho de banda dedicado por puerto** —un conmutador de 24 puertos a 1 Gbit/s ofrece 24 Gbit/s de capacidad de conmutación, no 1—; **dúplex**; **sin colisiones**; y **privacidad relativa**, porque una estación **no ve el tráfico ajeno** salvo la difusión, lo que dificulta la escucha pasiva.

> **[DATO CLAVE EXAMEN]** La comparación concentrador/conmutador es de las preguntas más frecuentes. Cinco pares: **capa 1 / capa 2**; **un dominio de colisión / uno por puerto**; **semidúplex / dúplex**; **ancho de banda compartido / dedicado por puerto**; **inunda siempre / reenvía selectivamente por dirección MAC**. Y lo que **tienen en común**: **ninguno de los dos divide el dominio de difusión**.

**Los tres modos de conmutación**, que se preguntan por la contraposición entre latencia y fiabilidad:

| Modo | Cuándo empieza a reenviar | Latencia | Comprueba errores |
|---|---|---|---|
| **Almacenamiento y reenvío** (*store and forward*) | Tras recibir la **trama completa** | Alta y variable con el tamaño | **Sí**, verifica el **CRC** y descarta las erróneas |
| **Directo** (*cut-through*) | Tras leer los **6 octetos** de la dirección de destino | **Mínima y constante** | **No**: propaga tramas erróneas |
| **Libre de fragmentos** (*fragment free*) | Tras recibir los **primeros 64 octetos** | Intermedia | Parcial: descarta los **fragmentos de colisión** |

El modo **libre de fragmentos** tiene una lógica que conviene explicitar porque explica de dónde sale el número: **los fragmentos de colisión son siempre menores de 64 octetos** (§4.2.1), así que esperar a recibir esos 64 octetos filtra la inmensa mayoría de las tramas defectuosas sin pagar la latencia del almacenamiento completo. En la práctica, **el modo dominante hoy es el de almacenamiento y reenvío**, porque es obligatorio cuando hay cambio de velocidad entre puertos —no se puede reenviar a 1 Gbit/s lo que entra a 100 Mbit/s sin almacenarlo— y porque la latencia ha dejado de ser un problema.

**Conmutadores de capa 3.** Un **conmutador multicapa** o **de capa 3** añade a lo anterior la capacidad de **encaminar entre VLAN** en hardware. Funcionalmente es un encaminador, pero implementado con la electrónica de un conmutador, lo que le da un rendimiento muy superior dentro de la red local a costa de no manejar interfaces de área extensa ni las funciones avanzadas de un encaminador. Es el equipo típico del **nivel de distribución** (§2.2.2).

#### 5.2.2. Funcionamiento de conmutadores y redes virtuales (VLAN)

**Definición.** Una **red de área local virtual (VLAN)** es una **agrupación lógica de puertos y estaciones que constituye un dominio de difusión independiente**, **con independencia de su ubicación física** [IEEE8021Q]. Dicho de otro modo: permite que dos puestos conectados al mismo conmutador estén en redes distintas y no se vean, y que dos puestos en edificios distintos estén en la misma red.

**Los cinco motivos** por los que se segmenta en VLAN, en orden de importancia para una Administración:

1. **Seguridad y separación de flujos.** Es el motivo normativo: `mp.com.4` del ENS (§6.3). Un incidente en un segmento **no se propaga** a los demás, y un equipo solo alcanza lo que necesita.
2. **Contención de la difusión.** Cada VLAN es un dominio de difusión propio, de modo que se acota el tráfico de difusión, que crece con el número de estaciones y degrada a todas.
3. **Agrupación lógica independiente de la ubicación.** Un empleado que cambia de planta no cambia de red.
4. **Simplificación de la gestión**: mover, añadir o cambiar un equipo es un cambio de configuración, no de cableado.
5. **Calidad de servicio**: permite tratar de forma distinta el tráfico de voz, el de datos y el de vídeo.

**Tipos de VLAN por criterio de pertenencia**: **por puerto** (estática, la habitual y la más segura), **por dirección MAC** (dinámica), **por protocolo** (en desuso) y **por autenticación**, que es la asignación dinámica de VLAN tras un **802.1X** correcto (§6.2) y la que interesa en una red administrativa moderna.

**Puertos de acceso y puertos troncales.** Un **puerto de acceso** pertenece a **una sola VLAN** y a él se conecta un equipo final; las tramas viajan **sin etiquetar**. Un **puerto troncal** (*trunk*) transporta el tráfico de **varias VLAN** por un mismo enlace físico —típicamente entre dos conmutadores, o entre el conmutador y el encaminador— y para ello **etiqueta** cada trama con el identificador de su VLAN.

**La etiqueta 802.1Q**, que es el dato duro de este epígrafe (ver **diagrama D17**). Se inserta **entre la dirección de origen y el campo de tipo/longitud**, y mide **4 octetos**:

| Campo | Bits | Contenido |
|---|---|---|
| **TPID** (identificador de protocolo de etiqueta) | **16** | Valor fijo **`0x8100`**, que indica que lo que sigue es una etiqueta |
| **PCP** (prioridad) | **3** | **8 niveles de prioridad** (0 a 7). Es lo que se conoce como **802.1p** |
| **DEI** (indicador de descarte elegible) | **1** | Marca la trama como descartable ante congestión. Antes se llamaba **CFI** |
| **VID** (identificador de VLAN) | **12** | Número de VLAN. `0` y `4095` **reservados** → **4.094 utilizables** |

> **[DATO CLAVE EXAMEN]** Los cuatro números de 802.1Q: **etiqueta de 4 octetos**; **TPID `0x8100`**; **VID de 12 bits**, de donde `2^12 = 4.096` valores y **4.094 VLAN utilizables** al reservarse el 0 y el 4095; y la trama máxima, que **pasa de 1518 a 1522 octetos**. Ese último dato es la causa de un problema práctico clásico: un equipo antiguo que no entienda 802.1Q **descarta la trama etiquetada por exceso de tamaño** y la registra como *baby giant*.

**La VLAN nativa** es la VLAN cuyo tráfico circula **sin etiquetar** por un enlace troncal. Su existencia es una herencia de compatibilidad y una **debilidad de seguridad** conocida —el ataque de **doble etiquetado** o *VLAN hopping* se apoya en ella—, por lo que la buena práctica y las guías del CCN recomiendan **asignar la VLAN nativa a una VLAN sin uso** y no dejarla en la VLAN 1 por defecto [CCN-STIC-816].

**Comunicación entre VLAN.** Como cada VLAN es un dominio de difusión y, normalmente, una subred IP distinta, **el tráfico entre VLAN necesita un dispositivo de capa 3**. Dos formas de conseguirlo: el **encaminador con enlace troncal** —un solo interfaz físico configurado con subinterfaces, uno por VLAN, esquema conocido como *router on a stick*— o, lo habitual hoy, un **conmutador de capa 3** que encamina internamente entre sus interfaces virtuales de VLAN.

> **[EJERCICIO RESUELTO]** ¿Cuántos dominios de colisión y cuántos de difusión hay en esta red? Un **encaminador** con dos interfaces; del primero cuelga un **conmutador de 8 puertos** con **dos VLAN**, la A con 3 puestos y la B con 4 puestos; del segundo cuelga un **concentrador de 6 puertos** con 5 puestos. Cálculo de **dominios de colisión**: el conmutador aporta **un dominio por puerto activo**, es decir, `7 puestos + 1 enlace al encaminador = 8`; el concentrador es **un único dominio** que incluye su enlace al encaminador, luego **1**; total **9 dominios de colisión**. Cálculo de **dominios de difusión**: la VLAN A es uno, la VLAN B es otro y el segmento del concentrador es un tercero, luego **3 dominios de difusión** —tantos como interfaces lógicos tenga el encaminador, contando las subinterfaces del troncal—. **La regla que se valora**: el número de dominios de colisión es el **número de puertos de conmutador activos más el número de segmentos compartidos**; el de dominios de difusión es el **número de VLAN más el de segmentos separados por el encaminador**.

**Agregación de enlaces.** Merece cita porque aparece en los pliegos: **IEEE 802.1AX** (antes 802.3ad) permite **agrupar varios enlaces físicos en uno lógico**, con reparto de carga y con **conmutación por fallo** automática si uno cae. Su protocolo de negociación es **LACP**. Es la forma normal de dar 2 o 4 Gbit/s a un enlace ascendente cuando no se dispone de puertos de 10 Gbit/s.

> **[REFERENCIA CRUZADA]** La **planificación y administración** de las VLAN, la configuración del árbol de expansión y de los enlaces troncales, y la monitorización del tráfico de un conmutador corresponden al **Tema 30**, que aborda la red local desde el punto de vista de quien la opera. Aquí se ha descrito **qué son y cómo funcionan**.

### 5.3. Interconexión en el nivel de red: enrutadores y encaminamiento

**Encaminador (*router*).** Dispositivo de **capa 3** que interconecta **redes distintas** y decide el camino de cada paquete en función de su **dirección IP de destino**, consultando su **tabla de encaminamiento**.

**Sus cuatro diferencias con el conmutador**, que es lo que se pregunta:

1. **Decide por dirección IP**, no por dirección MAC. Y la dirección IP es **jerárquica**, lo que permite **agregar rutas** y que la tabla no crezca con el número de equipos.
2. **Separa dominios de difusión.** Un encaminador **no reenvía la difusión** de capa 2: cada uno de sus interfaces es un dominio de difusión distinto. Es la única forma de contener la difusión sin recurrir a VLAN.
3. **Reconstruye la trama en cada salto.** Descarta la trama de entrada y construye una nueva con **direcciones MAC nuevas** para el siguiente enlace, decrementa el **tiempo de vida** del paquete y recalcula la suma de comprobación de la cabecera IP. **Las direcciones MAC cambian en cada salto; las direcciones IP no cambian en todo el trayecto.**
4. **Elimina los bucles por sí mismo**, gracias al campo de **tiempo de vida** del datagrama IP, que se agota. No necesita árbol de expansión.

Además, el encaminador es el punto natural donde se aplican **listas de control de acceso**, **traducción de direcciones (NAT)** y, en su versión de seguridad, las funciones de **cortafuegos**.

**Puerta de enlace predeterminada.** Es el concepto que une §5.2 y §5.3 desde el punto de vista del equipo final: cuando un puesto quiere enviar un paquete, aplica la **operación Y lógica** entre la dirección de destino y su propia máscara de subred; si el resultado coincide con su dirección de red, el destino es **local** y resuelve su MAC por **ARP** para entregárselo directamente; si no coincide, el destino es **remoto** y envía la trama a la **dirección MAC de la puerta de enlace predeterminada** —no a la del destino final—, que es la del interfaz del encaminador en su segmento.

> **[DATO CLAVE EXAMEN]** La frase que resume la diferencia y que conviene poder escribir tal cual: **el conmutador interconecta equipos dentro de una misma red y decide por dirección MAC; el encaminador interconecta redes distintas y decide por dirección IP. El conmutador propaga la difusión; el encaminador la detiene.**

> **[REFERENCIA CRUZADA]** El direccionamiento IP, las máscaras, el cálculo de subredes, los protocolos de encaminamiento (RIP, OSPF, BGP) y el detalle de la decisión de reenvío corresponden al **Tema 34**.

### 5.4. Dispositivos de frontera, pasarelas y puntos de acceso

**Pasarela (*gateway*).** En sentido estricto, un dispositivo que interconecta redes con **arquitecturas o protocolos incompatibles**, realizando la **traducción en las capas altas** —de la 4 a la 7— del modelo OSI. No se limita a reenviar: **reescribe el contenido**. Ejemplos: una pasarela de **correo** entre dos sistemas de mensajería distintos, una pasarela **de voz** que traduce entre telefonía IP y la red telefónica conmutada, una pasarela de **protocolo industrial** que traduce Modbus a MQTT.

Conviene advertir de una **ambigüedad terminológica que induce a error en los test**: en la práctica cotidiana, y en la configuración de cualquier sistema operativo, la palabra «pasarela» (*gateway*) designa la **puerta de enlace predeterminada**, que es simplemente **un encaminador de capa 3** y no traduce nada. **En sentido estricto, pasarela y encaminador no son lo mismo**: si una pregunta define la pasarela como el dispositivo que interconecta arquitecturas heterogéneas traduciendo protocolos de capas altas, la respuesta es esa; si la define como la salida de la subred local, se está hablando del encaminador.

**Punto de acceso inalámbrico (*access point*).** Dispositivo de **capa 2** que actúa como **puente entre el medio inalámbrico (802.11) y el cableado (802.3)**, traduciendo entre dos formatos de trama distintos. Sus rasgos:

- Es el **coordinador de la celda**: emite **balizas** (*beacons*) periódicas anunciando el SSID, gestiona la **asociación** y **autenticación** de las estaciones, y almacena tramas para las estaciones en modo de ahorro de energía.
- **Es un dominio de colisión compartido**, a diferencia del puerto de conmutador. Todas las estaciones asociadas compiten por el mismo medio (§4.2.2).
- Se despliega en dos arquitecturas: **autónoma**, en la que cada punto de acceso se configura por separado, y **centralizada**, en la que una **controladora** —física o en la nube— gestiona todos los puntos de acceso, planifica canales y potencias automáticamente y coordina la **itinerancia** entre celdas. En una red municipal con decenas de dependencias, la arquitectura centralizada es la única viable.
- Se alimenta habitualmente por **PoE**, lo que evita llevar corriente a los falsos techos: es una de las razones prácticas por las que 802.3at y 802.3bt importan en un pliego.

**Otros dispositivos de frontera** que conviene ubicar en su capa:

| Dispositivo | Capa | Función |
|---|---|---|
| **Transceptor / conversor de medio** | **1** | Adapta entre medios (cobre y fibra) sin interpretar |
| **Módem** | **1** | Modula y demodula: adapta la señal digital al medio del operador |
| **Cortafuegos** | **3-4**, y **7** si es de nueva generación | Filtra por dirección, puerto, estado de conexión y aplicación |
| **Servidor de acceso remoto / concentrador de VPN** | **3** | Termina túneles cifrados de acceso remoto |
| **Equilibrador de carga** | **4-7** | Reparte peticiones entre varios servidores |
| **Repartidor y panel de parcheo** | **0** (pasivo) | Elemento **pasivo** de cableado: no es un dispositivo de red |

> **[DATO CLAVE EXAMEN]** El **panel de parcheo** (*patch panel*) **no es un dispositivo de interconexión**: es un elemento **pasivo** del cableado estructurado que solo termina y ordena los cables. Es una trampa habitual en los test, porque está en el armario junto al conmutador y se parece a él.

> **[EJEMPLO AYTO MADRID]** El armario de una planta de la oficina reúne casi todo el catálogo. Arriba, dos **paneles de parcheo** con las 48 tomas de la planta (pasivos). Debajo, un **conmutador** de acceso de 48 puertos con **PoE de tipo 3**, que alimenta los teléfonos IP, las cámaras y los dos **puntos de acceso** del pasillo. Del conmutador sale un enlace de **fibra multimodo** hacia el armario principal, donde un **conmutador de capa 3** encamina entre las VLAN de la oficina y conecta con el **encaminador** de salida hacia la red corporativa, protegido por un **cortafuegos**. La red de invitados de la sala de espera viaja etiquetada en su propia VLAN hasta ese cortafuegos y sale **directamente a internet**, sin tocar ninguna otra VLAN municipal. No hay ningún **concentrador**: no se admite en la red del Ayuntamiento.

---

## 6. Normativa y aplicación en la Administración pública

### 6.1. Estándares de cableado estructurado e infraestructura

**Qué es el cableado estructurado y por qué existe.** Antes de su normalización, cada tecnología de red exigía su propio cable: coaxial grueso para Ethernet, par apantallado para Token Ring, otro tendido para la telefonía. Cambiar de tecnología significaba **recablear el edificio**. El **cableado estructurado** invierte el planteamiento: se instala una **infraestructura genérica, normalizada e independiente de la aplicación**, capaz de soportar voz, datos, vídeo y control durante toda la vida útil del edificio, de modo que cambiar de tecnología sea un cambio de electrónica en el armario, no de obra [ISO11801].

Ese es el argumento que hay que saber dar en un caso práctico: **el cableado es la parte más duradera y más cara de intervenir de una red** —vive veinte o treinta años, frente a los cinco o siete de un conmutador— y por eso **se sobredimensiona deliberadamente**.

**Las tres familias normativas** y su correspondencia:

| Ámbito | Norma | Observaciones |
|---|---|---|
| **Internacional** | **ISO/IEC 11801** (serie) | Norma de referencia. Parte 1 general; partes por tipo de recinto |
| **Europeo** | **EN 50173** (serie), **UNE-EN 50173** en España, con **EN 50174** de instalación | **Es la que se cita en un pliego español** |
| **Norteamericano** | **ANSI/TIA-568** (`.1-D` general, `.2-D` cobre, `.3-D` fibra), con **TIA-569**, **606** y **607** | Terminología distinta para los mismos conceptos |

**Los subsistemas del cableado**, que hay que saber enumerar y que reproducen la jerarquía de §2.2.2 (ver **diagrama D18**):

1. **Subsistema de campus** o troncal de edificios: une el **distribuidor de campus** con los distribuidores de cada edificio. Medio típico: **fibra monomodo**.
2. **Subsistema vertical** o troncal de edificio: une el **distribuidor de edificio** (armario principal) con los **distribuidores de planta**. Medio típico: **fibra multimodo**, y par trenzado para la voz.
3. **Subsistema horizontal**: une el **distribuidor de planta** con las **tomas de usuario**. Medio: **par trenzado**. **Máximo 90 metros** de cable fijo.
4. **Área de trabajo**: de la toma al equipo, mediante **latiguillo**. Junto con el del armario, **máximo 10 metros** entre ambos.

**Los elementos** que hay que saber nombrar: el **armario o repartidor** (*rack*), el **panel de parcheo** donde terminan los cables horizontales, la **toma de usuario** (roseta) con conector **RJ-45** hembra, los **latiguillos** de conexión, las **canalizaciones** y **bandejas**, y el **sistema de etiquetado y documentación**, que la norma **TIA-606** convierte en obligación y que en la práctica es lo primero que falla y lo que más caro sale.

> **[DATO CLAVE EXAMEN]** La cifra que se pregunta siempre y su desglose exacto: **el canal máximo es de 100 metros**, repartidos en **90 m de cable horizontal fijo** más **10 m de latiguillos** sumando los de ambos extremos. Y el corolario práctico: **si la toma está a 95 m del armario, el enlace no cumple la norma aunque el equipo funcione**; la solución es un armario intermedio, no un cable más largo.

**Las dos normas de despliegue que también se exigen**: la **certificación del cableado** con equipo homologado, que mide los parámetros de §3.5.1 y emite un informe por toma —requisito habitual de recepción de la obra en un contrato público—, y la **documentación y etiquetado** de cada elemento.

**El marco jurídico español de la infraestructura del edificio.** Cuando la red local se instala en un **edificio de nueva planta o rehabilitado**, entra en juego la normativa de **infraestructuras comunes de telecomunicación (ICT)**:

- El **artículo 55 de la Ley 11/2022**, *Infraestructuras comunes y redes de comunicaciones electrónicas en los edificios*, remite a real decreto la regulación del **punto de interconexión de la red interior con las redes públicas** y de las **condiciones aplicables a la red interior**, y ordena que la normativa técnica básica de edificación prevea **capacidad de obra civil suficiente para el paso de las redes de distintos operadores**, de modo que se facilite su **uso compartido** [LGT].
- La **disposición adicional tercera** de la misma ley remite el régimen de las ICT al **Real Decreto-ley 1/1998** y a sus desarrollos reglamentarios [RDL1-1998].
- El desarrollo vigente es el **Real Decreto 346/2011**, Reglamento regulador de las ICT, con los recintos **RITI**, **RITS** y **RITU**, los **registros** principal, secundarios y de terminación de red, y la exigencia de **proyecto técnico** firmado por titulado competente [RD346].

> **[DATO CLAVE EXAMEN]** La distinción que conviene tener clara y que casi nunca se explicita: **la normativa de ICT regula la infraestructura de obra civil y el acceso a los servicios de telecomunicación del edificio** —canalizaciones, recintos, registros, acometida de los operadores—, mientras que **ISO/IEC 11801 y EN 50173 regulan el cableado genérico de la red local** que discurre por esa infraestructura. **Son planos distintos y compatibles**: en una obra municipal nueva hay que cumplir **las dos**.

### 6.2. Seguridad y control de acceso en redes administrativas

La red local de una Administración tiene una particularidad que condiciona su seguridad: **es una red física accesible al público**. En una Oficina de Atención a la Ciudadanía hay tomas de red en zonas de atención, salas de espera, salas de reuniones donde entran terceros y despachos que no siempre están cerrados. **Cualquier toma es un punto de entrada potencial**, y esa es la amenaza que la normativa manda tratar.

**Los seis controles** que hay que saber enunciar, de menos a más:

**1. Seguridad física del cableado y de los armarios.** Es la primera y la que se olvida. Los armarios de comunicaciones **deben estar cerrados con llave y en local de acceso restringido**, y las canalizaciones no deben ser accesibles. Tiene apoyo normativo expreso: **`mp.if.1`, «Áreas separadas y con control de acceso»**, aplica en **las tres categorías** del ENS y ordena que el equipamiento del centro de proceso de datos se instale en áreas separadas y que se controlen los accesos a ellas [ENS].

**2. Desactivación de puertos no usados y seguridad de puerto.** Un puerto de conmutador que no se usa debe estar **administrativamente deshabilitado**. La **seguridad de puerto** (*port security*) limita además el número de direcciones MAC que puede aprender un puerto y actúa —bloqueando o alertando— si aparece otra, lo que impide conectar un conmutador no autorizado bajo una mesa.

**3. Segmentación en VLAN.** Es el control estructural: la red se parte en segmentos que se corresponden con **funciones y niveles de confianza distintos**. En la oficina de referencia, como mínimo: **puestos de tramitación**, **telefonía IP**, **impresión**, **videovigilancia**, **gestión de los equipos de red**, **Wi-Fi corporativa** y **Wi-Fi de invitados**. La última **no debe tener ninguna visibilidad de las demás** y sale directamente a internet.

**4. Control de admisión con IEEE 802.1X.** Es el control que convierte la toma de red de un espacio público en algo seguro: **el puerto no da servicio hasta que el equipo se autentica**. Sus **tres papeles** [IEEE8021X]:

- El **suplicante**: el programa cliente del equipo que quiere conectarse.
- El **autenticador**: el **conmutador** —o el **punto de acceso**—, que mantiene el puerto en estado **no controlado** hasta que la autenticación tenga éxito, dejando pasar únicamente tramas **EAPOL**.
- El **servidor de autenticación**: normalmente un servidor **RADIUS**, que verifica las credenciales contra el directorio corporativo.

Tras una autenticación correcta, el servidor puede además **devolver la VLAN que corresponde a ese usuario o equipo**, lo que permite que **la segmentación siga a la persona y no al cable**: el mismo puerto pone a un empleado en la VLAN de tramitación y a un visitante en la de invitados. Para los equipos que no admiten suplicante —impresoras, cámaras, teléfonos antiguos— se emplean mecanismos de excepción como la **autenticación por MAC** o el **acceso invitado**, que son más débiles y hay que documentar como tales.

**5. Protección del plano de conmutación.** Un conjunto de controles que las guías del CCN detallan y que conviene citar: **protección del árbol de expansión** frente a un equipo que se anuncie como raíz, **inspección de ARP** contra la suplantación, **vigilancia de DHCP** para impedir servidores no autorizados, **control de tormentas de difusión** y **desactivación de la negociación automática de enlaces troncales** en los puertos de acceso, que es la defensa contra el salto de VLAN [CCN-STIC-641].

**6. Seguridad de la red inalámbrica.** Cifrado **WPA3** —o **WPA2 empresarial** como mínimo—, autenticación **802.1X** para la red corporativa, **red de invitados separada** con portal y con salida directa a internet, desactivación de mecanismos heredados (WEP, WPS, TKIP), y **planificación de potencia** para no radiar innecesariamente fuera del edificio [CCN-STIC-816].

> **[EJEMPLO AYTO MADRID]** El caso que hace tangible todo lo anterior: un ciudadano espera en la sala de la oficina y ve una **toma de red** en el zócalo. Sin controles, conectar un portátil le daría **dirección IP por DHCP** y **visibilidad de la VLAN de tramitación**. Con los controles descritos: la toma está **deshabilitada** si no se usa; si se usa, **802.1X** deja el puerto en estado no controlado y su portátil, sin credenciales, **no pasa de EAPOL**; y aunque se autenticara como invitado, el servidor RADIUS lo colocaría en la **VLAN de invitados**, cuyo tráfico va etiquetado hasta el cortafuegos y **sale a internet sin ver ninguna otra VLAN municipal**. Los tres controles son **acumulativos**: ninguno basta por sí solo, y esa es exactamente la idea de defensa en profundidad que el ENS presupone.

### 6.3. Adecuación al Esquema Nacional de Seguridad

**El encaje legal.** El **artículo 156 de la Ley 40/2015** establece el **Esquema Nacional de Seguridad**, desarrollado por el **Real Decreto 311/2022** [L40-2015] [ENS]. Es de **aplicación directa al Ayuntamiento de Madrid y a sus organismos autónomos**, incluido el IAM, y por tanto a la red local de cualquier dependencia municipal.

**Las cuatro medidas del grupo `mp.com`** —protección de las comunicaciones— del anexo II, **verificadas literalmente contra el PDF consolidado del BOE** (ver **diagrama D19**):

| Medida | Denominación literal | Dimensiones | Aplicación |
|---|---|---|---|
| **`mp.com.1`** | **Perímetro seguro** | Todas | **Las tres categorías**: BÁSICA, MEDIA y ALTA |
| **`mp.com.2`** | **Protección de la confidencialidad** | C | BAJO: aplica · MEDIO: + R1 · ALTO: + R1 + R2 + R3 |
| **`mp.com.3`** | **Protección de la integridad y de la autenticidad** | I, A | BAJO: aplica · MEDIO: + R1 + R2 · ALTO: + R1 + R2 + R3 + R4 |
| **`mp.com.4`** | **Separación de flujos de información en la red** | Todas | BÁSICA: **no aplica** · MEDIA: + [R1 o R2 o R3] · ALTA: + [R2 o R3] + R4 |

**Contenido de cada una, en lo que atañe a la red local:**

- **`mp.com.1` — Perímetro seguro.** Exige *«un sistema de protección perimetral que separe la red interna del exterior»*, y que **todo el tráfico atraviese dicho sistema**; además, **todos los flujos a través del perímetro deben estar autorizados previamente**. El propio ENS remite a una **Instrucción Técnica de Seguridad de Interconexión de Sistemas de Información** para el detalle por categoría.
- **`mp.com.2` — Protección de la confidencialidad.** Exige emplear **redes privadas virtuales cifradas** cuando la comunicación discurra **fuera del propio dominio de seguridad**. Su **refuerzo R1** obliga a usar **algoritmos y parámetros autorizados por el CCN**.
- **`mp.com.3` — Protección de la integridad y de la autenticidad.** Exige **asegurar la autenticidad del otro extremo** antes de intercambiar información y **prevenir ataques activos**, que la norma enumera expresamente como **la alteración de la información en tránsito**, **la inyección de información espuria** y **el secuestro de la sesión por una tercera parte**.
- **`mp.com.4` — Separación de flujos de información en la red.** Es **la medida nuclear de este tema**. Su requisito general: *«el tráfico por la red se segregará para que cada equipo solamente tenga acceso a la información que necesita»*, y **`mp.com.4.2`**: *«si se emplean comunicaciones inalámbricas, será en un segmento separado»*. Sus cuatro refuerzos son escalonados y hay que saberlos: **R1, segmentación lógica básica**, que ordena literalmente implantar los segmentos **mediante VLAN** y segregar **como mínimo en usuarios, servicios y administración**; **R2, segmentación lógica avanzada** mediante **VPN**; **R3, segmentación física** con **medios separados**; y **R4, puntos de interconexión**, que exige control de entrada de usuarios y de entrada y salida de información en cada segmento, y que el punto de interconexión esté **particularmente asegurado, mantenido y monitorizado**.

> **[DATO CLAVE EXAMEN]** Cuatro precisiones sobre `mp.com` que discriminan una respuesta correcta de una aproximada: **`mp.com.4` es la única del grupo que NO APLICA en categoría BÁSICA**; su denominación oficial es **«separación de flujos de información en la red»**, no «segregación de redes», que era su nombre en el derogado RD 3/2010; **`mp.com.3` es «protección de la integridad y de la autenticidad»**, en ese orden; y **el refuerzo R1 de `mp.com.4` nombra expresamente las VLAN** y fija la segregación mínima en **usuarios, servicios y administración**. Es el único punto del ENS donde una tecnología concreta de red local aparece citada por su nombre.

**Otras medidas del anexo II que se predican de la red local**, y que conviene añadir al desarrollo para demostrar alcance:

- **`mp.eq.4` — Otros dispositivos conectados a la red** (dimensión C; BAJO aplica, MEDIO y ALTO con R1). Alcanza expresamente a los **dispositivos multifunción** (impresoras y escáneres), los **dispositivos multimedia**, los de **internet de las cosas** y los **personales de los empleados (BYOD)**. Exige que tengan **configuración de seguridad adecuada** que garantice el control del flujo de entrada y salida de información, y que permitan **eliminar la información** de sus soportes. Su **refuerzo R2** pide soluciones que permitan **visualizar los dispositivos presentes en la red, controlar su conexión y desconexión y verificar su configuración**, que es, en términos de producto, un **sistema de control de admisión a la red**.
- **`mp.if.1` — Áreas separadas y con control de acceso**, ya citada en §6.2, aplicable en las **tres categorías**.
- **`op.acc.5` — Mecanismo de autenticación**, que es a lo que remite `mp.com.3.1` para asegurar la autenticidad del otro extremo y lo que da cobertura al despliegue de 802.1X.
- **`op.exp.8` — Registro de la actividad**, que exige una **base de tiempo común** y por tanto **sincronización horaria** de todos los equipos de red, sin la cual los registros de conmutadores y puntos de acceso no son correlacionables.
- **`op.mon.1` — Detección de intrusión**, que se apoya en la instrumentación de la propia red local.

> **[EJEMPLO AYTO MADRID]** Traducido a la oficina de referencia, la normativa dicta el diseño casi elemento por elemento. La conexión con la red corporativa pasa por un **sistema de protección perimetral** que todo el tráfico atraviesa (`mp.com.1`). La red está **segmentada en VLAN** separando como mínimo puestos, servicios y gestión de los equipos de red (`mp.com.4.r1`), lo que en categoría MEDIA es exigible y satisface el requisito con solo uno de los tres refuerzos. La **Wi-Fi de invitados y la corporativa van en segmentos separados** del resto, no por buena práctica sino porque lo ordena `mp.com.4.2`. Las **impresoras multifunción y las cámaras** viven en segmentos propios y con configuración endurecida (`mp.eq.4`). Los **armarios de comunicaciones** están en locales cerrados con control de acceso (`mp.if.1`). El acceso a la red exige **autenticación** (`op.acc.5` vía 802.1X). Y todos los equipos de red comparten **hora NTP** para que sus registros sean correlacionables (`op.exp.8`).

> **[REFERENCIA CRUZADA]** Los **principios generales del ENS y del ENI**, sus categorías, el análisis de riesgos, la declaración de aplicabilidad y el régimen de auditoría corresponden al **Tema 39**. La **seguridad perimetral**, los cortafuegos, los sistemas de detección de intrusión, el **acceso remoto seguro** y las **VPN**, al **Tema 36**. La **administración diaria** de esta misma red —altas y bajas de usuarios, gestión de dispositivos, monitorización y control de tráfico—, al **Tema 30**. Y la **conexión de la red municipal a la red SARA**, con su norma técnica de interoperabilidad, al **Tema 34**.

---

## Los diez datos que no se pueden fallar

Bloque de repaso final. Si el día del examen solo hubiera tiempo para una hoja, sería esta.

1. **Los cinco rasgos de una red local**: ámbito reducido, **medio propio** —el criterio decisivo, no la distancia—, alta velocidad, retardo y error bajos, y **medio compartido**, del que nace el problema del acceso.
2. **El IEEE 802 normaliza solo las capas 1 y 2** y **parte la capa de enlace en dos subcapas**: **LLC (802.2)**, común a la familia, y **MAC**, específica de cada tecnología. **Solo la MAC toca el medio.** La dirección MAC tiene **48 bits**, los 24 primeros de **OUI**.
3. **Las normas**: **802.1Q** VLAN · **802.1D/w/s** árbol de expansión · **802.1X** control de acceso por puerto · **802.3** Ethernet · **802.4** Token Bus · **802.5** Token Ring · **802.11** Wi-Fi · **802.15.1** Bluetooth · **802.15.4** base de Zigbee · **802.16** WiMAX. **FDDI no es IEEE**: es ANSI/ISO.
4. **Topología física ≠ lógica**: concentrador = **estrella física, bus lógico**; Token Ring con MAU = **estrella física, anillo lógico**; conmutador = **estrella física, punto a punto**.
5. **Banda base = señal digital sin modular, un canal, bidireccional, Ethernet** (partícula `BASE`). **Banda ancha = portadora modulada, varios canales por FDM, unidireccional por canal, televisión por cable y DSL**. Códigos de línea: **Manchester** en 10BASE-T, **4B/5B + MLT-3** en 100BASE-TX, **4D-PAM5** en 1000BASE-T, **64B/66B** en 10 Gbit/s.
6. **La trama Ethernet**: preámbulo **7** + SFD **1** + destino **6** + origen **6** + tipo/longitud **2** + datos **46-1500** + FCS **4**. **Mínima 64, máxima 1518, 1522 con etiqueta. MTU 1500.**
7. **CSMA/CD**: escucha antes y durante; ante colisión, **atasco de 32 bits** y **retroceso exponencial binario** `[0, 2^k − 1]` con **k = mín(n,10)**, hasta **16 intentos**. **Ranura de colisión de 512 tiempos de bit = 64 octetos**, de donde sale la trama mínima. **Se desactiva en dúplex** y **no existe en 10 Gbit/s**.
8. **CSMA/CA**: la colisión **no se puede detectar** porque el emisor no oye mientras transmite. Escucha física **y virtual (NAV)**; **DIFS + retroceso aleatorio obligatorio** en `[0, CW−1]` con **CWmín 15 y CWmáx 1023**; **ACK obligatorio tras un SIFS**; **RTS/CTS** opcional contra el **nodo oculto**. En 5 GHz: **SIFS 16 µs, ranura 9 µs, DIFS 34 µs**.
9. **Dispositivos y dominios**: **repetidor y concentrador** (capa 1) = **1 dominio de colisión, 1 de difusión**; **puente, conmutador y punto de acceso** (capa 2) = **1 dominio de colisión por puerto, 1 de difusión por VLAN**; **encaminador** (capa 3) = **1 y 1 por interfaz**. **Etiqueta 802.1Q**: 4 octetos, **TPID `0x8100`**, **PCP 3 bits**, **DEI 1**, **VID 12 bits → 4.094 VLAN**.
10. **Normativa**: cableado **ISO/IEC 11801 / EN 50173 / TIA-568**, **canal de 100 m = 90 + 10**, **Cat 6A = Clase EA = 500 MHz = 10 Gbit/s a 100 m**; obra civil del edificio por **ICT** (**art. 55 de la Ley 11/2022** y **RD 346/2011**); Wi-Fi en **uso común del dominio público radioeléctrico** (**art. 88 de la Ley 11/2022**, **sin título habilitante y sin protección frente a interferencias**); y del ENS, **`mp.com.1`** perímetro seguro en las tres categorías, **`mp.com.4`** separación de flujos —**que no aplica en BÁSICA** y cuyo **R1 nombra las VLAN** con segregación mínima en **usuarios, servicios y administración**— y **`mp.com.4.2`**, que ordena que **las comunicaciones inalámbricas vayan en un segmento separado**.
