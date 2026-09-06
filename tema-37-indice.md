# Tema 37 — Índice

> **Título oficial**: Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión.
>
> **Bloque**: Parte II — Técnico (Temas 11-40)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

---

## Estructura del tema

1. **Concepto y caracterización de las redes locales**
   1.1. Definición, evolución y características principales
   1.2. Modelo de referencia OSI y arquitectura TCP/IP en el ámbito local
   1.3. Normalización y familias de estándares IEEE 802

2. **Tipología de redes locales**
   2.1. Clasificación según cobertura y alcance geográfico
   2.2. Topologías físicas y lógicas de red
   2.2.1. Topologías básicas: estrella, bus, anillo y malla
   2.2.2. Topologías híbridas y estructuras jerárquicas
   2.3. Clasificación por medio físico y tecnología
   2.3.1. Redes locales cableadas
   2.3.2. Redes locales inalámbricas

3. **Técnicas de transmisión**
   3.1. Modos y sentidos de transmisión de datos
   3.2. Transmisión en banda base y banda ancha
   3.3. Técnicas de modulación y codificación de señal
   3.4. Técnicas de multiplexación de canales
   3.5. Medios de transmisión guiados y no guiados
   3.5.1. Cableado de par trenzado, fibra óptica y coaxial
   3.5.2. Espectro radioeléctrico y transmisión inalámbrica

4. **Métodos de acceso al medio**
   4.1. Clasificación y principios de los métodos de acceso
   4.2. Métodos aleatorios o por contienda
   4.2.1. Método CSMA/CD en redes Ethernet
   4.2.2. Método CSMA/CA en redes Wi-Fi
   4.3. Métodos deterministas o por paso de testigo
   4.4. Métodos basados en reserva y sondeo

5. **Dispositivos de interconexión**
   5.1. Interconexión en el nivel físico: repetidores y concentradores
   5.2. Interconexión en el nivel de enlace de datos
   5.2.1. Puentes y conmutadores
   5.2.2. Funcionamiento de conmutadores y redes virtuales (VLAN)
   5.3. Interconexión en el nivel de red: enrutadores y encaminamiento
   5.4. Dispositivos de frontera, pasarelas y puntos de acceso

6. **Normativa y aplicación en la Administración pública (material complementario)**
   6.1. Estándares de cableado estructurado e infraestructura
   6.2. Seguridad y control de acceso en redes administrativas
   6.3. Adecuación al Esquema Nacional de Seguridad

---

## Conceptos clave para memorizar

