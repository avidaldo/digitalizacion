# Tecnologías habilitadoras digitales (THD): panorámica, aplicaciones y el informe colaborativo

## Conclusión primero

"Tecnología habilitadora digital" es una etiqueta administrativa, no técnica: es la lista que el
programa español *Industria Conectada 4.0* usó para agrupar las tecnologías que hacen posible la
digitalización industrial. La lista cambia según la fuente, y varias de sus entradas son a su vez
términos paraguas (IA, nube, IoT). Lo que sí es estable — y lo que se pide en el proyecto — es la
**relación** entre cada tecnología y tres cosas: el producto o servicio que permite, el sitio donde
se aplica (negocio o planta) y la mejora concreta que produce en IT o en OT. Para un desarrollador,
la panorámica sirve para reconocer con qué se va a tener que integrar y qué está maduro.

## Una nota sobre el término

Hay dos listas oficiales con nombre parecido que no coinciden:

- **KET** (*Key Enabling Technologies*, tecnologías facilitadoras esenciales) es un término de la
  Comisión Europea (2009) para una lista industrial general: micro/nanoelectrónica, fotónica,
  nanotecnología, materiales avanzados, biotecnología, fabricación avanzada. No son "digitales".
- **THD** (tecnologías habilitadoras digitales) es la lista de *Industria Conectada 4.0* (Ministerio
  de Industria, 2015 en adelante), centrada en lo digital, y es la que usa el currículo.

Ninguna lista es cerrada, y cada consultora o informe añade o quita entradas. Lo que sigue es una
síntesis de las que aparecen en casi todas.

## Las THD, una a una

Para cada una: qué es en una frase, madurez en 2026, dónde se aplica y un ejemplo real. Las que ya
tienen apunte propio se tratan aquí solo como entrada del catálogo.

### Conectividad e IoT (Internet de las cosas)

Dotar a objetos físicos (máquinas, sensores, vehículos, contadores, electrodomésticos) de capacidad
de medir y comunicar. **IIoT** es su versión industrial. La conectividad que lo hace posible: 5G
(latencia baja y densidad de dispositivos, con redes privadas para plantas), Wi-Fi 6/7, LPWAN
(LoRaWAN, NB-IoT: poco ancho de banda, mucha autonomía de batería, para contadores y sensores
dispersos), y el protocolo de mensajería **MQTT** como lengua común. Madurez: alta en industria y
en *utilities* (contadores inteligentes); dispersa en consumo. Ejemplo: contadores eléctricos que
envían lecturas cada hora; sensores de vibración en motores para mantenimiento predictivo. Mejora IT/OT:
es literalmente la tecnología que conecta los dos entornos
([UD1-06](../ud1-digitalizacion-ia-software/06-extremo-a-extremo.md)).

### Computación en la nube y en el borde (cloud, edge)

Apuntes propios: [03](03-niveles-y-funciones-de-la-nube.md) y [04](04-edge-fog-mist.md). Como THD:
la nube es la que hace posible casi todas las demás (dónde se almacenan los datos de IoT, dónde se
entrenan los modelos, dónde corre el software como servicio); el *edge* es la que permite que las
demás funcionen en planta con latencia y autonomía.

### Big Data y analítica

Apuntes: [UD1-08](../ud1-digitalizacion-ia-software/08-ia-datos-sectores-lenguajes.md),
[07](07-ciencia-de-datos.md), [08](08-almacenamiento-y-cloud-computing.md). Como THD: la capacidad
de almacenar y explotar los datos que generan las demás. Sin ella, IoT produce ruido.

### Inteligencia artificial

Apuntes: [UD1-07](../ud1-digitalizacion-ia-software/07-que-es-la-ia.md) a
[09](../ud1-digitalizacion-ia-software/09-ia-para-el-desarrollo-de-software.md). Como THD: la que
convierte datos en decisiones y automatiza tareas cognitivas. En planta: visión artificial,
mantenimiento predictivo, optimización. En negocio: previsión, atención al cliente, asistentes,
desarrollo de software.

