# Tema 37 — Test de Autoevaluación

> **Título**: Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión.
> **Formato**: 60 preguntas tipo test A/B/C (formato oficial oposición)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-08-27
> **Fuentes**: ver tema-37-fuentes.md

---

## Instrucciones

- Cada pregunta tiene **3 opciones** (A, B, C). Solo una es correcta.
- Penalización en examen real: respuesta incorrecta descuenta **1/3** del valor de una correcta.
- Tiempo orientativo: 1 minuto por pregunta.
- Distribución: concepto y normalización IEEE 802 (P1-P8), tipología y topologías (P9-P18), técnicas de transmisión (P19-P30), métodos de acceso al medio (P31-P42), dispositivos de interconexión (P43-P54) y normativa en la Administración pública (P55-P60).

---

### Pregunta 1

**De los rasgos que caracterizan a una red de área local, ¿cuál es el que mejor la discrimina frente a una red de área extensa?**

A) La distancia máxima entre sus nodos, fijada normativamente en 2 kilómetros
B) La titularidad del medio de transmisión, que es propiedad de la organización que la explota
C) La velocidad de transmisión, que debe ser siempre igual o superior a 1 Gbit/s

<details><summary>Respuesta</summary>

**Correcta: B) La titularidad del medio de transmisión, que es propiedad de la organización que la explota** Es el criterio decisivo y también el jurídicamente más significativo: en una red local el cable se instala y se mantiene sin operador ni contrato de servicio. Ni la distancia ni la velocidad tienen umbrales normativos: son características cualitativas y orientativas.

*Referencia: §1.1 [IEEE802]*
</details>

---

### Pregunta 2

**Dos edificios municipales separados por 800 metros se unen mediante fibra óptica propiedad del Ayuntamiento. ¿Cómo se clasifica esa red?**

A) Como red de área extensa, porque supera los 500 metros de un segmento de red local
B) Como red de área metropolitana, por el hecho de discurrir por vía pública
C) Como red de área local o de campus, porque el medio es propio y el alcance es reducido

<details><summary>Respuesta</summary>

**Correcta: C) Como red de área local o de campus, porque el medio es propio y el alcance es reducido** Si esos mismos 800 metros se cubrieran con un enlace contratado a un operador, técnicamente ya no sería una red local. Misma distancia y misma velocidad, distinta respuesta: lo que cambia es de quién es el medio.

*Referencia: §1.1 y §2.1 [IEEE802]*
</details>

---

### Pregunta 3

**¿Qué aportación arquitectónica introduce el IEEE 802 respecto del modelo OSI?**

A) Divide la capa de enlace de datos en dos subcapas, LLC y MAC
B) Añade una octava capa por encima de la de aplicación para las redes locales
C) Fusiona la capa física y la de enlace en una sola capa de acceso a la red

<details><summary>Respuesta</summary>

**Correcta: A) Divide la capa de enlace de datos en dos subcapas, LLC y MAC** La subcapa LLC (802.2) es común a toda la familia y ofrece a la capa de red un servicio independiente de la tecnología; la subcapa MAC es específica de cada tecnología y es la única que toca el medio. La fusión de las capas 1 y 2 en un nivel de acceso a la red es del modelo TCP/IP, no del IEEE.

*Referencia: §1.2 [IEEE802] [IEEE8022]*
</details>

---

### Pregunta 4

**¿Cuál es el ámbito normativo del comité IEEE 802?**

A) Las siete capas del modelo OSI aplicadas a redes locales y metropolitanas
B) Las capas de red y de transporte de las redes de área local
C) Las capas física y de enlace de datos de las redes de área local y metropolitana

<details><summary>Respuesta</summary>

**Correcta: C) Las capas física y de enlace de datos de las redes de área local y metropolitana** Todo lo que está por encima —IP, TCP, HTTP— corresponde al IETF. Por eso una red local es, técnicamente, una tecnología de capas 1 y 2: entrega tramas dentro de un segmento y nada más.

*Referencia: §1.2 [IEEE802]*
</details>

---

### Pregunta 5

**En una trama Ethernet, el campo de dos octetos situado tras las direcciones vale `0x0800`. ¿Cómo debe interpretarse?**

A) Como un campo de tipo (EtherType), porque su valor es igual o superior a 1536
B) Como un campo de longitud, porque todo valor hexadecimal designa longitud en 802.3
C) Como un campo de prioridad de la etiqueta 802.1Q

<details><summary>Respuesta</summary>

**Correcta: A) Como un campo de tipo (EtherType), porque su valor es igual o superior a 1536** La regla de desambiguación es: si el valor es igual o menor que 1500 se trata de una longitud (trama 802.3); si es igual o mayor que 1536 (`0x0600`) se trata de un tipo (trama Ethernet II). `0x0800` equivale a 2048 e identifica IPv4.

*Referencia: §1.2 [IEEE8023] [RFC1122]*
</details>

---

### Pregunta 6

**¿Cuántos bits tiene una dirección MAC y qué representan sus 24 primeros bits?**

A) 32 bits, de los que los 24 primeros son el identificador de red
B) 48 bits, de los que los 24 primeros son el identificador único de organización (OUI)
C) 64 bits, de los que los 24 primeros identifican el segmento de red local

<details><summary>Respuesta</summary>

**Correcta: B) 48 bits, de los que los 24 primeros son el identificador único de organización (OUI)** El OUI lo asigna el IEEE al fabricante, y los 24 bits restantes los asigna el fabricante a cada tarjeta. La dirección de difusión es `FF:FF:FF:FF:FF:FF`, con los 48 bits a uno.

*Referencia: §1.2 [IEEE802]*
</details>

---

### Pregunta 7

**Un sistema operativo aleatoriza la dirección MAC de su interfaz Wi-Fi por privacidad. ¿Qué bit de la dirección indica que ha sido asignada por software?**

A) El bit U/L, segundo menos significativo del primer octeto, puesto a 1
B) El bit I/G, menos significativo del primer octeto, puesto a 1
C) El bit más significativo del último octeto, puesto a 0

<details><summary>Respuesta</summary>

