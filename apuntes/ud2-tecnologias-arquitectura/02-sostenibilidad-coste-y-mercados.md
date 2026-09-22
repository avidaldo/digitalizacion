# Sostenibilidad, coste y nuevos mercados: la economía de las THD y de los tokens

## Conclusión primero

Las tecnologías digitales tienen dos relaciones opuestas con la sostenibilidad: **permiten** ahorrar
recursos en casi todos los sectores (menos desplazamientos, menos desperdicio, menos energía por
unidad producida) y **consumen** recursos por sí mismas a una escala que ha dejado de ser
despreciable — los centros de datos, y dentro de ellos la IA, son ya un factor en la planificación
eléctrica de varios países. Para un desarrollador, la versión práctica de este debate es el **coste
por token**: un LLM cobra por cantidad de texto, cada vuelta de un agente reenvía todo el contexto, y
diseñar una aplicación con IA sin pensar en eso produce facturas y consumos que nadie previó. Y de
todo lo anterior salen mercados nuevos: no solo lo que se vende con la tecnología, sino la propia
tecnología como mercado.

## Las dos caras de la sostenibilidad

**Lo que las THD permiten ahorrar** (la cara que defiende cualquier informe sectorial):

| Ámbito | Mecanismo | Ejemplo |
|---|---|---|
| Energía | Redes eléctricas inteligentes que casan generación renovable y demanda; gestión de edificios | Contadores inteligentes, previsión de producción eólica con ML |
| Industria | Mantenimiento predictivo (no se cambia lo que no falla), optimización de procesos, menos rechazos por calidad | Una línea con visión artificial que detecta el defecto en la primera pieza y no en el lote |
| Transporte | Optimización de rutas, cargas completas, flotas compartidas | Software de rutas en reparto; menos km vacíos |
| Agricultura | Riego y fertilización de precisión | Sensores de humedad por parcela |
| Trabajo | Reuniones y trabajo remoto | Menos desplazamientos (con matices: los datos posteriores a 2020 son ambiguos) |
| Materiales | Impresión 3D bajo demanda, simulación antes de fabricar | Menos prototipos físicos, menos stock obsoleto |
| Desmaterialización | Servicios en vez de bienes | Música, prensa, software: cero unidades físicas |

**Lo que las THD consumen** (la cara que hay que conocer para no repetir eslóganes):

- **Electricidad de los centros de datos.** Las estimaciones de la Agencia Internacional de la
  Energía sitúan el consumo de los centros de datos en torno al 1,5 % de la electricidad mundial en
  2024, con previsión de duplicarse antes de 2030, impulsado por la IA. En países pequeños con
  concentración de centros de datos (Irlanda) la cifra supera el 20 % del consumo nacional. No es
  marginal.
- **Agua.** La refrigeración evaporativa de centros de datos consume agua, y las nuevas
  instalaciones compiten con la agricultura y las ciudades por ella; hay conflictos locales
  documentados en España, Chile, Países Bajos y EE. UU.
- **Entrenamiento e inferencia de IA.** Entrenar un modelo frontera consume una cantidad de energía
  equivalente a la de miles de hogares durante un año; pero el consumo *acumulado* de la
  **inferencia** (responder a millones de usuarios cada día) supera al del entrenamiento con
  rapidez. Las estimaciones publicadas sitúan una petición a un LLM muy por encima de una búsqueda
  web clásica, desde decenas hasta miles de veces más cómputo según el modelo, el tamaño del contexto
  y si hay generación larga o no.
- **Hardware.** Fabricar chips es intensivo en energía, agua y materiales; los aceleradores de IA
  se renuevan cada pocos años; los residuos electrónicos son el flujo de residuos que más crece.
- **El efecto rebote (paradoja de Jevons).** Cuando una tecnología abarata un recurso, se consume
  más de él. Cada mejora de eficiencia en cómputo se ha compensado históricamente con más cómputo.
  Que un modelo sea diez veces más eficiente no garantiza que se consuma diez veces menos: puede
  garantizar que se usa cien veces más.

