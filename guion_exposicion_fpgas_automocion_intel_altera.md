# Silicio sobre Ruedas: Qué Necesitaba el Sector Automovilístico de las FPGAs para Impulsar la Compra de Altera por Intel

> **Asignatura:** Dispositivos Electrónicos Programables  
> **Formato objetivo:** 10 diapositivas en formato panorámico 16:9 (escala equivalente a `Computación Heterogénea.pdf`)  
> **Duración estimada de exposición oral:** 8 – 10 minutos (~45–60 s por diapositiva)  
> **Estética de referencia:** *Engineering Blueprint / Silicon Architecture* (cuadrícula técnica, diagramas esquemáticos limpios, tarjetas estructuradas y matrices diagnósticas coherentes con `Computación Heterogénea.pdf` y `Pelayo_debate.pdf`)  
> **Relación con otras exposiciones del aula:** Continúa y profundiza exactamente en la rama que quedó apuntada en la **diapositiva 9** de `Pelayo_debate.pdf` (*«Diversificación estratégica: 5G y Automoción — sistemas ADAS»*) y aplica al automóvil la dualidad **arquitectura temporal (CPU/GPU) vs. arquitectura espacial (FPGA)** presentada en `Computación Heterogénea.pdf`, conectándola con los apuntes oficiales de clase (`Introducción FPGAs.pdf` y `Arquitectura PLDs.pdf`).

---

## Nota de Uso para el Pipeline (NotebookLM → `.pptx` → `.html`)

Este documento es la **Fuente Única de Verdad (SSOT)** del proyecto. Cada diapositiva separa de forma estricta:
- **`Contenido visual para la diapositiva`** y **`Propuesta de diagrama técnico`**: es lo **ÚNICO** que debe aparecer en las diapositivas generadas por NotebookLM y en la presentación final en HTML.
- **`Guion oral del ponente`**: texto hablado para el orador y para el **Modo Presentador** del HTML final (**NO** debe volcarse en el área visual de las diapositivas).

*(Consulta `AGENTS.md` para obtener el prompt exacto de NotebookLM, el protocolo de auditoría del `.pptx` y la especificación técnica completa del `.html` final).*

---

## Mapa Mental de Memoria Rápida (Las 10 Diapositivas en 10 Anclas)

Usa esta tabla para memorizar de memoria el hilo completo de la exposición antes de salir a presentar:

| Diap. | Título breve | Dato / Ancla clave para recordar | Tiempo |
|---:|---|---|---:|
| **01** | **Portada: Silicio sobre Ruedas** | Tesis en 3 pilares: coche ADAS → 4 necesidades FPGA → apuesta de Intel ($16.700M). | 0:35 |
| **02** | **La Encrucijada de 2015** | 5 ene 2015 (Audi elige Altera) → 1 jun / 28 dic 2015 (Intel compra Altera por **$16.700M**) + cita de **Brian Krzanich** (*«autonomous driving»*) + crisis de **70–100 ECUs**. | 0:55 |
| **03** | **La Era de la Incertidumbre** | Tabla de clase (FPGA vs. ASIC): ASIC automotriz = **3–5 años** y alto NRE vs. algoritmos ADAS cambiantes y vida útil del coche de **10–15 años** (OTA). | 0:55 |
| **04** | **Fusión de Sensores y Latencia** | **120 km/h = 33,3 m/s** (~3,3 cm/ms). Cámaras + radar 77 GHz + LiDAR → arquitectura espacial FPGA = **latencia determinista (cero *jitter*)**. | 1:00 |
| **05** | **Seguridad Funcional y 4 Dominios** | **AEC-Q100 Grado 2** (-40 a +105 °C), **ISO 26262 (ASIL D)** y el paquete **AFSDP** (TÜV Rheinland, ahorra **12–18 meses-hombre**) + 4 dominios (ADAS, redes/TSN, IVI/HUD, EV). | 1:00 |
| **06** | **Matriz del Silicio Automotriz** | Comparativa **MCU (AURIX)** vs. **GPU (Tegra/Orin)** vs. **FPGA (Cyclone V / Arria 10)** vs. **ASIC (Mobileye EyeQ)**. Conclusión: computación heterogénea. | 0:55 |
| **07** | **Caso Real: Audi zFAS** | Puente con clase: **DE2 Cyclone II → Cyclone V SoC** en Audi A8. **4 chips en la misma PCB**: Altera Cyclone V + Mobileye EyeQ3 + NVIDIA Tegra K1 + Infineon AURIX. | 1:00 |
| **08** | **Estrategia de Intel (2015–2017)** | 3 actos: **2015 Altera ($16.700M)** → **CES 2017 Intel GO (Arria 10 + Atom/Xeon)** → **Marzo 2017 Mobileye ($15.300M)**. Binomio FPGA + ASIC. | 0:50 |
| **09** | **Balance Crítico (2016–2025) y Futuro** | Retrasos 10 nm de Intel, avance de **Xilinx/AMD** (caso **Subaru EyeSight** con Zynq UltraScale+), venta del **51% de Altera a Silver Lake ($8.750M, sept 2025)** y futuro **SDV / Zonal / eFPGA**. | 1:00 |
| **10** | **Conclusiones y Bibliografía** | **3 claves numeradas (`01`, `02`, `03`)** respondiendo directamente a la pregunta + bloque compacto de fuentes primarias. | 0:45 |

**Tiempo total estimado:** ~8 min 55 s (margen ideal para exponer con calma en 8–10 minutos).

---

# Desarrollo Diapositiva por Diapositiva

---

## Diapositiva 1 — Portada: Silicio sobre Ruedas: La Automoción detrás de Intel + Altera

**Subtítulo:** Qué necesidades de FPGAs tenía el sector automovilístico para impulsar la adquisición de Altera por $16.700 millones (2015)

**Idea fuerza:** La compra de Altera por Intel no solo buscaba proteger los centros de datos; también perseguía resolver el cuello de botella tecnológico del automóvil conectado y asistido (ADAS), donde solo la lógica reconfigurable ofrecía determinismo, flexibilidad y certificación de seguridad a la vez.

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Título principal:** Silicio sobre Ruedas: La Automoción detrás de Intel + Altera
- **Subtítulo:** Necesidades de FPGAs en ADAS, fusión de sensores y seguridad funcional en la compra de 2015
- **Tres tarjetas de tesis (lateral izquierdo, estilo `Computación Heterogénea.pdf`):**
  1. **El nuevo coche ADAS:** De la mecánica tradicional a un centro de datos rodante con decenas de sensores y límites térmicos estrictos.
  2. **La brecha del silicio:** Por qué ni los microcontroladores, ni las GPUs ni los ASICs resolvían solos el reto automotriz de 2015.
  3. **La apuesta estratégica ($16.700M):** De la compra de Altera (2015) al Audi zFAS, Mobileye y el vehículo definido por software (SDV).
- **Pie discreto:** Dispositivos Electrónicos Programables · Análisis Técnico y Estratégico

### Propuesta de diagrama técnico
Ilustración isométrica estilo plano técnico (*blueprint*) sobre cuadrícula fina: silueta esquemática de un vehículo moderno visto desde arriba/en perspectiva isométrica con conos de sensores (cámaras, radar frontal/trasero, LiDAR y ultrasonidos) convergiendo hacia un encapsulado central heterogéneo en el chasis donde destacan un dado azul (CPU/SoC) y una matriz terracota de bloques lógicos (FPGA) unidos por trazas de circuito impreso.

