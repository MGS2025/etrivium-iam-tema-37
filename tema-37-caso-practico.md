# Tema 37 — Casos Prácticos

> **Título oficial**: Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión.
>
> **Formato**: 3 casos prácticos sobre supuestos reales del Ayuntamiento de Madrid. Cada caso suma **10 puntos**.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

Los tres casos recorren el supuesto de referencia del tema (ver tema-37-contenido.md, «Convenciones»): la **red local de una Oficina de Atención a la Ciudadanía** de un distrito, en un edificio municipal de tres plantas, conectada con el centro de proceso de datos del IAM. El **Caso 1** trabaja el **diseño físico**: topología, medios, cableado estructurado y alimentación por Ethernet (§2, §3 y §6.1). El **Caso 2**, el **diagnóstico de cuatro incidencias** que solo se explican entendiendo las técnicas de transmisión y los métodos de acceso (§3, §4 y §5). Y el **Caso 3**, la **segmentación, el control de acceso y la adecuación al Esquema Nacional de Seguridad** (§5.2.2, §6.2 y §6.3).

---

## Caso 1 — Diseño de la red local de una Oficina de Atención a la Ciudadanía

### Enunciado

El Ayuntamiento rehabilita un edificio municipal de **tres plantas** para instalar en él una **Oficina de Atención a la Ciudadanía**. El IAM debe redactar las prescripciones técnicas del cableado y de la electrónica de red. Datos de partida:

- Cada planta tendrá **44 puestos de tramitación**, **12 teléfonos IP** y **2 impresoras multifunción**.
- Habrá **6 cámaras de videovigilancia** por planta, con tráfico continuo, y **4 puntos de acceso inalámbrico** por planta para la red corporativa y la de la sala de espera.
- Se dispondrá de un **armario de comunicaciones por planta** y de un **armario principal** en la planta baja, junto al recinto de instalaciones de telecomunicación.
- La toma de usuario **más alejada** de su armario de planta queda, medida sobre canalización, a **86 metros**; hay una segunda toma, en un anexo del patio, a **112 metros**.
- La distancia entre cada armario de planta y el armario principal es de **unos 40 metros**.
- El edificio se conectará con el centro de proceso de datos del IAM, situado a **6 kilómetros**.
- El horizonte de vida útil previsto para el cableado es de **20 años**.

Se pide un informe técnico previo a la licitación.

### Cuestiones

**Cuestión 1 — Medios y categorías (3 puntos).** Especifique el medio de transmisión y la categoría o el tipo de fibra para **cada uno de los cuatro tramos** de la instalación (puesto a armario de planta; armario de planta a armario principal; armario principal a centro de proceso de datos; y cobertura de la sala de espera), justificando cada elección por distancia, velocidad objetivo y necesidad de alimentación.

**Cuestión 2 — Cableado estructurado y las dos tomas conflictivas (2 puntos).** Identifique los **subsistemas** del cableado estructurado presentes en el edificio. Indique si las tomas situadas a **86 y a 112 metros** cumplen la norma y, en caso negativo, qué solución procede. Cite la norma aplicable.

**Cuestión 3 — Topología y dimensionado del enlace ascendente (3 puntos).** Describa la **topología física y lógica** resultante. Calcule si un enlace ascendente de **1 Gbit/s** entre el armario de planta y el armario principal es suficiente, y proponga alternativa razonada si no lo es.

**Cuestión 4 — Alimentación por Ethernet (2 puntos).** Determine qué **norma de PoE** debe exigirse en el pliego para alimentar teléfonos, cámaras y puntos de acceso, y qué precaución hay que tomar al dimensionar el conmutador. Indique además cómo debe redactarse la prescripción técnica para no vulnerar la normativa de contratación.

### Solución orientativa

- **C1**: (§3.5.1 y §6.1) Los cuatro tramos:

| Tramo | Medio | Justificación |
|---|---|---|
| **Puesto a armario de planta** | Par trenzado **U/UTP Cat 6A**, clase EA, 500 MHz | Garantiza **10GBASE-T a 100 m**, cubre los 20 años de vida útil del cableado y admite **PoE de tipo 3 o 4**. Cat 6 se descarta: solo llega a 10 Gbit/s hasta 55 m |
| **Armario de planta a armario principal** | **Fibra multimodo OM4**, dos hilos por enlace | 40 m con velocidad objetivo de 10 Gbit/s y margen; además **elimina los problemas de tierras entre plantas**, que en cobre apantallado son una fuente clásica de averías |
| **Armario principal a CPD del IAM** | **Fibra monomodo OS2** | 6 km exceden por completo el alcance del cobre y el de la multimodo; la monomodo con fuente láser cubre decenas de kilómetros |
| **Sala de espera** | **Sin cable de usuario**: puntos de acceso **802.11ax** alimentados por PoE | El acceso de la ciudadanía es inalámbrico; el cable llega solo hasta el punto de acceso |

  **Se valora** que la justificación se dé siempre con la misma tríada —**distancia, velocidad objetivo y necesidad de alimentación**— y que se observe que **el cableado es la parte más duradera y más cara de intervenir de una red**: vive veinte o treinta años, frente a los cinco o siete de un conmutador, y por eso se sobredimensiona deliberadamente.

- **C2**: (§6.1) Los **subsistemas** presentes, conforme a **ISO/IEC 11801-1:2017** y su equivalente europea **EN 50173** —que es la que procede citar en un pliego español—: **subsistema horizontal** (del distribuidor de planta a las tomas), **área de trabajo** (de la toma al equipo, con latiguillo), **subsistema vertical o troncal de edificio** (de los distribuidores de planta al distribuidor de edificio) y, si el complejo tuviera más edificios, **subsistema de campus**. La norma fija un **canal máximo de 100 metros**, repartidos en **90 m de cable horizontal fijo** más **10 m de latiguillos** sumando ambos extremos.

  **La toma a 86 metros CUMPLE**, pero **con muy poco margen**: 86 m de cable fijo dejan solo 4 m para los dos latiguillos, lo que en la práctica es inviable. Se valora que se señale que **el límite operativo real de la tirada horizontal es de 90 m** y que 86 m obliga a latiguillos muy cortos y a documentarlo expresamente. **La toma a 112 metros NO CUMPLE** y no hay excepción posible: **la solución no es un cable más largo** —el enlace no certificaría—, sino **instalar un armario intermedio** en el anexo, alimentado por fibra desde el armario de planta, que actúe como nuevo distribuidor y desde el cual la tirada horizontal vuelva a estar dentro de los 90 m.

- **C3**: (§2.2.2 y §5.2.1) **Topología física**: un **árbol** o estructura jerárquica, es decir, tres estrellas —una por planta— colgando de una cuarta estrella en el armario principal. **Topología lógica**: **punto a punto conmutado**, porque cada puerto de conmutador es un enlace dedicado en dúplex; y, superpuesta a ella, una segmentación en **VLAN**, de modo que la topología lógica no se parece al dibujo del cableado. Se valora que se explicite que **con conmutador no hay bus lógico ni colisiones**, y por tanto CSMA/CD está desactivado.

  **Dimensionado del enlace ascendente.** El planteamiento correcto **no es sumar las velocidades nominales** —nunca transmiten todos a la vez— sino trabajar con una **relación de sobresuscripción** aceptada, que en el nivel de acceso se sitúa habitualmente entre **20:1 y 4:1**. Por planta hay `44 + 12 + 2 + 6 + 4 = 68` puertos activos de 1 Gbit/s. Con un ascendente de **1 Gbit/s** la relación sería de **68:1**, muy por encima de lo admisible. Con **10 Gbit/s** baja a **6,8:1**, que sí es razonable. **Conclusión: el enlace ascendente debe ser de 10 Gbit/s sobre la fibra multimodo**, lo que además es coherente con haber cableado el horizontal en Cat 6A.

  **Alternativa si el presupuesto lo impidiera**: **dos enlaces de 1 Gbit/s agregados** mediante **IEEE 802.1AX** con **LACP**, que dan 2 Gbit/s con conmutación por fallo automática, aunque la relación seguiría siendo de 34:1. Se valora que se advierta de un matiz de dimensionado que suele olvidarse: **el tráfico de las cámaras es continuo y ascendente**, a diferencia del de los puestos, que es a ráfagas, de modo que **en una red con mucha videovigilancia la sobresuscripción admisible es menor**.

