# Tema 37 — Validación

> **Título oficial**: Redes locales. Tipología. Técnicas de transmisión. Métodos de acceso. Dispositivos de interconexión.
>
> **Versión**: v1.0 — **Pendiente de validación por María, Ana y el IAM**
> **Fecha**: 2026-08-27

---

## 1. Cobertura del temario oficial

El enunciado oficial (BOAM 10.032, tema 37) enumera **cinco materias encadenadas**. Correspondencia con las secciones del contenido:

| Enunciado oficial | Sección | Estado |
|---|---|---|
| Redes locales | §1 | ✅ Completo |
| Tipología | §2 | ✅ Completo |
| Técnicas de transmisión | §3 | ✅ Completo |
| Métodos de acceso | §4 | ✅ Completo |
| Dispositivos de interconexión | §5 | ✅ Completo |
| — Normativa y aplicación en la Administración (no está en el enunciado, sí en el esqueleto) | §6 | ✅ Completo |

El **esqueleto de partida** se ha seguido **literalmente**: sus seis bloques de primer nivel son las seis secciones, sus veintidós bloques de segundo nivel son los veintidós epígrafes y sus diez bloques de tercer nivel son los diez subepígrafes. **Es el segundo tema de la serie cuyo esqueleto mapea sin ningún ajuste a los tres niveles de numeración**, tras el T34 y a diferencia de lo ocurrido en T27 y T30, cuya decisión de mapeo sigue pendiente de validación.

## 2. Contenido teórico

- **6 secciones · 22 epígrafes · 10 subepígrafes** (numeración de tres niveles, `N.M.K`, coherente con el resto de la serie técnica).
- **~23.000 palabras** medidas con `wc -w`. Es el **tercer tema más extenso de la serie**, por detrás de T32 (≈25.000) y T33 (≈24.500), y por delante de T34 (≈21.500). La causa es estructural: el enunciado encadena **cinco materias completas**, cada una de las cuales tiene entidad propia.
- **4 tipos de callout**: `[DATO CLAVE]`, `[EJERCICIO RESUELTO]`, `[EJEMPLO DE APLICACIÓN EN EL AYTO]` y `[RELACIÓN CON OTROS TEMAS]`.
- **Caso de referencia transversal**: la red local de una Oficina de Atención a la Ciudadanía de distrito, en un edificio municipal de tres plantas, conectada con el centro de proceso de datos del IAM. Atraviesa las seis secciones y enlaza con los tres casos prácticos.
- Cierre con un bloque de **«los diez datos que no se pueden fallar»**, no numerado, a modo de resumen memorístico de última hora.
- **Sin fragmentos de código.** Decisión deliberada, igual que en T26, T28, T29, T30, T32, T33 y T34: el enunciado no menciona ningún lenguaje y lo memorizable son **tamaños de trama, tiempos, distancias, categorías de cableado, numeración de normas IEEE y códigos del ENS**. Se han concentrado en tablas y en los diagramas D8, D10, D13, D14, D16 y D17.

## 3. Fronteras con otros temas, declaradas de entrada

Es el punto que más conviene que **valide el IAM**, porque el enunciado oficial de este tema **solapa con cuatro temas** del bloque técnico. El reparto adoptado, explicitado en el propio contenido:

| Materia | Tema | Reparto adoptado |
|---|---|---|
| Medios de transmisión, modos de comunicación, equipos de interconexión y conmutación, redes inalámbricas | **T33** | El T33 los cubre **en general**; el T37 los recorre **solo en su versión de red local**: el par trenzado tal y como lo instala un cableado estructurado, el punto de acceso del vestíbulo de una junta de distrito |
| Modelo OSI, modelo TCP/IP y protocolos de la pila | **T34** | Aquí se usan como **regla para clasificar dispositivos** por capa; no se describen las capas 3 a 7 |
| Administración de la red de área local: usuarios, dispositivos, monitorización y control de tráfico | **T30** | Frontera enunciada como consigna: **el T37 describe la red y el T30 la administra**. Aquí se explica qué es una VLAN y cómo viaja su etiqueta; allí, cómo se planifican, se despliegan y se supervisan |
| Seguridad perimetral, acceso remoto, VPN, y principios del ENS y del ENI | **T36 y T39** | Aquí solo §6.2 y §6.3, y únicamente en lo que la normativa exige a la **red local** |