### Guion oral del ponente (NO poner en la diapositiva)
> *(~35 segundos)*  
> «Buenos días. En las exposiciones anteriores vimos muy bien cómo el fin del escalado de Dennard y la explosión de la nube y la inteligencia artificial empujaron a Intel a comprar Altera en 2015 para defender sus servidores Xeon. Sin embargo, en la presentación de Pelayo quedó apuntada una segunda puerta muy interesante: la **diversificación estratégica hacia el sector de la automoción y los sistemas ADAS**.  
> Hoy voy a centrarme exactamente en esa pregunta: **¿qué necesidades técnicas tan específicas tenía el coche de 2015 respecto a las FPGAs para convertirse en una de las razones de peso detrás de aquella compra de 16.700 millones de dólares?** Veremos qué ocurría dentro de los vehículos, por qué las FPGAs eran la única pieza capaz de cubrir esa brecha, cómo se materializó en coches reales como el Audi A8 y qué ocurrió después hasta hoy.»

**Referencias de soporte:** [1], [2], [14], [15].

---

## Diapositiva 2 — La Encrucijada de 2015: Intel, Altera y el Nuevo Automóvil

**Subtítulo:** Dos transformaciones simultáneas que convergieron en la mayor compra histórica de Intel hasta esa fecha

**Idea fuerza:** En 2015 Intel necesitaba diversificarse fuera del PC hacia Data Center e IoT/Automoción justo cuando el automóvil afrontaba una explosión de sensores ADAS y la crisis de las 70–100 ECUs aisladas; además, Altera acababa de ganar en el CES 2015 el gran contrato de serie de Audi.

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Bloque destacado superior (Cifra y cita verificada):**
  - **$16.700 millones** en efectivo ($54/acción) · Anunciada el **1 de junio de 2015** · Cerrada el **28 de diciembre de 2015**
  - *«Inventaremos nuevos productos que hagan posibles experiencias asombrosas del futuro, como la **conducción autónoma** y el aprendizaje automático.»* — **Brian Krzanich**, CEO de Intel (28 dic. 2015)
- **Columna izquierda — La presión sobre Intel (2015):**
  - Mercado de PC estancado; urgencia por capturar dos grandes motores de crecimiento: **Centros de Datos** e **Internet de las Cosas (IoT / Automoción)**.
  - Presencia mínima de Intel en ADAS (limitada a chips Atom en infoentretenimiento).
  - **Catalizador inmediato (5 enero 2015, CES):** Audi anuncia que elige la **Altera Cyclone V SoC FPGA** para vehículos de producción con conducción pilotada (**zFAS**), cinco meses antes de la oferta de Intel.
- **Columna derecha — La crisis arquitectónica del automóvil:**
  - Oleada regulatoria de seguridad activa (**Euro NCAP** / NHTSA): frenado autónomo de emergencia (AEB), mantenimiento de carril y visión 360°.
  - **Saturación de ECUs distribuidas:** De **70 a 100 centralitas (ECUs)** aisladas por coche, con kilómetros de cableado, peso excesivo y latencia entre subsistemas.
  - Imperativo industrial: migrar hacia **controladores de dominio centralizados** capaces de procesar múltiples sensores a la vez.

### Propuesta de diagrama técnico
Esquema comparativo en dos paneles horizontales sobre cuadrícula técnica:
- *Izquierda («Antes: Arquitectura Distribuida»)*: silueta de coche saturada de decenas de pequeñas cajas independientes (ECUs) conectadas por una maraña roja de cables pesados.
- *Derecha («Transición 2015: Controlador de Dominio»)*: sensores convergiendo de forma limpia hacia una unidad central unificada (FPGA + procesador), acompañado de una pequeña línea temporal con dos hitos clave: `5 Ene 2015: Audi elige Altera` → `1 Jun / 28 Dic 2015: Intel compra Altera ($16.700M)`.

### Guion oral del ponente (NO poner en la diapositiva)
> *(~55 segundos)*  
> «Para entender la operación hay que mirar los dos lados de la moneda en 2015. Por el lado de Intel, el mercado de PCs estaba estancado y necesitaba nuevos motores de crecimiento. Cuando anunció la compra de Altera el 1 de junio de 2015 por **16.700 millones de dólares en efectivo**, el discurso oficial tenía dos grandes pilares: centros de datos e **Internet de las Cosas**, donde la automoción era la gran apuesta de futuro. De hecho, el mismo día en que se cerró la compra, el 28 de diciembre de 2015, el CEO de Intel, **Brian Krzanich**, citó expresamente la **conducción autónoma** como una de las experiencias clave que buscaban habilitar.  
> Y fijaos en un dato cronológico muy revelador: solo cinco meses antes del anuncio, el **5 de enero de 2015 en el CES**, Audi había anunciado públicamente que elegía la FPGA **Cyclone V SoC de Altera** para su unidad central de conducción pilotada. ¿Por qué? Porque el automóvil vivía su propia crisis: los coches acumulaban entre **70 y 100 centralitas electrónicas aisladas (ECUs)** —una para cada función—, lo que disparaba el peso del cableado justo cuando normativas como Euro NCAP exigían meter cámaras, radares y frenado autónomo. Había que centralizar, y ahí empezaba el verdadero problema del silicio.»

**Referencias de soporte:** [1], [2], [3], [15].

---

## Diapositiva 3 — La «Era de la Incertidumbre» en el Coche: Por qué el ASIC No Bastaba

**Subtítulo:** Coste de desarrollo, velocidad de cambio en ADAS y ciclos de vida de 15 años

**Idea fuerza:** Igual que vimos en la tabla comparativa de clase (`Introducción FPGAs.pdf`) y en el dilema inicial de la nube de Google, el automóvil de 2015 sufría un desajuste insalvable entre el ritmo mensual de evolución de los algoritmos ADAS y el ciclo rígido de 3 a 5 años de un ASIC automotriz.

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Tarjeta 1 — Desfase de tiempos (*Time-to-Market*):**
  - Un **ASIC automotriz** exige **3–5 años** de diseño, verificación y homologación + decenas de millones de dólares en coste fijo (**NRE**).
  - Entre 2014 y 2017, los algoritmos de percepción ADAS, interfaces de cámara/LiDAR y pruebas Euro NCAP cambiaban cada pocos meses: un ASIC corría el riesgo de nacer obsoleto.
- **Tarjeta 2 — Fragmentación de volumen:**
  - A diferencia de un servidor hiperescala homogéneo, la automoción se divide en decenas de plataformas, gamas y configuraciones de sensores por fabricante.
  - En volúmenes bajos o medios por modelo, la FPGA amortiza mucho mejor el **coste de desarrollo medio** frente al altísimo coste inicial del ASIC *(tabla de `Introducción FPGAs.pdf`, pág. 21)*.
- **Tarjeta 3 — Longevidad de 10–15 años y actualización en campo:**
  - Un vehículo debe fabricarse y recibir soporte técnico durante **10 a 15 años**.
  - La **reconfigurabilidad hardware** de la FPGA permite corregir fallos, adaptarse a nuevos sensores o desplegar mejoras en fábrica y vía **OTA** sin rediseñar la placa ni el silicio.

### Propuesta de diagrama técnico
Gráfica cartesiana estilo plano técnico (evolución directa de la gráfica *Engineering Cost / Time to Develop* de `Introducción FPGAs.pdf`, pág. 22) combinada con dos barras de línea temporal en paralelo:
- *Eje temporal superior (Evolución ADAS / Sensores / Normativa)*: saltos rápidos cada 6–12 meses (`ADAS L1 → L2 → Radar 77 GHz → LiDAR → Deep Learning`).
- *Barra ASIC*: bloque rígido azul oscuro de `3–5 años (NRE alto, función congelada)` que llega tarde al cambio.
- *Barra FPGA*: bloque modular terracota con **corto TTM** y flechas circulares de **reprogramación / actualización en campo** cubriendo todo el ciclo de vida de `10–15 años`.