**Correcta: A) El bit U/L, segundo menos significativo del primer octeto, puesto a 1** A 0 indica administración universal, es decir, la dirección que grabó el fabricante; a 1 indica administración local. El bit I/G distingue las direcciones individuales de las de grupo, que es cosa distinta.

*Referencia: §1.2 [IEEE802]*
</details>

---

### Pregunta 8

**¿Cuál de las siguientes asociaciones entre norma y materia es INCORRECTA?**

A) IEEE 802.15.1 corresponde a Bluetooth
B) IEEE 802.1X corresponde al cifrado de las redes inalámbricas
C) IEEE 802.1Q corresponde a las redes de área local virtuales

<details><summary>Respuesta</summary>

**Correcta: B) IEEE 802.1X corresponde al cifrado de las redes inalámbricas** 802.1X es control de acceso a la red basado en puerto, no cifrado; la seguridad inalámbrica es 802.11i, base de WPA2. Las otras dos asociaciones son correctas, y conviene añadir que 802.16 es WiMAX, una red metropolitana y no local, y que FDDI no es una norma del IEEE sino de ANSI e ISO.

*Referencia: §1.3 [IEEE802] [IEEE8021X]*
</details>

---

### Pregunta 9

**Una red Ethernet construida con un concentrador presenta:**

A) Topología física de bus y topología lógica de estrella
B) Topología física y lógica de estrella, sin colisiones
C) Topología física de estrella y topología lógica de bus

<details><summary>Respuesta</summary>

**Correcta: C) Topología física de estrella y topología lógica de bus** El concentrador cablea en estrella pero repite por todos los puertos, de modo que eléctricamente sigue siendo un bus con colisiones. Fue el conmutador, y no el concentrador, el que acabó con el bus lógico.

*Referencia: §2.2 [IEEE8023]*
</details>

---

### Pregunta 10

**¿Cuántos enlaces necesita una malla completa de 12 nodos?**

A) 132 enlaces, uno por cada par ordenado de nodos
B) 66 enlaces, resultado de aplicar la fórmula n × (n − 1) / 2
C) 12 enlaces, uno por nodo, igual que en una estrella

<details><summary>Respuesta</summary>

**Correcta: B) 66 enlaces, resultado de aplicar la fórmula n × (n − 1) / 2** Con n = 12 resultan 12 × 11 / 2 = 66 enlaces y 11 interfaces por equipo. El número de enlaces crece con el cuadrado del número de nodos, lo que hace inviable la malla completa más allá de un puñado de equipos.

*Referencia: §2.2.1 [TANENBAUM]*
</details>

---

### Pregunta 11

**¿Cuál es la principal desventaja estructural de la topología en anillo simple?**

A) Que la señal se atenúa porque ninguna estación la regenera
B) Que el rendimiento se degrada rápidamente al aumentar la carga de la red
C) Que el fallo de un nodo o de un enlace deja inoperativa toda la red

<details><summary>Respuesta</summary>

**Correcta: C) Que el fallo de un nodo o de un enlace deja inoperativa toda la red** Es precisamente la debilidad que FDDI resolvió con su doble anillo contrarrotante. Las otras dos opciones son falsas: en un anillo cada estación regenera la señal, y el rendimiento del paso de testigo no se degrada con la carga, a diferencia de CSMA/CD.

*Referencia: §2.2.1 [FDDI]*
</details>

---

### Pregunta 12

**En una arquitectura jerárquica de red local, ¿qué nivel realiza el encaminamiento entre VLAN y aplica las políticas?**

A) El nivel de distribución
B) El nivel de acceso
C) El nivel de núcleo, en toda arquitectura sin excepción

<details><summary>Respuesta</summary>

**Correcta: A) El nivel de distribución** Agrega los conmutadores de acceso del edificio, encamina entre VLAN y aplica políticas; está en el armario principal. En una oficina pequeña el nivel de núcleo se colapsa con el de distribución, en la llamada arquitectura de dos capas o de núcleo colapsado.

*Referencia: §2.2.2 [KUROSE]*
</details>

---

### Pregunta 13

**¿Qué significa la partícula BASE en la nomenclatura 1000BASE-T?**

A) Que la señal se transmite modulando una portadora de banda estrecha
B) Que la transmisión es en banda base, sin modular una portadora
C) Que el cableado debe ser de la categoría base, es decir, Cat 5e o superior

<details><summary>Respuesta</summary>

**Correcta: B) Que la transmisión es en banda base, sin modular una portadora** La alternativa normalizada era BROAD, de banda ancha, que solo llegó a usarse en la histórica 10BROAD36, jamás implantada. Toda Ethernet real es de banda base.

*Referencia: §2.3.1 y §3.2 [IEEE8023]*
</details>

---

### Pregunta 14

**Un enlace de 1000BASE-T deja de funcionar a 1 Gbit/s pero sigue enlazando a 100 Mbit/s. ¿Cuál es la causa más probable?**

A) La avería de uno de los pares del cable, porque 1000BASE-T usa los cuatro y 100BASE-TX solo dos
B) Un exceso de longitud del canal, que a 100 Mbit/s admite 200 metros
C) Una incompatibilidad del código de línea, que en Gigabit es Manchester

<details><summary>Respuesta</summary>

**Correcta: A) La avería de uno de los pares del cable, porque 1000BASE-T usa los cuatro y 100BASE-TX solo dos** Es un síntoma de diagnóstico clásico. Las otras dos opciones son falsas: el canal máximo son 100 metros con independencia de la velocidad, y el código de 1000BASE-T es 4D-PAM5, no Manchester.

*Referencia: §2.3.1 y §3.3 [IEEE8023] [ISO11801]*
</details>

---

### Pregunta 15

**En la banda de 2,4 GHz de 802.11, ¿cuántos canales no se solapan entre sí?**

A) Trece, que es el número de canales disponibles en Europa
B) Ocho, uno por cada 10 MHz de banda
C) Tres: los canales 1, 6 y 11

<details><summary>Respuesta</summary>

**Correcta: C) Tres: los canales 1, 6 y 11** Cada canal ocupa entre 20 y 22 MHz mientras que los canales están separados solo 5 MHz, de modo que la mayoría se solapan. Es la razón por la que en un edificio con muchos puntos de acceso la banda de 2,4 GHz se satura y la cobertura debe planificarse en 5 GHz.