- **C4**: (§1.3 y §5.4) La norma que debe exigirse es **IEEE 802.3bt**, y como mínimo **IEEE 802.3at**. El razonamiento por dispositivo: un **teléfono IP** se cubre con **802.3af** (tipo 1, **15,4 W** en el equipo alimentador y **12,95 W** garantizados en el dispositivo); una **cámara** con motorización o calefactor necesita ya **802.3at** (tipo 2, **30 / 25,5 W**); y un **punto de acceso Wi-Fi 6 o 7 con varias radios** puede requerir **802.3bt** de tipo 3 (**60 / 51 W**), que además utiliza **los cuatro pares** en lugar de dos.

  **La precaución de dimensionado** es la que se valora más: **no basta con que el conmutador tenga PoE en todos los puertos**, hay que comprobar su **presupuesto total de potencia**. Un conmutador de 48 puertos con 802.3at en todos ellos necesitaría 48 × 30 = 1.440 W, cifra que ningún equipo entrega; los fabricantes ofrecen presupuestos muy inferiores, de modo que **hay que sumar el consumo real de los dispositivos previstos y elegir la fuente en consecuencia**, previendo además **redundancia de alimentación** si de esos puertos cuelga la telefonía, que es un servicio crítico.

  **Redacción de la prescripción**: debe citarse **la norma y no la marca**. El **artículo 126.6 de la Ley 9/2017** prohíbe mencionar una marca, patente o fabricante determinado en las prescripciones técnicas salvo que resulte imprescindible, y aun entonces con la coletilla **«o equivalente»**. Se valora que se proponga una redacción del tipo «conmutador de 48 puertos 10/100/1000BASE-T con alimentación conforme a IEEE 802.3at, presupuesto mínimo de potencia de X vatios, soporte de IEEE 802.1Q, 802.1D/w/s, 802.1X y 802.1AX», que describe funcionalmente sin cerrar el mercado.

### Criterios de evaluación

| Cuestión | Puntos | Se valora |
|---|---|---|
| **C1** | 3 | Los cuatro tramos con medio y categoría correctos (2). Justificación por distancia, velocidad y alimentación en cada uno (0,5). Observación sobre la vida útil del cableado frente a la de la electrónica (0,5) |
| **C2** | 2 | Enumeración correcta de los subsistemas y cita de ISO/IEC 11801 o EN 50173 (0,7). Regla de los 90 + 10 metros (0,5). Diagnóstico correcto de las dos tomas (0,5). Solución del armario intermedio, no del cable largo (0,3) |
| **C3** | 3 | Topología física de árbol y lógica punto a punto conmutada (1). Planteamiento por sobresuscripción y no por suma nominal (1). Conclusión de 10 Gbit/s con cálculo (0,5). Alternativa de agregación 802.1AX y matiz del tráfico continuo de las cámaras (0,5) |
| **C4** | 2 | Identificación de la norma por tipo de dispositivo con sus vatajes (1). Advertencia sobre el presupuesto total de potencia del conmutador (0,7). Redacción sin marca conforme al art. 126.6 de la LCSP (0,3) |

---

## Caso 2 — Diagnóstico de cuatro incidencias en la red de la oficina

### Enunciado

La Oficina de Atención a la Ciudadanía lleva una semana en servicio y el Centro de Atención a Usuarios acumula **cuatro incidencias simultáneas**, aparentemente inconexas:

1. **Un puesto de la segunda planta** funciona, pero con una lentitud extrema al abrir expedientes. Las estadísticas de su puerto de conmutador muestran **colisiones tardías** y errores de secuencia de comprobación, pese a que se trata de una red conmutada.
2. **Toda la primera planta** sufre cortes intermitentes de varios segundos. La utilización de los enlaces está al máximo y los conmutadores muestran un **volumen enorme de tráfico de difusión**. Un técnico recuerda haber conectado el día anterior **un pequeño conmutador bajo una mesa** para ampliar tomas.
3. **La Wi-Fi de la sala de espera** funciona bien a primera hora y se vuelve inservible a media mañana, cuando hay unas cuarenta personas esperando. Las quejas son de lentitud, no de falta de cobertura.
4. **Las cámaras del anexo del patio** pierden la conexión de forma aleatoria. Se instalaron con una tirada de cable de **112 metros** desde el armario de planta, «porque el rollo daba de sobra».

### Cuestiones

**Cuestión 1 — Incidencia 1 (2,5 puntos).** Diagnostique la causa. Explique qué son las colisiones tardías, por qué su aparición en una red conmutada es significativa y cómo se corrige.

**Cuestión 2 — Incidencia 2 (2,5 puntos).** Diagnostique la causa. Explique el mecanismo por el que un conmutador conectado bajo una mesa puede tumbar una planta entera, por qué la trama Ethernet no lo evita por sí sola y qué dos controles —uno de protocolo y otro de configuración— lo habrían impedido.