### Guion oral del ponente (NO poner en la diapositiva)
> *(~55 segundos)*  
> «Si recordáis la tabla comparativa que vimos en clase en *Introducción a las FPGAs* —entre microprocesador, FPGA y ASIC—, aquí cobra sentido económico y técnico total. Pelayo explicó que Google usó primero FPGAs en la nube durante su "era de la incertidumbre" porque los algoritmos de IA cambiaban cada mes. En automoción ocurría exactamente lo mismo, pero agravado por dos factores brutales.  
> Primero, el **Time-to-Market**: diseñar, verificar y homologar un **ASIC automotriz** cuesta decenas de millones de dólares en ingeniería no recurrente (NRE) y tarda entre **3 y 5 años**. Si congelabas un algoritmo ADAS en silicio en 2014, cuando el coche salía al mercado en 2018 ese algoritmo ya se había quedado viejo. Segundo, la **fragmentación y longevidad**: un modelo concreto de coche no siempre tiene el volumen masivo necesario para amortizar un ASIC a medida, pero sí exige **10 a 15 años** de soporte. La FPGA resolvía la ecuación: permitía llegar rápido al mercado con coste de desarrollo moderado y **reprogramar el hardware** si cambiaba un sensor o una normativa.»

**Referencias de soporte:** [11], [12], [13], [15].

---

## Diapositiva 4 — Necesidad Técnica #1: Fusión de Sensores y Latencia Determinista

**Subtítulo:** Arquitectura espacial paralela frente al riesgo mortal del *jitter* en carretera

**Idea fuerza:** Al fusionar cámaras, radar y LiDAR en tiempo real, el coche no solo necesita potencia de cálculo, sino **garantía matemática de respuesta en microsegundos (cero *jitter*)**; ahí la arquitectura espacial de la FPGA supera las colas impredecibles de CPUs y GPUs.

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Dato físico de impacto:**
  - **120 km/h = 33,3 metros por segundo** (~**3,3 cm** por cada milisegundo).
  - Un retraso variable (*jitter*) de 20–50 ms por interrupciones del sistema operativo o fallos de caché equivale a **0,7 – 1,7 metros** recorridos «a ciegas» antes de frenar.
- **Avalancha de flujos heterogéneos simultáneos:**
  - **Cámaras (MIPI CSI-2 / LVDS / GMSL):** corrección de lente, *stitching* 360°, visión estereoscópica.
  - **Radar de 77 GHz:** transformadas FFT y *beamforming* en bloques **DSP** dedicados.
  - **LiDAR y ultrasonidos:** sincronización temporal exacta y nube de puntos 3D.
- **Ventaja de la Arquitectura Espacial (FPGA):**
  - **Concurrencia hardware real:** cada sensor entra por su propio *pipeline* físico independiente en paralelo.
  - **Latencia determinista (microsegundos):** sin sistema operativo, sin planificación de hilos ni cuello de botella Von Neumann.
  - **Precisión aritmética a medida:** procesamiento en coma fija (*INT8/INT12*) que maximiza rendimiento por vatio frente a palabras rígidas de 32/64 bits.

### Propuesta de diagrama técnico
Diagrama de flujo espacial (*dataflow*) estilo `Computación Heterogénea.pdf` (diapositivas 3 y 4) aplicado al automóvil:
- *Izquierda*: 4 bloques de sensores con sus buses (`Cámaras MIPI/LVDS`, `Radar 77 GHz`, `LiDAR`, `Ultrasonidos`) inyectando flujos simultáneos.
- *Centro*: Matriz FPGA en terracota dividida en **carriles hardware paralelos** (preprocesado de imagen, bloques DSP para FFT, sincronización de reloj/marca temporal y fusión) con un cronómetro limpio marcado **`Latencia fija (µs) · Cero Jitter`**.
- *Contrapunto inferior pequeño*: barra comparativa mostrando **CPU/GPU** con picos variables de latencia (*jitter* por caché/SO) frente a la línea recta y predecible de la **FPGA**, junto a la regla de distancia `120 km/h → 33,3 m/s`.

### Guion oral del ponente (NO poner en la diapositiva)
> *(~1 minuto)*  
> «La primera gran necesidad estrictamente técnica del coche era la **fusión de sensores con latencia determinista**. Un coche moderno recibe a la vez vídeo de varias cámaras, señales de radar de 77 GHz, pulsos de LiDAR y ultrasonidos, y tiene que sincronizarlo todo en un único mapa coherente del entorno.  
> Pensad en la física más básica: a **120 km/h**, un coche recorre **33,3 metros cada segundo**, más de 3 centímetros por milisegundo. En un servidor web no pasa nada si un paquete tarda 30 milisegundos más por un fallo de caché o porque el sistema operativo cambió de hilo; en un coche, esa variabilidad —lo que llamamos ***jitter***— puede ser la diferencia entre frenar a tiempo o atropellar a un peatón.  
> Aquí encaja perfectamente lo que vimos en la exposición de *Computación Heterogénea*: frente a la arquitectura temporal y secuencial de una CPU o el *scheduling* por software de una GPU, la **arquitectura espacial de la FPGA** crea tuberías hardware físicas dedicadas para cada sensor en paralelo real. Los datos entran, pasan por los bloques DSP y salen con una **latencia fija de microsegundos**, determinista y repetible ciclo tras ciclo.»

**Referencias de soporte:** [4], [12], [14].

---

## Diapositiva 5 — Necesidad Técnica #2: Seguridad Funcional, Fiabilidad Extrema y los 4 Dominios

**Subtítulo:** El «foso regulatorio» que Intel compró ya construido en Altera (ISO 26262 y AEC-Q100)

**Idea fuerza:** Ningún chip de servidor sobrevive en un automóvil sin años de homologación física y normativa; Altera ya poseía el silicio cualificado **AEC-Q100** y el ecosistema **ISO 26262** certificado con TÜV Rheinland, aplicable a cuatro dominios clave del vehículo.

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Panel izquierdo — El foso de fiabilidad y certificación (activo clave de Altera):**
  - **AEC-Q100 Grado 2:** cualificación frente a estrés térmico y mecánico extremo (**-40 °C a +105 °C** ambiente; hasta +125 °C en unión) y envolvente térmico reducido (sin ventiladores de servidor de 300 W).
  - **ISO 26262 (niveles ASIL A–D):** estándar internacional de seguridad funcional para sistemas E/E críticos en carretera.
  - **AFSDP (*Automotive Functional Safety Data Package*):** paquete certificado de Altera validado con **TÜV Rheinland** para **Cyclone V / Cyclone V SoC y MAX 10** (manuales de seguridad, herramientas **FMEDA** e IP de diagnóstico), capaz de ahorrar **12 a 18 meses-hombre** de certificación a cada fabricante.
- **Panel derecho — Los 4 dominios automotrices con demanda real de FPGAs (cuadrícula 2×2):**
  1. **ADAS y Percepción:** Fusión multisensor, visión 360°, DSP de radar 77 GHz y preprocesado LiDAR.
  2. **Redes Intra-Vehículo (*Glue Logic*):** Puente flexible entre buses heterogéneos (CAN-FD, FlexRay, LVDS, MIPI y **Automotive Ethernet / TTEthernet / TSN**).
  3. **Infoentretenimiento (IVI) y HUD:** Gestión multipantalla, cuadros digitales y corrección óptica (*warping*) para *Head-Up Displays*.
  4. **Electrificación (HEV/EV):** Control vectorial (FOC/PWM) de alta frecuencia en inversores de motor y monitorización de baterías (BMS).