*Referencia: §2.3.2 [IEEE80211] [SETSI]*
</details>

---

### Pregunta 16

**¿Qué es un ESS en la arquitectura de 802.11?**

A) El conjunto de estaciones que se comunican entre sí sin punto de acceso
B) El identificador de la radio del punto de acceso, que suele ser su dirección MAC
C) Varios BSS unidos por un sistema de distribución que se presentan como una sola red

<details><summary>Respuesta</summary>

**Correcta: C) Varios BSS unidos por un sistema de distribución que se presentan como una sola red** Es lo que permite la itinerancia al moverse por el edificio bajo un mismo SSID. La primera opción describe un IBSS o modo ad hoc, y la segunda, el BSSID.

*Referencia: §2.3.2 [IEEE80211]*
</details>

---

### Pregunta 17

**Cuál de estas afirmaciones sobre las bandas de las redes locales inalámbricas es CORRECTA:**

A) La banda de 6 GHz tiene mayor alcance que la de 2,4 GHz por su mayor anchura
B) La banda de 2,4 GHz ofrece mejor alcance y mejor penetración en muros que la de 5 GHz
C) La banda de 5 GHz está exenta de la obligación de selección dinámica de frecuencia

<details><summary>Respuesta</summary>

**Correcta: B) La banda de 2,4 GHz ofrece mejor alcance y mejor penetración en muros que la de 5 GHz** A cambio es mucho más estrecha y está mucho más interferida. La banda de 6 GHz es la de menor alcance de las tres, y en varias subbandas de 5 GHz son obligatorios el DFS y el control automático de potencia.

*Referencia: §2.3.2 [IEEE80211] [SETSI]*
</details>

---

### Pregunta 18

**La norma IEEE 802.11be, conocida comercialmente como Wi-Fi 7, se publicó en:**

A) Julio de 2025
B) Enero de 2021, junto con 802.11ax
C) Está aún en fase de borrador, con aprobación prevista para 2028

<details><summary>Respuesta</summary>

**Correcta: A) Julio de 2025** Concretamente el 22 de julio de 2025. La que está en fase de borrador con aprobación prevista para 2028 es 802.11bn (Wi-Fi 8), cuyo objetivo declarado no es la velocidad de pico sino la fiabilidad ultraalta.

*Referencia: §1.3 [IEEE802-WG] [WIFI-ALLIANCE]*
</details>

---

### Pregunta 19

**Una red inalámbrica Wi-Fi opera siempre en modo:**

A) Símplex, porque el punto de acceso solo transmite hacia las estaciones
B) Dúplex, gracias a la separación de canales de subida y de bajada
C) Semidúplex, porque una radio no puede transmitir y recibir a la vez en la misma frecuencia

<details><summary>Respuesta</summary>

**Correcta: C) Semidúplex, porque una radio no puede transmitir y recibir a la vez en la misma frecuencia** Es la razón última de que Wi-Fi conserve íntegro el problema del acceso al medio y de que use CSMA/CA. Ethernet con conmutador, en cambio, es dúplex y por eso no necesita método de acceso.

*Referencia: §3.1 [IEEE80211]*
</details>

---

### Pregunta 20

**En una transmisión asíncrona con un bit de arranque y uno de parada por carácter de 8 bits, ¿cuál es la sobrecarga?**

A) Del 10 %, un bit de cada diez
B) Del 20 %, porque de cada 10 bits transmitidos solo 8 son útiles
C) Nula, porque los bits de arranque y parada se transmiten fuera de banda

<details><summary>Respuesta</summary>

**Correcta: B) Del 20 %, porque de cada 10 bits transmitidos solo 8 son útiles** Es el motivo por el que la transmisión asíncrona quedó limitada al puerto serie clásico. Todas las redes locales usan transmisión síncrona, por bloques o tramas, con sincronización extraída de la propia señal.

*Referencia: §3.1 [STALLINGS]*
</details>

---

### Pregunta 21

**Señale la afirmación CORRECTA sobre la transmisión en banda ancha:**

A) La señal modula una portadora y cada canal es unidireccional, por lo que hace falta un canal para cada sentido
B) La señal digital se transmite sin modular y ocupa todo el ancho de banda del medio
C) Es el modo de transmisión de toda la familia Ethernet, de ahí la partícula BASE

<details><summary>Respuesta</summary>

**Correcta: A) La señal modula una portadora y cada canal es unidireccional, por lo que hace falta un canal para cada sentido** La amplificación es direccional, de ahí la necesidad de dos cables o de una división del espectro en banda de subida y de bajada, con una cabecera que traslade la frecuencia. Las otras dos opciones describen la banda base.

*Referencia: §3.2 [STALLINGS]*
</details>

---

### Pregunta 22

**¿Qué código de línea utiliza 10BASE-T?**

A) MLT-3 combinado con la codificación en bloque 4B/5B
B) 4D-PAM5 sobre los cuatro pares
C) Manchester, con transición obligatoria en la mitad de cada intervalo de bit

<details><summary>Respuesta</summary>

**Correcta: C) Manchester, con transición obligatoria en la mitad de cada intervalo de bit** Garantiza siempre la autosincronización y elimina la componente continua, pero a costa de hasta dos transiciones por bit, es decir, el doble de ancho de banda. MLT-3 con 4B/5B es de 100BASE-TX y 4D-PAM5 es de 1000BASE-T.

*Referencia: §3.3 [STALLINGS] [IEEE8023]*
</details>

---

### Pregunta 23

**¿Qué relación liga la velocidad de transmisión en bits por segundo con la velocidad de modulación en baudios?**

A) Son siempre iguales: un baudio equivale a un bit por segundo
B) Vt = Vm × log2(n), donde n es el número de niveles del símbolo
C) Vt = Vm / log2(n), porque cada nivel adicional reduce la capacidad del canal

<details><summary>Respuesta</summary>

**Correcta: B) Vt = Vm × log2(n), donde n es el número de niveles del símbolo** Solo coinciden cuando el símbolo tiene dos niveles. Es la fórmula que explica que 1000BASE-T alcance 1 Gbit/s sobre un cable certificado hasta 100 MHz: usa cinco niveles (PAM-5) por los cuatro pares.