**Solapamiento residual asumido y por qué.** Con el **T33** hay tres puntos de contacto inevitables —topologías, medios guiados y no guiados, y equipos de interconexión— que **el temario oficial pide en los dos temas**. Se ha optado por **desarrollarlos en ambos con enfoque distinto** en lugar de remitir, porque un opositor que estudie el T37 no puede quedarse sin saber qué es un par trenzado. Con el **T30** el solapamiento se concentra en **VLAN y árbol de expansión**, resuelto con la consigna «describir frente a administrar». **Se solicita al IAM que confirme este reparto**, en los mismos términos en que se pidió al generar el T30.

## 4. Fuentes

- **Tier 1**: 22 referencias (familia IEEE 802 completa, ISO/IEC 11801, EN 50173, TIA-568, ISO/IEC 9314 para FDDI, ISO/IEC 7498-1, RFC 1122 y 7042, ENS, Ley 11/2022, RD 346/2011, RDL 1/1998, Ley 40/2015 y Ley 9/2017).
- **Tier 2**: 11 referencias (manuales canónicos de Tanenbaum, Kurose, Stallings, Spurgeon y Gast; artículos fundacionales de Metcalfe y Boggs y de Abramson; guías CCN-STIC; Wi-Fi Alliance; páginas de los grupos de trabajo del IEEE; CNAF).
- **Tier 3**: 3 referencias de contexto municipal.
- **Verificación contra fuente oficial** (no de memoria):
  - **ENS**: extraído del PDF consolidado del BOE (`BOE-A-2022-7191`) con `pdftotext -layout`. De ahí proceden **literalmente** el bloque `mp.com` completo del anexo II —las cuatro medidas con su denominación exacta, sus dimensiones, sus tablas de aplicación por categoría y el texto de sus requisitos y de los cuatro refuerzos de `mp.com.4`—, y las medidas **`mp.eq.4`** y **`mp.if.1`**.
  - **Ley 11/2022**: descargado el PDF del texto consolidado del BOE (`BOE-A-2022-10757`) y extraído con `pdftotext -layout`. De ahí proceden el **artículo 55** con sus cinco apartados, el **artículo 63** y el **artículo 88**, además de la **disposición adicional tercera**.
  - **IEEE 802.11be y 802.11bn**: verificadas en línea en agosto de 2026 la fecha de publicación de Wi-Fi 7 (**22 de julio de 2025**) y el estado de borrador de Wi-Fi 8, con aprobación prevista para **2028**.
  - **IEEE 802.3df y P802.3dj**: verificado que 802.3df-2024 se aprobó el **16 de febrero de 2024** y normaliza 800 Gbit/s, y que P802.3dj está en desarrollo en 2026 con 1,6 Tbit/s como objetivo.
  - **ISO/IEC 11801-1:2017**: verificada la correspondencia entre categorías y clases y la incorporación en la edición de 2017 de las clases **I** y **II** y de las categorías **8.1** y **8.2**.

### 4.1. Tres datos que la verificación contra fuente primaria ha permitido afinar