### Propuesta de diagrama técnico
Composición dividida en dos mitades equilibradas sobre cuadrícula:
- *Mitad izquierda*: icono de escudo técnico de certificación con dos medidores esquemáticos: un termómetro de rango **`-40 °C ↔ +105 °C (AEC-Q100 Grado 2)`** y una pirámide/escala **`ASIL A → D (ISO 26262)`** conectada a una caja etiquetada **`Altera AFSDP + TÜV Rheinland (-12 a -18 meses-hombre)`**.
- *Mitad derecha*: cuadrícula limpia 2×2 con iconos lineales de ingeniería para los 4 dominios (`ADAS`, `Redes/TSN`, `IVI/HUD`, `Inversor EV`).

### Guion oral del ponente (NO poner en la diapositiva)
> *(~1 minuto)*  
> «La segunda necesidad —y esta suele pasarse por alto— es el **foso de fiabilidad y seguridad funcional**. Un procesador Intel Xeon de centro de datos no puede meterse en un coche: dentro de un vehículo hay vibraciones constantes, humedad, límites muy duros de disipación térmica y temperaturas extremas. La norma **AEC-Q100 Grado 2** exige operar de forma fiable entre **-40 °C y +105 °C ambiente**.  
> Pero aún más exigente es la norma **ISO 26262**, que clasifica el riesgo de fallo desde ASIL A hasta **ASIL D**. Certificar un chip y sus herramientas desde cero lleva años. ¿Qué compró Intel en Altera que no podía improvisar por sí sola? Compró un **ecosistema ya homologado**: familias como **Cyclone V y MAX 10** cualificadas AEC-Q100 y el paquete **AFSDP** (manuales de seguridad, herramientas de análisis de fallos FMEDA e IP de diagnóstico revisadas por **TÜV Rheinland**), que ahorra a los fabricantes entre **12 y 18 meses-hombre** de certificación.  
> Y además, como veis a la derecha, las FPGAs no servían solo para ADAS: cubrían cuatro dominios del coche, actuando como puente programable entre buses (*glue logic* y Automotive Ethernet determinista), procesando vídeo en cuadros digitales y *Head-Up Displays*, y controlando inversores de motores eléctricos con PWM de altísima precisión.»

**Referencias de soporte:** [5], [9], [10], [12].

---

## Diapositiva 6 — La Matriz del Silicio Automotriz: MCU vs. GPU vs. FPGA vs. ASIC

**Subtítulo:** Diagnóstico comparativo de arquitecturas dentro del vehículo (evolución de la tabla de clase)

**Idea fuerza:** Ningún tipo de silicio domina todos los requisitos del automóvil a la vez; la FPGA ocupa el punto óptimo irreemplazable donde convergen alto ancho de banda de sensores, latencia determinista y flexibilidad post-fabricación.

### Contenido visual para la diapositiva (NotebookLM / HTML)

| Criterio Automotriz | **MCU** *(ej. Infineon AURIX)* | **GPU / SoC** *(ej. NVIDIA Tegra / Orin)* | **FPGA / SoC FPGA** *(Altera Cyclone V / Arria 10)* | **ASIC ADAS** *(ej. Mobileye EyeQ)* |
|---|---|---|---|---|
| **Latencia determinista** | **Muy alta** (tiempo real estricto) | **Baja / Media** (riesgo de *jitter* por SO/drivers) | **Muy alta** (microsegundos, cero *jitter*) | **Alta** (circuito dedicado) |
| **Ancho de banda sensores y paralelismo** | **Muy bajo** (insuficiente para vídeo/LiDAR) | **Muy alto** (redes neuronales densas) | **Alto** (concurrencia hardware y E/S flexible) | **Muy alto** (optimizado a una carga fija) |
| **Flexibilidad post-fabricación** | **Alta** (software en CPU limitada) | **Alta** (software CUDA / frameworks) | **Total en hardware** (reconfigurable en campo/OTA) | **Nula** (lógica grabada en silicio) |
| **Eficiencia / Envolvente térmico (TDP)** | **Excelente** (< 5 W) | **Baja / Exigente** (alto consumo y refrigeración) | **Alta** (lógica adaptada al flujo de datos) | **Máxima** (mejor rendimiento por vatio en volumen) |
| **Coste NRE y Time-to-Market** | **Bajo / Inmediato** | **Bajo / Rápido** | **Medio / Corto** (ideal transición y volúmenes medios) | **Muy alto / 3–5 años** (solo viable a gran escala) |
| **Rol ideal en el vehículo** | Seguridad ASIL-D y actuación (freno, dirección) | Inferencia IA pesada y visión 360° compleja | **Fusión multisensor, *glue logic* E/S, prototipado y redes deterministas** | Visión por computador homogénea en producción masiva |

### Propuesta de diagrama técnico
Matriz diagnóstica limpia estilo `Pelayo_debate.pdf` (diapositiva 13), con sombreado semántico suave:
- Celdas críticas/limitantes en rojo pastel muy suave (ej. ancho de banda en MCU, *jitter*/TDP en GPU, flexibilidad nula y 3–5 años en ASIC).
- Columna **FPGA / SoC FPGA** sutilmente resaltada en marco terracota/azul técnico mostrando su equilibrio único sin casillas «rojas» críticas en la etapa de transición ADAS.

### Guion oral del ponente (NO poner en la diapositiva)
> *(~55 segundos)*  
> «Para ver con claridad por qué ninguna otra arquitectura podía sustituir a la FPGA, he adaptado la *Matriz del Silicio* que presentó Pelayo para centros de datos —y la tabla original de nuestros apuntes— al entorno concreto del automóvil.  
> Fijaos en los cuatro grandes actores del coche:  
> - El **microcontrolador (MCU)**, como el Infineon AURIX, es ultradeterminista y fiable, pero se ahoga en cuanto le metes varias cámaras o un LiDAR.  
> - La **GPU**, como NVIDIA Tegra u Orin, es espectacular entrenando y ejecutando redes neuronales pesadas, pero sufre variabilidad de latencia por su pila de software y exige mucha más energía y refrigeración.  
> - El **ASIC especializado**, como Mobileye EyeQ, es imbatible en eficiencia y coste por unidad cuando produces millones de coches con una tarea ya madura, pero no se puede cambiar en hardware y tarda años en salir.  
> - La **FPGA** —y especialmente la **SoC FPGA**, que une lógica programable y núcleos ARM en un solo chip— cubre justo el hueco que queda vacío: **alto ancho de banda de sensores, latencia determinista de microsegundos y reconfigurabilidad total**. Por eso la conclusión clave es que el coche moderno no elige un chip: exige **computación heterogénea**.»

**Referencias de soporte:** [4], [11], [12], [13], [15].

---

## Diapositiva 7 — Caso Real Emblemático: Audi zFAS y el Salto desde la Placa de Clase

**Subtítulo:** La demostración física en producción de que la FPGA era una pieza insustituible

**Idea fuerza:** La evolución directa de la familia Altera que usamos en laboratorio (`Cyclone II` en la placa DE2) llegó a las carreteras en el controlador central **Audi zFAS** (Audi A8), donde una **Altera Cyclone V SoC FPGA** trabajaba codo con codo con un ASIC, una GPU y un MCU en la misma placa.

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Puente con la asignatura (*Dispositivos Electrónicos Programables*):**
  - **En el aula:** Placa **Altera DE2 (`Cyclone II EP2C35`)** (35.000 elementos lógicos) y evolución desde PLDs segmentados (`MAX 7000`).
  - **En carretera (Audi A8):** **Altera Cyclone V SoC FPGA** (matriz FPGA programable + doble núcleo **ARM Cortex-A9** integrados en el mismo silicio, cualificación automotriz AEC-Q100).