*Referencia: §3.3 [STALLINGS]*
</details>

---

### Pregunta 24

**Una modulación 256-QAM transporta por símbolo:**

A) 8 bits, porque log2(256) = 8
B) 256 bits, uno por cada punto de la constelación
C) 4 bits, dos de amplitud y dos de fase

<details><summary>Respuesta</summary>

**Correcta: A) 8 bits, porque log2(256) = 8** La regla es general: una constelación de n puntos transporta log2(n) bits por símbolo. Por eso 1024-QAM de Wi-Fi 6 lleva 10 bits y 4096-QAM de Wi-Fi 7 lleva 12, y por eso la velocidad cae con la distancia: al empeorar la relación señal/ruido se negocia a la baja la constelación.

*Referencia: §3.3 [STALLINGS] [IEEE80211]*
</details>

---

### Pregunta 25

**La multiplexación por división de tiempo estadística se diferencia de la síncrona en que:**

A) Asigna a cada canal una subbanda de frecuencia en lugar de una ranura temporal
B) Asigna las ranuras solo a los canales que tienen datos que enviar, en lugar de reservarlas fijamente
C) Emplea códigos ortogonales para que todos los canales transmitan a la vez en toda la banda

<details><summary>Respuesta</summary>

**Correcta: B) Asigna las ranuras solo a los canales que tienen datos que enviar, en lugar de reservarlas fijamente** Aprovecha mucho mejor la capacidad y es el principio de la conmutación de paquetes, a costa de tener que identificar en cada ranura a qué canal pertenece. La opción A describe FDM y la C, CDM.

*Referencia: §3.4 [STALLINGS]*
</details>

---

### Pregunta 26

**¿Qué técnica permite multiplicar la capacidad de una fibra óptica ya tendida sin sustituirla?**

A) La multiplexación por división de tiempo síncrona
B) La codificación 64B/66B, que reduce la sobrecarga al 3,125 %
C) La multiplexación por división de longitud de onda (WDM)

<details><summary>Respuesta</summary>

**Correcta: C) La multiplexación por división de longitud de onda (WDM)** Varias señales de distinta longitud de onda viajan simultáneamente por la misma fibra y se separan con filtros ópticos. DWDM, en su versión densa, llega a decenas o centenares de canales.

*Referencia: §3.4 [STALLINGS]*
</details>

---

### Pregunta 27

**La gran novedad de Wi-Fi 6 (802.11ax) frente a Wi-Fi 5 en un entorno denso es:**

A) OFDMA, que asigna subconjuntos de subportadoras a estaciones distintas para que transmitan simultáneamente
B) La ampliación de los canales a 320 MHz, que multiplica la velocidad de pico
C) La sustitución de CSMA/CA por CSMA/CD, que elimina las colisiones

<details><summary>Respuesta</summary>

**Correcta: A) OFDMA, que asigna subconjuntos de subportadoras a estaciones distintas para que transmitan simultáneamente** No transmite mucho más rápido a un solo cliente, sino que atiende a muchos clientes pequeños a la vez en lugar de por turnos. Los canales de 320 MHz son de Wi-Fi 7, y CSMA/CD no puede usarse en radio.

*Referencia: §3.4 y §4.4 [IEEE80211]*
</details>

---

### Pregunta 28

**¿Qué significa la nomenclatura S/FTP en un cable de par trenzado?**

A) Que carece de todo apantallamiento, tanto global como por par
B) Que dispone de una lámina de apantallamiento global pero no por par
C) Que dispone de una trenza de apantallamiento global y de una lámina por cada par

<details><summary>Respuesta</summary>

**Correcta: C) Que dispone de una trenza de apantallamiento global y de una lámina por cada par** La primera letra designa la pantalla global y las que siguen a la barra, el material y el elemento apantallado. U/UTP es no apantallado y F/UTP lleva lámina global sin pantalla por par. El apantallamiento exige puesta a tierra correcta en ambos extremos: mal instalado, empeora el comportamiento.

*Referencia: §3.5.1 [ISO11801]*
</details>

---

### Pregunta 29

**¿Qué categoría de cableado se exige hoy en una obra nueva para garantizar 10 Gbit/s a 100 metros?**

A) Cat 6, que corresponde a la clase E y a 250 MHz
B) Cat 6A, que corresponde a la clase EA y a 500 MHz
C) Cat 5e, que corresponde a la clase D y a 100 MHz

<details><summary>Respuesta</summary>

**Correcta: B) Cat 6A, que corresponde a la clase EA y a 500 MHz** Cat 6 también admite 10 Gbit/s, pero solo hasta 55 metros. Conviene recordar además la distinción: la categoría se predica de los componentes y la clase, del enlace instalado y medido.

*Referencia: §3.5.1 [ISO11801] [EN50173]*
</details>

---

### Pregunta 30

**Para el troncal vertical entre los armarios de planta y el armario principal de un edificio de oficinas, el medio habitual es:**

A) Fibra óptica multimodo, con fuente LED o VCSEL y alcance de cientos de metros
B) Cable coaxial RG-58, por su gran inmunidad al ruido
C) Fibra óptica monomodo, obligatoria por norma dentro de todo edificio

<details><summary>Respuesta</summary>

**Correcta: A) Fibra óptica multimodo, con fuente LED o VCSEL y alcance de cientos de metros** La monomodo, con núcleo de 8 a 10 micras y fuente láser, se reserva para los enlaces entre edificios y con el operador, donde su alcance de decenas de kilómetros compensa su mayor coste. El coaxial está retirado de las redes locales.

*Referencia: §3.5.1 [ISO11801]*
</details>

---

### Pregunta 31

**¿Cuál es el rendimiento máximo teórico del protocolo ALOHA ranurado?**

A) El 18,4 % del canal, igual que el de ALOHA puro
B) El 100 %, porque las ranuras eliminan por completo las colisiones
C) El 36,8 % del canal, el doble que el de ALOHA puro

<details><summary>Respuesta</summary>