### Robótica y automatización avanzada

Robots industriales (brazos en jaula), **cobots** (colaborativos: trabajan junto a personas, con
sensores de fuerza que los detienen al contacto), **AGV/AMR** (vehículos de almacén guiados por
cinta o autónomos con navegación propia), robots móviles de inspección, drones. En 2024-2026,
robots humanoides en pruebas piloto en fábricas y almacenes, con mucho ruido mediático y despliegue
real todavía pequeño. Madurez: muy alta en automoción y logística; creciente en PYME gracias a los
cobots (más baratos y sin necesidad de reprogramación por especialistas). En negocio, su equivalente
es la **RPA** (automatización de tareas de oficina imitando clics), ya descrita en
[UD1-09](../ud1-digitalizacion-ia-software/09-ia-para-el-desarrollo-de-software.md). Mejora OT:
productividad, calidad constante, tareas peligrosas sin personas. Producto/servicio: el "robot como
servicio" (alquiler por hora de uso) es un modelo de negocio nuevo.

### Fabricación aditiva (impresión 3D)

Construir piezas capa a capa a partir de un modelo digital, en plástico, metal, resina, cerámica.
Madurez: consolidada para prototipos, utillaje, piezas de repuesto bajo demanda, implantes médicos
personalizados, aeronáutica (piezas ligeras imposibles de mecanizar); no compite con la producción en
masa. Producto/servicio: personalización individual (plantillas ortopédicas, audífonos —
prácticamente el 100 % de los audífonos se fabrican así), inventario de repuestos que pasa de físico
a "fichero + impresora". Mejora OT: menos stock, menos tiempo de espera de repuestos.

### Simulación y gemelo digital

**Simulación**: modelos numéricos de procesos físicos (flujo de una línea, resistencia de una pieza,
comportamiento térmico) para probar antes de construir. **Gemelo digital**: la simulación conectada
a datos reales en tiempo real, de forma que el modelo refleja el estado actual del activo físico y
permite predecir y probar cambios ([UD1-06](../ud1-digitalizacion-ia-software/06-extremo-a-extremo.md)).
Madurez: alta en simulación (CAD/CAE llevan décadas); el gemelo digital "completo" es más marketing
que realidad en la mayoría de PYME, y aparece en el nivel más alto de madurez de la escalera de
[UD1-01](../ud1-digitalizacion-ia-software/01-que-es-digitalizar.md). Ejemplo real: gemelos de
turbinas eólicas, de redes de agua, de plantas químicas; Singapur tiene un gemelo digital de la
ciudad. Producto/servicio: vender la garantía de rendimiento en vez de la máquina, porque se puede
monitorizar.

### Realidad virtual, aumentada y mixta

**VR**: inmersión completa (gafas opacas). **AR**: información superpuesta sobre el mundo real (móvil,
tableta o gafas transparentes). **MR/XR**: términos paraguas. Madurez en industria: AR para
mantenimiento e instrucciones de montaje (el operario ve sobre la máquina qué tornillo tocar) y para
asistencia remota (el experto ve lo que ve el operario); VR para formación en entornos peligrosos.
En consumo, tras el ciclo de expectativas del "metaverso" (2021-2022) y el lanzamiento de Apple
Vision Pro (2024), la adopción sigue siendo de nicho. Producto/servicio: formación como servicio,
soporte técnico remoto.

### Ciberseguridad

Apunte: [UD1-10](../ud1-digitalizacion-ia-software/10-seguridad-y-regulacion.md). Como THD: la que
hace *posible* conectar lo demás sin que sea una temeridad. En planta: segmentación, IEC 62443,
detección de anomalías en protocolos industriales. En negocio: identidad, MFA, copias, SIEM.
Mercado propio y en crecimiento continuo ([02](02-sostenibilidad-coste-y-mercados.md)).

### Blockchain y registros distribuidos

