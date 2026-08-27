# Tema 37 — Changelog

> **Título oficial**: Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión.

---

## v1.0 — 2026-08-27 — Primera versión

Generación completa del tema desde el esqueleto oficial `Test_Prompting/temas agosto/37.md`, siguiendo el patrón de la serie técnica (plantilla de referencia: **T34**).

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | 6 secciones · 22 epígrafes · 10 subepígrafes · **~23.000 palabras** |
| Diagramas SVG inline | **19** |
| Banco de test | **60 preguntas** A/B/C, balanceadas **20/20/20** |
| Casos prácticos | **3**, de 10 puntos cada uno |
| Fuentes | 22 Tier 1 · 11 Tier 2 · 3 Tier 3 |
| Pestañas del `index.html` | 8 (Inicio, Contenido, Índice, Diagramas, Test, Casos, Validación, Fuentes) |

### Decisiones de generación

1. **Estructura fiel al esqueleto, sin ningún ajuste.** Es el segundo tema de la serie cuyo esqueleto mapea **exactamente** a los tres niveles de numeración: los seis bloques `##` son las seis secciones, los veintidós `###` son los epígrafes y los diez `####` son los subepígrafes. No ha hecho falta promover ni degradar ningún nivel, como sí ocurrió en T27 y T30.

2. **Fronteras con T33, T30, T34, T36 y T39 declaradas de entrada.** Es la decisión de mayor calado del tema, porque el enunciado oficial **solapa con cuatro temas**. El reparto adoptado se enuncia en las «Convenciones» del contenido y se recoge en el punto 3 del documento de validación, con una consigna que conviene fijar con el IAM: **el T37 describe la red y el T30 la administra**. El solapamiento residual con el T33 en topologías, medios y equipos se ha resuelto **desarrollándolo en ambos con enfoque distinto** en lugar de remitir, porque el temario oficial lo pide en los dos.

3. **Normativa verificada contra el BOE, no de memoria.** Se descargó el PDF del texto consolidado de la **Ley 11/2022** (`BOE-A-2022-10757`) y se extrajo con `pdftotext -layout`. De ahí proceden literalmente el **artículo 55** (infraestructuras comunes y redes de comunicaciones electrónicas en los edificios), el **artículo 63** (integridad y seguridad de las redes), el **artículo 88** (títulos habilitantes para el uso del dominio público radioeléctrico) y la **disposición adicional tercera**. El bloque `mp.com` del anexo II del **ENS**, junto con `mp.eq.4` y `mp.if.1`, procede del PDF consolidado de `BOE-A-2022-7191`.

4. **El artículo 88 como aportación diferencial.** El régimen de **uso común** del dominio público radioeléctrico —que **no precisa de título habilitante** pero **carece de protección frente a interferencias**— es el fundamento jurídico del despliegue de Wi-Fi municipal y **prácticamente ningún temario de oposición lo recoge**. Se ha incorporado a §3.5.2, a §6.1, al diagrama D11 y a la pregunta 57 del test. En el mismo barrido se corrigió una atribución frecuente en fuentes secundarias: **las ICT cuelgan del artículo 55 de la Ley 11/2022**, no del artículo 45 de la derogada Ley 9/2014.

5. **Datos técnicos de actualidad verificados en línea en agosto de 2026.** **IEEE 802.11be (Wi-Fi 7) se publicó el 22 de julio de 2025**; **802.11bn (Wi-Fi 8) está en borrador**, con aprobación prevista para **2028** y con la **fiabilidad ultraalta**, no la velocidad de pico, como objetivo declarado; **802.3df-2024** normalizó los **800 Gbit/s** el 16 de febrero de 2024 y **P802.3dj** llegará a **1,6 Tbit/s**. Son datos que distinguen un temario al día de uno desfasado, y que **envejecen**: se anotan en el punto 5 del documento de validación para revisarlos en cada convocatoria.

6. **Tratamiento deliberado de las tecnologías retiradas.** Token Ring, Token Bus, FDDI, el concentrador y el coaxial se desarrollan con detalle, no de pasada, por dos razones: **el temario oficial las pide expresamente** al hablar de métodos de acceso y de dispositivos, y son preguntas cerradas y rentables; y porque **la red local moderna se entiende por contraste con ellas** —un conmutador no se entiende sin haber entendido antes por qué era un problema el concentrador—.

7. **Sin fragmentos de código.** Decisión deliberada, igual que en T26, T28, T29, T30, T32, T33 y T34: el enunciado no menciona ningún lenguaje y lo memorizable son tamaños de trama, tiempos, distancias, categorías de cableado, numeración de normas IEEE y códigos del ENS. Se han concentrado en tablas y en los diagramas D8, D10, D13, D14, D16 y D17.

8. **Secuencia de letras del test fijada antes de redactar.** Aplicando la lección de T23, se definió de antemano la secuencia de 60 respuestas correctas con 20 de cada letra. El primer recuento por script dio **19/20/21** y se corrigió **intercambiando el texto de las opciones A y C de la pregunta 53** —no solo su letra—, conforme al procedimiento documentado. Resultado final verificado: **20/20/20**.