**Correcta: C) El 36,8 % del canal, el doble que el de ALOHA puro** Obligar a empezar a transmitir solo al comienzo de una ranura reduce a la mitad el periodo de vulnerabilidad. La lección que de ahí se extrajo —escuchar el medio antes de transmitir— dio origen a CSMA.

*Referencia: §4.1 [ABRAMSON] [TANENBAUM]*
</details>

---

### Pregunta 32

**¿Qué variante de CSMA emplea Ethernet?**

A) No persistente: si el medio está ocupado, espera un tiempo aleatorio antes de volver a escuchar
B) 1-persistente: sigue escuchando y transmite con probabilidad 1 en cuanto el medio queda libre
C) p-persistente: transmite con probabilidad p y espera a la siguiente ranura con probabilidad 1 − p

<details><summary>Respuesta</summary>

**Correcta: B) 1-persistente: sigue escuchando y transmite con probabilidad 1 en cuanto el medio queda libre** Aprovecha bien el canal, pero garantiza la colisión si dos estaciones estaban esperando a la vez, que es exactamente el escenario que CSMA/CD tiene que resolver.

*Referencia: §4.2 [IEEE8023] [TANENBAUM]*
</details>

---

### Pregunta 33

**¿Cuál es la longitud de la señal de atasco (jam) que emite una estación Ethernet al detectar una colisión?**

A) 32 bits
B) 96 bits, igual que el espacio entre tramas
C) 512 bits, igual que la ranura de colisión

<details><summary>Respuesta</summary>

**Correcta: A) 32 bits** Su función es asegurar que todas las demás estaciones detecten también la colisión y ninguna se quede con una trama a medias que crea válida. El espacio entre tramas es de 96 tiempos de bit y la ranura de colisión, de 512.

*Referencia: §4.2.1 [IEEE8023]*
</details>

---

### Pregunta 34

**En el retroceso exponencial binario de Ethernet, tras la colisión número n la estación espera un número aleatorio de ranuras en el intervalo:**

A) De 0 a n − 1, creciendo linealmente con el número de colisiones
B) De 0 a 2^k − 1, con k igual al menor valor entre n y 10
C) De 1 a 16, que es también el número máximo de intentos

<details><summary>Respuesta</summary>

**Correcta: B) De 0 a 2^k − 1, con k igual al menor valor entre n y 10** El truncamiento en 10 significa que el intervalo deja de crecer a partir de la décima colisión, con un máximo de 1.024 ranuras posibles. El límite de 16 intentos es cosa distinta: al alcanzarlo, la trama se descarta y se notifica el error.

*Referencia: §4.2.1 [IEEE8023]*
</details>

---

### Pregunta 35

**¿Por qué la trama mínima de Ethernet es de 64 octetos?**

A) Porque es el tamaño necesario para alojar las dos direcciones MAC y el campo de tipo
B) Porque es el tamaño mínimo que admite la codificación 4B/5B sin perder sincronización
C) Porque equivale a la ranura de colisión de 512 tiempos de bit, y la estación debe seguir transmitiendo hasta que la colisión le llegue de vuelta

<details><summary>Respuesta</summary>

**Correcta: C) Porque equivale a la ranura de colisión de 512 tiempos de bit, y la estación debe seguir transmitiendo hasta que la colisión le llegue de vuelta** Si terminase antes, se iría creyendo que todo ha ido bien. Ese tiempo es el de ida y vuelta del segmento en el peor caso, con las dos estaciones en extremos opuestos.

*Referencia: §4.2.1 [IEEE8023] [SPURGEON]*
</details>

---

### Pregunta 36

**Al pasar de Ethernet a 10 Mbit/s a Fast Ethernet a 100 Mbit/s manteniendo la ranura de colisión en 512 tiempos de bit, ¿qué ocurre con el diámetro máximo del dominio de colisión?**

A) Se reduce aproximadamente a la décima parte, porque cada bit dura diez veces menos
B) Se multiplica por diez, porque la señal se propaga diez veces más deprisa
C) No varía, porque la distancia depende solo de la atenuación del medio

<details><summary>Respuesta</summary>

**Correcta: A) Se reduce aproximadamente a la décima parte, porque cada bit dura diez veces menos** De unos 2.500 metros se pasa a unos 250, de ahí que Fast Ethernet solo admita uno o dos repetidores. En Gigabit habría bajado a 25 metros, y por eso la norma amplió la ranura a 4.096 tiempos de bit e introdujo la extensión de portadora.

*Referencia: §4.2.1 [IEEE8023] [SPURGEON]*
</details>

---

### Pregunta 37

**¿En qué situación sigue estando activo CSMA/CD en una red local moderna?**

A) En todo enlace de 10 Gbit/s, donde el semidúplex es el modo predeterminado
B) En ninguna: con enlace dúplex punto a punto se desactiva, y en 10 Gbit/s el semidúplex ni siquiera está definido
C) En los enlaces troncales entre conmutadores, que siguen siendo un medio compartido

<details><summary>Respuesta</summary>

**Correcta: B) En ninguna: con enlace dúplex punto a punto se desactiva, y en 10 Gbit/s el semidúplex ni siquiera está definido** Ver contadores de colisión distintos de cero en un puerto es síntoma de una negociación automática fallida que ha dejado un extremo en dúplex y el otro en semidúplex, la avería clásica conocida como duplex mismatch.

*Referencia: §4.2.1 [IEEE8023]*
</details>

---

### Pregunta 38

**¿Por qué 802.11 no puede emplear detección de colisión?**

A) Porque el espectro radioeléctrico es de dominio público y no admite escucha
B) Porque las tramas de 802.11 son demasiado cortas para que la colisión llegue a tiempo
C) Porque el emisor no puede oír mientras transmite: su propia antena ensordece su receptor

<details><summary>Respuesta</summary>

**Correcta: C) Porque el emisor no puede oír mientras transmite: su propia antena ensordece su receptor** A ello se añade que en radio cada estación oye un subconjunto distinto de las demás, de modo que una colisión detectada en el emisor no diría nada sobre lo ocurrido en el receptor, que es donde importa.

*Referencia: §4.2.2 [IEEE80211] [GAST]*
</details>