- **Anatomía del Audi zFAS (desarrollado por Audi junto a TTTech y fabricado por Delphi/Aptiv):**
  - Primer controlador central de dominio ADAS de producción en serie (anunciado en CES 2015, desplegado en el Audi A8).
  - **Los 4 chips especializados en la misma PCB:**
    1. **Altera Cyclone V SoC (FPGA + ARM):** Fusión de datos multisensor (radar, LiDAR, cámaras, ultrasonidos) + **TTEthernet** determinista (TTTech).
    2. **Mobileye EyeQ3 (ASIC):** Procesamiento crítico de la cámara frontal (objetos, carriles, peatones).
    3. **NVIDIA Tegra K1 (GPU/SoC):** Visión envolvente 360° (*surround-view*).
    4. **Infineon AURIX TriCore (MCU):** Supervisión de seguridad funcional **ASIL-D** y ejecución de freno/dirección.

### Propuesta de diagrama técnico
Diagrama de arquitectura de placa impresa (*PCB schematic*) sobre cuadrícula técnica mostrando el módulo **Audi zFAS** visto desde arriba con sus **4 circuitos integrados claramente etiquetados y conectados**:
- Bloque destacado en terracota (**Altera Cyclone V SoC FPGA**) en posición central-articuladora recibiendo flujos de `Radar`, `LiDAR`, `Ultrasonidos` y `Cámaras`, con etiqueta interna `Lógica FPGA + Dual ARM Cortex-A9 + TTEthernet`.
- Conectado por buses de datos internos a los otros 3 dados: **Mobileye EyeQ3 (ASIC)**, **NVIDIA Tegra K1 (GPU)** e **Infineon AURIX (MCU ASIL-D)**.
- Pequeña flecha de linaje técnico en la esquina superior izquierda: `Laboratorio: Altera Cyclone II (DE2)` ➔ `Producción: Altera Cyclone V SoC (Audi zFAS)`.

### Guion oral del ponente (NO poner en la diapositiva)
> *(~1 minuto)*  
> «Para que esto no se quede en teoría, vamos al caso real más famoso de aquella época y, además, lo conectamos directamente con nuestra asignatura. En el laboratorio trabajamos con la placa **Altera DE2** que lleva una **Cyclone II**, y en teoría vimos cómo Altera evolucionó desde los CPLDs segmentados MAX 7000 hasta las FPGAs complejas. Pues bien, la evolución automotriz de esa misma familia —la **Altera Cyclone V SoC FPGA**, que integra lógica programable y un doble núcleo ARM Cortex-A9 en el mismo chip— fue elegida por **Audi y TTTech** para el corazón del **Audi zFAS**, el primer gran controlador central de dominio ADAS que llegó a producción en serie en el Audi A8.  
> Y mirad qué obra de arte de computación heterogénea había dentro de esa única placa: convivían exactamente **los cuatro paradigmas** de la matriz anterior. **NVIDIA Tegra K1** montaba la vista 360°; **Mobileye EyeQ3** analizaba la cámara frontal; el microcontrolador **Infineon AURIX** garantizaba la seguridad ASIL-D sobre frenos y dirección; y en el centro, la **FPGA Altera Cyclone V** hacía de columna vertebral para la **fusión multisensor** y ejecutaba el protocolo **TTEthernet** determinista de TTTech. No había mejor prueba de que el automóvil necesitaba FPGAs… y esto se anunció en enero de 2015, justo antes de que Intel pusiera los 16.700 millones sobre la mesa.»

**Referencias de soporte:** [3], [4], [12], [13].

---

## Diapositiva 8 — De Altera a Mobileye: La Estrategia Completa de Intel (2015–2017)

**Subtítulo:** Cómo encajaba Altera dentro del plan maestro de Intel para dominar el coche autónomo

**Idea fuerza:** Altera fue el primer escalón —no el único— de la ofensiva automotriz de Intel: le dio acceso inmediato a fabricantes y la capa reconfigurable para prototipado y fusión (**Intel GO con Arria 10**), antes de añadir el ASIC de visión masiva al comprar **Mobileye** en 2017.

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Línea temporal en 3 actos (2015 → 2017):**
  - **Acto 1 · Junio / Dic. 2015 — Compra de Altera ($16.700M):**
    - Puerta de entrada instantánea a OEMs y Tier-1 con silicio ya homologado (**AEC-Q100 / ISO 26262**) y contratos activos (Audi zFAS).
    - Creación del *Programmable Solutions Group* (PSG) dentro de Intel.
  - **Acto 2 · Enero 2017 (CES) — Plataforma Intel GO + Alianza BMW–Intel–Mobileye:**
    - Intel presenta su kit de desarrollo *car-to-cloud* para conducción autónoma integrando procesadores **Intel Atom / Xeon** junto a **FPGAs Altera Arria 10** (fusión de sensores, modelado de entorno y alto ancho de banda de transceptores y DDR4).
    - Anuncio de flota de **40 vehículos autónomos de prueba** junto a BMW y Mobileye.
  - **Acto 3 · 13 de Marzo de 2017 — Compra de Mobileye ($15.300M):**
    - Intel adquiere el líder en visión ADAS y sus **ASICs EyeQ** para cubrir el despliegue masivo de bajo coste unitario.
- **Tesis estratégica inferior (síntesis del binomio):**
  - **FPGA (Altera):** flexibilidad, prototipado rápido, fusión multisensor y puentes de E/S en la fase cambiante.
  - **ASIC (Mobileye EyeQ):** inferencia de visión madura a millones de unidades con máxima eficiencia PPA.

### Propuesta de diagrama técnico
Línea de tiempo horizontal estilo hoja de ruta de ingeniería con 3 nodos principales conectados por flechas sólidas (`2015: Altera $16.700M` ➔ `Ene 2017: Intel GO [Atom/Xeon + Arria 10]` ➔ `Mar 2017: Mobileye $15.300M`), y debajo una llave estructural que agrupa el bloque **`Altera (FPGA) + Intel (CPU) + Mobileye (ASIC)`** bajo la etiqueta **`Arquitectura Automotriz Completa "Car-to-Cloud"`**.

### Guion oral del ponente (NO poner en la diapositiva)
> *(~50 segundos)*  
> «Una pregunta muy lógica que podría surgir en el debate es: *si Intel compró Altera en parte por la automoción, ¿por qué dos años después pagó otros 15.300 millones de dólares por Mobileye?*  
> Esta línea temporal explica perfectamente que no eran apuestas contradictorias, sino **piezas complementarias** de una estrategia en tres actos. En **2015**, Intel apenas existía en ADAS; comprar **Altera** le dio de golpe silicio automotriz certificado y relaciones con fabricantes de primer nivel. En **enero de 2017**, en el CES, Intel lanzó la plataforma de conducción autónoma **Intel GO**, que combinaba CPUs Atom o Xeon directamente con **FPGAs Altera Arria 10** para acelerar fusión de sensores y prototipado en la alianza con BMW y Mobileye. Y solo dos meses después, en **marzo de 2017**, Intel compró **Mobileye** para aportar el **ASIC de visión (EyeQ)** capaz de fabricarse a millones de unidades con menor coste por chip. Exactamente el mismo patrón híbrido que vimos en la nube: **FPGA donde manda la flexibilidad y la fusión; ASIC donde el algoritmo ya es masivo y estable**.»