9. **Reglas de composición de SVG aplicadas desde el origen.** Los 19 diagramas se diseñaron ya con la atribución `[Fuente: …]` a **12 px o más** del borde inferior del `viewBox` y a **12 px o más** del último elemento dibujado, conforme a las lecciones de T28 y T31.

10. **Colores por `style`, nunca por atributo `fill` sobre un elemento con clase.** Aplicada desde el primer diagrama la lección de T33 y T34: en un SVG, **la clase CSS gana al atributo de presentación**, de modo que un `fill="#fff"` sobre un elemento con clase gris se pintaría gris. Cuando ha hecho falta un color distinto se ha usado **`style="fill:…"`**. Comprobado con `grep -n 'class="[a-z]*[0-9]*" fill='` sobre el fichero de diagramas: **sin coincidencias**.

11. **El `build_t37.py` nace con los dos bugs del conversor ya corregidos**: el `inline()` admite negrita con cursiva anidada (bug de T26 y T27) y el manejador de blockquote convierte las tablas markdown embebidas en un callout mediante el helper `bq_body()` (bug de T34 y T35). Además, **el contenido se ha redactado sin tablas dentro de callouts**, que es la recomendación de fondo de esa lección.

### QA realizado

- **Validación XML de los 19 SVG antes de medir nada**, conforme a la lección del T32: un SVG mal formado pasa el recuento de elementos y el `getBBox` con un falso OK, porque el parser HTML es tolerante y el elemento roto mide `0×0`.
- **Integridad del test**: 60 preguntas, 3 opciones únicas por pregunta, coincidencia exacta entre el texto de la opción correcta y el de la solución, referencia presente en las 60. Distribución **20 A / 20 B / 20 C**.
- **Render real** con Chrome headless y sonda `getBBox` sobre el `index.html` generado, forzando la clase activa en la pestaña de diagramas, con los **tres chequeos** de `_tools-qa/qa_svg.py`: desbordes del `viewBox`, colisiones entre textos y **texto solapado con un `<rect>` que no lo contiene**.
- **Revisión visual de las 19 capturas**, una a una, porque el QA programático no ve rótulos que no cuadran con lo que encabezan ni flechas que apuntan a un hueco entre dos cajas.
- **Motor de test** probado sobre HTTP, no sobre `file://`, donde el `<script>` no se ejecuta en este entorno.
- **Asteriscos crudos y tablas markdown sin convertir**: recuento en el `index.html` tras excluir `<script>`, `<svg>`, `<style>` y `<pre><code>`. Ambos dan **0**.
- **Tildes en mayúsculas** dentro de los SVG y en los `aria-label`, que es donde más se escapan (lección de T33).

### Dos lecciones nuevas para la serie, aprendidas al generar este tema

**1. `getBBox` no mira los `<path>`: es un quinto modo de fallo silencioso.** Las tres sondas de `qa_svg.py` comparan texto contra `viewBox`, texto contra texto y texto contra `<rect>`. **Ningún `<path>` entra en la comparación.** Eso dejó pasar, con el QA en verde, un muro dibujado como `<path>` que cruzaba un rótulo en D14 y dos flechas de retorno que se apoyaban justo encima del pie de su caja en D6. Solo se vieron en la captura. Regla derivada: dejar **8 px o más** entre cualquier `<path>` —flecha, muro, subrayado, conector— y la caja de texto más próxima. Y su corolario de composición: **un conector de un árbol no puede barrer por encima de una rama vecina**; en D12 la línea que unía «asignación dinámica» con sus tres hijos atravesaba el texto de la rama estática y hubo que reencaminarla por debajo del bloque.

**2. Estimar el ancho del texto a ojo no sirve: hay que medirlo.** Calcular «unos 4,2 px por carácter a 8,5 px» produjo **21 desbordes reales** en la primera pasada. El ancho real oscila entre **3,8 y 5,0 px por carácter** según las letras, y un `<tspan>` en negrita dentro de un `<text>` lo dispara. El método que funciona: clonar `qa_svg.py` cambiando su bloque `JS` para que **vuelque `x`, `x + width` e `y` de cada `<text>`** en lugar de listar incidencias, y filtrar por `x < 18` o `x + width > 660`. Da en una sola pasada la lista exacta de qué acortar y cuánto.

**3. Método de verificación normativa, ya rutinario.** El índice consolidado del BOE es al derecho lo que `rfc-index.txt` es a lo técnico: `curl` sobre el PDF consolidado más `pdftotext -layout` y `grep` de cada artículo citado. Coste: dos minutos. En este tema reveló que **las ICT cuelgan del artículo 55 de la Ley 11/2022** —no del artículo 45 de la derogada Ley 9/2014, como repiten varias fuentes secundarias— y la existencia del **artículo 88**, con el régimen de uso común del espectro que ampara el Wi-Fi municipal sin título habilitante y sin protección frente a interferencias.