---

### Pregunta 39

**En CSMA/CA, tras encontrar el medio libre durante un DIFS completo, la estación:**

A) Espera además un retroceso aleatorio de entre 0 y CW − 1 ranuras antes de transmitir
B) Transmite inmediatamente, igual que en CSMA/CD 1-persistente
C) Envía obligatoriamente un RTS y espera el CTS del punto de acceso

<details><summary>Respuesta</summary>

**Correcta: A) Espera además un retroceso aleatorio de entre 0 y CW − 1 ranuras antes de transmitir** Es el punto que diferencia CSMA/CA de CSMA/CD y donde fallan las respuestas: el retroceso es previo y obligatorio, no solo posterior a una colisión. El contador se decrementa mientras el medio sigue libre y se congela si alguien transmite. RTS/CTS es opcional y está desactivado por defecto.

*Referencia: §4.2.2 [IEEE80211]*
</details>

---

### Pregunta 40

**En 802.11 sobre la banda de 5 GHz, con SIFS de 16 µs y ranura de 9 µs, ¿cuánto vale el DIFS?**

A) 25 µs, resultado de sumar un SIFS y una ranura
B) 16 µs, el mismo valor que el SIFS
C) 34 µs, resultado de aplicar DIFS = SIFS + 2 × ranura

<details><summary>Respuesta</summary>

**Correcta: C) 34 µs, resultado de aplicar DIFS = SIFS + 2 × ranura** La suma de un SIFS más una ranura, 25 µs, es el PIFS. En 802.11b a 2,4 GHz, con SIFS de 10 µs y ranura de 20 µs, el DIFS vale 50 µs. La existencia de varios espacios crea prioridades sin negociación: quien puede empezar antes, gana.

*Referencia: §4.2.2 [IEEE80211] [GAST]*
</details>

---

### Pregunta 41

**En el mecanismo RTS/CTS, ¿qué papel cumple el CTS frente al problema del nodo oculto?**

A) Cifra la transmisión para que el nodo oculto no pueda interceptarla
B) Lo oyen todas las estaciones al alcance del punto de acceso, incluido el nodo oculto, que actualiza su NAV y se abstiene
C) Fuerza al nodo oculto a asociarse a otro punto de acceso con mejor cobertura

<details><summary>Respuesta</summary>

**Correcta: B) Lo oyen todas las estaciones al alcance del punto de acceso, incluido el nodo oculto, que actualiza su NAV y se abstiene** Es detección virtual de portadora: la estación se abstiene no porque oiga la transmisión, sino porque se le ha dicho que hay una. Tanto el RTS como el CTS llevan la duración prevista de la ocupación.

*Referencia: §4.2.2 [IEEE80211]*
</details>

---

### Pregunta 42

**¿Cuál de las siguientes NO es una característica de los métodos deterministas por paso de testigo?**

A) El retardo máximo de acceso está acotado y es previsible
B) Nunca se producen colisiones, porque solo transmite quien posee el testigo
C) Son más eficientes que CSMA cuando la carga de la red es baja

<details><summary>Respuesta</summary>

**Correcta: C) Son más eficientes que CSMA cuando la carga de la red es baja** Es justo al revés: con carga baja el paso de testigo es menos eficiente, porque una estación con datos puede tener que esperar a que le llegue el testigo aunque nadie más transmita. Su ventaja aparece con carga alta, donde el rendimiento no se degrada.

*Referencia: §4.3 [TANENBAUM]*
</details>

---

### Pregunta 43

**FDDI resuelve la fragilidad estructural del anillo mediante:**

A) Un monitor activo que regenera el testigo cuando se pierde
B) La duplicación de las estaciones en modo de simple conexión
C) Un doble anillo contrarrotante que se pliega en uno solo ante un corte

<details><summary>Respuesta</summary>

**Correcta: C) Un doble anillo contrarrotante que se pliega en uno solo ante un corte** El anillo primario transporta los datos y el secundario circula en sentido contrario como respaldo; ante un corte, las dos estaciones adyacentes pliegan ambos anillos y reconstruyen un anillo único. El monitor activo es de Token Ring, no de FDDI.

*Referencia: §4.3 [FDDI]*
</details>

---

### Pregunta 44

**¿Qué norma corresponde a Token Bus y cuál era su ámbito característico?**

A) IEEE 802.5, en el entorno de la ofimática impulsada por IBM
B) IEEE 802.4, en el entorno industrial, como base del perfil MAP
C) ISO 9314, en las redes troncales de campus sobre fibra óptica

<details><summary>Respuesta</summary>

**Correcta: B) IEEE 802.4, en el entorno industrial, como base del perfil MAP** Combinaba el bus físico con un anillo lógico: las estaciones se ordenaban por dirección y cada una sabía a quién pasar el testigo. IEEE 802.5 es Token Ring e ISO 9314 es FDDI.

*Referencia: §4.3 [IEEE8025]*
</details>

---

### Pregunta 45

**¿Cuál de estos mecanismos pertenece a la familia de acceso por reserva o sondeo?**

A) La trama de activación de Wi-Fi 6, que asigna unidades de recurso a estaciones concretas
B) El retroceso exponencial binario de Ethernet
C) La liberación temprana del testigo de Token Ring a 16 Mbit/s

<details><summary>Respuesta</summary>

**Correcta: A) La trama de activación de Wi-Fi 6, que asigna unidades de recurso a estaciones concretas** Es conceptualmente un método de reserva: el punto de acceso asigna y las estaciones transmiten simultáneamente y sin contienda en la porción de canal que se les ha dado. Es la reintroducción del control centralizado en una tecnología nacida distribuida.

*Referencia: §4.4 [IEEE80211]*
</details>

---

### Pregunta 46

**Un concentrador de 24 puertos a 10 Mbit/s ofrece:**

A) 240 Mbit/s de capacidad total, a razón de 10 Mbit/s dedicados por puerto
B) 10 Mbit/s compartidos entre los 24 puertos, en un único dominio de colisión
C) 10 Mbit/s por puerto en dúplex, sin colisiones entre puertos distintos

<details><summary>Respuesta</summary>