**Cuestión 3 — Incidencia 3 (3 puntos).** Diagnostique la causa. Explique por qué la velocidad efectiva de una red Wi-Fi cae al aumentar el número de usuarios aunque la cobertura sea buena, y proponga **tres medidas correctoras**, indicando expresamente cuál NO debe adoptarse y por qué.

**Cuestión 4 — Incidencia 4 (2 puntos).** Diagnostique la causa y explique por qué el fallo es intermitente y no total, cuál es la solución correcta y qué prueba documental debe exigirse en la recepción de una obra de cableado.

### Solución orientativa

- **C1**: (§4.2.1 y §5.2.1) El diagnóstico es una **discordancia de dúplex** (*duplex mismatch*): un extremo del enlace ha quedado en **dúplex** y el otro en **semidúplex**, típicamente por una **negociación automática fallida** o por haber fijado la velocidad y el dúplex a mano solo en un lado.

  **Mecanismo**: el extremo en semidúplex aplica **CSMA/CD** y, por tanto, escucha mientras transmite; el extremo en dúplex transmite cuando quiere, sin escuchar. Cuando ambos coinciden, el extremo semidúplex detecta lo que interpreta como una colisión, **aborta, emite el atasco y retrocede**, mientras el otro sigue transmitiendo. El resultado es un enlace que **funciona**, y por eso el usuario dice «va lento» y no «no va», pero con pérdidas masivas y retransmisiones de la capa de transporte.

  **Las colisiones tardías** son las detectadas **después de haber transmitido los primeros 64 octetos**, es decir, **después de la ranura de colisión** (§4.2.1). Una colisión normal se detecta dentro de esa ventana; una tardía **no debería producirse nunca** en un segmento correctamente dimensionado, porque significa que la colisión llegó cuando la estación ya se creía a salvo. **Su aparición en una red conmutada es doblemente significativa**: en dúplex punto a punto **no debería haber colisión alguna**, así que **cualquier colisión es un síntoma**, y que además sea tardía apunta directamente a la discordancia de dúplex —o, con menos frecuencia, a un segmento demasiado largo—.

  **Corrección**: dejar **la negociación automática activada en ambos extremos**, que es hoy la recomendación de la norma, o bien **fijar velocidad y dúplex a mano en los dos**, nunca en uno solo. Se valora que se advierta de que fijar solo un extremo es precisamente la causa más frecuente del problema, porque el otro, al no recibir el intercambio de negociación, **cae por omisión a semidúplex**.

- **C2**: (§5.2.1) El diagnóstico es una **tormenta de difusión** provocada por un **bucle de capa 2**: el conmutador conectado bajo la mesa se enchufó, deliberadamente o por error, **con dos cables a la red**, cerrando un camino redundante.

  **Mecanismo**: una única trama de **difusión** entra en el bucle y **se replica indefinidamente**, y en cada vuelta los conmutadores la reenvían por todos sus puertos, multiplicándola. La red se satura en segundos, y con ella las tablas de direcciones MAC, que ven la misma dirección aparecer por puertos distintos. **La trama Ethernet no lo evita por sí sola** porque, a diferencia del datagrama IP, **carece de campo de tiempo de vida**: nada la detiene. Esta es exactamente la razón por la que un encaminador no necesita árbol de expansión y un conmutador sí.

  **Los dos controles**:

  - **De protocolo**: el **árbol de expansión** (**IEEE 802.1D**, y sus evoluciones **802.1w** de convergencia rápida y **802.1s** por grupos de VLAN, hoy integradas en 802.1Q), que **bloquea lógicamente los enlaces redundantes** dejando una topología sin bucles y los reactiva si el camino activo cae. Debe estar **activo en todos los conmutadores**, y conviene añadir la **protección del puente raíz** para que un equipo ajeno no pueda anunciarse como raíz y reorganizar toda la red a su favor.
  - **De configuración**: la **seguridad de puerto** (*port security*), que limita el número de direcciones MAC que puede aprender un puerto de acceso y bloquea o alerta si aparecen más, lo que impide conectar un conmutador no autorizado; y, en la misma línea, **deshabilitar administrativamente los puertos no usados** y **desactivar la negociación automática de enlace troncal** en los puertos de acceso.

  Se valora que se observe que la causa última es **organizativa** —un técnico ampliando tomas por su cuenta— y que la respuesta correcta incluye tanto el control técnico como el procedimiento: **ningún equipo de red se conecta a la red municipal sin inventariar**, que es lo que exige `mp.eq.4` del ENS.