Base de datos replicada entre participantes que no confían entre sí, donde los registros se
encadenan criptográficamente y no se pueden alterar sin que se note. Propuesta industrial:
trazabilidad entre empresas (origen de un alimento, de un diamante, de un medicamento), contratos
inteligentes, identidad digital. Madurez: tras el pico de expectativas de 2017-2018, la mayoría de
los proyectos empresariales se han abandonado o se han sustituido por una base de datos normal con
firma digital — porque casi siempre **sí hay** una entidad de confianza (el regulador, la
asociación sectorial) y entonces la cadena de bloques es más lenta y más cara sin aportar nada.
Sobrevive en criptomonedas, en algunos consorcios (TradeLens, de Maersk e IBM, cerró en 2023) y en
identidad digital descentralizada. Es el mejor caso de debate del catálogo: **una tecnología real
que resuelve un problema que casi nadie tiene**.

### Sistemas ciberfísicos y plataformas de integración

**CPS**: sistemas en los que cómputo y proceso físico están indisolublemente unidos (un coche, una
línea de envasado con visión). **Plataformas de integración** (iPaaS, buses de eventos, APIs): lo
que permite que todo lo anterior se hable — el "pegamento" que en la mayoría de proyectos de
digitalización es la mayor parte del trabajo de integración. Kafka, MQTT, brokers, APIs REST,
n8n/Make para lo ligero.

### Computación cuántica

Se incluye en muchas listas de THD por su potencial; en 2026 no tiene aplicación industrial
práctica. Lo que sí es real y afecta ya al desarrollo de software: la **criptografía poscuántica**
— los algoritmos de cifrado actuales (RSA, curvas elípticas) se romperán cuando exista un ordenador
cuántico suficientemente grande, así que los estándares nuevos (NIST, 2024) ya se están desplegando
en TLS y en firmas. Un desarrollador la verá en las bibliotecas antes que en los titulares.

## Tabla resumen: THD × negocio × planta × producto/servicio × mejora IT/OT

| THD | En negocio (IT) | En planta (OT) | Producto o servicio que habilita | Mejora IT/OT |
|---|---|---|---|---|
| IoT / conectividad | Flotas, activos, contadores | Sensorización de máquinas | Servicios basados en uso (pago por hora, seguro por km) | Une los dos entornos |
| Nube | Todo el software como servicio | Análisis de datos de planta fuera de ella | SaaS, plataformas | Elasticidad, centralización |
| *Edge* | Tiendas, sucursales | Cómputo al pie de máquina | Productos con inteligencia local | Latencia, autonomía, privacidad |
| Big Data / analítica | Cuadros de mando, previsión | Históricos de proceso | Datos como producto | Decisiones con datos reales |
| IA | Asistentes, previsión, desarrollo de software | Visión, predictivo, optimización | Cualquier producto "inteligente" | Automatización de tareas cognitivas |
| Robótica | RPA | Robots, cobots, AMR | Robot como servicio | Productividad, seguridad |
| Fabricación aditiva | — | Prototipos, repuestos, utillaje | Personalización individual | Menos stock, menos espera |
| Simulación / gemelo | Escenarios de negocio | Modelo de la planta | Garantía de rendimiento | Probar sin parar la línea |
| VR/AR | Formación, marketing | Mantenimiento asistido, soporte remoto | Soporte como servicio | Menos errores, menos desplazamientos |
| Ciberseguridad | Identidad, cumplimiento | Segmentación, IEC 62443 | Servicios gestionados de seguridad | Hace posible conectar |
| Blockchain | Trazabilidad entre empresas, identidad | Poco | Registros compartidos sin autoridad central | Casi nunca; debatible |
| Integración / CPS | APIs, buses, iPaaS | MES, pasarelas | — | Es la mejora: que todo se hable |
| Cuántica | Criptografía poscuántica | — | — | Aún ninguna |

## El ciclo de expectativas como herramienta de debate