**Referencias de soporte:** [1], [2], [6], [7], [12].

---

## Diapositiva 9 — Balance Crítico (2016–2025): Intel+Altera vs. AMD+Xilinx y el Horizonte SDV

**Subtítulo:** Qué funcionó, dónde falló la ejecución de Intel y hacia dónde evolucionan las FPGAs en el coche actual

**Idea fuerza:** Automoción justificó una parte clave de la compra pero la ejecución de Intel tropezó con sus retrasos de fabricación (14/10 nm) frente al avance *fabless* de Xilinx/AMD; tras su escisión e independencia en 2025, las FPGAs siguen siendo esenciales en el Vehículo Definido por Software (SDV).

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Columna izquierda — Realidad crítica de Intel + Altera (2016–2025):**
  - **Peso real en la compra:** Automoción fue una **razón estratégica real de diversificación** (pilar IoT), pero compartida con los pilares de **Data Center/Xeon** y **5G Telecom**.
  - **Fricciones de ejecución:** Los retrasos litográficos de Intel (**14 nm / 10 nm**) frenaron el catálogo de Altera, mientras la inversión automotriz interna se concentró en **Mobileye**.
  - **Desenlace corporativo:** Escisión en 2024 y acuerdo con **Silver Lake** (anunciado el 14 abr. 2025, cerrado el **15 sept. 2025**) vendiendo el **51%** de Altera a una valoración de **$8.750M** (frente a los $16.700M de 2015), recuperando agilidad como fabricante independiente puro de FPGAs.
- **Columna derecha — El rival (AMD/Xilinx) y caso real contrario al ASIC:**
  - **Ventaja *fabless* (TSMC):** Xilinx (adquirida por AMD en 2022) tomó clara ventaja en ADAS de alto rendimiento con **Zynq-7000** y **Zynq UltraScale+ MPSoC**.
  - **Caso Subaru EyeSight (2020):** Subaru sustituyó **ASICs fijos** por **Xilinx Zynq UltraScale+** en su sistema de visión estereoscópica para ganar procesamiento 3D en tiempo real, fusión con radar y actualizaciones flexibles.
- **Franja inferior — Horizonte actual del automóvil (conectando con *Computación Heterogénea*):**
  - **Vehículo Definido por Software (SDV) y Arquitecturas Zonales:** consolidación extrema de ECUs y puentes Ethernet/TSN.
  - **Edge AI eficiente (INT4/INT8):** inferencia en el borde sin penalizar la autonomía de coches eléctricos.
  - **eFPGAs y Ciberseguridad:** bloques FPGA embebidos en SoCs automotrices para 15 años de actualización OTA y defensa hardware (detección de intrusiones CAN/Ethernet y **criptografía post-cuántica, PQC**).

### Propuesta de diagrama técnico
Diseño en dos capas sobre cuadrícula técnica:
- *Parte superior (comparativa balanceada)*: dos cajas enfrentadas **`Intel + Altera (IDM · 10 nm retrasados → Spin-off Silver Lake $8.750M, 2025)`** vs. **`AMD + Xilinx (Fabless TSMC → Liderazgo ADAS · Caso Subaru EyeSight)`**.
- *Parte inferior (banda tecnológica de horizonte)*: 3 nodos vectoriales conectados al chasis de un coche eléctrico/zonal: `Arquitectura Zonal / TSN`, `Edge AI (INT4/INT8)` y `eFPGA + Ciberseguridad / PQC`.

### Guion oral del ponente (NO poner en la diapositiva)
> *(~1 minuto)*  
> «Para ser rigurosos —como ya hicieron nuestros compañeros al analizar el centro de datos— tenemos que hacer un **balance crítico** de qué pasó realmente después de 2015.  
> Primero, hay que ser honestos con la proporción: la automoción fue un pilar estratégico muy importante de diversificación, pero no el único; compartió factura con los centros de datos y las redes 5G. Segundo, aunque la tesis técnica sobre las FPGAs en el coche era acertada, **la ejecución de Intel falló**: sus famosos retrasos en los nodos de **14 y 10 nanómetros** lastraron a Altera, y tras 2017 la prioridad interna en conducción autónoma se volcó en Mobileye.  
> Mientras tanto, ¿quién demostró que el mercado automotriz de FPGAs sí era enorme? Su gran rival, **Xilinx** —hoy parte de AMD—, fabricando en **TSMC**. El ejemplo perfecto es **Subaru EyeSight**, que en 2020 abandonó sus ASICs fijos para pasarse a un **Xilinx Zynq UltraScale+** precisamente por lo que explicamos al principio: necesitaban visión 3D rápida y capacidad de actualizar algoritmos.  
> El desenlace de Intel llegó recientemente: tras separar Altera en 2024, en **septiembre de 2025** cerró la venta del **51% a Silver Lake** valorando Altera en **8.750 millones de dólares**, casi la mitad de lo pagado en 2015, para que vuelva a competir con libertad en Edge, robótica y automoción. Y el futuro confirma la vigencia de la FPGA en el coche: **arquitecturas zonales** del Vehículo Definido por Software, **Edge AI** de bajo consumo, **eFPGAs** integradas dentro de SoCs y **agilidad criptográfica** para proteger coches conectados durante 15 años.»

**Referencias de soporte:** [8], [11], [12], [14], [15].

---

## Diapositiva 10 — Conclusiones y Bibliografía Clave

**Subtítulo:** Tres claves definitivas sobre las necesidades automotrices detrás de Intel + Altera

**Idea fuerza:** El sector automovilístico necesitaba la combinación irreemplazable de determinismo, flexibilidad y certificación de seguridad que solo ofrecía la FPGA; esa necesidad dio sentido estratégico a la compra de Altera en 2015 y sigue vigente en el coche heterogéneo actual.

### Contenido visual para la diapositiva (NotebookLM / HTML)
- **Bloque superior — 3 Tarjetas Numeradas de Conclusión (estilo `Computación Heterogénea.pdf`, diap. 10):**
  - **`01` | La Necesidad Real del Automóvil:** Fusión multisensor concurrente con **latencia determinista** (cero *jitter*), resistencia **AEC-Q100**, seguridad **ISO 26262** y reconfigurabilidad para ciclos de **10–15 años** donde el ASIC era demasiado rígido y lento.
  - **`02` | El Valor Estratégico para Intel (2015):** Comprar Altera por **$16.700M** dio a Intel entrada inmediata en ADAS/OEMs (validada por el contrato **Audi zFAS** meses antes), certificaciones listas (AFSDP) y el puente técnico hacia **Intel GO** y **Mobileye**.
  - **`03` | La Lección de Ingeniería:** Aunque los retrasos de fabricación de Intel llevaron a la escisión de Altera en 2025, la tesis técnica triunfó: el coche del presente y del futuro es **heterogéneo** (MCU + GPU + ASIC + FPGA/eFPGA).
- **Bloque inferior — Bibliografía y Fuentes Principales (compacto y legible):**
  - **Intel Corp. (2015, 2017):** Notas de prensa oficiales *Intel to Acquire Altera* (jun. 2015), *Intel Completes Acquisition of Altera* (dic. 2015), *BMW/Intel/Mobileye CES 2017* e *Intel to Acquire Mobileye* (mar. 2017).
  - **Altera / Intel & TTTech (2015–2025):** *Audi Selects Altera SoC FPGA* (CES 2015), *Automotive-Grade Device Handbook (AEC-Q100 / ISO 26262 / AFSDP)* y *Silver Lake Investment* (sept. 2025).
  - **Estándares y casos sectoriales:** ISO 26262 (seguridad funcional), AEC-Q100 (fiabilidad automotriz), EE Times / Embedded.com (*Subaru EyeSight – Xilinx Zynq UltraScale+*).
  - **Asignatura:** *Dispositivos Electrónicos Programables* (`Introducción FPGAs.pdf`, `Arquitectura PLDs.pdf`) y exposiciones `Computación Heterogénea.pdf` y `Pelayo_debate.pdf`.