- **C3**: (§4.2.2) El diagnóstico es la **saturación por contienda del medio inalámbrico**, no un problema de cobertura. Cuatro causas encadenadas, y hay que enumerarlas:

  1. **El medio es compartido y semidúplex**: la velocidad nominal es la del canal, no la de cada cliente, y **se reparte entre todas las estaciones asociadas**.
  2. **Cada trama de datos exige un ACK** precedido de su SIFS, y **antes de cada transmisión hay un DIFS más un retroceso aleatorio** que, con CWmín = 15, promedia 7,5 ranuras. Al aumentar el número de estaciones aumenta la contienda, crecen las ventanas y **se gasta cada vez más canal sin transmitir datos**.
  3. **El problema de la tasa ancla**: los móviles situados en el límite de cobertura **negocian una modulación lenta** y, al tardar mucho en enviar poco, **ocupan el canal un tiempo desproporcionado**, degradando a todas las demás estaciones aunque estén cerca del punto de acceso.
  4. **Nodos ocultos**: quienes están detrás de una columna de hormigón no oyen a quienes están junto a la puerta, y sus transmisiones colisionan en el punto de acceso pese a que ambos «escucharon» el medio libre.

  **Tres medidas correctoras**:

  - **Más puntos de acceso con menos potencia cada uno**, planificando **canales que no se solapen** —recuérdese que en 2,4 GHz solo lo son el 1, el 6 y el 11— y llevando la cobertura principal a **5 GHz**, donde hay muchos más canales.
  - **Fijar una velocidad mínima de asociación**, para que los clientes demasiado lejanos no se asocien a esa celda y pasen al punto de acceso vecino. Ataca directamente el problema de la tasa ancla.
  - **Desplegar puntos de acceso 802.11ax** para aprovechar **OFDMA**, que atiende simultáneamente a muchos clientes con tráfico pequeño en lugar de por turnos, que es exactamente el perfil de una sala de espera llena de móviles. Se acepta como alternativa activar **RTS/CTS** por encima de un umbral de tamaño de trama, contra el nodo oculto, advirtiendo de su coste en sobrecarga.

  **La medida que NO debe adoptarse es subir la potencia de emisión del punto de acceso.** Es la reacción intuitiva y es contraproducente: **agrandar la celda hace que más estaciones compitan por el mismo canal**, empeora la contienda, aumenta la interferencia con las celdas vecinas y **no mejora el enlace de subida**, porque la potencia del móvil no cambia. Se valora expresamente esta observación.

- **C4**: (§3.5.1 y §6.1) El diagnóstico es un **incumplimiento de la longitud máxima del canal**: **112 metros superan los 100 metros** que fija **ISO/IEC 11801** (**90 m de cable horizontal fijo más 10 m de latiguillos**).

  **Por qué el fallo es intermitente y no total**: superar el límite no corta el enlace, **degrada sus márgenes**. La **atenuación** crece con la longitud y con la frecuencia, y la **relación entre atenuación y diafonía** se estrecha hasta quedar por debajo del margen que la norma exige. El resultado es un enlace **que enlaza y funciona en condiciones favorables** pero que pierde tramas cuando sube la temperatura del falso techo, cuando aumenta la actividad de los pares vecinos o cuando el tráfico continuo de la cámara exige sostener la velocidad máxima. Se valora que se relacione con el síntoma del caso: **las cámaras generan tráfico continuo**, que es el peor escenario para un enlace al límite.

  **Solución correcta**: **instalar un armario intermedio** en el anexo, enlazado por **fibra** desde el armario de planta, de modo que la tirada horizontal hasta las cámaras vuelva a estar dentro de los 90 metros. Se admite como alternativa técnica llevar **fibra hasta un conmutador industrial** en el propio anexo. Lo que **no** es solución es cambiar a una categoría superior de cable: **el límite de 100 metros no depende de la categoría**.

  **Prueba documental exigible en la recepción**: la **certificación del cableado** realizada con equipo homologado, que mide toma a toma la **pérdida de inserción**, la **diafonía en el extremo cercano (NEXT y PSNEXT)**, la **ACR-F**, la **pérdida de retorno**, el **retardo de propagación** y la **diferencia de retardo entre pares**, y emite un informe con el resultado de aptitud por enlace. Con esa certificación exigida en el pliego, **el enlace de 112 metros no habría pasado la recepción de la obra**. Se valora que se añada la exigencia de **documentación y etiquetado** conforme a **TIA-606**, que es lo primero que se descuida y lo que más caro sale a medio plazo.

### Criterios de evaluación