**Software verde** (*green software*) es la respuesta de la industria en el lado del desarrollador:
medir el consumo, usar la energía cuando y donde es más limpia (*carbon-aware computing*: ejecutar
los trabajos por lotes cuando hay excedente renovable), dimensionar correctamente la infraestructura
(la mayoría de los servidores en la nube están sobredimensionados), elegir lenguajes y algoritmos
eficientes cuando el volumen lo justifica, y — en IA — elegir el modelo más pequeño que resuelve el
problema. La Green Software Foundation (Linux Foundation) publica patrones y una métrica de
intensidad de carbono del software.

## La economía de los tokens

Un LLM comercial se paga **por token**, y entender ese modelo de coste es tan necesario como
entender el de la nube.

**Qué es un token.** Un fragmento de texto, típicamente entre un carácter y una palabra. En inglés,
una palabra son ~1,3 tokens; en español, algo más (~1,5-2), porque los tokenizadores se entrenaron
sobre todo con inglés. El código también cuesta tokens, y los espacios de indentación cuentan.

**Cómo se cobra.** Por millón de tokens, con precios distintos para **entrada** (lo que se envía:
instrucciones, contexto, historial) y **salida** (lo que el modelo genera), y la salida es
habitualmente entre 3 y 5 veces más cara. Los precios varían en más de dos órdenes de magnitud
entre un modelo pequeño y uno frontera, y bajan cada pocos meses; no tiene sentido memorizar cifras
concretas, sí el orden de magnitud y el mecanismo.

**Por qué una conversación cuesta cada vez más.** El modelo no tiene memoria
([UD1-07](../ud1-digitalizacion-ia-software/07-que-es-la-ia.md)): en cada turno se reenvía la
conversación entera. El turno 20 de un chat paga los 19 anteriores como entrada. Un agente que da
50 vueltas de bucle con un contexto de 100 000 tokens envía 5 millones de tokens de entrada aunque
"solo" haya generado unos miles de salida.

**Ejemplo de cálculo** con precios hipotéticos redondos (3 € por millón de tokens de entrada, 15 €
por millón de salida, un modelo de gama alta):

| Escenario | Entrada | Salida | Coste |
|---|---|---|---|
| Una pregunta suelta con 500 tokens de contexto y 300 de respuesta | 500 | 300 | 0,006 € |
| Un chat de 30 turnos con contexto creciente hasta 20 000 tokens | ~300 000 acumulados | ~10 000 | ~1,05 € |
| Una tarea de agente de código: 60 vueltas, contexto medio de 80 000 tokens | 4 800 000 | 30 000 | ~14,85 € |
| Clasificar 100 000 correos de soporte con un modelo pequeño (0,1 € / 0,4 € por millón), 400 tokens cada uno | 40 000 000 | 5 000 000 | ~6 € |

La tercera fila es la que sorprende: **una tarea de agente puede costar más que una hora de
trabajo**, y sin límites configurados un agente en bucle puede consumir sin fin (OWASP lo lista
como riesgo: consumo ilimitado, [UD1-10](../ud1-digitalizacion-ia-software/10-seguridad-y-regulacion.md)).
La cuarta muestra lo contrario: **elegir el modelo adecuado** convierte un proceso masivo en algo
barato.

**Mecanismos para controlar el coste**, que son a la vez mecanismos de sostenibilidad:

| Mecanismo | Qué hace |
|---|---|
| **Enrutado de modelos** | Un modelo pequeño para tareas fáciles, uno grande solo cuando hace falta |
| **Caché de *prompt*** | Los proveedores cobran mucho menos por la parte del contexto que se repite entre llamadas (instrucciones, documentos) si se marca como cacheable |
| **Procesamiento por lotes** | Tareas no urgentes a mitad de precio con entrega en horas |
| **Contexto mínimo** | Enviar lo relevante (RAG bien hecho) en vez de todo |
| **Salida estructurada y corta** | Pedir JSON con lo justo, no prosa |
| **Límites y presupuestos** | Tope de tokens por petición, por usuario, por día; alertas |
| **Modelos locales** | Coste marginal cero por token a cambio de coste fijo de hardware y menos capacidad ([04](04-edge-fog-mist.md)) |

