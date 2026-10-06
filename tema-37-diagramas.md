# Tema 37 — Catálogo de Diagramas

> **Título oficial**: Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión.
>
> **Versión**: v1.0
> **Fecha**: 2026-08-27
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (zero-dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)
> **Nota técnica**: las clases CSS de cada SVG llevan sufijo numérico único (`.t1`, `.h1`…) para evitar colisiones de estilos entre los 19 diagramas embebidos en la misma página. Ningún elemento mezcla `class` con el atributo `fill`: cuando hace falta un color distinto del de su clase se usa `style="fill:…"`, porque en la cascada CSS **la clase gana al atributo de presentación**.

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | Los cinco rasgos que definen una red local | §1.1 | Lista razonada | 680×340 |
| D2 | La familia IEEE 802 y las dos subcapas del nivel de enlace | §1.2 · §1.3 | Pila + mapa de normas | 680×372 |
| D3 | PAN, LAN, CAN, MAN y WAN: alcance, velocidad y titularidad | §2.1 | Escala comparativa | 680×340 |
| D4 | Las cuatro topologías básicas: fallo, cable y método de acceso | §2.2.1 | Comparativa gráfica | 680×366 |
| D5 | Topología física frente a topología lógica: los tres casos | §2.2.2 | Tabla-esquema | 680×346 |
| D6 | Modos de transmisión: sentido, número de líneas y sincronismo | §3.1 | Tres ejes | 680×352 |
| D7 | Banda base frente a banda ancha | §3.2 | Comparativa doble | 680×346 |
| D8 | Códigos de línea de las redes locales | §3.3 | Formas de onda | 680×372 |
| D9 | Las cinco técnicas de multiplexación | §3.4 | Esquemas de reparto | 680×352 |
| D10 | Medios guiados: par trenzado, coaxial y fibra | §3.5.1 | Secciones + tabla | 680×372 |
| D11 | El espectro de las redes locales inalámbricas | §3.5.2 | Bandas y canales | 680×352 |
| D12 | Mapa de los métodos de acceso al medio | §4.1 | Árbol de clasificación | 680×358 |
| D13 | CSMA/CD: algoritmo y regla de los 64 octetos | §4.2.1 | Diagrama de flujo + tiempos | 680×390 |
| D14 | CSMA/CA: DIFS, retroceso, ACK y el nodo oculto | §4.2.2 | Línea temporal + escenario | 680×384 |
| D15 | Paso de testigo: Token Ring, Token Bus y FDDI | §4.3 | Comparativa de anillos | 680×358 |
| D16 | Dispositivos por capa: dominios de colisión y de difusión | §5 | Mapa de capas | 680×372 |
| D17 | La etiqueta 802.1Q y la trama etiquetada | §5.2.2 | Mapa de bits | 680×346 |
| D18 | Cableado estructurado: subsistemas y distancias | §6.1 | Corte de edificio | 680×366 |
| D19 | 802.1X y las medidas del ENS sobre la red local | §6.2 · §6.3 | Flujo + tabla normativa | 680×378 |

---

## D1 · Los cinco rasgos que definen una red local