| Cuestión | Puntos | Se valora |
|---|---|---|
| **C1** | 2,5 | Diagnóstico de discordancia de dúplex (1). Mecanismo: un extremo aplica CSMA/CD y el otro no (0,7). Definición de colisión tardía como posterior a la ranura de colisión (0,5). Corrección en AMBOS extremos (0,3) |
| **C2** | 2,5 | Diagnóstico de bucle y tormenta de difusión (1). Ausencia de tiempo de vida en la trama Ethernet como causa (0,6). Árbol de expansión con su numeración correcta (0,5). Seguridad de puerto y puertos deshabilitados (0,4) |
| **C3** | 3 | Diagnóstico de saturación por contienda, no de cobertura (0,8). Al menos tres de las cuatro causas, con la tasa ancla entre ellas (1). Tres medidas correctoras coherentes (0,8). Advertencia expresa de que subir la potencia empeora el problema (0,4) |
| **C4** | 2 | Identificación del incumplimiento de los 100 m con la norma citada (0,7). Explicación de por qué el fallo es intermitente, por degradación de márgenes (0,6). Armario intermedio como solución, y descarte del cambio de categoría (0,4). Certificación del cableado como prueba de recepción (0,3) |

---

## Caso 3 — Segmentación, control de acceso y adecuación al ENS

### Enunciado

El sistema de tramitación de expedientes al que accede la Oficina de Atención a la Ciudadanía ha sido categorizado como de **categoría MEDIA** conforme al **Esquema Nacional de Seguridad**. Durante una auditoría interna se detectan **cinco hallazgos** en la red local de la oficina:

1. **Toda la oficina está en una única red plana**: puestos de tramitación, teléfonos IP, impresoras multifunción, cámaras de videovigilancia y la interfaz de gestión de los propios conmutadores comparten el mismo segmento.
2. La **red Wi-Fi de la sala de espera** para la ciudadanía **usa el mismo segmento** que la red corporativa, con una contraseña compartida que se entrega en el mostrador.
3. Existen **tomas de red activas y accesibles** en la sala de espera y en la sala de reuniones, sin ningún control: quien conecta un portátil **obtiene dirección por DHCP** y alcanza el sistema de expedientes.
4. Los **armarios de comunicaciones** de las plantas primera y segunda **están abiertos**, en el pasillo, sin puerta con llave.
5. Los conmutadores y los puntos de acceso **no tienen la hora sincronizada** y cada uno registra sus eventos con un desfase distinto.

### Cuestiones

**Cuestión 1 — Segmentación exigible (3 puntos).** Proponga la segmentación en VLAN de la oficina y justifique **qué medida concreta del anexo II del ENS la exige**, si es exigible a este sistema y **qué refuerzo** satisface la solución. Explique además cómo viaja el tráfico de varias VLAN por un mismo enlace entre conmutadores.

**Cuestión 2 — La red inalámbrica (2 puntos).** Analice el hallazgo 2 a la luz de la normativa. Cite el requisito literal que se incumple y proponga el diseño correcto de las dos redes inalámbricas.

**Cuestión 3 — Control de acceso a la toma de red (3 puntos).** Analice el hallazgo 3. Describa el mecanismo normalizado que lo corrige, sus **tres papeles**, cómo se comporta el puerto antes y después de la autenticación, y qué hacer con los dispositivos que no admiten ese mecanismo.

**Cuestión 4 — Hallazgos 4 y 5 (2 puntos).** Identifique la medida del ENS que ampara cada uno de los dos últimos hallazgos y explique la consecuencia práctica de no corregirlos.

### Solución orientativa

- **C1**: (§5.2.2 y §6.3) **Segmentación propuesta**, con una VLAN por función y nivel de confianza:

| VLAN | Contenido | Observación |
|---|---|---|
| **Puestos de tramitación** | Los equipos de los empleados | Acceso al sistema de expedientes |
| **Telefonía IP** | Teléfonos y pasarela de voz | Permite además priorizar con 802.1p |
| **Impresión** | Impresoras multifunción | Dispositivos de `mp.eq.4` |
| **Videovigilancia** | Cámaras y grabador | Tráfico continuo y equipos de baja capacidad de actualización |
| **Gestión de red** | Interfaces de administración de conmutadores y puntos de acceso | **Nunca accesible desde la VLAN de usuarios** |
| **Wi-Fi corporativa** | Portátiles y móviles de servicio | Autenticada contra el directorio |
| **Wi-Fi de invitados** | Ciudadanía en la sala de espera | **Salida directa a internet, sin visibilidad del resto** |

  **La medida que lo exige** es **`mp.com.4` — «Separación de flujos de información en la red»** del anexo II del **RD 311/2022**. Su requisito general es que *«el tráfico por la red se segregará para que cada equipo solamente tenga acceso a la información que necesita»*.

  **Es exigible a este sistema**: `mp.com.4` **no aplica en categoría BÁSICA** —es la única del grupo `mp.com` que no se exige siempre— pero **sí en MEDIA**, donde se exige la medida **más uno** de los refuerzos **R1, R2 o R3**. La solución propuesta, implantada con **VLAN**, satisface el **refuerzo R1, «segmentación lógica básica»**, que además ordena segregar **como mínimo en usuarios, servicios y administración**: el diseño lo cumple con holgura al separar siete segmentos, entre ellos una **VLAN de gestión propia**. Se valora que se identifique R2 (VPN) y R3 (medios físicos separados) como las otras dos vías posibles, y que se recuerde que en categoría **ALTA** haría falta **[R2 o R3] más R4**, puntos de interconexión.

  **Doble función de la segmentación**, que conviene enunciar: **acota la propagación de un incidente** —el propio ENS lo dice: *«la segmentación acota el acceso a la información y, consiguientemente, la propagación de los incidentes de seguridad»*— y **contiene el tráfico de difusión**, porque cada VLAN es un dominio de difusión independiente.

  **Cómo viaja el tráfico de varias VLAN por un mismo enlace**: mediante un **puerto troncal** que **etiqueta** cada trama conforme a **IEEE 802.1Q**, insertando **4 octetos** entre la dirección de origen y el campo de tipo: **TPID `0x8100`**, **PCP** de 3 bits de prioridad, **DEI** de 1 bit e identificador **VID** de 12 bits, de los que se reservan el 0 y el 4095, quedando **4.094 VLAN utilizables**. La trama pasa de **1518 a 1522 octetos**. Los puertos a los que se conectan los equipos finales son **puertos de acceso**, pertenecen a una sola VLAN y su tráfico viaja **sin etiquetar**. Se valora que se advierta de la **VLAN nativa** —la que circula sin etiquetar por el troncal— como debilidad conocida frente al **salto de VLAN por doble etiquetado**, y de la recomendación de **asignarla a una VLAN sin uso** en lugar de dejarla en la VLAN 1 por defecto.

- **C2**: (§3.5 y §6.3) El hallazgo incumple un requisito **literal y expreso**: **`mp.com.4.2`** del anexo II del ENS establece que *«si se emplean comunicaciones inalámbricas, será en un segmento separado»*. **No es una recomendación de buena práctica: es un requisito normativo**, y su fundamento técnico es que **el medio inalámbrico no se puede acotar físicamente** —la señal se escapa a la calle— de modo que el control de acceso al edificio no protege la red.

  **Diseño correcto**, con **dos redes inalámbricas distintas**:

  - **Wi-Fi corporativa**: SSID propio, **VLAN corporativa** separada, autenticación **802.1X** contra el directorio (**WPA3-Enterprise**, o **WPA2-Enterprise** como mínimo), asignación dinámica de VLAN por usuario.
  - **Wi-Fi de invitados**: SSID distinto, **VLAN de invitados** cuyo tráfico va etiquetado hasta el cortafuegos y **sale directamente a internet**, **sin ninguna visibilidad de las demás VLAN municipales**, con **aislamiento entre clientes** para que los dispositivos de la sala no se vean entre sí, y con portal de acceso y condiciones de uso.

  Se valora que se ordene además **eliminar la contraseña compartida entregada en el mostrador** —una credencial conocida por cientos de personas no es un control de acceso—, **desactivar los mecanismos heredados** (WEP, WPS, TKIP) y **planificar la potencia** para no radiar innecesariamente fuera del edificio.