**Cuotas.** Los planes de suscripción (Copilot, los chats de pago) no cobran por token al usuario,
pero limitan el número de peticiones "premium" a modelos avanzados por mes; agotado el cupo, se
degrada a un modelo básico o se paga aparte. Copilot Education entra en esta categoría, y es la
razón por la que este módulo demuestra agentes en proyección y practica con capa gratuita y local.

**Nube y coste**, la versión general del mismo problema: el modelo de pago por uso de la nube
([03](03-niveles-y-funciones-de-la-nube.md)) convierte el gasto de capital (comprar servidores) en
gasto operativo (alquilar por hora), lo que es una ventaja de flexibilidad y un riesgo de sorpresa.
**FinOps** es la disciplina — con nombre desde 2019 — de gestionar el coste de la nube como se
gestiona el rendimiento: medir, atribuir a equipos, optimizar continuamente. Las sorpresas típicas:
tráfico de salida (*egress*), recursos olvidados encendidos, almacenamiento que nadie borra, y desde
2023, facturas de API de LLM.

## Nuevos mercados generados por las THD

Las THD no solo cambian sectores existentes: también crean mercados que antes no existían y
transforman o destruyen otros.

**Mercados nuevos:**

| Mercado | Qué se vende | Lo hizo posible |
|---|---|---|
| Nube y SaaS | Infraestructura y software por suscripción | Virtualización, Internet de alta capacidad |
| Economía de las aplicaciones | Apps, compras dentro de la app, suscripciones móviles | *Smartphones* y tiendas de aplicaciones (2008) |
| Economía de plataformas | Intermediación entre oferta y demanda con comisión (Uber, Airbnb, Glovo, Amazon Marketplace) | Móvil, geolocalización, pagos digitales |
| Economía de datos | Datos, analítica, publicidad dirigida; intermediarios de datos | Big Data, rastreo, IA |
| IA como servicio | Acceso a modelos por API; agentes; herramientas para construir con IA | LLM, nube con GPU |
| Infraestructura de IA | Chips, centros de datos, energía para IA; "neonubes" de GPU | Demanda de cómputo |
| Ciberseguridad | Productos y servicios gestionados de seguridad | Todo lo anterior conectado |
| IoT y servicios conectados | Producto + servicio (el coche que se actualiza, la máquina con contrato de rendimiento) | Sensores, conectividad |
| Fabricación bajo demanda | Piezas personalizadas, repuestos impresos | Fabricación aditiva |
| Economía de creadores | Contenido monetizado directamente | Plataformas, pagos, herramientas de creación (incluida IA generativa) |
| Trabajo por plataformas (*gig economy*) | Tareas y servicios a demanda | Plataformas, móvil; con regulación laboral en disputa |

**Mercados transformados o destruidos:** fotografía química (Kodak), videoclubs (Blockbuster),
agencias de viajes físicas, enciclopedias impresas, prensa en papel, telefonía fija, taxis (en
disputa), y en curso: ilustración y traducción comerciales, atención al cliente de primer nivel,
parte de la programación de tareas repetitivas. Un mercado nuevo suele nacer de la caída de otro,
y quién captura el valor (el fabricante, la plataforma, el trabajador) es la pregunta política que
hay detrás de cada fila de la tabla.

## Para debatir

- Un agente de código que cuesta 15 € por tarea frente a una hora de un desarrollador. ¿Cuándo
  compensa? ¿Qué pasa con el cálculo si el agente tiene que repetir la tarea tres veces? ¿Y si el
  resultado hay que revisarlo una hora?
- "La IA ayuda a reducir emisiones." Encontrar un caso en el que sea verdad, uno en el que sea
  falso, y explicar qué los distingue.
- Una aplicación con chat integrado que la empresa ofrece gratis a sus usuarios. Diseñar qué
  límites hay que poner para que un usuario no cueste más de lo que aporta. ¿Qué pasa si alguien
  automatiza peticiones?
- ¿Es la "economía de plataformas" un mercado nuevo o un intermediario nuevo en un mercado viejo?
  ¿Cambia la respuesta según se mire desde el taxista, el pasajero o la plataforma?