El **ciclo de sobreexpectación** de Gartner (*hype cycle*) no es un modelo científico — es una
curva dibujada a mano por una consultora cada año — pero es una herramienta útil para situar una
THD en una conversación: lanzamiento → pico de expectativas infladas → abismo de desilusión →
rampa de consolidación → meseta de productividad.

```
expectativas
    ▲
    │        ╭─╮ pico                    ────────── meseta
    │       ╱   ╲                    ╭──╯
    │      ╱     ╲                 ╱
    │     ╱       ╲              ╱  rampa
    │    ╱         ╲___________╱
    │   ╱             abismo
    │  ╱
    └──────────────────────────────────────────► tiempo
     lanzamiento
```

Posiciones defendibles en 2026 (y discutibles, que es el objetivo): IA generativa saliendo del pico
hacia el abismo en expectativas mientras el uso real sigue creciendo (las dos cosas a la vez);
agentes de IA en el pico; blockchain empresarial en el abismo desde hace años y con meseta de nicho;
metaverso en el abismo; robots humanoides en el pico; computación cuántica en la rampa inicial
desde hace veinte años; impresión 3D e IoT en la meseta de sus nichos; *edge* en la rampa. Una THD
en el abismo no es una THD muerta: es una THD sobre la que se puede decidir con datos.

## El informe THD colaborativo

Entregable de esta unidad: un repositorio Git compartido en el que cada alumno documenta una
tecnología asignada, mediante una rama y un *pull request* que el resto revisa. Practica dos cosas a
la vez: escribir documentación técnica que otros usan, y el flujo de trabajo colaborativo con Git
que se da por sabido en el sector.

**Estructura de cada sección** (un fichero por tecnología, en Markdown):

1. **Definición** en dos o tres frases, con la fuente de la que se toma.
2. **Cómo funciona**, un párrafo, al nivel de un compañero de ciclo que no la conoce.
3. **Madurez** en 2026: posición argumentada en el ciclo de expectativas, con un dato real.
4. **Aplicaciones en negocio y en planta**, una tabla de dos columnas con ejemplos concretos
   (empresa, sector, qué hace).
5. **Producto o servicio que habilita**: al menos un ejemplo de algo que se vende y que no existiría
   sin esta tecnología.
6. **Mejora en IT y en OT**: qué cambia en cada entorno.
7. **Ventajas, inconvenientes y casos en los que no conviene.**
8. **Relación con otras THD**: de cuáles depende, con cuáles se combina. Enlaces a las secciones de
   los compañeros.
9. **Fuentes**: enlaces verificables; se distingue fuente primaria (fabricante, norma, artículo) de
   secundaria (prensa).

**Flujo de trabajo:** rama por alumno → *commits* pequeños → PR con descripción → revisión de al
menos un compañero (comentarios en el PR, no en persona) → corrección → fusión. Las revisiones a
los demás deben ser concretas, verificables y útiles para mejorar la sección.

**Uso de IA en el informe:** permitido y esperado para investigar y redactar, con la misma regla que
el proyecto: las fuentes se verifican (un LLM inventa referencias con soltura), y se declara qué se
pidió y qué se corrigió. Una sección con una fuente inexistente es una sección no entregada.

## Para debatir

- Elegir una THD y argumentar que está en el abismo de desilusión. Después, argumentar que está en la
  meseta. ¿Qué dato cambiaría de una a otra?
- ¿Qué THD de la lista podría quitarse sin que la digitalización de una PYME cambiara? ¿Y cuál no
  puede faltar?
- Blockchain para trazar el pescado de una conservera: enumerar qué problema resolvería, quién
  tendría que participar, y qué solución más simple haría lo mismo.
- Un cobot de 30 000 euros en un taller de 6 personas. ¿Qué tarea? ¿Qué cambia en la organización
  ([UD1-02](../ud1-digitalizacion-ia-software/02-la-empresa-por-dentro.md))? ¿Qué pasa con la
  persona que hacía esa tarea?