- **C3**: (§6.2) El mecanismo normalizado es el **control de acceso a la red basado en puerto, IEEE 802.1X**. Sus **tres papeles**:

  - **Suplicante**: el programa cliente del equipo que quiere conectarse.
  - **Autenticador**: **el conmutador** —o el punto de acceso—, que controla el estado del puerto.
  - **Servidor de autenticación**: normalmente un **servidor RADIUS**, que verifica las credenciales contra el directorio corporativo.

  **Comportamiento del puerto**: antes de la autenticación el puerto está en estado **no controlado** y **solo deja pasar tramas EAPOL**; el equipo no obtiene dirección por DHCP ni alcanza nada. Tras una autenticación correcta el puerto pasa a estado **controlado** y da servicio; además, el servidor puede **devolver la VLAN que corresponde a ese usuario o equipo**, con lo que **la segmentación sigue a la persona y no al cable**: el mismo puerto de la sala de reuniones coloca a un empleado en la VLAN de tramitación y a un visitante en la de invitados. Es la conexión directa entre esta cuestión y la primera.

  **Dispositivos que no admiten suplicante** —impresoras, cámaras, teléfonos antiguos—: se emplean mecanismos de excepción, principalmente la **autenticación por dirección MAC** (*MAC Authentication Bypass*) o el **acceso invitado** a una VLAN restringida. Se valora que se advierta de que **son mecanismos más débiles** —una dirección MAC se suplanta trivialmente, y más aún desde que los sistemas operativos la aleatorizan por privacidad— y que por tanto **hay que documentarlos como excepción**, limitarlos a puertos concretos y combinarlos con **seguridad de puerto**.

  **Controles complementarios** que completan la respuesta: **deshabilitar administrativamente los puertos no usados**, **vigilancia de DHCP** para impedir servidores no autorizados, **inspección de ARP** contra la suplantación y **control de tormentas de difusión**. Se valora la formulación de defensa en profundidad: **los controles son acumulativos y ninguno basta por sí solo**.

- **C4**: (§6.2 y §6.3) Los dos hallazgos y sus medidas:

  - **Hallazgo 4, armarios abiertos**: incumple **`mp.if.1` — «Áreas separadas y con control de acceso»**, que **aplica en las tres categorías** del ENS y ordena que el equipamiento se instale en áreas separadas y que se controlen los accesos a ellas. **Consecuencia práctica**: un armario abierto en un pasillo por el que pasa público permite **conectar un equipo a un puerto troncal** —que transporta todas las VLAN etiquetadas y anularía de un golpe toda la segmentación de la cuestión 1—, **conectar un analizador**, **apagar el conmutador** o **reiniciarlo a valores de fábrica**. Se valora la observación de que **la seguridad física es la primera capa y la que se olvida**: sin ella, los controles lógicos de las cuestiones anteriores son inútiles.
  - **Hallazgo 5, sin hora sincronizada**: incumple **`op.exp.8` — «Registro de la actividad»**, que exige que los registros se apoyen en una **base de tiempo común**. **Consecuencia práctica**: los registros de los conmutadores, de los puntos de acceso, del servidor RADIUS y del cortafuegos **no son correlacionables**, de modo que ante un incidente **no se puede reconstruir la secuencia de los hechos** ni determinar qué ocurrió antes y qué después. La corrección es sencilla y barata: **sincronizar todos los equipos de red por NTP** contra una fuente común de la red corporativa.

  Se valora que se cite adicionalmente **`mp.eq.4` — «Otros dispositivos conectados a la red»**, aplicable a las **impresoras multifunción**, las **cámaras** y los dispositivos de **internet de las cosas** del hallazgo 1, que exige configuración de seguridad adecuada, y cuyo **refuerzo R2** pide soluciones que permitan **visualizar los dispositivos presentes en la red, controlar su conexión y desconexión y verificar su configuración**, es decir, un sistema de control de admisión.

### Criterios de evaluación

| Cuestión | Puntos | Se valora |
|---|---|---|
| **C1** | 3 | Propuesta de segmentación con VLAN de gestión separada (0,8). Identificación de `mp.com.4` con su denominación literal (0,6). Que NO aplica en BÁSICA y sí en MEDIA con uno de los tres refuerzos (0,6). Etiqueta 802.1Q con sus campos y los 4.094 identificadores (0,7). Advertencia sobre la VLAN nativa (0,3) |
| **C2** | 2 | Cita literal de `mp.com.4.2` (0,7). Fundamento: el medio inalámbrico no se acota físicamente (0,4). Diseño de las dos redes con VLAN separada y salida directa a internet para invitados (0,6). Eliminación de la contraseña compartida (0,3) |
| **C3** | 3 | Identificación de 802.1X (0,6). Los tres papeles correctamente asignados (0,8). Estado no controlado con solo EAPOL, y controlado tras autenticar (0,7). Asignación dinámica de VLAN (0,5). Excepciones para dispositivos sin suplicante, con su advertencia (0,4) |
| **C4** | 2 | `mp.if.1` para los armarios, con la consecuencia del puerto troncal accesible (0,8). `op.exp.8` para la hora, con la consecuencia de la no correlación de registros (0,8). Cita adicional de `mp.eq.4` (0,4) |