**Sección**: §1.1 — Definición, evolución y características principales
**Propósito**: Fijar la definición operativa de red local en cinco rasgos y destacar cuál de ellos es el que realmente discrimina, que no es el alcance geográfico sino la **titularidad del medio**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Los cinco rasgos que definen una red local: ámbito geográfico reducido, titularidad privada del medio, velocidad elevada, retardo y tasa de error bajos y medio inicialmente compartido; el criterio que de verdad discrimina no es la distancia sino que el cable sea propiedad de la organización y no de un operador">
  <style>.h1{font:700 13px system-ui,sans-serif;fill:#0055a0}.k1{font:700 10px system-ui,sans-serif;fill:#0055a0}.d1{font:9px system-ui,sans-serif;fill:#333}.n1{font:8.5px system-ui,sans-serif;fill:#666}.t1{font:700 11px system-ui,sans-serif;fill:#fff}.g1{font:700 9.5px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="20" text-anchor="middle" class="h1">Los cinco rasgos que definen una red local (LAN)</text>
  <text x="340" y="37" text-anchor="middle" class="n1">Si una pregunta describe una red y hay que decidir si es local, el rasgo 2 es el que decide</text>

  <rect x="22" y="46" width="636" height="32" rx="4" fill="#eef4fa"/>
  <rect x="22" y="46" width="30" height="32" rx="4" fill="#0055a0"/>
  <text x="37" y="67" text-anchor="middle" class="t1">1</text>
  <text x="62" y="60" class="k1">ÁMBITO GEOGRÁFICO REDUCIDO</text>
  <text x="62" y="73" class="d1">Un edificio, un grupo de edificios próximos o un recinto. De metros a pocos kilómetros. Es cualitativo: no hay cifra normativa</text>

  <rect x="22" y="82" width="636" height="32" rx="4" fill="#e6f2ec"/>
  <rect x="22" y="82" width="30" height="32" rx="4" fill="#2d8659"/>
  <text x="37" y="103" text-anchor="middle" class="t1">2</text>
  <text x="62" y="96" class="g1">TITULARIDAD PRIVADA DEL MEDIO — EL CRITERIO QUE DECIDE</text>
  <text x="62" y="109" class="d1">El cable es de la organización: se instala y se mantiene sin operador ni contrato de servicio. En una WAN el medio es del operador</text>

  <rect x="22" y="118" width="636" height="32" rx="4" fill="#eef4fa"/>
  <rect x="22" y="118" width="30" height="32" rx="4" fill="#0055a0"/>
  <text x="37" y="139" text-anchor="middle" class="t1">3</text>
  <text x="62" y="132" class="k1">VELOCIDAD DE TRANSMISIÓN ELEVADA</text>
  <text x="62" y="145" class="d1">Hoy: 1 Gbit/s en el puesto, 10 Gbit/s en la agregación, 25 a 100 Gbit/s y más en el centro de proceso de datos</text>

  <rect x="22" y="154" width="636" height="32" rx="4" fill="#eef4fa"/>
  <rect x="22" y="154" width="30" height="32" rx="4" fill="#0055a0"/>
  <text x="37" y="175" text-anchor="middle" class="t1">4</text>
  <text x="62" y="168" class="k1">RETARDO BAJO Y TASA DE ERROR MUY BAJA</text>
  <text x="62" y="181" class="d1">Consecuencia de diseño: en la capa 2 basta con DETECTAR el error y descartar la trama; recuperar es tarea del transporte</text>

  <rect x="22" y="190" width="636" height="32" rx="4" fill="#fdf3e3"/>
  <rect x="22" y="190" width="30" height="32" rx="4" fill="#e89822"/>
  <text x="37" y="211" text-anchor="middle" class="t1">5</text>
  <text x="62" y="204" class="k1">MEDIO COMPARTIDO, AL MENOS EN SU ORIGEN</text>
  <text x="62" y="217" class="d1">De aquí nace el problema del acceso al medio. La LAN conmutada lo elimina en el cable; la inalámbrica lo conserva íntegro</text>

  <rect x="22" y="238" width="636" height="56" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="256" text-anchor="middle" class="k1">Dos edificios municipales a 800 m unidos por FIBRA PROPIA = red local (o de campus)</text>
  <text x="340" y="272" text-anchor="middle" class="k1">Los mismos 800 m con un ENLACE CONTRATADO a un operador = ya no lo es</text>
  <text x="340" y="287" text-anchor="middle" class="d1">Misma distancia, misma velocidad, distinta respuesta: lo que cambia es de quién es el medio</text>

  <text x="670" y="328" text-anchor="end" class="n1">[Fuente: IEEE 802-2014 · Tanenbaum]</text>
</svg>
```

---

## D2 · La familia IEEE 802 y las dos subcapas del nivel de enlace

**Sección**: §1.2 y §1.3 — Modelo de referencia y normalización
**Propósito**: Mostrar de un vistazo las dos ideas que hay que retener del bloque conceptual: que el IEEE 802 solo normaliza las capas 1 y 2, y que **parte la capa de enlace en LLC y MAC**, siendo la MAC la única que depende de la tecnología del medio.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="El comité IEEE 802 normaliza únicamente las capas física y de enlace de datos, y divide la capa de enlace en dos subcapas: LLC, definida en 802.2 y común a toda la familia, y MAC, específica de cada tecnología; a la derecha, el reparto de los grupos de trabajo 802.1, 802.3, 802.5, 802.11 y 802.15 y su estado de vigencia">
  <style>.h2{font:700 13px system-ui,sans-serif;fill:#0055a0}.k2{font:700 10px system-ui,sans-serif;fill:#0055a0}.d2{font:9px system-ui,sans-serif;fill:#333}.n2{font:8.5px system-ui,sans-serif;fill:#666}.t2{font:700 10.5px system-ui,sans-serif;fill:#fff}.w2{font:9px system-ui,sans-serif;fill:#fff}.g2{font:700 9px system-ui,sans-serif;fill:#2d8659}.r2{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h2">El ámbito del IEEE 802: capas 1 y 2, con la capa 2 partida en dos</text>

  <text x="160" y="40" text-anchor="middle" class="k2">MODELO OSI</text>
  <rect x="30" y="48" width="260" height="26" rx="4" fill="#c9d6e2"/>
  <text x="160" y="65" text-anchor="middle" class="d2">Capas 3 a 7 — FUERA del ámbito del IEEE 802 (IETF)</text>

  <rect x="30" y="80" width="260" height="76" rx="4" fill="#0055a0"/>
  <text x="160" y="97" text-anchor="middle" class="t2">CAPA 2 · ENLACE DE DATOS</text>
  <rect x="40" y="103" width="240" height="22" rx="3" fill="#3d82c4"/>
  <text x="160" y="118" text-anchor="middle" class="w2">LLC (802.2) — común a toda la familia</text>
  <rect x="40" y="128" width="240" height="22" rx="3" fill="#e89822"/>
  <text x="160" y="143" text-anchor="middle" class="w2">MAC — específica de cada tecnología</text>

  <rect x="30" y="162" width="260" height="26" rx="4" fill="#0055a0"/>
  <text x="160" y="179" text-anchor="middle" class="t2">CAPA 1 · FÍSICA</text>

  <text x="160" y="206" text-anchor="middle" class="d2">LLC: multiplexa protocolos superiores (DSAP/SSAP)</text>
  <text x="160" y="219" text-anchor="middle" class="d2">MAC: delimita la trama, direcciona y decide quién transmite</text>
  <text x="160" y="234" text-anchor="middle" class="g2">SOLO LA SUBCAPA MAC TOCA EL MEDIO</text>
  <text x="160" y="248" text-anchor="middle" class="r2">La subcapa MAC no existe en el OSI puro: la añade el IEEE</text>

  <text x="490" y="40" text-anchor="middle" class="k2">LOS GRUPOS DE TRABAJO</text>
  <rect x="320" y="48" width="338" height="20" rx="3" fill="#eef4fa"/>
  <text x="330" y="62" class="d2"><tspan class="k2">802.1</tspan>  Arquitectura: 1Q VLAN · 1D/w/s árbol · 1X acceso</text>
  <rect x="320" y="70" width="338" height="20" rx="3" fill="#f7f9fb"/>
  <text x="330" y="84" class="d2"><tspan class="k2">802.2</tspan>  LLC — control del enlace lógico</text>
  <rect x="320" y="92" width="338" height="20" rx="3" fill="#eef4fa"/>
  <text x="330" y="106" class="d2"><tspan class="k2">802.3</tspan>  Ethernet (CSMA/CD) — af/at/bt: PoE</text>
  <rect x="320" y="114" width="338" height="20" rx="3" fill="#f7f9fb"/>
  <text x="330" y="128" class="d2"><tspan class="k2">802.4</tspan>  Token Bus — anillo lógico sobre bus físico (MAP)</text>
  <rect x="320" y="136" width="338" height="20" rx="3" fill="#eef4fa"/>
  <text x="330" y="150" class="d2"><tspan class="k2">802.5</tspan>  Token Ring — 4 y 16 Mbit/s (IBM)</text>
  <rect x="320" y="158" width="338" height="20" rx="3" fill="#f7f9fb"/>
  <text x="330" y="172" class="d2"><tspan class="k2">802.11</tspan>  WLAN — Wi-Fi (CSMA/CA)</text>
  <rect x="320" y="180" width="338" height="20" rx="3" fill="#eef4fa"/>
  <text x="330" y="194" class="d2"><tspan class="k2">802.15</tspan>  WPAN — .1 Bluetooth · .4 base de Zigbee</text>
  <rect x="320" y="202" width="338" height="20" rx="3" fill="#f7f9fb"/>
  <text x="330" y="216" class="d2"><tspan class="k2">802.16</tspan>  WMAN — WiMAX (metropolitana, NO local)</text>
  <rect x="320" y="228" width="338" height="24" rx="3" fill="#fdf3e3"/>
  <text x="330" y="244" class="d2">FDDI <tspan class="r2">NO es IEEE</tspan>: es ANSI X3T9.5 / ISO 9314</text>

  <rect x="30" y="266" width="628" height="60" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="344" y="284" text-anchor="middle" class="k2">Por qué LLC cayó en desuso: Ethernet II resolvió lo mismo con el campo EtherType</text>
  <text x="344" y="300" text-anchor="middle" class="d2">Regla de desambiguación del campo de 2 octetos: si vale 1500 o menos es LONGITUD (trama 802.3);</text>
  <text x="344" y="315" text-anchor="middle" class="d2">si vale 1536 (0x0600) o más es TIPO (trama Ethernet II). Ganó Ethernet II: 0x0800 IPv4 · 0x0806 ARP · 0x86DD IPv6</text>

  <text x="670" y="360" text-anchor="end" class="n2">[Fuente: IEEE 802-2014 · IEEE 802.2 · ISO/IEC 7498-1]</text>
</svg>
```

---

## D3 · PAN, LAN, CAN, MAN y WAN: alcance, velocidad y titularidad

**Sección**: §2.1 — Clasificación según cobertura y alcance geográfico
**Propósito**: Ordenar la clasificación por alcance sobre una escala continua y, sobre todo, señalar dónde está la frontera que importa: la del **régimen de propiedad del medio**, que no coincide con ninguna cifra redonda de distancia.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Escala comparativa de redes por alcance: red de área personal hasta diez metros, red de área local hasta uno o dos kilómetros, red de campus de uno a diez kilómetros, red metropolitana de diez a cien kilómetros y red de área extensa por encima de cien kilómetros; la frontera relevante no es la distancia sino que el medio sea propio o de un operador">
  <style>.h3{font:700 13px system-ui,sans-serif;fill:#0055a0}.k3{font:700 10px system-ui,sans-serif;fill:#0055a0}.d3{font:9px system-ui,sans-serif;fill:#333}.n3{font:8.5px system-ui,sans-serif;fill:#666}.t3{font:700 11px system-ui,sans-serif;fill:#fff}.g3{font:700 9.5px system-ui,sans-serif;fill:#2d8659}.r3{font:700 9.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h3">Clasificación por alcance, y la frontera que de verdad importa</text>

  <rect x="24" y="42" width="104" height="44" rx="4" fill="#7fa8cc"/>
  <text x="76" y="60" text-anchor="middle" class="t3">PAN</text>
  <text x="76" y="76" text-anchor="middle" class="t3">hasta 10 m</text>
  <rect x="132" y="42" width="128" height="44" rx="4" fill="#0055a0"/>
  <text x="196" y="60" text-anchor="middle" class="t3">LAN</text>
  <text x="196" y="76" text-anchor="middle" class="t3">1-2 km · edificio</text>
  <rect x="264" y="42" width="120" height="44" rx="4" fill="#0055a0"/>
  <text x="324" y="60" text-anchor="middle" class="t3">CAN</text>
  <text x="324" y="76" text-anchor="middle" class="t3">1-10 km · campus</text>
  <rect x="388" y="42" width="128" height="44" rx="4" fill="#e89822"/>
  <text x="452" y="60" text-anchor="middle" class="t3">MAN</text>
  <text x="452" y="76" text-anchor="middle" class="t3">10-100 km · ciudad</text>
  <rect x="520" y="42" width="136" height="44" rx="4" fill="#d13c3c"/>
  <text x="588" y="60" text-anchor="middle" class="t3">WAN</text>
  <text x="588" y="76" text-anchor="middle" class="t3">&gt; 100 km · país</text>

  <path d="M24,98 L656,98" stroke="#666" stroke-width="1"/>
  <text x="30" y="112" class="n3">centímetros</text>
  <text x="650" y="112" text-anchor="end" class="n3">continentes</text>

  <rect x="24" y="122" width="360" height="26" rx="4" fill="#e6f2ec"/>
  <text x="204" y="139" text-anchor="middle" class="g3">MEDIO PROPIO — sin operador, sin contrato de servicio</text>
  <rect x="388" y="122" width="268" height="26" rx="4" fill="#fbeaea"/>
  <text x="522" y="139" text-anchor="middle" class="r3">MEDIO DE OPERADOR — contratado</text>

  <rect x="24" y="158" width="632" height="22" rx="3" fill="#eef4fa"/>
  <text x="34" y="173" class="d3"><tspan class="k3">Velocidad</tspan>   PAN: kbit/s a Mbit/s   ·   LAN y CAN: 1 a 100 Gbit/s   ·   MAN y WAN: la contratada, típicamente menor que la LAN</text>
  <rect x="24" y="182" width="632" height="22" rx="3" fill="#f7f9fb"/>
  <text x="34" y="197" class="d3"><tspan class="k3">Retardo</tspan>     LAN: microsegundos   ·   MAN: décimas de milisegundo   ·   WAN: milisegundos o decenas de milisegundos</text>
  <rect x="24" y="206" width="632" height="22" rx="3" fill="#eef4fa"/>
  <text x="34" y="221" class="d3"><tspan class="k3">Problema</tspan>    LAN: el ACCESO al medio compartido   ·   WAN: el ENCAMINAMIENTO entre nodos con enlaces punto a punto</text>
  <rect x="24" y="230" width="632" height="22" rx="3" fill="#f7f9fb"/>
  <text x="34" y="245" class="d3"><tspan class="k3">Derecho</tspan>     La red interior de un edificio no exige título habilitante; explotar una red pública que cruce el dominio público, sí</text>

  <rect x="24" y="262" width="632" height="42" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="280" text-anchor="middle" class="k3">La SAN no es una categoría de alcance sino de FUNCIÓN</text>
  <text x="340" y="296" text-anchor="middle" class="d3">Red especializada en el tráfico entre servidores y almacenamiento (Fibre Channel, iSCSI, NVMe-oF). Ver Tema 26</text>

  <text x="670" y="328" text-anchor="end" class="n3">[Fuente: Tanenbaum · Ley 11/2022]</text>
</svg>
```

---

## D4 · Las cuatro topologías básicas: fallo, cable y método de acceso

**Sección**: §2.2.1 — Topologías básicas
**Propósito**: Comparar las cuatro topologías por cinco criterios, dibujando cada una y anotando qué ocurre cuando se rompe un enlace, que es la diferencia más significativa.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 366" role="img" aria-label="Las cuatro topologías básicas dibujadas y comparadas: bus, con mínimo cable pero cuya rotura parte la red; estrella, con equipo central que es punto único de fallo pero fácil de diagnosticar; anillo, determinista pero que se rompe si cae un nodo salvo doble anillo; y malla, máxima tolerancia a fallos pero con un número de enlaces que crece con el cuadrado del número de nodos">
  <style>.h4{font:700 13px system-ui,sans-serif;fill:#0055a0}.k4{font:700 10px system-ui,sans-serif;fill:#0055a0}.d4{font:8.5px system-ui,sans-serif;fill:#333}.n4{font:8.5px system-ui,sans-serif;fill:#666}.g4{font:700 8.5px system-ui,sans-serif;fill:#2d8659}.r4{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h4">Las cuatro topologías básicas y qué pasa cuando algo se rompe</text>

  <rect x="22" y="32" width="152" height="128" rx="5" fill="#eef4fa"/>
  <text x="98" y="48" text-anchor="middle" class="k4">BUS</text>
  <path d="M38,80 L158,80" stroke="#0055a0" stroke-width="2.5"/>
  <path d="M38,74 L38,86 M158,74 L158,86" stroke="#333" stroke-width="2"/>
  <circle cx="60" cy="64" r="5" fill="#0055a0"/><path d="M60,69 L60,80" stroke="#666" stroke-width="1"/>
  <circle cx="90" cy="64" r="5" fill="#0055a0"/><path d="M90,69 L90,80" stroke="#666" stroke-width="1"/>
  <circle cx="120" cy="96" r="5" fill="#0055a0"/><path d="M120,91 L120,80" stroke="#666" stroke-width="1"/>
  <circle cx="145" cy="96" r="5" fill="#0055a0"/><path d="M145,91 L145,80" stroke="#666" stroke-width="1"/>
  <text x="98" y="118" text-anchor="middle" class="g4">Mínimo cable · sin nodo central</text>
  <text x="98" y="132" text-anchor="middle" class="r4">Una rotura PARTE la red en dos</text>
  <text x="98" y="146" text-anchor="middle" class="d4">10BASE5 500 m · 10BASE2 185 m</text>

  <rect x="182" y="32" width="152" height="128" rx="5" fill="#eef4fa"/>
  <text x="258" y="48" text-anchor="middle" class="k4">ESTRELLA</text>
  <rect x="246" y="76" width="24" height="16" rx="3" fill="#0055a0"/>
  <circle cx="212" cy="62" r="5" fill="#0055a0"/><path d="M216,66 L246,78" stroke="#666" stroke-width="1"/>
  <circle cx="304" cy="62" r="5" fill="#0055a0"/><path d="M300,66 L270,78" stroke="#666" stroke-width="1"/>
  <circle cx="212" cy="104" r="5" fill="#0055a0"/><path d="M216,101 L246,90" stroke="#666" stroke-width="1"/>
  <circle cx="304" cy="104" r="5" fill="#0055a0"/><path d="M300,101 L270,90" stroke="#666" stroke-width="1"/>
  <text x="258" y="118" text-anchor="middle" class="g4">Rotura: afecta solo a ese nodo</text>
  <text x="258" y="132" text-anchor="middle" class="r4">El centro: punto único de fallo</text>
  <text x="258" y="146" text-anchor="middle" class="d4">Topología física universal hoy</text>

  <rect x="342" y="32" width="152" height="128" rx="5" fill="#eef4fa"/>
  <text x="418" y="48" text-anchor="middle" class="k4">ANILLO</text>
  <circle cx="418" cy="80" r="24" fill="none" stroke="#0055a0" stroke-width="2.5"/>
  <circle cx="418" cy="56" r="5" fill="#0055a0"/>
  <circle cx="442" cy="80" r="5" fill="#0055a0"/>
  <circle cx="418" cy="104" r="5" fill="#0055a0"/>
  <circle cx="394" cy="80" r="5" fill="#0055a0"/>
  <text x="418" y="118" text-anchor="middle" class="g4">Determinista · retardo acotado</text>
  <text x="418" y="132" text-anchor="middle" class="r4">Un corte rompe el anillo</text>
  <text x="418" y="146" text-anchor="middle" class="d4">Token Ring · FDDI (doble anillo)</text>

  <rect x="502" y="32" width="156" height="128" rx="5" fill="#eef4fa"/>
  <text x="580" y="48" text-anchor="middle" class="k4">MALLA</text>
  <circle cx="546" cy="62" r="5" fill="#0055a0"/>
  <circle cx="614" cy="62" r="5" fill="#0055a0"/>
  <circle cx="546" cy="104" r="5" fill="#0055a0"/>
  <circle cx="614" cy="104" r="5" fill="#0055a0"/>
  <path d="M546,62 L614,62 M546,104 L614,104 M546,62 L546,104 M614,62 L614,104 M546,62 L614,104 M614,62 L546,104" stroke="#666" stroke-width="1"/>
  <text x="580" y="118" text-anchor="middle" class="g4">Máxima tolerancia a fallos</text>
  <text x="580" y="132" text-anchor="middle" class="r4" style="font-size:8px">Coste prohibitivo: n(n-1)/2 enlaces</text>
  <text x="580" y="146" text-anchor="middle" class="d4">Solo entre conmutadores de núcleo</text>

  <rect x="22" y="172" width="636" height="22" rx="3" fill="#f7f9fb"/>
  <text x="32" y="187" class="d4"><tspan class="k4">Cantidad de cable</tspan>      Bus: la menor   ·   Anillo: media   ·   Estrella: alta (un enlace por nodo)   ·   Malla completa: n(n-1)/2 enlaces</text>
  <rect x="22" y="196" width="636" height="22" rx="3" fill="#eef4fa"/>
  <text x="32" y="211" class="d4"><tspan class="k4">Añadir un nodo</tspan>       Bus: fácil pero interrumpe   ·   Estrella: conectar un cable   ·   Anillo: hay que abrir el anillo   ·   Malla: n-1 enlaces nuevos</text>
  <rect x="22" y="220" width="636" height="22" rx="3" fill="#f7f9fb"/>
  <text x="32" y="235" class="d4"><tspan class="k4">Diagnóstico</tspan>          Bus: difícil, no hay punto central   ·   Estrella: sencillo, todo pasa por el centro   ·   Anillo: por sectores</text>
  <rect x="22" y="244" width="636" height="22" rx="3" fill="#eef4fa"/>
  <text x="32" y="259" class="d4"><tspan class="k4">Método de acceso</tspan>     Bus: contienda (CSMA/CD)   ·   Anillo: paso de testigo   ·   Estrella conmutada: NINGUNO, no hay medio compartido</text>

  <rect x="22" y="272" width="636" height="48" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="290" text-anchor="middle" class="k4">El árbol o topología jerárquica es la que adopta un edificio real: estrellas colgando de estrellas</text>
  <text x="340" y="306" text-anchor="middle" class="d4">Un armario por planta (acceso) colgando de un armario principal (distribución). Coincide punto por punto con el cableado estructurado</text>

  <text x="670" y="354" text-anchor="end" class="n4">[Fuente: Tanenbaum · Stallings]</text>
</svg>
```

---

## D5 · Topología física frente a topología lógica: los tres casos

**Sección**: §2.2.2 — Topologías híbridas y estructuras jerárquicas
**Propósito**: Aislar la distinción central de la sección, con los tres casos canónicos enfrentados: el mismo dibujo de cableado puede esconder tres comportamientos completamente distintos.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 346" role="img" aria-label="Los tres casos en que la topología física y la lógica no coinciden: Ethernet con concentrador es estrella física y bus lógico con colisiones; Token Ring con unidad de acceso al medio es estrella física y anillo lógico; y Ethernet con conmutador es estrella física y punto a punto lógico, sin bus y sin colisiones">
  <style>.h5{font:700 13px system-ui,sans-serif;fill:#0055a0}.k5{font:700 10px system-ui,sans-serif;fill:#0055a0}.d5{font:8.5px system-ui,sans-serif;fill:#333}.n5{font:8.5px system-ui,sans-serif;fill:#666}.t5{font:700 10px system-ui,sans-serif;fill:#fff}.r5{font:700 9px system-ui,sans-serif;fill:#d13c3c}.g5{font:700 9px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="20" text-anchor="middle" class="h5">Topología FÍSICA (cómo está el cable) frente a topología LÓGICA (cómo circula la información)</text>
  <text x="340" y="37" text-anchor="middle" class="n5">Las tres columnas tienen el MISMO dibujo de cableado y tres comportamientos distintos</text>

  <rect x="22" y="48" width="204" height="150" rx="5" fill="#fbeaea"/>
  <text x="124" y="65" text-anchor="middle" class="k5">CONCENTRADOR (HUB)</text>
  <rect x="94" y="106" width="60" height="20" rx="3" fill="#d13c3c"/>
  <text x="124" y="120" text-anchor="middle" class="t5">HUB</text>
  <circle cx="52" cy="86" r="5" fill="#0055a0"/><path d="M56,90 L94,108" stroke="#666" stroke-width="1"/>
  <circle cx="196" cy="86" r="5" fill="#0055a0"/><path d="M192,90 L154,108" stroke="#666" stroke-width="1"/>
  <circle cx="52" cy="146" r="5" fill="#0055a0"/><path d="M56,142 L94,126" stroke="#666" stroke-width="1"/>
  <circle cx="196" cy="146" r="5" fill="#0055a0"/><path d="M192,142 L154,126" stroke="#666" stroke-width="1"/>
  <text x="124" y="170" text-anchor="middle" class="d5">Física: ESTRELLA</text>
  <text x="124" y="184" text-anchor="middle" class="r5">Lógica: BUS — hay colisiones</text>

  <rect x="238" y="48" width="204" height="150" rx="5" fill="#fdf3e3"/>
  <text x="340" y="65" text-anchor="middle" class="k5">TOKEN RING CON MAU</text>
  <ellipse cx="340" cy="116" rx="80" ry="38" fill="none" stroke="#e89822" stroke-width="1.6" stroke-dasharray="5,4"/>
  <rect x="310" y="106" width="60" height="20" rx="3" fill="#e89822"/>
  <text x="340" y="120" text-anchor="middle" class="t5">MAU</text>
  <circle cx="268" cy="86" r="5" fill="#0055a0"/><path d="M272,90 L310,108" stroke="#666" stroke-width="1"/>
  <circle cx="412" cy="86" r="5" fill="#0055a0"/><path d="M408,90 L370,108" stroke="#666" stroke-width="1"/>
  <circle cx="268" cy="146" r="5" fill="#0055a0"/><path d="M272,142 L310,126" stroke="#666" stroke-width="1"/>
  <circle cx="412" cy="146" r="5" fill="#0055a0"/><path d="M408,142 L370,126" stroke="#666" stroke-width="1"/>
  <text x="340" y="170" text-anchor="middle" class="d5">Física: ESTRELLA</text>
  <text x="340" y="184" text-anchor="middle" class="d5">Lógica: ANILLO — pasa el testigo</text>

  <rect x="454" y="48" width="204" height="150" rx="5" fill="#e6f2ec"/>
  <text x="556" y="65" text-anchor="middle" class="k5">CONMUTADOR (SWITCH)</text>
  <rect x="526" y="106" width="60" height="20" rx="3" fill="#2d8659"/>
  <text x="556" y="120" text-anchor="middle" class="t5">SWITCH</text>
  <circle cx="484" cy="86" r="5" fill="#0055a0"/><path d="M488,90 L526,108" stroke="#2d8659" stroke-width="1.8"/>
  <circle cx="628" cy="86" r="5" fill="#0055a0"/><path d="M624,90 L586,108" stroke="#2d8659" stroke-width="1.8"/>
  <circle cx="484" cy="146" r="5" fill="#0055a0"/><path d="M488,142 L526,126" stroke="#2d8659" stroke-width="1.8"/>
  <circle cx="628" cy="146" r="5" fill="#0055a0"/><path d="M624,142 L586,126" stroke="#2d8659" stroke-width="1.8"/>
  <text x="556" y="170" text-anchor="middle" class="d5">Física: ESTRELLA</text>
  <text x="556" y="184" text-anchor="middle" class="g5">Lógica: PUNTO A PUNTO — sin bus</text>

  <rect x="22" y="210" width="636" height="22" rx="3" fill="#f7f9fb"/>
  <text x="32" y="225" class="d5"><tspan class="k5">Dominios de colisión</tspan>     Concentrador: UNO para todos   ·   MAU: no hay colisiones (testigo)   ·   Conmutador: UNO POR PUERTO</text>
  <rect x="22" y="234" width="636" height="22" rx="3" fill="#eef4fa"/>
  <text x="32" y="249" class="d5"><tspan class="k5">Ancho de banda</tspan>          Concentrador: COMPARTIDO entre los puertos   ·   Conmutador: DEDICADO por puerto, y en dúplex</text>

  <rect x="22" y="266" width="636" height="46" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="284" text-anchor="middle" class="k5">El concentrador NO cambió la topología lógica, solo el cableado</text>
  <text x="340" y="300" text-anchor="middle" class="d5">Fue el CONMUTADOR el que acabó con el bus lógico y, con él, con las colisiones y con CSMA/CD</text>

  <text x="670" y="334" text-anchor="end" class="n5">[Fuente: IEEE 802.3 · IEEE 802.5 · Kurose]</text>
</svg>
```

---

## D6 · Modos de transmisión: sentido, número de líneas y sincronismo

**Sección**: §3.1 — Modos y sentidos de transmisión de datos
**Propósito**: Separar las tres clasificaciones que suelen mezclarse y subrayar la consecuencia que arrastra la primera: **el método de acceso solo hace falta en semidúplex sobre medio compartido**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 352" role="img" aria-label="Tres clasificaciones independientes de los modos de transmisión: por sentido en símplex, semidúplex y dúplex; por número de líneas en serie y paralelo; y por sincronismo en asíncrona, síncrona e isócrona; la consecuencia clave es que el método de acceso al medio solo hace falta cuando la transmisión es semidúplex sobre medio compartido">
  <style>.h6{font:700 13px system-ui,sans-serif;fill:#0055a0}.k6{font:700 10px system-ui,sans-serif;fill:#0055a0}.d6{font:8.5px system-ui,sans-serif;fill:#333}.n6{font:8.5px system-ui,sans-serif;fill:#666}.g6{font:700 9px system-ui,sans-serif;fill:#2d8659}.r6{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <defs><marker id="m6" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker><marker id="m6g" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#999"/></marker><marker id="m6v" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#2d8659"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h6">Tres clasificaciones independientes que no hay que mezclar</text>

  <text x="112" y="42" text-anchor="middle" class="k6">1 · SEGÚN EL SENTIDO</text>
  <rect x="22" y="50" width="180" height="46" rx="4" fill="#eef4fa"/>
  <text x="32" y="66" class="d6">SÍMPLEX — un solo sentido</text>
  <path d="M40,80 L150,80" stroke="#0055a0" stroke-width="1.8" marker-end="url(#m6)"/>
  <text x="32" y="92" class="n6">Radiodifusión · sensor a central</text>
  <rect x="22" y="100" width="180" height="46" rx="4" fill="#fdf3e3"/>
  <text x="32" y="116" class="d6">SEMIDÚPLEX — alternando</text>
  <path d="M40,124 L150,124" stroke="#0055a0" stroke-width="1.8" marker-end="url(#m6)"/>
  <path d="M150,131 L40,131" stroke="#999" stroke-width="1.8" stroke-dasharray="4,3" marker-end="url(#m6g)"/>
  <text x="32" y="143" class="n6">Por turnos · walkie-talkie · hub · WI-FI</text>
  <rect x="22" y="150" width="180" height="46" rx="4" fill="#e6f2ec"/>
  <text x="32" y="166" class="d6">DÚPLEX — los dos a la vez</text>
  <path d="M40,174 L150,174" stroke="#0055a0" stroke-width="1.8" marker-end="url(#m6)"/>
  <path d="M150,181 L40,181" stroke="#2d8659" stroke-width="1.8" marker-end="url(#m6v)"/>
  <text x="32" y="193" class="n6">A la vez · ETHERNET CONMUTADA</text>

  <text x="340" y="42" text-anchor="middle" class="k6">2 · SEGÚN LAS LÍNEAS</text>
  <rect x="216" y="50" width="180" height="70" rx="4" fill="#eef4fa"/>
  <text x="226" y="66" class="d6">SERIE — bits uno tras otro</text>
  <path d="M234,80 L380,80" stroke="#0055a0" stroke-width="1.6"/>
  <text x="226" y="96" class="n6">Menos conductores, sin desfase</text>
  <text x="226" y="110" class="g6">TODA RED LOCAL ES SERIE</text>
  <rect x="216" y="124" width="180" height="72" rx="4" fill="#fbeaea"/>
  <text x="226" y="140" class="d6">PARALELO — varios bits a la vez</text>
  <path d="M234,152 L380,152 M234,160 L380,160 M234,168 L380,168" stroke="#d13c3c" stroke-width="1.2"/>
  <text x="226" y="182" class="n6">Desfase entre líneas y diafonía</text>
  <text x="226" y="192" class="n6">Descartado incluso en buses internos</text>

  <text x="556" y="42" text-anchor="middle" class="k6">3 · SEGÚN EL SINCRONISMO</text>
  <rect x="410" y="50" width="248" height="46" rx="4" fill="#eef4fa"/>
  <text x="420" y="66" class="d6">ASÍNCRONA — carácter a carácter</text>
  <text x="420" y="80" class="n6">Bit de arranque y de parada. De 10 bits, 8 útiles:</text>
  <text x="420" y="91" class="n6">un 20 % de sobrecarga. Puerto serie clásico</text>
  <rect x="410" y="100" width="248" height="52" rx="4" fill="#e6f2ec"/>
  <text x="420" y="116" class="d6">SÍNCRONA — por bloques o tramas</text>
  <text x="420" y="130" class="n6">Reloj común, o extraído de la propia señal por un</text>
  <text x="420" y="141" class="n6">código de línea autosincronizante (ver D8)</text>
  <rect x="410" y="156" width="248" height="40" rx="4" fill="#fdf3e3"/>
  <text x="420" y="172" class="d6">ISÓCRONA — retardo constante</text>
  <text x="420" y="186" class="n6">Garantía de plazo entre unidades: voz y vídeo</text>

  <rect x="22" y="212" width="636" height="24" rx="3" fill="#f7f9fb"/>
  <text x="340" y="228" text-anchor="middle" class="d6">1000BASE-T usa los CUATRO PARES a la vez y aun así NO es transmisión paralelo: multiplexa un flujo serie sobre cuatro canales serie</text>

  <rect x="22" y="248" width="636" height="66" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="266" text-anchor="middle" class="k6">La consecuencia que vertebra el tema entero</text>
  <text x="340" y="282" text-anchor="middle" class="d6">El MÉTODO DE ACCESO AL MEDIO solo hace falta cuando la transmisión es SEMIDÚPLEX sobre MEDIO COMPARTIDO</text>
  <text x="340" y="297" text-anchor="middle" class="g6">Enlace dúplex punto a punto = no hay con quién colisionar = CSMA/CD se desactiva</text>
  <text x="340" y="309" text-anchor="middle" class="r6">La radio no puede transmitir y recibir a la vez: Wi-Fi sigue siendo semidúplex y conserva íntegro el problema</text>

  <text x="670" y="340" text-anchor="end" class="n6">[Fuente: Stallings · IEEE 802.3 · IEEE 802.11]</text>
</svg>
```

---

## D7 · Banda base frente a banda ancha

**Sección**: §3.2 — Transmisión en banda base y banda ancha
**Propósito**: Enfrentar las dos modalidades por sus cinco diferencias y desactivar la confusión con el sentido comercial de «banda ancha», señalando además la única Ethernet de banda ancha que llegó a normalizarse y nunca se implantó.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 346" role="img" aria-label="Comparación entre transmisión en banda base, en la que la señal digital se transmite sin modular ocupando todo el ancho de banda del medio en un único canal bidireccional, propia de Ethernet, y transmisión en banda ancha, en la que la señal modula una portadora y el medio se reparte en varios canales unidireccionales por división de frecuencia, propia de la televisión por cable y de DSL">
  <style>.h7{font:700 13px system-ui,sans-serif;fill:#0055a0}.k7{font:700 10.5px system-ui,sans-serif;fill:#0055a0}.d7{font:8.5px system-ui,sans-serif;fill:#333}.n7{font:8.5px system-ui,sans-serif;fill:#666}.t7{font:700 10.5px system-ui,sans-serif;fill:#fff}.r7{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h7">Banda base frente a banda ancha</text>

  <rect x="22" y="34" width="312" height="24" rx="4" fill="#0055a0"/>
  <text x="178" y="51" text-anchor="middle" class="t7">BANDA BASE — partícula BASE</text>
  <rect x="346" y="34" width="312" height="24" rx="4" fill="#e89822"/>
  <text x="502" y="51" text-anchor="middle" class="t7">BANDA ANCHA — partícula BROAD</text>

  <rect x="22" y="62" width="312" height="62" rx="4" fill="#eef4fa"/>
  <text x="32" y="78" class="d7">La señal digital se transmite TAL CUAL, sin portadora</text>
  <path d="M40,98 L60,98 L60,86 L88,86 L88,98 L112,98 L112,86 L140,86 L140,98 L170,98" fill="none" stroke="#0055a0" stroke-width="1.8"/>
  <text x="190" y="94" class="n7">Solo una codificación de línea</text>
  <text x="190" y="106" class="n7">convierte bits en niveles (ver D8)</text>
  <text x="32" y="118" class="n7">Ocupa TODO el ancho de banda del medio</text>

  <rect x="346" y="62" width="312" height="62" rx="4" fill="#fdf3e3"/>
  <text x="356" y="78" class="d7">La señal digital MODULA una portadora de alta frecuencia</text>
  <path d="M362,98 q6,-12 12,0 q6,12 12,0 q6,-12 12,0 q6,12 12,0 q6,-12 12,0 q6,12 12,0" fill="none" stroke="#e89822" stroke-width="1.8"/>
  <text x="452" y="94" class="n7">Ocupa solo UNA banda del espectro:</text>
  <text x="452" y="106" class="n7">las demás quedan libres para otros canales</text>
  <text x="356" y="118" class="n7">Multiplexación por división de frecuencia (FDM)</text>

  <rect x="22" y="130" width="636" height="21" rx="3" fill="#f7f9fb"/>
  <text x="32" y="145" class="d7"><tspan class="k7">Canales</tspan>            UNO solo por medio                                    ·   VARIOS simultáneos, cada uno con su portadora</text>
  <rect x="22" y="153" width="636" height="21" rx="3" fill="#eef4fa"/>
  <text x="32" y="168" class="d7"><tspan class="k7">Sentido</tspan>            BIDIRECCIONAL por naturaleza                     ·   UNIDIRECCIONAL por canal: la amplificación es direccional</text>
  <rect x="22" y="176" width="636" height="21" rx="3" fill="#f7f9fb"/>
  <text x="32" y="191" class="d7"><tspan class="k7">Distancia</tspan>          Limitada: exige regeneración periódica          ·   Mayor alcance con la misma calidad</text>
  <rect x="22" y="199" width="636" height="21" rx="3" fill="#eef4fa"/>
  <text x="32" y="214" class="d7"><tspan class="k7">Equipo terminal</tspan>    Sencillo y barato                                        ·   Más complejo y caro: hace falta módem y cabecera</text>
  <rect x="22" y="222" width="636" height="21" rx="3" fill="#f7f9fb"/>
  <text x="32" y="237" class="d7"><tspan class="k7">Dónde está</tspan>         TODA la familia ETHERNET (10BASE-T…)          ·   Televisión por cable, DOCSIS, ADSL/VDSL y, en radio, Wi-Fi</text>

  <rect x="22" y="256" width="636" height="52" rx="5" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <text x="340" y="274" text-anchor="middle" class="r7">La trampa recurrente</text>
  <text x="340" y="290" text-anchor="middle" class="d7">La única Ethernet de banda ancha que llegó a normalizarse fue 10BROAD36, y NUNCA SE IMPLANTÓ.</text>
  <text x="340" y="303" text-anchor="middle" class="d7">Toda Ethernet real es de banda base. No confundir con el sentido comercial de «banda ancha» = conexión rápida a internet</text>

  <text x="670" y="334" text-anchor="end" class="n7">[Fuente: Stallings · IEEE 802.3]</text>
</svg>
```

---

## D8 · Códigos de línea de las redes locales

**Sección**: §3.3 — Técnicas de modulación y codificación de señal
**Propósito**: Dibujar la misma secuencia de bits codificada de tres formas distintas para que se vea de un golpe el compromiso central: **Manchester autosincroniza siempre, pero a costa de duplicar las transiciones**; MLT-3 y los códigos en bloque nacieron para evitar ese coste.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="La secuencia de bits uno cero uno uno cero cero uno cero representada en tres códigos de línea: NRZ, que mantiene un nivel por bit y no autosincroniza; Manchester, con transición obligatoria en la mitad de cada bit, que siempre autosincroniza pero duplica las transiciones; y MLT-3, con tres niveles recorridos cíclicamente, que reduce mucho la frecuencia de la señal; abajo, tabla de los códigos usados en cada variante de Ethernet">
  <style>.h8{font:700 13px system-ui,sans-serif;fill:#0055a0}.k8{font:700 10px system-ui,sans-serif;fill:#0055a0}.d8{font:8.5px system-ui,sans-serif;fill:#333}.n8{font:8.5px system-ui,sans-serif;fill:#666}.b8{font:700 9px system-ui,sans-serif;fill:#0055a0}.g8{font:700 9px system-ui,sans-serif;fill:#2d8659}.r8{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h8">La misma secuencia de bits en tres códigos de línea</text>
  <text x="340" y="37" text-anchor="middle" class="n8">Lo que se pide a un buen código: sin componente continua, autosincronizante y con pocas transiciones por bit</text>

  <text x="200" y="54" text-anchor="middle" class="b8">1</text>
  <text x="240" y="54" text-anchor="middle" class="b8">0</text>
  <text x="280" y="54" text-anchor="middle" class="b8">1</text>
  <text x="320" y="54" text-anchor="middle" class="b8">1</text>
  <text x="360" y="54" text-anchor="middle" class="b8">0</text>
  <text x="400" y="54" text-anchor="middle" class="b8">0</text>
  <text x="440" y="54" text-anchor="middle" class="b8">1</text>
  <text x="480" y="54" text-anchor="middle" class="b8">0</text>
  <path d="M180,58 L180,176 M220,58 L220,176 M260,58 L260,176 M300,58 L300,176 M340,58 L340,176 M380,58 L380,176 M420,58 L420,176 M460,58 L460,176 M500,58 L500,176" stroke="#ccc" stroke-width="0.8" stroke-dasharray="3,3"/>

  <text x="24" y="76" class="k8">NRZ</text>
  <text x="24" y="88" class="n8">un nivel por bit</text>
  <path d="M180,66 H220 V82 H260 V66 H340 V82 H420 V66 H460 V82 H500" fill="none" stroke="#0055a0" stroke-width="2"/>
  <text x="516" y="72" class="r8">NO autosincroniza</text>
  <text x="516" y="84" class="n8">Una cadena larga de bits</text>
  <text x="516" y="95" class="n8">iguales despista al receptor</text>

  <text x="24" y="116" class="k8">MANCHESTER</text>
  <text x="24" y="128" class="n8">transición central</text>
  <path d="M180,122 H200 V106 H240 V122 H280 V106 H300 V122 H320 V106 H360 V122 H380 V106 H400 V122 H440 V106 H480 V122 H500" fill="none" stroke="#2d8659" stroke-width="2"/>
  <text x="516" y="112" class="g8">SIEMPRE autosincroniza</text>
  <text x="516" y="124" class="n8">Precio: dos transiciones por</text>
  <text x="516" y="135" class="n8">bit, doble ancho de banda</text>

  <text x="24" y="156" class="k8">MLT-3</text>
  <text x="24" y="168" class="n8">tres niveles</text>
  <path d="M180,146 H260 V158 H300 V170 H420 V158 H500" fill="none" stroke="#e89822" stroke-width="2"/>
  <path d="M170,146 L510,146 M170,158 L510,158 M170,170 L510,170" stroke="#ddd" stroke-width="0.6"/>
  <text x="512" y="152" class="d8">Transición al nivel siguiente</text>
  <text x="512" y="164" class="d8">si el bit es 1; ninguna si 0</text>
  <text x="512" y="176" class="n8">Ciclo 0,+1,0,-1 · 100BASE-TX</text>

  <rect x="22" y="190" width="636" height="18" rx="3" fill="#0055a0"/>
  <text x="32" y="203" style="fill:#fff" class="d8">CÓDIGO</text>
  <text x="150" y="203" style="fill:#fff" class="d8">CÓMO FUNCIONA</text>
  <text x="470" y="203" style="fill:#fff" class="d8">DÓNDE SE USA</text>
  <rect x="22" y="209" width="636" height="17" rx="0" fill="#f7f9fb"/>
  <text x="32" y="221" class="d8">NRZI</text>
  <text x="150" y="221" class="d8">Hay transición para el 1 y no la hay para el 0 (diferencial)</text>
  <text x="470" y="221" class="d8">100BASE-FX (con 4B/5B) · USB</text>
  <rect x="22" y="227" width="636" height="17" fill="#eef4fa"/>
  <text x="32" y="239" class="d8">Manchester dif.</text>
  <text x="150" y="239" class="d8">Transición central siempre; el bit se codifica al inicio</text>
  <text x="470" y="239" class="d8">Token Ring (802.5)</text>
  <rect x="22" y="245" width="636" height="17" fill="#f7f9fb"/>
  <text x="32" y="257" class="d8">4B/5B</text>
  <text x="150" y="257" class="d8">Cada 4 bits se sustituyen por 5, sin más de 3 ceros seguidos</text>
  <text x="470" y="257" class="d8">100BASE-TX y FX · FDDI</text>
  <rect x="22" y="263" width="636" height="17" fill="#eef4fa"/>
  <text x="32" y="275" class="d8">8B/10B</text>
  <text x="150" y="275" class="d8">Cada 8 bits en 10, equilibrando unos y ceros. Coste 25 %</text>
  <text x="470" y="275" class="d8">1000BASE-X (fibra) · Fibre Channel</text>
  <rect x="22" y="281" width="636" height="17" fill="#f7f9fb"/>
  <text x="32" y="293" class="d8">4D-PAM5</text>
  <text x="150" y="293" class="d8">Cinco niveles de amplitud por los CUATRO PARES a la vez</text>
  <text x="470" y="293" class="d8">1000BASE-T</text>
  <rect x="22" y="299" width="636" height="17" fill="#eef4fa"/>
  <text x="32" y="311" class="d8">64B/66B</text>
  <text x="150" y="311" class="d8">Cada 64 bits en 66: solo un 3,125 % de sobrecarga</text>
  <text x="470" y="311" class="d8">10GBASE-R y superiores</text>

  <text x="340" y="336" text-anchor="middle" class="k8">Fórmula que hay que llevar memorizada:  Vt (bit/s) = Vm (baudios) × log2(n)   ·   n = número de niveles del símbolo</text>
  <text x="340" y="350" text-anchor="middle" class="n8">Es la razón por la que 1000BASE-T alcanza 1 Gbit/s sobre un cable certificado solo hasta 100 MHz</text>

  <text x="670" y="366" text-anchor="end" class="n8">[Fuente: Stallings · IEEE 802.3]</text>
</svg>
```

---

## D9 · Las cinco técnicas de multiplexación

**Sección**: §3.4 — Técnicas de multiplexación de canales
**Propósito**: Representar el reparto del medio que hace cada técnica y, con ello, dejar clara la frontera con el capítulo siguiente: **multiplexar es repartir de forma planificada; acceder al medio es arbitrar una contienda imprevisible**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 384" role="img" aria-label="Las cinco técnicas de multiplexación representadas sobre un plano de tiempo y frecuencia: división de frecuencia, división de tiempo en sus variantes síncrona y estadística, división de longitud de onda sobre fibra, división de código y división de frecuencias ortogonales con su versión de acceso múltiple OFDMA, que es la novedad de Wi-Fi 6">
  <style>.h9{font:700 13px system-ui,sans-serif;fill:#0055a0}.k9{font:700 10px system-ui,sans-serif;fill:#0055a0}.d9{font:8.5px system-ui,sans-serif;fill:#333}.n9{font:8px system-ui,sans-serif;fill:#666}.w9{font:700 8px system-ui,sans-serif;fill:#fff}.g9{font:700 9px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="20" text-anchor="middle" class="h9">Las cinco técnicas de multiplexación: cómo reparten el medio</text>

  <text x="120" y="42" text-anchor="middle" class="k9">FDM · por FRECUENCIA</text>
  <rect x="26" y="50" width="188" height="76" rx="4" fill="#eef4fa"/>
  <rect x="36" y="58" width="168" height="14" fill="#0055a0"/><text x="120" y="69" text-anchor="middle" class="w9">CANAL A</text>
  <rect x="36" y="76" width="168" height="6" fill="#ccc"/>
  <rect x="36" y="86" width="168" height="14" fill="#3d82c4"/><text x="120" y="97" text-anchor="middle" class="w9">CANAL B</text>
  <rect x="36" y="104" width="168" height="6" fill="#ccc"/>
  <rect x="36" y="112" width="168" height="10" fill="#7fa8cc"/>
  <text x="222" y="66" class="n9">Subbandas</text>
  <text x="222" y="78" class="n9">de frecuencia</text>
  <text x="222" y="90" class="n9">separadas por</text>
  <text x="222" y="102" class="n9">bandas de guarda.</text>
  <text x="222" y="114" class="n9">Simultáneas y</text>
  <text x="222" y="126" class="n9">continuas</text>

  <text x="420" y="42" text-anchor="middle" class="k9">TDM · por TIEMPO</text>
  <rect x="316" y="50" width="188" height="76" rx="4" fill="#eef4fa"/>
  <rect x="326" y="58" width="40" height="26" fill="#0055a0"/><text x="346" y="75" text-anchor="middle" class="w9">A</text>
  <rect x="368" y="58" width="40" height="26" fill="#3d82c4"/><text x="388" y="75" text-anchor="middle" class="w9">B</text>
  <rect x="410" y="58" width="40" height="26" fill="#7fa8cc"/><text x="430" y="75" text-anchor="middle" class="w9">C</text>
  <rect x="452" y="58" width="40" height="26" fill="#0055a0"/><text x="472" y="75" text-anchor="middle" class="w9">A</text>
  <text x="326" y="98" class="n9">SÍNCRONA: ranura fija reservada</text>
  <rect x="326" y="104" width="40" height="16" fill="#e89822"/><text x="346" y="116" text-anchor="middle" class="w9">A</text>
  <rect x="368" y="104" width="60" height="16" fill="#e89822"/><text x="398" y="116" text-anchor="middle" class="w9">C</text>
  <rect x="430" y="104" width="62" height="16" fill="#e89822"/><text x="461" y="116" text-anchor="middle" class="w9">A</text>
  <text x="512" y="112" class="n9">ESTADÍSTICA:</text>
  <text x="512" y="123" class="n9">solo a quien</text>
  <text x="512" y="134" class="n9">tiene datos</text>

  <text x="120" y="150" text-anchor="middle" class="k9">WDM · por LONGITUD DE ONDA</text>
  <rect x="26" y="158" width="188" height="52" rx="4" fill="#eef4fa"/>
  <path d="M40,172 L200,172" stroke="#d13c3c" stroke-width="2.4"/>
  <path d="M40,182 L200,182" stroke="#2d8659" stroke-width="2.4"/>
  <path d="M40,192 L200,192" stroke="#0055a0" stroke-width="2.4"/>
  <text x="40" y="205" class="n9">Varios «colores» por la MISMA fibra</text>
  <text x="222" y="172" class="n9">Es FDM aplicada</text>
  <text x="222" y="184" class="n9">a la fibra óptica.</text>
  <text x="222" y="196" class="n9">CWDM pocos canales,</text>
  <text x="222" y="208" class="n9">DWDM decenas</text>

  <text x="420" y="150" text-anchor="middle" class="k9">CDM · por CÓDIGO</text>
  <rect x="316" y="158" width="188" height="52" rx="4" fill="#eef4fa"/>
  <rect x="326" y="166" width="166" height="30" fill="#7fa8cc"/>
  <text x="409" y="185" text-anchor="middle" class="w9">TODOS a la vez, en TODA la banda</text>
  <text x="326" y="206" class="n9">Cada uno con su código ortogonal</text>
  <text x="512" y="172" class="n9">El receptor</text>
  <text x="512" y="184" class="n9">correla con su</text>
  <text x="512" y="196" class="n9">código; el resto</text>
  <text x="512" y="208" class="n9">le suena a ruido</text>

  <text x="150" y="232" text-anchor="middle" class="k9">OFDM / OFDMA · FRECUENCIAS ORTOGONALES</text>
  <rect x="26" y="240" width="478" height="42" rx="4" fill="#e6f2ec"/>
  <rect x="36" y="248" width="60" height="26" fill="#0055a0"/><text x="66" y="265" text-anchor="middle" class="w9">EST. 1</text>
  <rect x="100" y="248" width="30" height="26" fill="#2d8659"/><text x="115" y="265" text-anchor="middle" class="w9">2</text>
  <rect x="134" y="248" width="90" height="26" fill="#3d82c4"/><text x="179" y="265" text-anchor="middle" class="w9">ESTACIÓN 3</text>
  <rect x="228" y="248" width="45" height="26" fill="#e89822"/><text x="250" y="265" text-anchor="middle" class="w9">EST. 4</text>
  <rect x="277" y="248" width="70" height="26" fill="#7fa8cc"/><text x="312" y="265" text-anchor="middle" class="w9">ESTACIÓN 5</text>
  <rect x="351" y="248" width="143" height="26" fill="#c9d6e2"/><text x="422" y="265" text-anchor="middle" class="w9" style="fill:#33475b">UNIDADES DE RECURSO LIBRES</text>
  <text x="512" y="252" class="g9">La novedad real</text>
  <text x="512" y="264" class="n9">de Wi-Fi 6: atiende</text>
  <text x="512" y="276" class="n9">a muchos clientes</text>
  <text x="512" y="288" class="n9">pequeños A LA VEZ</text>

  <rect x="26" y="300" width="632" height="48" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="342" y="320" text-anchor="middle" class="k9">Frontera con la sección 4: MULTIPLEXAR reparte de forma planificada</text>
  <text x="342" y="336" text-anchor="middle" class="d9">ACCEDER AL MEDIO arbitra una contienda imprevisible entre estaciones que compiten</text>

  <text x="670" y="372" text-anchor="end" class="n9">[Fuente: Stallings · IEEE 802.11ax]</text>
</svg>
```

---

## D10 · Medios guiados: par trenzado, coaxial y fibra

**Sección**: §3.5.1 — Cableado de par trenzado, fibra óptica y coaxial
**Propósito**: Reunir en una sola lámina la sección de los tres medios, la nomenclatura del apantallamiento y la correspondencia entre **categorías de componente** y **clases de enlace**, que es la pareja que más se confunde.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 390" role="img" aria-label="Los tres medios guiados de una red local: par trenzado con su nomenclatura de apantallamiento y su tabla de categorías y clases desde Cat 5e clase D hasta Cat 8.1 clase I; cable coaxial, retirado de las redes locales y superviviente en la distribución de televisión; y fibra óptica en sus dos variantes multimodo para el troncal del edificio y monomodo para el enlace entre edificios">
  <style>.h10{font:700 13px system-ui,sans-serif;fill:#0055a0}.k10{font:700 10px system-ui,sans-serif;fill:#0055a0}.d10{font:8.5px system-ui,sans-serif;fill:#333}.n10{font:8px system-ui,sans-serif;fill:#666}.w10{font:700 8.5px system-ui,sans-serif;fill:#fff}.g10{font:700 8.5px system-ui,sans-serif;fill:#2d8659}.r10{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h10">Los tres medios guiados y su nomenclatura</text>

  <rect x="22" y="32" width="206" height="126" rx="5" fill="#eef4fa"/>
  <text x="125" y="48" text-anchor="middle" class="k10">PAR TRENZADO</text>
  <path d="M40,62 q10,-8 20,0 q10,8 20,0 q10,-8 20,0 q10,8 20,0 q10,-8 20,0" fill="none" stroke="#0055a0" stroke-width="1.6"/>
  <path d="M40,62 q10,8 20,0 q10,-8 20,0 q10,8 20,0 q10,-8 20,0 q10,8 20,0" fill="none" stroke="#d13c3c" stroke-width="1.6"/>
  <text x="152" y="65" class="n10">Cuatro pares</text>
  <text x="32" y="82" class="d10">El trenzado cancela la interferencia y</text>
  <text x="32" y="93" class="d10">reduce la diafonía entre pares</text>
  <text x="32" y="107" class="g10">A más trenzas por metro, más categoría</text>
  <text x="32" y="123" class="d10">U/UTP no apantallado · F/UTP lámina</text>
  <text x="32" y="134" class="d10">S/FTP trenza global y lámina por par</text>
  <text x="32" y="149" class="r10">Apantallado: TIERRA en los dos extremos</text>

  <rect x="236" y="32" width="206" height="126" rx="5" fill="#fbeaea"/>
  <text x="339" y="48" text-anchor="middle" class="k10">CABLE COAXIAL</text>
  <circle cx="290" cy="88" r="26" fill="none" stroke="#333" stroke-width="1.4"/>
  <circle cx="290" cy="88" r="19" fill="none" stroke="#999" stroke-width="1.4"/>
  <circle cx="290" cy="88" r="12" fill="#eee" stroke="#ccc" stroke-width="1"/>
  <circle cx="290" cy="88" r="3.5" fill="#d13c3c"/>
  <text x="324" y="74" class="n10">Conductor central</text>
  <text x="324" y="86" class="n10">Dieléctrico</text>
  <text x="324" y="98" class="n10">Malla conductora</text>
  <text x="324" y="110" class="n10">Cubierta</text>
  <text x="246" y="130" class="r10">RETIRADO de las redes locales</text>
  <text x="246" y="144" class="d10">Sobrevive en televisión (RG-6), en las ICT</text>
  <text x="246" y="154" class="d10">del edificio y en el acceso DOCSIS</text>

  <rect x="450" y="32" width="208" height="126" rx="5" fill="#e6f2ec"/>
  <text x="554" y="48" text-anchor="middle" class="k10">FIBRA ÓPTICA</text>
  <rect x="462" y="62" width="184" height="18" rx="9" fill="#cfe3d8"/>
  <rect x="462" y="68" width="184" height="6" fill="#2d8659"/>
  <path d="M470,71 L500,66 L530,76 L560,66 L590,76 L620,71" fill="none" stroke="#e89822" stroke-width="1.2"/>
  <text x="460" y="93" class="n10">Reflexión total interna: la luz queda confinada</text>
  <text x="460" y="109" class="g10">MULTIMODO 50 o 62,5 µm · LED o VCSEL</text>
  <text x="460" y="120" class="n10">Cientos de metros. Troncal DENTRO del edificio</text>
  <text x="460" y="136" class="g10">MONOMODO 8-10 µm · láser</text>
  <text x="460" y="147" class="n10">Decenas de km. ENTRE edificios y operador</text>

  <text x="340" y="180" text-anchor="middle" class="k10">CATEGORÍA (de los componentes)  frente a  CLASE (del enlace instalado y medido)</text>
  <rect x="22" y="188" width="636" height="17" fill="#0055a0"/>
  <text x="32" y="200" class="w10">CATEGORÍA</text>
  <text x="130" y="200" class="w10">CLASE</text>
  <text x="210" y="200" class="w10">FRECUENCIA</text>
  <text x="320" y="200" class="w10">APLICACIÓN TÍPICA</text>
  <rect x="22" y="206" width="636" height="17" fill="#f7f9fb"/>
  <text x="32" y="218" class="d10">Cat 5e</text><text x="130" y="218" class="d10">D</text><text x="210" y="218" class="d10">100 MHz</text><text x="320" y="218" class="d10">1000BASE-T · 2.5GBASE-T</text>
  <rect x="22" y="224" width="636" height="17" fill="#eef4fa"/>
  <text x="32" y="236" class="d10">Cat 6</text><text x="130" y="236" class="d10">E</text><text x="210" y="236" class="d10">250 MHz</text><text x="320" y="236" class="d10">1000BASE-T · 10GBASE-T SOLO HASTA 55 m</text>
  <rect x="22" y="242" width="636" height="17" fill="#cfe3d8"/>
  <text x="32" y="254" class="d10">Cat 6A</text><text x="130" y="254" class="d10">EA</text><text x="210" y="254" class="d10">500 MHz</text><text x="320" y="254" class="d10">10GBASE-T a 100 m — ES EL ESTÁNDAR DE OBRA NUEVA</text>
  <rect x="22" y="260" width="636" height="17" fill="#f7f9fb"/>
  <text x="32" y="272" class="d10">Cat 7 / 7A</text><text x="130" y="272" class="d10">F / FA</text><text x="210" y="272" class="d10">600 / 1000 MHz</text><text x="320" y="272" class="d10">Conector no RJ-45 (GG45, TERA). Poca implantación</text>
  <rect x="22" y="278" width="636" height="17" fill="#eef4fa"/>
  <text x="32" y="290" class="d10">Cat 8.1</text><text x="130" y="290" class="d10">I</text><text x="210" y="290" class="d10">2000 MHz</text><text x="320" y="290" class="d10">25 y 40 Gbit/s a 30 m. Centro de proceso de datos</text>

  <rect x="22" y="306" width="636" height="48" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="326" text-anchor="middle" class="k10">Parámetros que se miden al certificar el cableado instalado</text>
  <text x="340" y="342" text-anchor="middle" class="d10">Atenuación · NEXT y PSNEXT · ACR-F · pérdida de retorno · retardo de propagación y diferencia de retardo entre pares</text>

  <text x="670" y="378" text-anchor="end" class="n10">[Fuente: ISO/IEC 11801-1:2017 · EN 50173]</text>
</svg>
```

---

## D11 · El espectro de las redes locales inalámbricas

**Sección**: §3.5.2 — Espectro radioeléctrico y transmisión inalámbrica
**Propósito**: Explicar de una vez el dato de los **tres canales sin solape en 2,4 GHz** y añadir el marco jurídico que casi ningún temario recoge: el régimen de **uso común** del dominio público radioeléctrico del artículo 88 de la Ley 11/2022.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 352" role="img" aria-label="Las tres bandas de las redes locales inalámbricas: 2,4 gigahercios, estrecha y muy interferida, con solo tres canales que no se solapan, el 1, el 6 y el 11; 5 gigahercios, ancha y con obligación de selección dinámica de frecuencia en algunas subbandas; y 6 gigahercios, la más limpia, abierta para Wi-Fi 6E y Wi-Fi 7; abajo, el régimen jurídico de uso común del dominio público radioeléctrico">
  <style>.h11{font:700 13px system-ui,sans-serif;fill:#0055a0}.k11{font:700 10px system-ui,sans-serif;fill:#0055a0}.d11{font:8.5px system-ui,sans-serif;fill:#333}.n11{font:8px system-ui,sans-serif;fill:#666}.w11{font:700 9px system-ui,sans-serif;fill:#fff}.r11{font:700 9px system-ui,sans-serif;fill:#d13c3c}.g11{font:700 9px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="20" text-anchor="middle" class="h11">Las tres bandas de la red local inalámbrica y sus compromisos</text>

  <rect x="22" y="32" width="636" height="86" rx="5" fill="#fbeaea"/>
  <text x="34" y="48" class="k11">2,4 GHz — 2400 a 2483,5 MHz · banda ICM</text>
  <path d="M120,88 L640,88" stroke="#999" stroke-width="1"/>
  <path d="M120,88 q40,-30 80,0" fill="none" stroke="#d13c3c" stroke-width="2"/>
  <text x="160" y="98" text-anchor="middle" class="r11">1</text>
  <path d="M180,88 q40,-22 80,0" fill="none" stroke="#ccc" stroke-width="1.4"/>
  <path d="M240,88 q40,-22 80,0" fill="none" stroke="#ccc" stroke-width="1.4"/>
  <path d="M300,88 q40,-30 80,0" fill="none" stroke="#d13c3c" stroke-width="2"/>
  <text x="340" y="98" text-anchor="middle" class="r11">6</text>
  <path d="M360,88 q40,-22 80,0" fill="none" stroke="#ccc" stroke-width="1.4"/>
  <path d="M420,88 q40,-22 80,0" fill="none" stroke="#ccc" stroke-width="1.4"/>
  <path d="M480,88 q40,-30 80,0" fill="none" stroke="#d13c3c" stroke-width="2"/>
  <text x="520" y="98" text-anchor="middle" class="r11">11</text>
  <text x="34" y="66" class="d11">Mejor alcance y</text>
  <text x="34" y="78" class="d11">mejor penetración</text>
  <text x="34" y="90" class="d11">en muros, pero</text>
  <text x="34" y="102" class="d11">MUY interferida</text>
  <text x="120" y="112" class="r11">SOLO 3 CANALES SIN SOLAPE: 1, 6 y 11 — cada canal ocupa 20-22 MHz y están separados solo 5 MHz</text>

  <rect x="22" y="126" width="312" height="72" rx="5" fill="#eef4fa"/>
  <text x="34" y="142" class="k11">5 GHz — varias subbandas desde 5150 MHz</text>
  <rect x="34" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="57" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="80" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="103" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="126" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="149" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="172" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="195" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="218" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="241" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="264" y="150" width="20" height="14" fill="#0055a0"/>
  <rect x="287" y="150" width="20" height="14" fill="#0055a0"/>
  <text x="34" y="178" class="d11">Más de 20 canales sin solape con 20 MHz</text>
  <text x="34" y="191" class="d11">Obligatorios DFS y TPC en varias subbandas</text>

  <rect x="346" y="126" width="312" height="72" rx="5" fill="#e6f2ec"/>
  <text x="358" y="142" class="k11">6 GHz — 5945 a 6425 MHz (Wi-Fi 6E y 7)</text>
  <rect x="358" y="150" width="38" height="14" fill="#2d8659"/>
  <rect x="399" y="150" width="38" height="14" fill="#2d8659"/>
  <rect x="440" y="150" width="38" height="14" fill="#2d8659"/>
  <rect x="481" y="150" width="38" height="14" fill="#2d8659"/>
  <rect x="522" y="150" width="38" height="14" fill="#2d8659"/>
  <rect x="563" y="150" width="38" height="14" fill="#2d8659"/>
  <rect x="604" y="150" width="38" height="14" fill="#2d8659"/>
  <text x="358" y="178" class="d11">Hasta 7 canales de 160 MHz. La más limpia</text>
  <text x="358" y="191" class="d11">Menor alcance · uso restringido a interiores</text>

  <rect x="22" y="208" width="636" height="20" rx="3" fill="#f7f9fb"/>
  <text x="32" y="222" class="d11"><tspan class="k11">Fenómenos de propagación</tspan>   Atenuación con la distancia · absorción (agua, personas, hormigón armado) · reflexión, refracción y difracción</text>
  <rect x="22" y="230" width="636" height="20" rx="3" fill="#eef4fa"/>
  <text x="32" y="244" class="d11"><tspan class="k11">Multitrayecto</tspan>                    La misma señal llega por varios caminos y se cancela parcialmente. OFDM lo resuelve y MIMO llega a aprovecharlo</text>

  <rect x="22" y="260" width="636" height="58" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="278" text-anchor="middle" class="k11">Régimen jurídico — artículo 88 de la Ley 11/2022: uso COMÚN, ESPECIAL o PRIVATIVO</text>
  <text x="340" y="294" text-anchor="middle" class="g11">Wi-Fi opera en USO COMÚN: NO precisa de ningún título habilitante</text>
  <text x="340" y="309" text-anchor="middle" class="d11">Pero queda sujeta a las condiciones técnicas del CNAF y CARECE DE PROTECCIÓN FRENTE A INTERFERENCIAS: no hay a quién reclamar</text>

  <text x="670" y="340" text-anchor="end" class="n11">[Fuente: Ley 11/2022 art. 88 · CNAF · IEEE 802.11]</text>
</svg>
```

---

## D12 · Mapa de los métodos de acceso al medio

**Sección**: §4.1 — Clasificación y principios de los métodos de acceso
**Propósito**: Dar el árbol completo de la clasificación con las realizaciones reales colgando de cada rama, y enfrentar en la conclusión la contraposición que vertebra toda la sección: contienda frente a determinismo.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 358" role="img" aria-label="Árbol de clasificación de los métodos de acceso al medio: asignación estática por división de frecuencia o de tiempo, y asignación dinámica dividida en tres familias, la de contienda con ALOHA, CSMA, CSMA barra CD y CSMA barra CA, la de paso de testigo con Token Ring, Token Bus y FDDI, y la de reserva y sondeo con polling, DQDB, DOCSIS, redes ópticas pasivas y el OFDMA coordinado de Wi-Fi 6">
  <style>.h12{font:700 13px system-ui,sans-serif;fill:#0055a0}.k12{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d12{font:8.5px system-ui,sans-serif;fill:#333}.n12{font:8px system-ui,sans-serif;fill:#666}.t12{font:700 10px system-ui,sans-serif;fill:#fff}.w12{font:700 8.5px system-ui,sans-serif;fill:#fff}.g12{font:700 9px system-ui,sans-serif;fill:#2d8659}.r12{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h12">Mapa completo de los métodos de acceso al medio</text>

  <rect x="250" y="32" width="180" height="24" rx="4" fill="#0055a0"/>
  <text x="340" y="49" text-anchor="middle" class="t12">ACCESO AL MEDIO COMPARTIDO</text>
  <path d="M340,56 L340,66 M150,66 L530,66 M150,66 L150,76 M530,66 L530,76" stroke="#666" stroke-width="1.2"/>

  <rect x="60" y="76" width="180" height="22" rx="4" fill="#c9d6e2"/>
  <text x="150" y="91" text-anchor="middle" class="k12">ASIGNACIÓN ESTÁTICA</text>
  <rect x="60" y="102" width="180" height="46" rx="4" fill="#f7f9fb"/>
  <text x="70" y="117" class="d12">FDM · TDM síncrona</text>
  <text x="70" y="130" class="n12">Retardo garantizado, pero desperdicia</text>
  <text x="70" y="141" class="n12">el canal y no escala: cada uno 1/n</text>
  <text x="150" y="162" text-anchor="middle" class="r12">NO se usa en redes locales de datos</text>

  <rect x="440" y="76" width="180" height="22" rx="4" fill="#0055a0"/>
  <text x="530" y="91" text-anchor="middle" class="w12">ASIGNACIÓN DINÁMICA</text>

  <rect x="60" y="180" width="200" height="20" rx="4" fill="#e89822"/>
  <text x="160" y="194" text-anchor="middle" class="w12">POR CONTIENDA (aleatorios)</text>
  <rect x="60" y="204" width="200" height="70" rx="4" fill="#fdf3e3"/>
  <text x="70" y="219" class="d12">ALOHA puro — rendimiento 18,4 %</text>
  <text x="70" y="232" class="d12">ALOHA ranurado — 36,8 %</text>
  <text x="70" y="245" class="d12">CSMA (1-persistente, no persist., p-persist.)</text>
  <text x="70" y="258" class="k12">CSMA/CD — Ethernet 802.3</text>
  <text x="70" y="270" class="k12">CSMA/CA — Wi-Fi 802.11</text>

  <rect x="270" y="180" width="180" height="20" rx="4" fill="#2d8659"/>
  <text x="360" y="194" text-anchor="middle" class="w12">PASO DE TESTIGO</text>
  <rect x="270" y="204" width="180" height="70" rx="4" fill="#e6f2ec"/>
  <text x="280" y="219" class="d12">802.5 Token Ring — 4 y 16 Mbit/s</text>
  <text x="280" y="232" class="d12">802.4 Token Bus — industrial (MAP)</text>
  <text x="280" y="245" class="d12">FDDI — 100 Mbit/s, doble anillo</text>
  <text x="280" y="260" class="g12">Sin colisiones · retardo ACOTADO</text>
  <text x="280" y="270" class="n12">Determinista: garantiza plazo máximo</text>

  <rect x="460" y="180" width="160" height="20" rx="4" fill="#3d82c4"/>
  <text x="540" y="194" text-anchor="middle" class="w12">RESERVA Y SONDEO</text>
  <rect x="460" y="204" width="160" height="70" rx="4" fill="#eef4fa"/>
  <text x="470" y="219" class="d12">Sondeo (polling) y selección</text>
  <text x="470" y="232" class="d12">DQDB (802.6) · DOCSIS · PON</text>
  <text x="470" y="245" class="d12">PCF y HCCA de 802.11</text>
  <text x="470" y="260" class="k12">OFDMA coordinado de Wi-Fi 6</text>
  <text x="470" y="270" class="n12">Trama de activación + unidades</text>

  <path d="M530,98 L530,172 M160,172 L540,172 M160,172 L160,180 M360,172 L360,180 M540,172 L540,180" stroke="#0055a0" stroke-width="1.4" fill="none"/>

  <rect x="22" y="286" width="636" height="46" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="304" text-anchor="middle" class="d12">CONTIENDA: eficiente con poca carga, pero el retardo NO está acotado y se degrada al saturarse</text>
  <text x="340" y="320" text-anchor="middle" class="d12">DETERMINISTA: garantiza un retardo máximo y no se degrada, a costa de una sobrecarga constante que penaliza con poca carga</text>

  <text x="670" y="348" text-anchor="end" class="n12">[Fuente: Tanenbaum · Abramson · IEEE 802]</text>
</svg>
```

---

## D13 · CSMA/CD: algoritmo y regla de los 64 octetos

**Sección**: §4.2.1 — Método CSMA/CD en redes Ethernet
**Propósito**: Encadenar en una sola lámina el algoritmo con sus cinco números memorizables y el razonamiento del que sale la **trama mínima de 64 octetos**, que es el argumento más elegante del tema.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 390" role="img" aria-label="Algoritmo de CSMA barra CD paso a paso: escuchar el medio, esperar el espacio entre tramas de 96 tiempos de bit, transmitir escuchando a la vez, y ante colisión emitir una señal de atasco de 32 bits y esperar un tiempo aleatorio calculado por retroceso exponencial binario truncado en 10 con un límite de 16 intentos; a la derecha, el razonamiento del que sale la ranura de colisión de 512 tiempos de bit y la trama mínima de 64 octetos">
  <style>.h13{font:700 13px system-ui,sans-serif;fill:#0055a0}.k13{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d13{font:8.5px system-ui,sans-serif;fill:#333}.n13{font:8px system-ui,sans-serif;fill:#666}.w13{font:700 9px system-ui,sans-serif;fill:#fff}.r13{font:700 9px system-ui,sans-serif;fill:#d13c3c}.g13{font:700 9px system-ui,sans-serif;fill:#2d8659}</style>
  <defs><marker id="m13" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#666"/></marker><marker id="c13" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#d13c3c"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h13">CSMA/CD: el algoritmo y de dónde sale la trama mínima de 64 octetos</text>

  <text x="160" y="40" text-anchor="middle" class="k13">EL ALGORITMO</text>
  <rect x="30" y="48" width="260" height="20" rx="4" fill="#0055a0"/>
  <text x="160" y="62" text-anchor="middle" class="w13">1 · ESCUCHAR EL MEDIO</text>
  <path d="M160,68 L160,76" stroke="#666" stroke-width="1.2" marker-end="url(#m13)"/>
  <rect x="30" y="78" width="260" height="20" rx="4" fill="#3d82c4"/>
  <text x="160" y="92" text-anchor="middle" class="w13">2 · SI OCUPADO, SEGUIR ESCUCHANDO (1-persistente)</text>
  <path d="M160,98 L160,106" stroke="#666" stroke-width="1.2" marker-end="url(#m13)"/>
  <rect x="30" y="108" width="260" height="20" rx="4" fill="#0055a0"/>
  <text x="160" y="122" text-anchor="middle" class="w13">3 · ESPERAR 96 TIEMPOS DE BIT Y TRANSMITIR</text>
  <path d="M160,128 L160,136" stroke="#666" stroke-width="1.2" marker-end="url(#m13)"/>
  <rect x="30" y="138" width="260" height="20" rx="4" fill="#2d8659"/>
  <text x="160" y="152" text-anchor="middle" class="w13">4 · SEGUIR ESCUCHANDO MIENTRAS SE TRANSMITE</text>
  <path d="M160,158 L160,166" stroke="#d13c3c" stroke-width="1.2" marker-end="url(#c13)"/>
  <rect x="30" y="168" width="260" height="20" rx="4" fill="#d13c3c"/>
  <text x="160" y="182" text-anchor="middle" class="w13">5 · ¿COLISIÓN? ATASCO DE 32 BITS</text>
  <path d="M160,188 L160,196" stroke="#d13c3c" stroke-width="1.2" marker-end="url(#c13)"/>
  <rect x="30" y="198" width="260" height="32" rx="4" fill="#fdf3e3"/>
  <text x="160" y="212" text-anchor="middle" class="d13">6 · RETROCESO EXPONENCIAL BINARIO</text>
  <text x="160" y="225" text-anchor="middle" class="d13">esperar r ranuras, r aleatorio en [0, 2^k − 1], k = mín(n,10)</text>
  <path d="M30,214 L18,214 L18,58 L30,58" fill="none" stroke="#666" stroke-width="1.2" marker-end="url(#m13)"/>
  <rect x="30" y="240" width="260" height="20" rx="4" fill="#fbeaea"/>
  <text x="160" y="254" text-anchor="middle" class="r13">7 · A LOS 16 INTENTOS, DESCARTAR LA TRAMA</text>

  <text x="490" y="40" text-anchor="middle" class="k13">DE DÓNDE SALEN LOS 64 OCTETOS</text>
  <rect x="322" y="48" width="336" height="86" rx="4" fill="#eef4fa"/>
  <circle cx="346" cy="76" r="9" fill="#0055a0"/>
  <text x="346" y="79" text-anchor="middle" class="w13">A</text>
  <circle cx="634" cy="76" r="9" fill="#0055a0"/>
  <text x="634" y="79" text-anchor="middle" class="w13">C</text>
  <path d="M356,72 L620,72" stroke="#2d8659" stroke-width="1.8" marker-end="url(#m13)"/>
  <text x="490" y="66" text-anchor="middle" class="n13">ida: la señal de A tarda un tiempo T</text>
  <path d="M624,86 L360,86" stroke="#d13c3c" stroke-width="1.8" marker-end="url(#c13)"/>
  <text x="490" y="100" text-anchor="middle" class="n13">vuelta: C transmite justo antes de oír a A; la colisión tarda otro T</text>
  <text x="490" y="116" text-anchor="middle" class="k13">A debe SEGUIR TRANSMITIENDO durante al menos 2T</text>
  <text x="490" y="128" text-anchor="middle" class="d13">Si terminase antes, no se enteraría de la colisión</text>

  <rect x="322" y="140" width="336" height="20" rx="3" fill="#0055a0"/>
  <text x="490" y="154" text-anchor="middle" class="w13">2T = RANURA DE COLISIÓN = 512 TIEMPOS DE BIT = 64 OCTETOS</text>

  <rect x="322" y="166" width="336" height="94" rx="4" fill="#f7f9fb"/>
  <text x="332" y="182" class="d13">A 10 Mbit/s: 512 bits ÷ 10 Mbit/s = 51,2 µs de ranura</text>
  <text x="332" y="195" class="d13">Ida T = 25,6 µs × 2·10⁸ m/s = 5.120 m teóricos</text>
  <text x="332" y="208" class="d13">La norma lo reduce a ~2.500 m por los repetidores</text>
  <text x="332" y="224" class="r13">A 100 Mbit/s el bit dura 10 veces menos: ~250 m</text>
  <text x="332" y="240" class="g13">En Gigabit habrían quedado 25 m: por eso la ranura</text>
  <text x="332" y="252" class="g13">subió a 4.096 tiempos de bit con extensión de portadora</text>

  <rect x="30" y="272" width="628" height="20" rx="3" fill="#0055a0"/>
  <text x="40" y="286" class="w13">TRAMA</text>
  <text x="120" y="286" class="w13">Preámbulo 7</text>
  <text x="205" y="286" class="w13">SFD 1</text>
  <text x="258" y="286" class="w13">Destino 6</text>
  <text x="330" y="286" class="w13">Origen 6</text>
  <text x="400" y="286" class="w13">Tipo/Long 2</text>
  <text x="484" y="286" class="w13">Datos 46-1500</text>
  <text x="592" y="286" class="w13">FCS 4</text>
  <text x="344" y="306" text-anchor="middle" class="d13">Mínima 64 octetos · máxima 1518 (1522 con etiqueta 802.1Q) · MTU 1500 · el preámbulo y el SFD NO se cuentan en el tamaño</text>

  <rect x="30" y="318" width="628" height="42" rx="5" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <text x="344" y="336" text-anchor="middle" class="r13">CSMA/CD solo tiene sentido en SEMIDÚPLEX sobre medio compartido</text>
  <text x="344" y="352" text-anchor="middle" class="d13">Con conmutador y enlace dúplex SE DESACTIVA, y en 10 Gbit/s y superiores el semidúplex ni siquiera está definido</text>

  <text x="670" y="378" text-anchor="end" class="n13">[Fuente: IEEE 802.3 · Spurgeon]</text>
</svg>
```

---

## D14 · CSMA/CA: DIFS, retroceso, ACK y el nodo oculto

**Sección**: §4.2.2 — Método CSMA/CA en redes Wi-Fi
**Propósito**: Representar la secuencia temporal completa de una transmisión Wi-Fi con sus espacios entre tramas y, debajo, el escenario del nodo oculto con la solución RTS/CTS, que es el par de conceptos central de toda la sección.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 424" role="img" aria-label="Secuencia temporal de CSMA barra CA: tras encontrar el medio libre durante un DIFS de 34 microsegundos la estación espera además un retroceso aleatorio de entre cero y CW menos uno ranuras de 9 microsegundos, transmite y el receptor responde con un acuse de recibo tras un SIFS de 16 microsegundos; debajo, el escenario del nodo oculto en el que dos estaciones que no se oyen entre sí colisionan en el punto de acceso, y su solución mediante el intercambio RTS CTS que actualiza el vector de asignación de red">
  <style>.h14{font:700 13px system-ui,sans-serif;fill:#0055a0}.k14{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d14{font:8.5px system-ui,sans-serif;fill:#333}.n14{font:8px system-ui,sans-serif;fill:#666}.w14{font:700 8.5px system-ui,sans-serif;fill:#fff}.r14{font:700 9px system-ui,sans-serif;fill:#d13c3c}.g14{font:700 9px system-ui,sans-serif;fill:#2d8659}</style>
  <defs><marker id="m14" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h14">CSMA/CA: la colisión no se puede detectar, así que se evita</text>
  <text x="340" y="37" text-anchor="middle" class="n14">El emisor no oye mientras transmite: su propia antena ensordece su receptor</text>

  <text x="30" y="58" class="k14">SECUENCIA TEMPORAL</text>
  <rect x="30" y="66" width="80" height="26" rx="3" fill="#c9d6e2"/>
  <text x="70" y="83" text-anchor="middle" class="d14">MEDIO OCUPADO</text>
  <rect x="112" y="66" width="76" height="26" rx="3" fill="#3d82c4"/>
  <text x="150" y="83" text-anchor="middle" class="w14">DIFS 34 µs</text>
  <rect x="190" y="66" width="24" height="26" rx="2" fill="#e89822"/>
  <rect x="216" y="66" width="24" height="26" rx="2" fill="#e89822"/>
  <rect x="242" y="66" width="24" height="26" rx="2" fill="#e89822"/>
  <rect x="268" y="66" width="24" height="26" rx="2" fill="#e89822"/>
  <rect x="294" y="66" width="220" height="26" rx="3" fill="#0055a0"/>
  <text x="404" y="83" text-anchor="middle" class="w14">TRAMA DE DATOS</text>
  <rect x="516" y="66" width="42" height="26" rx="3" fill="#7fa8cc"/>
  <text x="537" y="83" text-anchor="middle" class="w14">SIFS</text>
  <rect x="560" y="66" width="60" height="26" rx="3" fill="#2d8659"/>
  <text x="590" y="83" text-anchor="middle" class="w14">ACK</text>
  <text x="241" y="60" text-anchor="middle" class="k14">RETROCESO ALEATORIO</text>

  <text x="190" y="105" class="n14">ranuras de 9 µs: se decrementa SOLO si el medio sigue libre, y se CONGELA si alguien transmite</text>
  <text x="344" y="120" text-anchor="middle" class="g14">El ACK espera solo un SIFS: prioridad absoluta, nunca colisiona</text>

  <rect x="30" y="128" width="628" height="20" rx="3" fill="#eef4fa"/>
  <text x="40" y="142" class="d14">Tiempos en 5 GHz: SIFS 16 µs · ranura 9 µs · DIFS = SIFS + 2 × ranura = 34 µs · PIFS = SIFS + 1 ranura = 25 µs</text>
  <rect x="30" y="152" width="628" height="20" rx="3" fill="#f7f9fb"/>
  <text x="40" y="166" class="d14">En 802.11b a 2,4 GHz: SIFS 10 µs y ranura 20 µs, luego DIFS = 50 µs. Los espacios crean prioridades: quien empieza antes, gana</text>
  <rect x="30" y="176" width="628" height="20" rx="3" fill="#eef4fa"/>
  <text x="40" y="190" class="d14">Ventana de contienda: CWmín 15 y CWmáx 1023 en OFDM. Se DUPLICA en cada intento fallido. Sin ACK, se supone colisión</text>

  <text x="30" y="214" class="k14">EL PROBLEMA DEL NODO OCULTO Y SU SOLUCIÓN</text>
  <rect x="30" y="222" width="300" height="100" rx="4" fill="#fbeaea"/>
  <circle cx="66" cy="266" r="12" fill="#0055a0"/><text x="66" y="270" text-anchor="middle" class="w14">A</text>
  <rect x="164" y="254" width="32" height="24" rx="3" fill="#333"/><text x="180" y="270" text-anchor="middle" class="w14">AP</text>
  <circle cx="294" cy="266" r="12" fill="#0055a0"/><text x="294" y="270" text-anchor="middle" class="w14">C</text>
  <path d="M80,266 L160,266" stroke="#2d8659" stroke-width="1.6" marker-end="url(#m14)"/>
  <path d="M280,266 L200,266" stroke="#2d8659" stroke-width="1.6" marker-end="url(#m14)"/>
  <text x="180" y="296" text-anchor="middle" class="r14">COLISIÓN aquí</text>
  <path d="M80,242 L280,242" stroke="#d13c3c" stroke-width="1.4" stroke-dasharray="5,4"/>
  <text x="180" y="238" text-anchor="middle" class="n14">A y C NO se oyen entre sí</text>
  <text x="40" y="314" class="d14">La escucha falla: el medio que oye A no es el que ve el AP</text>

  <rect x="336" y="222" width="322" height="100" rx="4" fill="#e6f2ec"/>
  <text x="346" y="238" class="k14">SOLUCIÓN: RTS / CTS + NAV (detección VIRTUAL)</text>
  <rect x="346" y="246" width="60" height="18" rx="3" fill="#0055a0"/>
  <text x="376" y="259" text-anchor="middle" class="w14">A → RTS</text>
  <path d="M408,255 L424,255" stroke="#0055a0" stroke-width="1.4" marker-end="url(#m14)"/>
  <rect x="428" y="246" width="66" height="18" rx="3" fill="#2d8659"/>
  <text x="461" y="259" text-anchor="middle" class="w14">AP → CTS</text>
  <path d="M496,255 L512,255" stroke="#2d8659" stroke-width="1.4" marker-end="url(#m14)"/>
  <rect x="516" y="246" width="132" height="18" rx="3" fill="#e89822"/>
  <text x="582" y="259" text-anchor="middle" class="w14">TODOS actualizan su NAV</text>
  <text x="346" y="280" class="d14">La clave: el CTS lo oyen TODAS las estaciones al alcance del</text>
  <text x="346" y="292" class="d14">punto de acceso, incluida C, aunque no oyese el RTS de A</text>
  <text x="346" y="310" class="n14">Ambos llevan la DURACIÓN prevista de la ocupación del medio</text>

  <rect x="30" y="334" width="628" height="56" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="344" y="354" text-anchor="middle" class="k14">CSMA/CD frente a CSMA/CA — la comparación central del tema</text>
  <text x="344" y="370" text-anchor="middle" class="d14">detecta la colisión / la evita · cable / radio · sin acuse / ACK obligatorio · atasco de 32 bits / RTS-CTS y NAV</text>
  <text x="344" y="384" text-anchor="middle" class="d14">retroceso solo tras colisionar / también antes · se desactiva en dúplex / siempre activa, porque la radio es semidúplex</text>

  <text x="670" y="412" text-anchor="end" class="n14">[Fuente: IEEE 802.11 · Gast]</text>
</svg>
```

---

## D15 · Paso de testigo: Token Ring, Token Bus y FDDI

**Sección**: §4.3 — Métodos deterministas o por paso de testigo
**Propósito**: Distinguir las tres realizaciones deterministas por los datos que las discriminan y explicar gráficamente el **plegado del doble anillo de FDDI**, que es la respuesta a la debilidad estructural de la topología en anillo.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 374" role="img" aria-label="Las tres realizaciones del paso de testigo: Token Ring de IEEE 802.5 a 4 y 16 megabits por segundo con unidad de acceso al medio y monitor activo; Token Bus de IEEE 802.4 con anillo lógico sobre bus físico para entorno industrial; y FDDI a 100 megabits por segundo sobre fibra con doble anillo contrarrotante que se pliega ante un corte para mantener el servicio">
  <style>.h15{font:700 13px system-ui,sans-serif;fill:#0055a0}.k15{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d15{font:8.5px system-ui,sans-serif;fill:#333}.n15{font:8px system-ui,sans-serif;fill:#666}.w15{font:700 8.5px system-ui,sans-serif;fill:#fff}.g15{font:700 9px system-ui,sans-serif;fill:#2d8659}.r15{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h15">Paso de testigo: sin colisiones y con retardo acotado</text>
  <text x="340" y="37" text-anchor="middle" class="n15">Circula un permiso explícito para transmitir; solo emite quien lo posee</text>

  <rect x="22" y="48" width="204" height="150" rx="5" fill="#eef4fa"/>
  <text x="124" y="64" text-anchor="middle" class="k15">IEEE 802.5 · TOKEN RING</text>
  <circle cx="124" cy="112" r="30" fill="none" stroke="#0055a0" stroke-width="2"/>
  <circle cx="124" cy="82" r="5" fill="#0055a0"/>
  <circle cx="154" cy="112" r="5" fill="#0055a0"/>
  <circle cx="124" cy="142" r="5" fill="#0055a0"/>
  <circle cx="94" cy="112" r="5" fill="#0055a0"/>
  <path d="M140,86 L158,86 L158,96 L140,96 z" fill="#e89822"/>
  <text x="176" y="94" class="n15">testigo</text>
  <text x="32" y="162" class="d15">4 y 16 Mbit/s · IBM · cableado en MAU</text>
  <text x="32" y="174" class="d15">Testigo de 3 octetos, 3 bits de prioridad</text>
  <text x="32" y="186" class="d15">y 3 de reserva · MONITOR ACTIVO</text>

  <rect x="238" y="48" width="204" height="150" rx="5" fill="#fdf3e3"/>
  <text x="340" y="64" text-anchor="middle" class="k15">IEEE 802.4 · TOKEN BUS</text>
  <path d="M256,120 L424,120" stroke="#0055a0" stroke-width="2.5"/>
  <circle cx="280" cy="100" r="5" fill="#0055a0"/><path d="M280,105 L280,120" stroke="#666" stroke-width="1"/>
  <circle cx="330" cy="100" r="5" fill="#0055a0"/><path d="M330,105 L330,120" stroke="#666" stroke-width="1"/>
  <circle cx="380" cy="100" r="5" fill="#0055a0"/><path d="M380,105 L380,120" stroke="#666" stroke-width="1"/>
  <circle cx="410" cy="140" r="5" fill="#0055a0"/><path d="M410,135 L410,120" stroke="#666" stroke-width="1"/>
  <path d="M280,92 q25,-16 50,0 M330,92 q25,-16 50,0" fill="none" stroke="#e89822" stroke-width="1.4" stroke-dasharray="4,3"/>
  <path d="M410,148 q-65,14 -130,-40" fill="none" stroke="#e89822" stroke-width="1.4" stroke-dasharray="4,3"/>
  <text x="340" y="162" text-anchor="middle" class="d15">ANILLO LÓGICO sobre BUS FÍSICO</text>
  <text x="248" y="176" class="d15">Las estaciones se ordenan por dirección</text>
  <text x="248" y="188" class="d15">Uso industrial · base del perfil MAP</text>

  <rect x="454" y="48" width="204" height="150" rx="5" fill="#e6f2ec"/>
  <text x="556" y="64" text-anchor="middle" class="k15">FDDI · ANSI / ISO, no IEEE</text>
  <circle cx="556" cy="108" r="32" fill="none" stroke="#0055a0" stroke-width="2"/>
  <circle cx="556" cy="108" r="24" fill="none" stroke="#2d8659" stroke-width="2" stroke-dasharray="5,3"/>
  <circle cx="556" cy="76" r="5" fill="#0055a0"/>
  <circle cx="588" cy="108" r="5" fill="#0055a0"/>
  <circle cx="556" cy="140" r="5" fill="#0055a0"/>
  <circle cx="524" cy="108" r="5" fill="#0055a0"/>
  <path d="M578,130 L594,146" stroke="#d13c3c" stroke-width="2.4"/>
  <path d="M594,130 L578,146" stroke="#d13c3c" stroke-width="2.4"/>
  <text x="622" y="144" class="r15">corte</text>
  <text x="464" y="160" class="d15">100 Mbit/s sobre fibra · 200 km</text>
  <text x="464" y="172" class="d15">500 estaciones · doble anillo</text>
  <text x="464" y="184" class="g15">PLIEGA LOS DOS ANILLOS EN UNO</text>
  <text x="464" y="194" class="n15">ante un corte, y el servicio continúa</text>

  <rect x="22" y="210" width="636" height="20" rx="3" fill="#f7f9fb"/>
  <text x="32" y="224" class="d15">Ventajas: sin colisiones por construcción · retardo máximo ACOTADO · el rendimiento NO se degrada al saturarse · admite prioridades</text>
  <rect x="22" y="234" width="636" height="20" rx="3" fill="#eef4fa"/>
  <text x="32" y="248" class="d15">Inconvenientes: complejidad de mantener el anillo y detectar el testigo perdido o duplicado · coste · menos eficiente con CARGA BAJA</text>
  <rect x="22" y="258" width="636" height="20" rx="3" fill="#f7f9fb"/>
  <text x="32" y="272" class="d15">FDDI, acceso temporizado: se pacta un tiempo objetivo de rotación (TTRT) y, si el testigo llega antes, hay tiempo de retención (THT)</text>

  <rect x="22" y="290" width="636" height="48" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="310" text-anchor="middle" class="k15">Con carga alta gana el testigo · con carga baja y a ráfagas gana Ethernet</text>
  <text x="340" y="326" text-anchor="middle" class="d15">Y con conmutador y dúplex la discusión desaparece: ya no hay colisiones que resolver</text>

  <text x="670" y="362" text-anchor="end" class="n15">[Fuente: IEEE 802.5 · IEEE 802.4 · ISO/IEC 9314]</text>
</svg>
```

---

## D16 · Dispositivos por capa: dominios de colisión y de difusión

**Sección**: §5 — Dispositivos de interconexión
**Propósito**: Es el diagrama de referencia de toda la sección 5. Sitúa cada dispositivo en su capa y responde de un vistazo a la pregunta canónica: **qué separa y qué propaga cada aparato**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 372" role="img" aria-label="Clasificación de los dispositivos de interconexión por la capa cuya información utilizan para decidir: repetidor y concentrador en la capa física, con un único dominio de colisión y uno de difusión; puente, conmutador y punto de acceso en la capa de enlace, con un dominio de colisión por puerto y uno de difusión por VLAN; encaminador en la capa de red, que separa dominios de difusión; y pasarela por encima de la capa 3, que traduce protocolos">
  <style>.h16{font:700 13px system-ui,sans-serif;fill:#0055a0}.k16{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d16{font:8.5px system-ui,sans-serif;fill:#333}.n16{font:8px system-ui,sans-serif;fill:#666}.w16{font:700 9.5px system-ui,sans-serif;fill:#fff}.g16{font:700 8.5px system-ui,sans-serif;fill:#2d8659}.r16{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h16">Cada dispositivo se clasifica por la capa MÁS ALTA cuya información usa para decidir</text>

  <rect x="22" y="34" width="636" height="17" fill="#0055a0"/>
  <text x="32" y="47" class="w16">CAPA</text>
  <text x="96" y="47" class="w16">DISPOSITIVO</text>
  <text x="232" y="47" class="w16">DECIDE POR</text>
  <text x="360" y="47" class="w16">DOMINIOS DE COLISIÓN</text>
  <text x="512" y="47" class="w16">DOMINIOS DE DIFUSIÓN</text>

  <rect x="22" y="52" width="636" height="52" fill="#fbeaea"/>
  <rect x="22" y="52" width="66" height="52" fill="#d13c3c"/>
  <text x="55" y="74" text-anchor="middle" class="w16">CAPA 1</text>
  <text x="55" y="88" text-anchor="middle" class="w16">FÍSICA</text>
  <text x="96" y="70" class="k16">Repetidor</text>
  <text x="96" y="84" class="k16">Concentrador (hub)</text>
  <text x="96" y="98" class="n16">Conversor de medio · módem</text>
  <text x="232" y="70" class="d16">Nada: regenera</text>
  <text x="232" y="84" class="d16">la señal sin</text>
  <text x="232" y="98" class="d16">interpretarla</text>
  <text x="360" y="78" class="r16">UNO SOLO — lo propaga</text>
  <text x="360" y="92" class="n16">Regenera incluso las colisiones</text>
  <text x="512" y="78" class="r16">UNO SOLO — lo propaga</text>
  <text x="512" y="92" class="n16">Obliga a semidúplex y a CSMA/CD</text>

  <rect x="22" y="106" width="636" height="60" fill="#eef4fa"/>
  <rect x="22" y="106" width="66" height="60" fill="#0055a0"/>
  <text x="55" y="130" text-anchor="middle" class="w16">CAPA 2</text>
  <text x="55" y="144" text-anchor="middle" class="w16">ENLACE</text>
  <text x="96" y="124" class="k16">Puente (bridge)</text>
  <text x="96" y="138" class="k16">Conmutador (switch)</text>
  <text x="96" y="152" class="k16">Punto de acceso Wi-Fi</text>
  <text x="232" y="124" class="d16">DIRECCIÓN MAC</text>
  <text x="232" y="138" class="n16">Aprende del campo</text>
  <text x="232" y="152" class="n16">de origen; reenvía</text>
  <text x="232" y="162" class="n16">por el de destino</text>
  <text x="360" y="130" class="g16">UNO POR PUERTO — lo divide</text>
  <text x="360" y="144" class="n16">Puerto de conmutador = enlace</text>
  <text x="360" y="156" class="n16">dedicado, dúplex, sin colisiones</text>
  <text x="512" y="130" class="r16">UNO POR VLAN — no lo divide</text>
  <text x="512" y="144" class="n16">La difusión se INUNDA siempre;</text>
  <text x="512" y="156" class="n16">solo la VLAN la acota</text>

  <rect x="22" y="168" width="636" height="52" fill="#e6f2ec"/>
  <rect x="22" y="168" width="66" height="52" fill="#2d8659"/>
  <text x="55" y="190" text-anchor="middle" class="w16">CAPA 3</text>
  <text x="55" y="204" text-anchor="middle" class="w16">RED</text>
  <text x="96" y="186" class="k16">Encaminador (router)</text>
  <text x="96" y="200" class="k16">Conmutador de capa 3</text>
  <text x="96" y="214" class="n16">Cortafuegos (3-4, y 7)</text>
  <text x="232" y="186" class="d16">DIRECCIÓN IP</text>
  <text x="232" y="200" class="n16">Jerárquica: permite</text>
  <text x="232" y="214" class="n16">agregar rutas</text>
  <text x="360" y="194" class="g16">UNO POR INTERFAZ</text>
  <text x="360" y="208" class="n16">Reconstruye la trama en cada salto</text>
  <text x="512" y="194" class="g16">UNO POR INTERFAZ — lo divide</text>
  <text x="512" y="208" class="n16">No reenvía la difusión de capa 2</text>

  <rect x="22" y="222" width="636" height="40" fill="#fdf3e3"/>
  <rect x="22" y="222" width="66" height="40" fill="#e89822"/>
  <text x="55" y="240" text-anchor="middle" class="w16">CAPAS</text>
  <text x="55" y="254" text-anchor="middle" class="w16">4 A 7</text>
  <text x="96" y="240" class="k16">Pasarela (gateway)</text>
  <text x="96" y="254" class="n16">Equilibrador de carga</text>
  <text x="232" y="240" class="d16">El CONTENIDO</text>
  <text x="232" y="254" class="n16">Traduce y reescribe</text>
  <text x="360" y="240" class="n16">Interconecta arquitecturas heterogéneas:</text>
  <text x="360" y="253" class="n16">correo, voz a red telefónica, protocolo industrial</text>

  <rect x="22" y="272" width="312" height="48" rx="5" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <text x="178" y="290" text-anchor="middle" class="r16">AMBIGÜEDAD QUE INDUCE A ERROR</text>
  <text x="178" y="304" text-anchor="middle" class="d16">La «pasarela» de la configuración de un equipo es la puerta</text>
  <text x="178" y="315.5" text-anchor="middle" class="d16">de enlace predeterminada: un ENCAMINADOR, no traduce nada</text>

  <rect x="346" y="272" width="312" height="48" rx="5" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <text x="502" y="290" text-anchor="middle" class="r16">TRAMPA CLÁSICA</text>
  <text x="502" y="304" text-anchor="middle" class="d16">El PANEL DE PARCHEO no es un dispositivo de interconexión:</text>
  <text x="502" y="315.5" text-anchor="middle" class="d16">es un elemento PASIVO del cableado estructurado</text>

  <text x="340" y="342" text-anchor="middle" class="k16">Las direcciones MAC cambian en cada salto · las direcciones IP no cambian en todo el trayecto</text>

  <text x="670" y="360" text-anchor="end" class="n16">[Fuente: ISO/IEC 7498-1 · IEEE 802.1D · Kurose]</text>
</svg>
```

---

## D17 · La etiqueta 802.1Q y la trama etiquetada

**Sección**: §5.2.2 — Funcionamiento de conmutadores y redes virtuales
**Propósito**: Desglosar campo a campo los cuatro octetos de la etiqueta, con los números clave, y señalar dónde se inserta exactamente y qué le ocurre al tamaño máximo de la trama.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 346" role="img" aria-label="La etiqueta IEEE 802.1Q se inserta entre la dirección de origen y el campo de tipo o longitud, mide cuatro octetos y se compone de un identificador de protocolo de etiqueta de valor fijo 0x8100, tres bits de prioridad conocidos como 802.1p, un bit indicador de descarte elegible y doce bits de identificador de VLAN, de los que se reservan el cero y el 4095, quedando 4094 VLAN utilizables; la trama pasa de 1518 a 1522 octetos">
  <style>.h17{font:700 13px system-ui,sans-serif;fill:#0055a0}.k17{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d17{font:8.5px system-ui,sans-serif;fill:#333}.n17{font:8px system-ui,sans-serif;fill:#666}.w17{font:700 8.5px system-ui,sans-serif;fill:#fff}.b17{font:700 10px system-ui,sans-serif;fill:#fff}.g17{font:700 9px system-ui,sans-serif;fill:#2d8659}.r17{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h17">La etiqueta 802.1Q: cuatro octetos que convierten una trama en una trama de VLAN</text>

  <text x="30" y="42" class="k17">TRAMA SIN ETIQUETAR — puerto de ACCESO</text>
  <rect x="30" y="50" width="90" height="24" fill="#7fa8cc"/><text x="75" y="66" text-anchor="middle" class="w17">Destino 6</text>
  <rect x="122" y="50" width="90" height="24" fill="#7fa8cc"/><text x="167" y="66" text-anchor="middle" class="w17">Origen 6</text>
  <rect x="214" y="50" width="90" height="24" fill="#3d82c4"/><text x="259" y="66" text-anchor="middle" class="w17">Tipo/Long 2</text>
  <rect x="306" y="50" width="266" height="24" fill="#0055a0"/><text x="439" y="66" text-anchor="middle" class="w17">DATOS 46 a 1500</text>
  <rect x="574" y="50" width="84" height="24" fill="#3d82c4"/><text x="616" y="66" text-anchor="middle" class="w17">FCS 4</text>
  <text x="344" y="88" text-anchor="middle" class="d17">Máximo 1518 octetos</text>

  <text x="30" y="112" class="k17">TRAMA ETIQUETADA — puerto TRONCAL (trunk)</text>
  <rect x="30" y="120" width="90" height="24" fill="#7fa8cc"/><text x="75" y="136" text-anchor="middle" class="w17">Destino 6</text>
  <rect x="122" y="120" width="90" height="24" fill="#7fa8cc"/><text x="167" y="136" text-anchor="middle" class="w17">Origen 6</text>
  <rect x="214" y="120" width="106" height="24" fill="#e89822"/><text x="267" y="136" text-anchor="middle" class="b17">ETIQUETA 4</text>
  <rect x="322" y="120" width="80" height="24" fill="#3d82c4"/><text x="362" y="136" text-anchor="middle" class="w17">Tipo/Long 2</text>
  <rect x="404" y="120" width="168" height="24" fill="#0055a0"/><text x="488" y="136" text-anchor="middle" class="w17">DATOS 46 a 1500</text>
  <rect x="574" y="120" width="84" height="24" fill="#3d82c4"/><text x="616" y="136" text-anchor="middle" class="w17">FCS 4</text>
  <text x="344" y="158" text-anchor="middle" class="r17">Máximo 1522 octetos — un equipo antiguo la descarta por exceso de tamaño («baby giant»)</text>

  <text x="380" y="174" text-anchor="middle" class="k17">Los cuatro octetos de la ETIQUETA, ampliados</text>

  <rect x="120" y="180" width="240" height="30" fill="#e89822"/>
  <text x="240" y="200" text-anchor="middle" class="b17">TPID = 0x8100 · 16 bits</text>
  <rect x="362" y="180" width="76" height="30" fill="#0055a0"/>
  <text x="400" y="196" text-anchor="middle" class="w17">PCP</text>
  <text x="400" y="206" text-anchor="middle" class="w17">3 bits</text>
  <rect x="440" y="180" width="52" height="30" fill="#7fa8cc"/>
  <text x="466" y="196" text-anchor="middle" class="w17">DEI</text>
  <text x="466" y="206" text-anchor="middle" class="w17">1 bit</text>
  <rect x="494" y="180" width="146" height="30" fill="#2d8659"/>
  <text x="567" y="200" text-anchor="middle" class="b17">VID · 12 bits</text>

  <rect x="30" y="222" width="628" height="20" rx="3" fill="#eef4fa"/>
  <text x="40" y="236" class="d17"><tspan class="k17">TPID</tspan>  Valor fijo 0x8100. Indica al conmutador que lo que sigue no es el campo de tipo sino una etiqueta</text>
  <rect x="30" y="246" width="628" height="20" rx="3" fill="#f7f9fb"/>
  <text x="40" y="260" class="d17"><tspan class="k17">PCP</tspan>   Ocho niveles de prioridad, de 0 a 7. Es lo que se conoce como 802.1p, que NUNCA fue norma independiente: es parte de 802.1Q</text>
  <rect x="30" y="270" width="628" height="20" rx="3" fill="#eef4fa"/>
  <text x="40" y="284" class="d17"><tspan class="k17">VID</tspan>   2¹² = 4.096 valores, pero el 0 y el 4095 están RESERVADOS → <tspan class="g17">4.094 VLAN UTILIZABLES</tspan></text>

  <rect x="30" y="298" width="628" height="20" rx="3" fill="#fdf3e3"/>
  <text x="40" y="312" class="d17"><tspan class="k17">VLAN NATIVA</tspan>  Viaja SIN etiquetar por el troncal. Es la debilidad del salto de VLAN por doble etiquetado: asignarla a una VLAN sin uso</text>

  <text x="670" y="334" text-anchor="end" class="n17">[Fuente: IEEE 802.1Q · CCN-STIC-641]</text>
</svg>
```

---

## D18 · Cableado estructurado: subsistemas y distancias

**Sección**: §6.1 — Estándares de cableado estructurado e infraestructura
**Propósito**: Situar los cuatro subsistemas sobre un corte de edificio con las distancias normalizadas, y separar con claridad los dos planos normativos que conviven en una obra municipal: el del **cableado genérico** y el de las **infraestructuras comunes de telecomunicación**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 380" role="img" aria-label="Corte de un edificio de tres plantas con los subsistemas del cableado estructurado: el subsistema horizontal de par trenzado con noventa metros máximos de cable fijo desde el distribuidor de planta hasta la toma de usuario, el área de trabajo con diez metros de latiguillos, el subsistema vertical de fibra multimodo entre los distribuidores de planta y el armario principal, y el subsistema de campus de fibra monomodo hacia otros edificios">
  <style>.h18{font:700 13px system-ui,sans-serif;fill:#0055a0}.k18{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d18{font:8.5px system-ui,sans-serif;fill:#333}.n18{font:8px system-ui,sans-serif;fill:#666}.w18{font:700 8.5px system-ui,sans-serif;fill:#fff}.g18{font:700 9px system-ui,sans-serif;fill:#2d8659}.r18{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="20" text-anchor="middle" class="h18">Los cuatro subsistemas del cableado estructurado y sus distancias</text>

  <rect x="30" y="34" width="380" height="52" fill="#eef4fa" stroke="#c9d6e2" stroke-width="1"/>
  <rect x="36" y="42" width="26" height="36" fill="#0055a0"/>
  <text x="49" y="56" text-anchor="middle" class="w18">DP</text>
  <text x="49" y="70" text-anchor="middle" class="w18">P2</text>
  <path d="M76,60 L300,60" stroke="#0055a0" stroke-width="1.8"/>
  <rect x="300" y="52" width="14" height="16" fill="#7fa8cc"/>
  <path d="M314,60 L360,60" stroke="#2d8659" stroke-width="1.8" stroke-dasharray="4,3"/>
  <circle cx="372" cy="60" r="7" fill="#333"/>
  <text x="215" y="48" text-anchor="middle" class="n18">SUBSISTEMA HORIZONTAL — par trenzado — máx. 90 m de cable FIJO</text>
  <text x="338" y="80" text-anchor="middle" class="n18">toma</text>
  <text x="372" y="80" text-anchor="middle" class="n18">puesto</text>

  <rect x="30" y="90" width="380" height="52" fill="#f7f9fb" stroke="#c9d6e2" stroke-width="1"/>
  <rect x="36" y="98" width="26" height="36" fill="#0055a0"/>
  <text x="49" y="112" text-anchor="middle" class="w18">DP</text>
  <text x="49" y="126" text-anchor="middle" class="w18">P1</text>
  <path d="M76,116 L300,116" stroke="#0055a0" stroke-width="1.8"/>
  <rect x="300" y="108" width="14" height="16" fill="#7fa8cc"/>
  <path d="M314,116 L360,116" stroke="#2d8659" stroke-width="1.8" stroke-dasharray="4,3"/>
  <circle cx="372" cy="116" r="7" fill="#333"/>
  <text x="240" y="136" text-anchor="middle" class="g18">ÁREA DE TRABAJO — máx. 10 m de latiguillos entre ambos extremos</text>

  <rect x="30" y="146" width="380" height="52" fill="#eef4fa" stroke="#c9d6e2" stroke-width="1"/>
  <rect x="36" y="154" width="26" height="36" fill="#2d8659"/>
  <text x="49" y="168" text-anchor="middle" class="w18">DE</text>
  <text x="49" y="182" text-anchor="middle" class="w18">PB</text>
  <path d="M76,172 L300,172" stroke="#0055a0" stroke-width="1.8"/>
  <rect x="300" y="164" width="14" height="16" fill="#7fa8cc"/>
  <path d="M314,172 L360,172" stroke="#2d8659" stroke-width="1.8" stroke-dasharray="4,3"/>
  <circle cx="372" cy="172" r="7" fill="#333"/>
  <text x="230" y="192" text-anchor="middle" class="n18">DE = distribuidor de EDIFICIO (armario principal) · DP = de PLANTA</text>

  <path d="M68,172 L68,60" stroke="#e89822" stroke-width="3"/>
  <path d="M32,207 L68,207" stroke="#e89822" stroke-width="3"/>
  <text x="78" y="210" class="k18">SUBSISTEMA VERTICAL — fibra MULTIMODO entre plantas</text>


  <rect x="424" y="34" width="234" height="176" rx="5" fill="#e6f2ec"/>
  <text x="541" y="52" text-anchor="middle" class="k18">SUBSISTEMA DE CAMPUS</text>
  <rect x="440" y="64" width="60" height="40" rx="3" fill="#2d8659"/>
  <text x="470" y="88" text-anchor="middle" class="w18">EDIFICIO A</text>
  <rect x="580" y="64" width="60" height="40" rx="3" fill="#2d8659"/>
  <text x="610" y="88" text-anchor="middle" class="w18">EDIFICIO B</text>
  <path d="M500,84 L580,84" stroke="#0055a0" stroke-width="2.4"/>
  <text x="540" y="78" text-anchor="middle" class="n18">fibra MONOMODO</text>
  <text x="434" y="124" class="d18">Une el distribuidor de campus con los</text>
  <text x="434" y="136" class="d18">distribuidores de cada edificio</text>
  <text x="434" y="156" class="g18">EL CABLEADO VIVE 20 O 30 AÑOS</text>
  <text x="434" y="168" class="d18">y un conmutador, 5 o 7: por eso se</text>
  <text x="434" y="180" class="d18">sobredimensiona deliberadamente</text>
  <text x="434" y="192" class="n18">Elementos: armario, panel de</text>
  <text x="434" y="204" class="n18">parcheo, toma, latiguillo y canalización</text>

  <rect x="30" y="222" width="628" height="24" rx="4" fill="#0055a0"/>
  <text x="344" y="238" text-anchor="middle" class="w18">CANAL MÁXIMO = 100 METROS = 90 m de cable horizontal FIJO + 10 m de LATIGUILLOS</text>
  <text x="344" y="260" text-anchor="middle" class="r18">Si la toma está a 95 m del armario, el enlace NO cumple la norma aunque el equipo funcione: la solución es un armario intermedio</text>

  <rect x="30" y="272" width="308" height="52" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="184" y="290" text-anchor="middle" class="k18">PLANO 1 — CABLEADO GENÉRICO</text>
  <text x="184" y="304" text-anchor="middle" class="d18">ISO/IEC 11801 · EN 50173 (UNE-EN) · TIA-568</text>
  <text x="184" y="317" text-anchor="middle" class="n18">Regula el cableado de la red local: categorías, clases, distancias</text>

  <rect x="350" y="272" width="308" height="52" rx="5" fill="none" stroke="#e89822" stroke-width="1.5"/>
  <text x="504" y="290" text-anchor="middle" class="k18">PLANO 2 — INFRAESTRUCTURA DEL EDIFICIO (ICT)</text>
  <text x="504" y="304" text-anchor="middle" class="d18">Art. 55 Ley 11/2022 · RDL 1/1998 · RD 346/2011</text>
  <text x="504" y="317" text-anchor="middle" class="n18">Regula la obra civil: recintos RITI/RITS/RITU, registros, proyecto</text>

  <text x="340" y="344" text-anchor="middle" class="g18">Son planos DISTINTOS y COMPATIBLES: en una obra municipal nueva hay que cumplir los DOS</text>

  <text x="670" y="368" text-anchor="end" class="n18">[Fuente: ISO/IEC 11801-1:2017 · Ley 11/2022 · RD 346/2011]</text>
</svg>
```

---

## D19 · 802.1X y las medidas del ENS sobre la red local

**Sección**: §6.2 y §6.3 — Seguridad, control de acceso y adecuación al ENS
**Propósito**: Cerrar el tema uniendo el mecanismo técnico —los tres papeles de 802.1X y la asignación dinámica de VLAN— con la norma que lo exige, con las cuatro medidas `mp.com` verificadas literalmente contra el BOE.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 406" role="img" aria-label="Arriba, los tres papeles del control de acceso IEEE 802.1X: el suplicante en el equipo, el autenticador que es el conmutador o el punto de acceso y mantiene el puerto sin servicio hasta que la autenticación tenga éxito, y el servidor de autenticación RADIUS que además devuelve la VLAN que corresponde al usuario; abajo, las cuatro medidas de protección de las comunicaciones del anexo II del Esquema Nacional de Seguridad con su aplicación por categoría, destacando que la separación de flujos no aplica en categoría básica">
  <style>.h19{font:700 13px system-ui,sans-serif;fill:#0055a0}.k19{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.d19{font:8.5px system-ui,sans-serif;fill:#333}.n19{font:8px system-ui,sans-serif;fill:#666}.w19{font:700 9px system-ui,sans-serif;fill:#fff}.g19{font:700 9px system-ui,sans-serif;fill:#2d8659}.r19{font:700 9px system-ui,sans-serif;fill:#d13c3c}</style>
  <defs><marker id="m19" markerWidth="8" markerHeight="8" refX="7" refY="3" orient="auto"><path d="M0,0 L7,3 L0,6 z" fill="#0055a0"/></marker></defs>
  <text x="340" y="20" text-anchor="middle" class="h19">IEEE 802.1X y las medidas del ENS que se predican de la red local</text>

  <text x="30" y="42" class="k19">CONTROL DE ADMISIÓN 802.1X — LOS TRES PAPELES</text>
  <rect x="30" y="50" width="150" height="48" rx="4" fill="#0055a0"/>
  <text x="105" y="70" text-anchor="middle" class="w19">SUPLICANTE</text>
  <text x="105" y="86" text-anchor="middle" class="w19">el equipo que se conecta</text>
  <path d="M182,74 L226,74" stroke="#0055a0" stroke-width="1.6" marker-end="url(#m19)"/>
  <text x="204" y="68" text-anchor="middle" class="n19">EAPOL</text>
  <rect x="230" y="50" width="180" height="48" rx="4" fill="#e89822"/>
  <text x="320" y="70" text-anchor="middle" class="w19">AUTENTICADOR</text>
  <text x="320" y="86" text-anchor="middle" class="w19">el conmutador o el punto de acceso</text>
  <path d="M412,74 L456,74" stroke="#0055a0" stroke-width="1.6" marker-end="url(#m19)"/>
  <text x="434" y="68" text-anchor="middle" class="n19">RADIUS</text>
  <rect x="460" y="50" width="198" height="48" rx="4" fill="#2d8659"/>
  <text x="559" y="70" text-anchor="middle" class="w19">SERVIDOR DE AUTENTICACIÓN</text>
  <text x="559" y="86" text-anchor="middle" class="w19">verifica contra el directorio corporativo</text>

  <rect x="30" y="106" width="308" height="36" rx="4" fill="#fbeaea"/>
  <text x="184" y="122" text-anchor="middle" class="r19">PUERTO NO CONTROLADO — sin autenticar</text>
  <text x="184" y="135" text-anchor="middle" class="d19">Solo deja pasar tramas EAPOL. Ni IP, ni DHCP, ni nada más</text>
  <rect x="350" y="106" width="308" height="36" rx="4" fill="#e6f2ec"/>
  <text x="504" y="122" text-anchor="middle" class="g19">PUERTO CONTROLADO — tras autenticar</text>
  <text x="504" y="135" text-anchor="middle" class="d19">El servidor devuelve la VLAN: la segmentación sigue a la persona</text>

  <text x="30" y="164" class="k19">ANEXO II DEL ENS — mp.com, PROTECCIÓN DE LAS COMUNICACIONES (verificado contra el BOE)</text>
  <rect x="30" y="172" width="628" height="17" fill="#0055a0"/>
  <text x="36" y="185" class="w19">MEDIDA</text>
  <text x="104" y="185" class="w19">DENOMINACIÓN LITERAL</text>
  <text x="340" y="185" class="w19">DIM.</text>
  <text x="386" y="185" class="w19">APLICACIÓN POR CATEGORÍA O NIVEL</text>
  <rect x="30" y="190" width="628" height="17" fill="#f7f9fb"/>
  <text x="36" y="202" class="d19">mp.com.1</text>
  <text x="104" y="202" class="d19">Perímetro seguro</text>
  <text x="340" y="202" class="d19">Todas</text>
  <text x="386" y="202" class="d19">Aplica en LAS TRES categorías</text>
  <rect x="30" y="208" width="628" height="17" fill="#eef4fa"/>
  <text x="36" y="220" class="d19">mp.com.2</text>
  <text x="104" y="220" class="d19">Protección de la confidencialidad</text>
  <text x="340" y="220" class="d19">C</text>
  <text x="386" y="220" class="d19">BAJO aplica · MEDIO +R1 · ALTO +R1+R2+R3</text>
  <rect x="30" y="226" width="628" height="17" fill="#f7f9fb"/>
  <text x="36" y="238" class="d19">mp.com.3</text>
  <text x="104" y="238" class="d19">Protección de la integridad y la autenticidad</text>
  <text x="340" y="238" class="d19">I, A</text>
  <text x="386" y="238" class="d19">BAJO aplica · MEDIO +R1+R2 · ALTO +R1 a R4</text>
  <rect x="30" y="244" width="628" height="17" fill="#fdf3e3"/>
  <text x="36" y="256" class="d19">mp.com.4</text>
  <text x="104" y="256" class="d19">Separación de flujos de información en la red</text>
  <text x="340" y="256" class="d19">Todas</text>
  <text x="386" y="256" class="d19">BÁSICA: NO APLICA · MEDIA +[R1/R2/R3] · ALTA +[R2/R3]+R4</text>

  <rect x="30" y="268" width="628" height="32" rx="3" fill="#eef4fa"/>
  <text x="40" y="281" class="d19"><tspan class="k19">Refuerzos de mp.com.4</tspan>   R1 segmentación lógica básica MEDIANTE VLAN, segregando en USUARIOS, SERVICIOS y ADMINISTRACIÓN</text>
  <text x="40" y="294" class="d19">R2 segmentación lógica avanzada mediante VPN · R3 segmentación física con medios separados · R4 puntos de interconexión controlados</text>
  <rect x="30" y="304" width="628" height="32" rx="3" fill="#f7f9fb"/>
  <text x="40" y="317" class="d19"><tspan class="k19">Otras medidas de red</tspan>   mp.eq.4 otros dispositivos conectados a la red (multifunción, multimedia, IoT y BYOD) · mp.if.1 áreas separadas</text>
  <text x="40" y="330" class="d19">op.acc.5 mecanismo de autenticación · op.exp.8 registro de la actividad con base de tiempo común · op.mon.1 detección de intrusión</text>

  <rect x="30" y="346" width="628" height="30" rx="5" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <text x="344" y="365" text-anchor="middle" class="r19">mp.com.4.2 — «Si se emplean comunicaciones inalámbricas, será en un SEGMENTO SEPARADO»: requisito normativo</text>

  <text x="670" y="394" text-anchor="end" class="n19">[Fuente: RD 311/2022 anexo II · IEEE 802.1X · CCN-STIC-816]</text>
</svg>
```