### Propuesta de diagrama técnico
Diseño limpio en dos bandas horizontales sobre cuadrícula técnica:
- *Banda superior (60% altura)*: 3 tarjetas técnicas bien proporcionadas con etiquetas oscuras `01`, `02`, `03` y una línea inferior minimalista de silicio heterogéneo convergiendo hacia el icono de un coche moderno.
- *Banda inferior (35% altura)*: caja sobria de **Fuentes y Bibliografía Clave** en dos columnas bien espaciadas con tipografía nítida (mínimo 12–13 pt equivalentes en 16:9).

### Guion oral del ponente (NO poner en la diapositiva)
> *(~45 segundos)*  
> «Para cerrar, resumo la respuesta a nuestra pregunta en tres ideas muy claras:  
> **Primero**, el automóvil de 2015 tenía necesidades que ninguna otra arquitectura resolvía sola: fusionar múltiples sensores con latencia determinista de microsegundos, cumplir normas extremas como AEC-Q100 e ISO 26262 y adaptarse a algoritmos ADAS cambiantes durante una vida útil de 15 años.  
> **Segundo**, para Intel, comprar Altera fue la forma más rápida de adquirir esa credibilidad y ese silicio ya homologado —avalado por el hito de Audi zFAS— y construir su puente hacia Intel GO y Mobileye dentro de una operación multi-pilar junto al centro de datos y el 5G.  
> **Y tercero**, aunque la ejecución industrial de Intel falló y acabó escindiendo Altera en 2025, la lección técnica de fondo quedó demostrada: igual que en los centros de datos, en el coche **la FPGA y el ASIC no se excluyen, sino que coevolucionan** en arquitecturas heterogéneas donde la adaptabilidad del hardware ya es un requisito de seguridad.  
> Aquí abajo tenéis las principales fuentes primarias consultadas. Muchas gracias y quedo abierto a cualquier pregunta del debate.»

**Referencias de soporte:** [1]–[15].

---

# Banco de Defensa y Debate (Preguntas Difíciles y Respuestas Modelo)

Prepárate estas 7 preguntas típicas de profesor o compañeros: te darán seguridad absoluta en el turno de debate.

1. **«Si las FPGAs eran tan importantes en automoción, ¿por qué hoy Tesla (FSD) o Mobileye (EyeQ) usan ASICs en lugar de FPGAs?»**
   - *Respuesta clave:* Porque un **ASIC** gana claramente en coste unitario y consumo (TOPS/W) **una vez que el algoritmo y la configuración de sensores se han estabilizado y se producen millones de unidades homogéneas** (caso de Tesla o la visión frontal masiva de Mobileye). Sin embargo, en 2015–2018 estábamos en la fase de incertidumbre y transición; y hoy las FPGAs/eFPGAs siguen cumpliendo roles donde el ASIC rígido sufre: **prototipado/HIL, fusión multisensor flexible, puentes de interfaces heterogéneas (MIPI/LVDS/Ethernet TSN), volúmenes medios y actualización hardware en ciclos de 15 años** (como demostró Subaru pasando de ASIC a Xilinx Zynq en 2020).

2. **«Entonces, ¿por qué compró Intel Mobileye en 2017 si ya había comprado Altera en 2015?»**
   - *Respuesta clave:* Porque cubrían capas distintas del mismo mapa automotriz. Altera aportaba el **hardware programable, la fusión de sensores, el prototipado (Intel GO con Arria 10) y el silicio homologado de entrada**; Mobileye aportaba los **algoritmos propietarios de visión por computador y el ASIC EyeQ** para vender millones de cámaras frontales de bajo coste a OEMs tradicionales. Era la combinación de *flexibilidad (FPGA) + volumen especializado (ASIC)*.

3. **«¿Fue la automoción la razón PRINCIPAL por la que Intel pagó $16.700 millones por Altera?»**
   - *Respuesta clave (honestidad académica):* No fue la única ni la mayor en facturación inmediata: el motor financiero principal a corto plazo era **proteger el monopolio Xeon en centros de datos** (frente a proyectos como Microsoft Catapult) y cubrir **telecomunicaciones/5G**. Pero el pilar **IoT y Automoción** fue una de las grandes razones estratégicas de diversificación a largo plazo, hasta el punto de que el propio CEO Brian Krzanich citó la *conducción autónoma* en el comunicado oficial de cierre de la compra.

4. **«¿Qué diferencia técnica hay entre la placa Altera DE2 (Cyclone II) que usamos en clase y la Cyclone V SoC del Audi zFAS?»**
   - *Respuesta clave:* Ambas pertenecen a la familia económica/media *Cyclone* de Altera, pero dan un salto arquitectónico enorme: la **Cyclone II (`EP2C35`)** de nuestra DE2 (año 2006) es una FPGA pura de 35.000 elementos lógicos donde un procesador como *Nios II* debe implementarse como *soft-core* consumiendo lógica programable; en cambio, la **Cyclone V SoC** del Audi zFAS integra en el mismo dado de silicio **lógica FPGA programable + un sistema procesador duro (*Hard Processor System*, HPS) basado en doble núcleo ARM Cortex-A9**, además de cualificación **AEC-Q100 Grado 2** y soporte certificado **ISO 26262 (AFSDP)**.

5. **«¿Por qué una GPU potente de NVIDIA no podía sustituir también a la FPGA en la placa Audi zFAS?»**
   - *Respuesta clave:* De hecho, **en la misma placa Audi zFAS había una NVIDIA Tegra K1** encargada de la vista envolvente 360°, ¡y aun así Audi y TTTech pusieron una **Altera Cyclone V** al lado! ¿Por qué? Porque la GPU ejecuta software sobre drivers y cachés que pueden introducir **latencia no determinista (*jitter*)** y no dispone de E/S hardware reconfigurables para conectar directamente buses heterogéneos y protocolos de red determinista como **TTEthernet** con garantías temporales estrictas.

6. **«¿Por qué Intel acabó perdiendo valor con Altera hasta vender el 51% a Silver Lake en 2025 por $8.750M?»**
   - *Respuesta clave:* No porque las FPGAs dejaran de ser útiles, sino por **problemas de ejecución industrial de Intel**. Al obligar a Altera a depender de las fundiciones internas de Intel (modelo IDM), los graves retrasos en los nodos de **14 nm y 10 nm** hicieron que Altera perdiera competitividad temporal frente a **Xilinx/AMD**, que fabricaba en **TSMC** bajo modelo *fabless*. Al escindirla y ceder el 51% a Silver Lake en septiembre de 2025, Altera recupera independencia operativa y acceso ágil a fundiciones externas.

7. **«¿Cómo encaja lo visto en *Arquitectura PLDs.pdf* (MAX 7000) con el uso de FPGAs en coches?»**
   - *Respuesta clave:* En `Arquitectura PLDs.pdf` vimos que las matrices simples AND-OR y las CPLDs segmentadas como **MAX 7000** eran insuficientes cuando aparecían **operaciones aritméticas intensivas** (multiplicaciones DSP) y necesidad de **más memoria interna** que los simples biestables. En un coche, el procesado de radar (FFT), el filtrado de vídeo de cámaras y el almacenamiento temporal de *frames* requieren exactamente esos **bloques multiplicadores/DSP y RAM de bloque** que definen a las FPGAs modernas.