1. **El artículo de la Ley 11/2022 que ampara las ICT es el 55**, «Infraestructuras comunes y redes de comunicaciones electrónicas en los edificios», y la **disposición adicional tercera** remite además al **Real Decreto-ley 1/1998**. Varias fuentes secundarias siguen citando el artículo 45 de la derogada Ley 9/2014.
2. **El artículo 88 clasifica el uso del dominio público radioeléctrico en común, especial y privativo**, y establece que **el uso común no precisa de ningún título habilitante**. Es el precepto que da cobertura jurídica al despliegue de Wi-Fi municipal, y **prácticamente ningún temario de oposición lo recoge**, pese a ser directamente examinable en la parte de normativa.
3. **`mp.com.4` se denomina «Separación de flujos de información en la red»**, no «segregación de redes» —su nombre en el derogado RD 3/2010—, y **`mp.com.3` es «Protección de la integridad y de la autenticidad»**, en ese orden. Son las mismas dos correcciones anotadas al generar el T30 y el T34, confirmadas aquí por tercera vez contra el PDF.

## 5. Test (60 preguntas)

- **60 preguntas** de 3 opciones (A/B/C), formato oficial de la oposición, con penalización de **1/3** en el motor de corrección.
- **Distribución de la respuesta correcta: 20 A / 20 B / 20 C**, verificada por script. Se fijó la secuencia de letras **antes** de redactar (lección aprendida en T23); el primer recuento dio 19/20/21 y se corrigió **intercambiando el texto de las opciones A y C de la pregunta 53**, no solo su letra, conforme al procedimiento documentado.
- Reparto por materia: P1-P8 concepto y normalización IEEE 802 · P9-P18 tipología y topologías · P19-P30 técnicas de transmisión · P31-P42 métodos de acceso al medio · P43-P54 dispositivos de interconexión · P55-P60 normativa en la Administración pública.
- Verificación automática: 60 preguntas, 3 opciones únicas por pregunta, coincidencia exacta entre el texto de la opción correcta y el de la solución, y referencia a epígrafe y fuente en las 60.
- **Cinco preguntas de cálculo o de razonamiento cuantitativo** (P10 malla completa, P23 y P24 relación entre baudios y bits, P36 diámetro del dominio de colisión al cambiar de velocidad, P53 recuento de dominios de difusión), pensadas para la parte práctica del examen.

## 6. Casos prácticos (3)

Los tres se sitúan en el Ayuntamiento de Madrid y comparten la red de referencia del tema:

1. **Diseño de la red local de una Oficina de Atención a la Ciudadanía** (§2, §3 y §6.1): medios y categorías por tramo, subsistemas del cableado estructurado con dos tomas que incumplen la distancia, topología y dimensionado del enlace ascendente por sobresuscripción, y elección de la norma de PoE con la advertencia sobre el presupuesto de potencia del conmutador y sobre la redacción sin marca conforme al art. 126.6 de la LCSP.
2. **Diagnóstico de cuatro incidencias simultáneas** (§3, §4 y §5): discordancia de dúplex con colisiones tardías, bucle de capa 2 y tormenta de difusión, saturación por contienda de la red inalámbrica con el problema de la tasa ancla, y enlace de 112 metros que degrada sin llegar a cortar.
3. **Segmentación, control de acceso y adecuación al ENS** (§5.2.2, §6.2 y §6.3): cinco hallazgos de auditoría resueltos contra `mp.com.4` y su refuerzo R1, `mp.com.4.2`, 802.1X con asignación dinámica de VLAN, `mp.if.1` y `op.exp.8`.

Cada caso suma **10 puntos** repartidos en cuatro cuestiones, con solución orientativa y tabla de criterios de evaluación.

## 7. Diagramas (19)

Los 19 diagramas son SVG inline, sin dependencias externas, con `role="img"` y `aria-label` descriptivo en español, y con las clases CSS sufijadas por número para evitar colisiones de estilo entre ellos.

**Los seis que hay que memorizar**, por orden de rentabilidad: **D16** (dispositivos por capa con sus dominios de colisión y de difusión), **D13** (CSMA/CD y la regla de los 64 octetos), **D14** (CSMA/CA con sus tiempos y el nodo oculto), **D17** (la etiqueta 802.1Q campo a campo), **D5** (topología física frente a lógica) y **D19** (las cuatro medidas `mp.com` con su aplicación por categoría).

**Reglas de composición aplicadas desde el origen**, conforme a las lecciones acumuladas en la serie:

- Atribución `[Fuente: …]` a **12 px o más** del borde inferior del `viewBox` y a **12 px o más** del último elemento dibujado.
- **Ningún elemento mezcla `class` con el atributo de presentación `fill`**: cuando hace falta un color distinto del de la clase se usa `style="fill:…"`, porque en la cascada CSS **la clase gana al atributo**. Es el cuarto modo de fallo silencioso documentado en la serie, y **ninguna de las tres sondas de QA lo detecta** porque no es un problema de geometría.
- Revisión de **tildes también en mayúsculas** y en los `aria-label`, que es donde más se escapan.

## 8. QA realizado

- **Validación XML de los 19 SVG antes de medir nada**, conforme a la lección del T32: un SVG mal formado pasa el recuento de elementos y el `getBBox` con un falso OK, porque el parser HTML es tolerante y el elemento roto mide `0×0`.
- **Render real** con Chrome headless y sonda `getBBox` sobre el `index.html` generado, forzando la clase activa en la pestaña de diagramas, con los **tres chequeos**: desbordes del `viewBox`, colisiones entre textos y **texto solapado con un `<rect>` que no lo contiene**.
- **Revisión visual de las 19 capturas**, una a una, y repetida tras cada retoque de los `.md`. Cazó **seis defectos que ninguna sonda ve**: un arco que se salía por encima de su rótulo (D5), tres flechas idénticas para símplex, semidúplex y dúplex (D6), un conector que atravesaba el texto de una rama vecina (D12), un muro dibujado como `<path>` sobre un rótulo (D14), dos guías discontinuas que cruzaban una línea de texto (D17) y una línea de troncal vertical que atravesaba las cajas de los distribuidores de planta (D18).
- **Lección nueva y reutilizable**: las tres sondas de `qa_svg.py` comparan texto contra `viewBox`, contra texto y contra `<rect>`, pero **ningún `<path>` entra en la comparación**. Es un quinto modo de fallo silencioso, que se suma a los cuatro ya documentados en la serie.
- **Integridad del test**: 60 preguntas, 3 opciones únicas por pregunta, coincidencia exacta entre el texto de la opción correcta y el de la solución, referencia presente en las 60. Distribución **20 A / 20 B / 20 C**.
- **Motor de test** probado sobre HTTP, no sobre `file://`.
- **Asteriscos crudos y tablas sin convertir**: recuento en el `index.html` tras excluir `<script>`, `<svg>`, `<style>` y `<pre><code>`. Ambos deben dar **0**.

## 9. Puntos que se someten a validación

1. **El reparto de fronteras con T33, T30, T34, T36 y T39** descrito en el punto 3. Es la decisión de mayor calado del tema y conviene fijarla con el IAM **antes de generar el T36**, que vuelve a limitar con este.
2. **La extensión.** ~23.000 palabras es mucho, pero es consecuencia directa de un enunciado con cinco materias. Si María o Ana consideran que hay que reducir, el candidato natural es §3.3 (modulación y codificación), que es la parte más técnica.
3. **El tratamiento de las tecnologías retiradas** (Token Ring, Token Bus, FDDI, concentrador, coaxial). Se han desarrollado con detalle porque **el temario oficial las pide expresamente** al hablar de métodos de acceso y de dispositivos, y porque son materia cerrada y estable. Se somete a validación si el nivel de detalle es el adecuado.
4. **La inclusión del artículo 88 de la Ley 11/2022** sobre el régimen del espectro. Es un dato que ningún temario recoge y que exige criterio: se ha incluido porque el enunciado del tema 37 no tiene bloque normativo propio y el esqueleto sí pide una sección de aplicación en la Administración pública.
5. **Los datos de actualidad de 2025 y 2026** (Wi-Fi 7 publicada, Wi-Fi 8 en borrador, 800 Gbit/s normalizados). Aportan valor frente a los temarios del mercado, pero **envejecen**: conviene revisarlos en cada convocatoria.