| Concepto | Dato clave |
|---|---|
| **Los cinco rasgos de una LAN** | **Ámbito geográfico reducido** (edificio o recinto) · **medio propio y privado**, no de un operador · **alta velocidad** y **retardo bajo** · **tasa de error muy baja** · **medio inicialmente compartido**, de donde nace el problema del acceso |
| **Las dos subcapas del nivel 2** | El **IEEE 802** parte la capa de enlace de OSI en **LLC** (control del enlace lógico, **802.2**, común a toda la familia) y **MAC** (control de acceso al medio, **específica de cada tecnología**). Solo la subcapa MAC toca el medio |
| **Las normas que hay que saber** | **802.1** puentes y arquitectura (**802.1Q** VLAN, **802.1D** STP, **802.1X** control de acceso por puerto) · **802.2** LLC · **802.3** Ethernet · **802.4** *token bus* · **802.5** *token ring* · **802.11** WLAN · **802.15** WPAN (Bluetooth, Zigbee) · **802.16** WiMAX · **802.3af/at/bt** PoE |
| **Topología física ≠ topología lógica** | Un **concentrador** cablea en **estrella física** y se comporta como un **bus lógico**. Un **Token Ring** con MAU cablea en **estrella física** y es un **anillo lógico**. Un **conmutador** es **estrella física** y **punto a punto lógico**: ya no hay bus |
| **Trama Ethernet** | Preámbulo **7 octetos** + SFD **1** + destino **6** + origen **6** + tipo/longitud **2** + datos **46-1500** + FCS **4**. **Trama mínima 64 octetos**, **máxima 1518** (**1522** con etiqueta 802.1Q). **MTU = 1500** |
| **Regla de los 64 octetos** | La trama mínima existe para que **la colisión se detecte antes de terminar de transmitir**: **512 tiempos de bit** = 64 octetos = **ranura de colisión** (*slot time*) de 10 y 100 Mbit/s. En Gigabit se amplía a **4.096 tiempos de bit** (512 octetos) con **extensión de portadora** |
| **CSMA/CD** | Escuchar → transmitir → si colisión, emitir **señal de atasco (*jam*) de 32 bits** → esperar un tiempo aleatorio por **retroceso exponencial binario** (`0..2^k−1` ranuras, con **k = mín(n,10)**) → reintentar hasta **16 veces** y abandonar. **Solo tiene sentido en semidúplex**: con conmutador y dúplex, **se desactiva** |
| **CSMA/CA** | **No se pueden detectar colisiones** al transmitir (el emisor no oye el medio): se **evitan**. Escuchar **DIFS** libre → **retroceso aleatorio** en `[0, CW−1]` ranuras → transmitir → esperar **ACK** tras un **SIFS**. **CWmín 15**, **CWmáx 1023** (OFDM). Opcional **RTS/CTS** con **NAV** contra el **nodo oculto** |
| **Tiempos de 802.11 en 5 GHz** | **SIFS 16 µs** · **ranura 9 µs** · **DIFS = SIFS + 2 × ranura = 34 µs**. En 802.11b (2,4 GHz): SIFS 10 µs, ranura 20 µs, **DIFS 50 µs** |
| **Paso de testigo** | **Determinista**: el retardo máximo está **acotado**, a diferencia de CSMA. **802.5 Token Ring** (4 y 16 Mbit/s, IBM, MAU, monitor activo) · **802.4 Token Bus** (anillo lógico sobre bus físico, entorno industrial, MAP) · **FDDI** (100 Mbit/s, **doble anillo** contrarrotante, 200 km, temporizador **TRT** y **THT**) |
| **Dominios** | Un **concentrador** propaga colisión y difusión: **un dominio de colisión y uno de difusión**. Un **conmutador** crea **un dominio de colisión por puerto** y **un dominio de difusión por VLAN**. Un **encaminador** separa **dominios de difusión** |
| **Etiqueta 802.1Q** | **4 octetos** insertados tras la dirección de origen: **TPID `0x8100`** (2 octetos) + **PCP 3 bits** (prioridad, 802.1p) + **DEI 1 bit** + **VID 12 bits**. VID **0** y **4095** reservados → **4.094 VLAN utilizables**. La trama pasa de 1518 a **1522 octetos** |
| **Cableado estructurado** | **ISO/IEC 11801-1:2017** (internacional) · **EN 50173** (europea) · **TIA-568** (norteamericana). **Canal de 100 m** = **90 m de cable horizontal fijo** + **10 m de latiguillos**. Categorías de componente (**Cat 5e, 6, 6A, 7, 8.1**) frente a clases de enlace (**D, E, EA, F, I**) |
| **Alimentación por Ethernet (PoE)** | **802.3af** (Tipo 1) **15,4 W** en el equipo alimentador y **12,95 W** en el dispositivo · **802.3at** (Tipo 2, PoE+) **30 / 25,5 W** · **802.3bt** (Tipos 3 y 4, PoE++) **60 / 51 W** y **90 / 71,3 W**, usando **los cuatro pares** |
| **Medidas del ENS sobre la red local** | **`mp.com.1`** perímetro seguro (**las tres categorías**) · **`mp.com.2`** confidencialidad · **`mp.com.3`** integridad y autenticidad · **`mp.com.4`** **separación de flujos de información en la red**, que **no aplica en categoría BÁSICA** y cuyo **refuerzo R1 nombra las VLAN** con segregación mínima en **usuarios, servicios y administración**; **`mp.com.4.2`**: las comunicaciones inalámbricas, **en un segmento separado**. Añádase **`mp.eq.4`** (otros dispositivos conectados a la red) y **`mp.if.1`** (áreas separadas con control de acceso) |
| **Marco legal español** | **Ley 11/2022, de 28 de junio, General de Telecomunicaciones** (art. **55**, infraestructuras comunes en el interior de las edificaciones; art. **63**, integridad y seguridad de las redes; arts. **85-97**, dominio público radioeléctrico) y **RD 346/2011**, Reglamento regulador de las **ICT** |