---

# Bibliografía Completa y Verificada

## A. Fuentes Corporativas y Notas de Prensa Oficiales

1. **Intel Corporation** (1 de junio de 2015). *Intel to Acquire Altera* [Nota de prensa oficial: adquisición en efectivo por $16.700 millones / $54 por acción orientada a Data Center e IoT]. Investor Relations (INTC).  
   https://www.intc.com/news-events/press-releases/detail/333/intel-to-acquire-altera

2. **Intel Corporation** (28 de diciembre de 2015). *Intel Completes Acquisition of Altera* [Nota de prensa oficial de cierre: creación del Programmable Solutions Group (PSG) y declaración textual del CEO Brian Krzanich citando *«autonomous driving and machine learning»*]. Investor Relations (INTC).  
   https://www.intc.com/news-events/press-releases/detail/302/intel-completes-acquisition-of-altera

3. **Altera Corporation / Intel Newsroom Archive** (5 de enero de 2015). *Audi Selects Altera SoC FPGA for Production Vehicles with Piloted Driving Capability* [Comunicado oficial en el CES 2015 sobre la adopción de Cyclone V SoC FPGA en Audi zFAS junto a TTTech].  
   https://download.intel.com/newsroom/2021/archive/2015-01-05-news-releases-audi-selects-altera-soc-fpga-production-vehicles-piloted-driving-capability.pdf

4. **TTTech Auto**. *Scalable ECU Platform for Autonomous Driving Is Going into Series Production and Is Now Available Worldwide* [Arquitectura zFAS, TTEthernet determinista e integración de Cyclone V SoC e Infineon AURIX con seguridad ASIL].  
   https://www.tttech.com/scalable-ecu-platform-for-autonomous-driving-is-going-into-series-production-and-is-now-available-worldwide

5. **Altera Documentation**. *The Automotive-Grade Device Handbook & Altera Automotive Qualifications* [Cualificación AEC-Q100 Grado 2, seguridad funcional ISO 26262 y Automotive Functional Safety Data Package (AFSDP) validado con TÜV Rheinland para Cyclone V y MAX 10].  
   https://docs.altera.com/r/docs/683121/current/the-automotive-grade-device-handbook  
   https://docs.altera.com/r/docs/683121/current/the-automotive-grade-device-handbook/altera-automotive-qualifications

6. **Intel Corporation** (enero de 2017). *BMW Group, Intel and Mobileye Will Have Autonomous Test Vehicles on the Roads by the Second Half of 2017* [Alianza CES 2017 vinculada al lanzamiento de la plataforma Intel GO con procesadores Intel y FPGAs Arria 10]. Investor Relations (INTC).  
   https://www.intc.com/news-events/press-releases/detail/255/bmw-group-intel-and-mobileye-will-have-autonomous-test

7. **Intel Corporation** (13 de marzo de 2017). *Intel to Acquire Mobileye* [Nota de prensa oficial sobre la adquisición de Mobileye por ~$15.300 millones para acelerar soluciones de conducción autónoma *car-to-cloud*]. Investor Relations (INTC).  
   https://www.intc.com/news-events/press-releases/detail/243/intel-to-acquire-mobileye

8. **Altera & Silver Lake** (14 de abril y 15 de septiembre de 2025). *Intel Announces Strategic Investment by Silver Lake in Altera* y *Altera Closes Silver Lake Investment to Become World's Largest Pure-Play FPGA Solutions Provider* [Venta del 51% a valoración de $8.750 millones y nueva etapa independiente].  
   https://www.altera.com/newsroom/altera-investment-silver-lake  
   https://www.silverlake.com/altera-closes-silver-lake-investment-to-become-worlds-largest-pure-play-fpga-solutions-provider/

## B. Estándares Internacionales, Soluciones Técnicas y Análisis de Industria

9. **International Organization for Standardization (ISO)** (2018; 1.ª ed. 2011). *ISO 26262-1:2018 — Road vehicles — Functional safety — Part 1: Vocabulary* [Marco internacional de seguridad funcional y niveles ASIL A–D en sistemas E/E automotrices].  
   https://www.iso.org/standard/68383.html

10. **Automotive Electronics Council (AEC)**. *AEC-Q100: Failure Mechanism Based Stress Test Qualification for Integrated Circuits* [Cualificación de circuitos integrados automotrices y grados térmicos, incluyendo Grado 2: -40 °C a +105 °C].  
    http://www.aecouncil.com/AECDocuments.html

11. **EE Times & Embedded.com** (2020). *Subaru Replaces ASICs with Xilinx FPGA for Latest Vision-Based ADAS* / *FPGAs Displace ASICs in Subaru EyeSight Vision-Based ADAS* [Caso práctico de migración de ASICs fijos a Xilinx Zynq UltraScale+ MPSoC por visión 3D, fusión multisensor y flexibilidad OTA].  
    https://www.eetimes.com/subaru-replaces-asics-with-xilinx-fpga-for-latest-vision-based-adas/  
    https://www.embedded.com/fpgas-displace-asics-in-subaru-eyesight-vision-based-adas/

12. **Altera Solutions, Data Center Frontier & Achronix**. Documentación técnica de evolución del silicio automotriz:
    - Altera — *Automotive & Transportation Solutions (ADAS, SDV y Arquitecturas Zonales)*: https://www.altera.com/solutions/transportation
    - Data Center Frontier — *Autonomous Cars Could Drive a Deluge of Data Center Demand* (plataforma Intel GO y papel de Arria 10 FPGA): https://www.datacenterfrontier.com/connected-cars/article/11430754/autonomous-cars-could-drive-a-deluge-of-data-center-demand
    - Achronix — *Autonomous Vehicle Trends and Technology Evolution* (fusión de sensores, latencia determinista y papel de eFPGAs): https://www.achronix.com/blog/autonomous-vehicle-trends-and-technology-evolution

## C. Material de la Asignatura y Exposiciones de Referencia del Aula

13. **Asignatura *Dispositivos Electrónicos Programables*** (documentos locales del curso):
    - `Introducción FPGAs.pdf` (27 págs.): Evolución de memorias/PLDs a FPGAs, comparación **DSP/micro vs. FPGA vs. ASIC** (pág. 21), gráfica de coste/tiempo de desarrollo frente a densidad/volumen (pág. 22) y placa de desarrollo **Altera DE2 (`Cyclone II EP2C35F672C6`)** (págs. 24–27).
    - `Arquitectura PLDs.pdf` (22 págs.): Macroceldas, asignación variable, arquitectura segmentada (**Altera MAX 7000**) y necesidad de bloques multiplicadores y memoria interna en la transición CPLD → FPGA (págs. 20–22).

14. **Exposición de referencia #1 (aula):** `Computación Heterogénea.pdf` (10 diapositivas). *Computación Heterogénea y el Nuevo Orden del Silicio* (estándar visual de referencia, arquitectura temporal CPU vs. espacial FPGA, integración hasta chiplets/CXL, Intel+Altera vs. AMD+Xilinx, horizonte Edge AI y agilidad criptográfica PQC).

15. **Exposición de referencia #2 (aula):** `Pelayo_debate.pdf` (13 diapositivas). *La Guerra por el Acelerador: El rediseño estratégico del Centro de Datos* (estándar visual y Matriz del Silicio, compra de Altera por $16.700M y punto de enlace en diapositiva 9: *«Diversificación estratégica: 5G y Automoción — sistemas ADAS»*).