**Correcta: B) 10 Mbit/s compartidos entre los 24 puertos, en un único dominio de colisión** El concentrador es un repetidor multipuerto: todo lo que entra por un puerto sale regenerado por los demás, lo que obliga al semidúplex y a CSMA/CD, y hace que ninguna estación tenga privacidad frente a las otras.

*Referencia: §5.1 [IEEE8023]*
</details>

---

### Pregunta 47

**La regla 5-4-3 de Ethernet a 10 Mbit/s establece que entre dos estaciones cualesquiera puede haber como máximo:**

A) 5 estaciones por segmento, 4 segmentos y 3 concentradores
B) 5 metros de latiguillo, 4 pares y 3 repetidores en cascada
C) 5 segmentos, unidos por 4 repetidores, de los que solo 3 pueden tener estaciones

<details><summary>Respuesta</summary>

**Correcta: C) 5 segmentos, unidos por 4 repetidores, de los que solo 3 pueden tener estaciones** Los otros dos segmentos son enlaces entre repetidores. Su fundamento no es arbitrario: es el presupuesto de retardo que garantiza que la ranura de colisión de 512 tiempos de bit siga bastando.

*Referencia: §5.1 [IEEE8023]*
</details>

---

### Pregunta 48

**Cuando un conmutador recibe una trama cuya dirección MAC de destino no figura en su tabla de reenvío:**

A) La inunda por todos los puertos menos por aquel por el que llegó
B) La descarta y envía un mensaje de error a la estación origen
C) La reenvía únicamente al puerto por el que llegó, para que el origen la reintente

<details><summary>Respuesta</summary>

**Correcta: A) La inunda por todos los puertos menos por aquel por el que llegó** Es el comportamiento del puente transparente. El aprendizaje se hace mirando la dirección de origen de cada trama recibida, y las entradas tienen un temporizador de envejecimiento, típicamente de 300 segundos.

*Referencia: §5.2.1 [IEEE8021D] [KUROSE]*
</details>

---

### Pregunta 49

**¿Por qué una red local conmutada con enlaces redundantes necesita el protocolo de árbol de expansión?**

A) Porque los conmutadores no saben calcular el camino más corto entre dos estaciones
B) Porque la trama Ethernet no tiene campo de tiempo de vida y una difusión circularía indefinidamente
C) Porque los enlaces redundantes provocan colisiones que CSMA/CD no puede resolver

<details><summary>Respuesta</summary>

**Correcta: B) Porque la trama Ethernet no tiene campo de tiempo de vida y una difusión circularía indefinidamente** Se multiplicaría en cada bucle hasta saturar la red en segundos: es la tormenta de difusión. El árbol de expansión bloquea lógicamente los enlaces redundantes y los reactiva si el camino activo cae. El encaminador no lo necesita porque el datagrama IP sí tiene tiempo de vida.

*Referencia: §5.2.1 [IEEE8021D]*
</details>

---

### Pregunta 50

**El modo de conmutación libre de fragmentos empieza a reenviar la trama tras recibir sus primeros 64 octetos porque:**

A) Es el tamaño mínimo necesario para leer las dos direcciones MAC y el campo de tipo
B) Es el tamaño a partir del cual la norma permite calcular el CRC de forma incremental
C) Los fragmentos de colisión son siempre menores de 64 octetos, de modo que filtra la mayoría de las tramas defectuosas

<details><summary>Respuesta</summary>

**Correcta: C) Los fragmentos de colisión son siempre menores de 64 octetos, de modo que filtra la mayoría de las tramas defectuosas** Es un compromiso entre el modo directo, que empieza tras los 6 octetos de la dirección de destino y no comprueba errores, y el de almacenamiento y reenvío, que espera la trama completa y sí verifica el CRC.

*Referencia: §5.2.1 [KUROSE]*
</details>

---

### Pregunta 51

**¿Cuántas VLAN son utilizables con el identificador de 12 bits de la etiqueta 802.1Q?**

A) 4.094, porque de los 4.096 valores posibles se reservan el 0 y el 4095
B) 4.096, todos los valores que caben en 12 bits
C) 1.024, porque los dos bits más significativos identifican la prioridad

<details><summary>Respuesta</summary>

**Correcta: A) 4.094, porque de los 4.096 valores posibles se reservan el 0 y el 4095** La prioridad no se toma del identificador sino de los tres bits del campo PCP, lo que se conoce como 802.1p, que nunca fue una norma independiente sino parte de 802.1Q.

*Referencia: §5.2.2 [IEEE8021Q]*
</details>

---

### Pregunta 52

**Al etiquetar una trama con 802.1Q, el tamaño máximo pasa de 1518 a:**

A) 1518 octetos, porque la etiqueta sustituye al campo de tipo y no añade tamaño
B) 1522 octetos, porque la etiqueta ocupa 4 octetos adicionales
C) 1526 octetos, porque la etiqueta ocupa 8 octetos adicionales

<details><summary>Respuesta</summary>

**Correcta: B) 1522 octetos, porque la etiqueta ocupa 4 octetos adicionales** Se insertan entre la dirección de origen y el campo de tipo o longitud, y se reparten en TPID de 16 bits con valor `0x8100`, PCP de 3 bits, DEI de 1 bit y VID de 12 bits. Un equipo antiguo que no entienda 802.1Q descarta la trama por exceso de tamaño.

*Referencia: §5.2.2 [IEEE8021Q]*
</details>

---

### Pregunta 53

**Una red tiene un encaminador con dos interfaces; del primero cuelga un conmutador de 8 puertos con dos VLAN y 7 puestos, y del segundo un concentrador con 5 puestos. ¿Cuántos dominios de difusión hay?**

A) 3: uno por cada VLAN del conmutador y otro por el segmento del concentrador
B) 2, uno por cada interfaz físico del encaminador
C) 9, uno por cada puerto activo de conmutador más el segmento del concentrador

<details><summary>Respuesta</summary>

**Correcta: A) 3: uno por cada VLAN del conmutador y otro por el segmento del concentrador** El número de dominios de difusión es el de VLAN más el de segmentos separados por el encaminador, contando las subinterfaces del troncal. Los 9 de la opción C son los dominios de colisión, cosa distinta.

*Referencia: §5.2.2 y §5 [KUROSE]*
</details>

---

### Pregunta 54

**¿Cuál de estos elementos NO es un dispositivo de interconexión?**

A) El panel de parcheo, que es un elemento pasivo del cableado estructurado
B) El punto de acceso inalámbrico, que hace de puente entre 802.11 y 802.3
C) El conversor de medio, que adapta entre par trenzado y fibra en la capa 1

<details><summary>Respuesta</summary>

**Correcta: A) El panel de parcheo, que es un elemento pasivo del cableado estructurado** Solo termina y ordena los cables. Es una trampa habitual en los test porque está en el armario junto al conmutador. Otra ambigüedad que induce a error: la «pasarela» que se configura en un equipo es la puerta de enlace predeterminada, es decir, un encaminador, no una pasarela en sentido estricto.

*Referencia: §5.4 [ISO11801] [X200]*
</details>

---

### Pregunta 55

**Según ISO/IEC 11801, la longitud máxima del canal de par trenzado es de 100 metros, repartidos en:**

A) 95 metros de cable horizontal fijo y 5 metros de latiguillos
B) 50 metros por cada mitad del enlace, medidos desde el panel de parcheo
C) 90 metros de cable horizontal fijo y 10 metros de latiguillos sumando ambos extremos

<details><summary>Respuesta</summary>

**Correcta: C) 90 metros de cable horizontal fijo y 10 metros de latiguillos sumando ambos extremos** Rige con independencia de la velocidad, desde 10BASE-T hasta 10GBASE-T. Si la toma está a 95 metros del armario, el enlace no cumple la norma aunque el equipo funcione: la solución es un armario intermedio, no un cable más largo.

*Referencia: §6.1 [ISO11801] [EN50173]*
</details>

---

### Pregunta 56

**¿Qué regula el artículo 55 de la Ley 11/2022, General de Telecomunicaciones?**

A) El régimen de títulos habilitantes para el uso del dominio público radioeléctrico
B) Las infraestructuras comunes y las redes de comunicaciones electrónicas en los edificios
C) Las categorías y clases del cableado estructurado exigibles a un edificio público

<details><summary>Respuesta</summary>

**Correcta: B) Las infraestructuras comunes y las redes de comunicaciones electrónicas en los edificios** Remite a real decreto el punto de interconexión de la red interior con las redes públicas y las condiciones de la red interior, y ordena que la normativa de edificación prevea capacidad de obra civil para varios operadores. El régimen del espectro es el artículo 88, y el cableado no lo regula ninguna ley, sino ISO/IEC 11801 y EN 50173.

*Referencia: §6.1 [LGT]*
</details>

---

### Pregunta 57

**El Ayuntamiento despliega puntos de acceso Wi-Fi en una biblioteca municipal. Respecto del dominio público radioeléctrico:**

A) Opera en régimen de uso común, que no precisa de título habilitante pero carece de protección frente a interferencias
B) Necesita una concesión administrativa de uso privativo de la banda de 2,4 GHz
C) Necesita una autorización general de uso especial, salvo que la red sea de acceso restringido

<details><summary>Respuesta</summary>

**Correcta: A) Opera en régimen de uso común, que no precisa de título habilitante pero carece de protección frente a interferencias** Así lo establece el artículo 88 de la Ley 11/2022, que clasifica el uso en común, especial y privativo. El corolario práctico: si un vecino interfiere usando legalmente la misma banda, no hay a quién reclamar; la solución es técnica, no jurídica.

*Referencia: §3.5.2 y §6.1 [LGT]*
</details>

---

### Pregunta 58

**En el control de acceso IEEE 802.1X, ¿qué papel desempeña el conmutador?**

A) El de suplicante, porque solicita las credenciales al servidor de autenticación
B) El de autenticador, que mantiene el puerto en estado no controlado hasta que la autenticación tenga éxito
C) El de servidor de autenticación, verificando las credenciales contra el directorio corporativo

<details><summary>Respuesta</summary>

**Correcta: B) El de autenticador, que mantiene el puerto en estado no controlado hasta que la autenticación tenga éxito** Mientras tanto solo deja pasar tramas EAPOL. El suplicante es el programa cliente del equipo y el servidor de autenticación suele ser un RADIUS, que además puede devolver la VLAN correspondiente al usuario.

*Referencia: §6.2 [IEEE8021X]*
</details>

---

### Pregunta 59

**Respecto de la medida `mp.com.4` del anexo II del Esquema Nacional de Seguridad, es CIERTO que:**

A) Se denomina «segregación de redes» y aplica en las tres categorías
B) Su refuerzo R1 exige implantar los segmentos mediante redes privadas virtuales
C) Se denomina «separación de flujos de información en la red» y NO aplica en categoría BÁSICA

<details><summary>Respuesta</summary>

**Correcta: C) Se denomina «separación de flujos de información en la red» y NO aplica en categoría BÁSICA** Es la única del grupo `mp.com` que no se exige siempre: en MEDIA se exige con uno de los refuerzos R1, R2 o R3, y en ALTA con R2 o R3 más R4. «Segregación de redes» era su nombre en el derogado RD 3/2010, y el refuerzo que nombra las VLAN es el R1; las VPN son el R2.

*Referencia: §6.3 [ENS]*
</details>

---

### Pregunta 60

**El requisito `mp.com.4.2` del Esquema Nacional de Seguridad establece literalmente que:**

A) Si se emplean comunicaciones inalámbricas, será en un segmento separado
B) Las comunicaciones inalámbricas quedan prohibidas en sistemas de categoría MEDIA y ALTA
C) Las comunicaciones inalámbricas deberán cifrarse mediante algoritmos autorizados por el CCN

<details><summary>Respuesta</summary>

**Correcta: A) Si se emplean comunicaciones inalámbricas, será en un segmento separado** No es una recomendación de buena práctica sino un requisito normativo, y su fundamento es que el medio inalámbrico no se puede acotar físicamente: la señal se escapa del edificio. El uso de algoritmos autorizados por el CCN es el refuerzo R1 de `mp.com.2`.

*Referencia: §6.3 y §3.5 [ENS]*
</details>
