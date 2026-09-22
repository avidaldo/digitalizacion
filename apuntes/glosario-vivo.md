# Glosario vivo: términos que cambian de significado según quién los usa

Este glosario no da una definición por término: da **varias**, porque la tesis del módulo es que
muchos de los términos centrales del sector no tienen una definición fija — significan cosas
distintas según el contexto, la capa técnica y la época, y la habilidad que se entrena es reconocer
cuál está en juego en cada frase. Para cada término: las acepciones en uso, un ejemplo de frase real
en la que aparece, y el apunte donde se desarrolla.

Es "vivo" en dos sentidos: se amplía durante el curso con los términos que surjan en los debates,
y cada alumno debería tener el suyo — la sección 3 del informe del proyecto (glosario de entidades)
es la versión de este documento para el dominio de su empresa.

**El patrón que se repite**, y que se debería poder aplicar a cualquier término nuevo: cuando un
término parece contradictorio, preguntar (1) *quién* lo dice — un administrador de sistemas, un
comercial, un desarrollador de frontend, un artículo de prensa —; (2) *en qué capa* — la máquina, el
proceso, la red, el negocio —; y (3) *con qué tecnología del momento* — el término se acuñó con una
tecnología y sobrevivió a ella. Casi siempre la contradicción desaparece y quedan dos acepciones
legítimas.

---

## Digitalización

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Convertir a formato digital (*digitization*) | "Hemos digitalizado el archivo: está todo escaneado" | [UD1-01](ud1-digitalizacion-ia-software/01-que-es-digitalizar.md) |
| Rediseñar un proceso con tecnología digital (*digitalization*) | "Hemos digitalizado la recepción de facturas: entran por API" | UD1-01 |
| Cambiar el modelo de negocio o la organización (*digital transformation*) | "El banco se ha digitalizado: cierra oficinas" | UD1-01 |
| Etiqueta política o de subvención | "Kit Digital", "Industria Conectada 4.0" | UD1-01, [UD2-01](ud2-tecnologias-arquitectura/01-tecnologias-habilitadoras.md) |

## IT

| Acepción | Ejemplo | Dónde |
|---|---|---|
| El departamento de sistemas | "Pídeselo a IT" | [UD1-02](ud1-digitalizacion-ia-software/02-la-empresa-por-dentro.md) |
| Cualquier entorno que procesa información (frente a OT) | "Finanzas es un entorno IT" | UD1-02, [UD1-03](ud1-digitalizacion-ia-software/03-it-y-ot.md) |
| El sector económico | "Trabaja en IT" | — |
| Los niveles 4-5 del modelo de Purdue | "La DMZ separa IT de OT" | UD1-03 |

## Servidor

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Máquina física | "El servidor está en el armario" | [UD1-04](ud1-digitalizacion-ia-software/04-front-back-cliente-servidor.md) |
| Proceso que escucha en un puerto | "Arranca el servidor de desarrollo" | UD1-04, [UD2-04](ud2-tecnologias-arquitectura/04-edge-fog-mist.md) (`ollama serve` en el portátil) |
| Rol en una conversación (quien responde) | "Postgres es el servidor y la API su cliente" | UD1-04 |
| Máquina virtual o instancia en la nube | "Levantamos tres servidores más para el pico" | [UD2-03](ud2-tecnologias-arquitectura/03-niveles-y-funciones-de-la-nube.md) |
| Contenedor | "Cada microservicio corre en su servidor" | UD1-04 |
| Función *serverless* (que "no tiene servidor") | "Esto va en un servidor *serverless*" | UD2-03 |
| El backend entero, esté donde esté | "Pregúntale al servidor si el usuario existe" | UD1-04, [UD2-05](ud2-tecnologias-arquitectura/05-donde-vive-la-logica.md) |
| Servidor MCP: un programa que expone herramientas a un LLM | "Escribe un servidor MCP para la base de datos" | [UD1-09](ud1-digitalizacion-ia-software/09-ia-para-el-desarrollo-de-software.md) |

## Cliente

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Proceso que inicia una petición | "El navegador es el cliente" | UD1-04 |
| Máquina del usuario | "Esto se ejecuta en el cliente" | UD1-04, UD2-05 |
| Biblioteca para consumir una API (SDK) | "El cliente de Python de la API" | UD1-04 |
| Quien paga (negocio) | "El cliente quiere que el cliente no vea ese campo" | UD1-02 |
| Cinco entidades distintas según el departamento: quien paga, quien firma, quien recibe, quien reclama, quien visita la web | "¿Tu `Cliente` es el mismo que el de atención al cliente?" | UD1-02, [UD3-02](ud3-proyecto/02-ejemplo-trabajado.md) |
| Cliente MCP: el componente de un *host* que habla con servidores MCP | — | UD1-09 |
| Cliente ligero / grueso: cuánta lógica tiene | "Un cliente grueso con sincronización" | UD2-05 |

## Frontend / backend

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Interfaz de usuario / lógica y datos (separación de responsabilidades) | "El backend valida, el frontend muestra" | UD1-04 |
| Lo que corre en el navegador / lo que corre en el servidor (lugar) | "El frontend hace un fetch al backend" | UD1-04 — y por qué las dos acepciones no coinciden siempre (SSR, RSC, móvil, Electron) |
| Frontend / backend de un compilador (análisis / generación de código) | "LLVM tiene muchos frontends y un backend" | UD1-04 |
| Backend como implementación intercambiable | "Esta biblioteca soporta varios backends de almacenamiento" | UD1-04 |
| BFF: un backend que es "del frontend" | "Un BFF por cada tipo de cliente" | UD1-04, UD2-05 |
| Los roles y "los equipos" | "Los de front y los de back" (y la ley de Conway) | UD1-02, [UD1-05](ud1-digitalizacion-ia-software/05-ciclos-de-vida-conway-y-el-caso-movil.md) |

## API

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Interfaz de programación entre sistemas o bibliotecas | "La app llama a la API del backend" | [UD1-04](ud1-digitalizacion-ia-software/04-front-back-cliente-servidor.md), [UD1-06](ud1-digitalizacion-ia-software/06-extremo-a-extremo.md) |
| API web HTTP expuesta a otras aplicaciones | "La factura entra por API al ERP" | [UD1-01](ud1-digitalizacion-ia-software/01-que-es-digitalizar.md) |
| Conjunto de funciones de una biblioteca local | "La API de JavaScript del navegador" | UD1-04 |
| Producto de negocio que se monetiza o se integra | "Stripe vende pagos por API" | [UD2-01](ud2-tecnologias-arquitectura/01-tecnologias-habilitadoras.md) |

## SDK

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Biblioteca y utilidades para usar un servicio desde un lenguaje | "El SDK de Python de la nube" | [UD1-09](ud1-digitalizacion-ia-software/09-ia-para-el-desarrollo-de-software.md) |
| Kit de desarrollo de una plataforma | "El SDK de Android" | [UD1-02](ud1-digitalizacion-ia-software/02-la-empresa-por-dentro.md) |
| Cliente oficial que envuelve una API remota | "En vez de hacer HTTP a mano, usa el SDK" | UD1-04 |

## IA (inteligencia artificial)

| Acepción | Ejemplo | Dónde |
|---|---|---|
| El campo académico (desde 1956) | "La IA es una rama de la informática" | [UD1-07](ud1-digitalizacion-ia-software/07-que-es-la-ia.md) |
| IA simbólica: reglas, búsqueda, lógica | "El motor de reglas de la aseguradora" | UD1-07 |
| Cualquier modelo de *machine learning* | "Detectamos fraude con IA" (un árbol de decisión) | UD1-07 |
| Un LLM o un producto sobre uno | "Le pregunté a la IA" | UD1-07 |
| Un agente con herramientas | "La IA ha abierto un PR" | UD1-09 |
| Etiqueta de marketing | "Lavadora con IA" | UD1-07 |
| Inteligencia artificial general (prensa, especulación) | "Cuando llegue la IA..." | UD1-07 |
| Lo que todavía sorprende ("efecto IA": cuando funciona, deja de llamarse IA) | El ajedrez, el OCR, el GPS | UD1-07 |

## Modelo

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Modelo de ML: la función aprendida de los datos, con sus pesos | "Entrenamos un modelo" | UD1-07 |
| Modelo de lenguaje concreto (producto) | "Cambiamos de modelo por coste" | UD1-09, [UD2-02](ud2-tecnologias-arquitectura/02-sostenibilidad-coste-y-mercados.md) |
| Modelo de datos: entidades y relaciones | "El modelo tiene una N:M" | [UD2-06](ud2-tecnologias-arquitectura/06-dato-informacion-ciclo-de-vida.md) |
| Modelo de negocio | "Modelo de suscripción" | UD1-02 |
| Modelo de referencia o de madurez | "Modelo de Purdue", "modelo de madurez digital" | UD1-01, UD1-03 |
| Modelo de despliegue (nube pública, privada...) | — | UD2-03 |
| Modelo de responsabilidad compartida | — | UD2-03 |
| Modelo de simulación / gemelo digital | — | UD2-01 |

## Agente

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Agente de IA actual: LLM en bucle con herramientas que dirige su propio proceso | "Un agente de código" | UD1-09 |
| Flujo de trabajo con LLM (a menudo llamado agente sin serlo) | "Nuestro agente clasifica correos" (es un flujo) | UD1-09 |
| Agente software clásico (BDI, sistemas multiagente, años 90) | — | UD1-09 |
| Agente de aprendizaje por refuerzo | "El agente aprende una política" | UD1-07 |
| *User agent*: el navegador | Cabecera HTTP | UD1-09 |
| Persona (agente comercial, de seguros) | — | UD1-09 |
| Agente personalizado en una herramienta (rol con instrucciones y herramientas restringidas) | "El agente revisor solo lee" | UD1-09 |

## MCP

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Protocolo para exponer herramientas y datos a un LLM | "Conecta GitHub por MCP" | [UD1-09](ud1-digitalizacion-ia-software/09-ia-para-el-desarrollo-de-software.md) |
| Servidor MCP: programa que publica herramientas, recursos o *prompts* | "Escribe un servidor MCP para la base de datos" | UD1-09 |
| Cliente MCP: componente del *host* que habla con esos servidores | "VS Code actúa como host con cliente MCP" | UD1-09 |

## RAG

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Técnica: recuperar documentos relevantes y meterlos en el contexto del modelo | "El chatbot responde con RAG sobre la wiki" | [UD1-09](ud1-digitalizacion-ia-software/09-ia-para-el-desarrollo-de-software.md) |
| Producto: "hacer un RAG" como sinónimo de chatbot sobre documentos | "Nos piden un RAG para normativa" | UD1-09 |
| Parte de un *pipeline* mayor con índice, búsqueda y generación | "El RAG falla por recuperar trozos irrelevantes" | UD1-09 |

## Big Data / datos

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Datos que no caben en una máquina (definición técnica relativa a las herramientas) | "10 TB de logs al día" | [UD1-08](ud1-digitalizacion-ia-software/08-ia-datos-sectores-lenguajes.md) |
| Las tecnologías para procesarlos (Hadoop, Spark, almacenes en la nube) | "Tenemos un equipo de Big Data" | UD1-08, [UD2-08](ud2-tecnologias-arquitectura/08-almacenamiento-y-cloud-computing.md) |
| Término de moda de 2012-2018, hoy sustituido por "datos", "plataforma de datos", "lakehouse" | — | UD1-08 |
| Confundido con IA o con ciencia de datos, sin serlo | "Usamos Big Data para predecir" | UD1-07 |

## LLM

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Modelo de lenguaje grande entrenado para predecir el siguiente *token* | "GPT, Claude y Llama son LLM" | [UD1-07](ud1-digitalizacion-ia-software/07-que-es-la-ia.md) |
| Servicio comercial de texto por API | "El backend llama a un LLM externo" | [UD1-09](ud1-digitalizacion-ia-software/09-ia-para-el-desarrollo-de-software.md) |
| Componente dentro de un agente o de un flujo con IA | "El LLM clasifica el correo y el flujo crea el ticket" | UD1-09 |

## Dato / información

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Dato: valor sin contexto; información: dato con contexto (pirámide DIKW) | "`23,5` frente a `horno 3, 23,5 °C, 10:02`" | UD2-06 |
| Información en teoría de la información: medida en bits, sin significado | "Entropía", "compresión" | UD2-06 |
| Dato = campo; datos = conjunto (uso en bases de datos) | "Un dato mal tecleado" / "los datos de ventas" | UD2-06 |
| Dato personal (RGPD): cualquier información sobre una persona identificable | "La IP es un dato personal" | [UD1-10](ud1-digitalizacion-ia-software/10-seguridad-y-regulacion.md) |
| Dato maestro: entidad de referencia compartida | "El dato maestro de cliente" | UD2-06 |
| "Datos" como departamento, sector o activo | "Los de datos", "estrategia de datos" | [UD2-07](ud2-tecnologias-arquitectura/07-ciencia-de-datos.md) |

## Nube

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Nube de consumo: un servicio de ficheros con interfaz | "Lo tengo en la nube" (Drive, iCloud) | UD2-08 |
| Nube de infraestructura: cómputo, almacenamiento y servicios por API y por uso | "Desplegamos en la nube" | UD2-03 |
| Un proveedor concreto | "Estamos en Azure" | UD2-03 |
| Modelo de despliegue: pública, privada, híbrida, soberana | "Nube privada" (que puede estar en el sótano) | UD2-03 |
| "En la nube" como contrario de "en local", aunque el *edge* sea nube desplazada | — | UD2-04 |
| Lo opuesto al *edge* (la región central del proveedor) | "Entrenar en la nube, ejecutar en el borde" | UD2-04 |

## Niveles (de la nube)

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Niveles de servicio: IaaS, PaaS, SaaS, FaaS, BaaS... | "Subir un nivel para no administrar el sistema operativo" | UD2-03 |
| Niveles geográficos: región, zona de disponibilidad, punto de presencia | "Desplegar en dos zonas" | UD2-03 |
| Niveles de almacenamiento: caliente, frío, archivo | "Mover a un nivel frío a los 90 días" | UD2-08 |
| Niveles del modelo de Purdue (0-5) | — | UD1-03 |
| Capas del continuo *mist* / *fog* / *edge* / nube | — | UD2-04 |

## Serverless

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Funciones bajo demanda sin servidor que administrar (FaaS) | "Una Lambda por evento" | UD2-03 |
| Cualquier servicio gestionado que escala a cero y se paga por uso ("base de datos *serverless*") | "Postgres *serverless*" | UD2-03 |
| Término engañoso: hay servidores, pero no son de quien programa | — | UD1-04, UD2-03 |

## Edge

| Acepción | Ejemplo | Dónde |
|---|---|---|
| *Edge* industrial: servidor o pasarela en la planta | "El modelo corre en el *edge* de la línea" | UD2-04, UD1-03 |
| *Edge* del operador de telecomunicaciones (MEC) | "Cómputo en la antena 5G" | UD2-04 |
| *Edge* de CDN: código en puntos de presencia cerca del usuario | "Cloudflare Workers", "*edge functions*" | UD2-04, UD1-04 |
| IA en el dispositivo (*edge AI*, *on-device*) | "Resumen en el móvil sin red" | UD2-04 |
| El navegador como *edge* | WebAssembly, WebGPU | UD2-04 |
| Término genérico que absorbe *fog* y *mist* | — | UD2-04 |

## Plataforma

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Sistema operativo o entorno de ejecución | "Multiplataforma" (el título del ciclo) | — |
| Servicio de nube de nivel PaaS | "Plataforma como servicio" | UD2-03 |
| Producto sobre el que otros construyen (ecosistema) | "Plataforma de comercio electrónico" | UD2-01 |
| Modelo de negocio de intermediación | "Economía de plataformas" (Uber, Airbnb) | UD2-02 |
| Equipo de plataforma (*platform engineering*) | "Los de plataforma nos dan el pipeline" | UD1-02 |
| Plataforma de datos: almacén, lago, herramientas | "Nuestra plataforma de datos" | UD2-08 |
| Plataformas que soportan los datos y las aplicaciones | — | [UD3-01](ud3-proyecto/01-metodologia-del-proyecto.md) |

## Pipeline

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Pipeline de CI/CD: pasos automáticos de integración y despliegue | "El pipeline ha fallado" | UD1-01, UD2-03 |
| Pipeline de datos: ingesta, transformación, carga | "El pipeline nocturno" | UD2-06, UD2-08 |
| Pipeline de ML: preparación, entrenamiento, evaluación | — | UD2-07 |
| Pipeline de RAG: trocear, vectorizar, buscar, generar | — | UD1-09 |
| Pipeline en Unix: tuberías entre procesos | `grep \| sort` | — |

## Automatización

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Automatización industrial: PLC, robots, control | "Ingeniero de automatización" | UD1-03 |
| Integración por scripts y APIs | "Un cron que sincroniza" | UD1-09 |
| RPA: imitar clics en pantallas | "Un robot de UiPath" | UD1-03, UD1-09 |
| Flujos *low-code* (n8n, Make, Zapier) | "Una automatización que crea el ticket" | UD1-09 |
| Flujo con un paso de LLM | — | UD1-09, UD3-02 |
| Agente autónomo | "Automatizarlo con un agente" | UD1-09 |
| Automatización del desarrollo: CI, tests, despliegue | — | UD1-01 |

## Optimización

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Matemática: encontrar la mejor solución (rutas, turnos, asignación) — investigación operativa | "Optimizar las rutas de 40 furgonetas" | UD1-07, UD1-09 |
| Entrenamiento de un modelo: minimizar una función de pérdida | "El optimizador Adam" | UD1-07 |
| Coloquial: mejorar un proceso | "Optimizar la atención al cliente" | UD1-09 |
| Rendimiento de software: hacer que vaya más rápido | "Optimizar la consulta" | — |
| Coste: FinOps, enrutado de modelos | "Optimizar la factura de la nube" | UD2-02 |

## Arquitectura

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Estructura de una aplicación: capas, componentes, dónde vive cada lógica | "Arquitectura de tres capas" | UD1-04, UD2-05 |
| Estilo: monolito, microservicios, *serverless*, *local-first* | "Arquitectura de microservicios" | UD1-04 |
| Arquitectura de red: cliente/servidor, P2P | — | UD1-04 |
| Arquitectura de referencia (Purdue, OpenFog) | — | UD1-03, UD2-04 |
| Arquitectura de un modelo de ML (*transformer*) | "Arquitectura *transformer*" | UD1-07 |
| El rol de arquitecto (actividad más que puesto) | — | UD1-02 |
| Arquitectura de empresa (organización + procesos + sistemas) | — | UD3-01 |

## DevOps

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Cultura: unir desarrollo y operaciones, entrega continua | "Hacer DevOps" | UD1-02, UD1-05 |
| Puesto de trabajo (lo que la cultura decía que no debía ser) | "Buscamos un DevOps" | UD1-02 |
| El conjunto de herramientas (CI/CD, contenedores, IaC) | "La cadena DevOps" | UD2-03 |
| Variantes: SRE, ingeniería de plataforma, MLOps, DataOps, FinOps | — | UD1-02, UD2-07, UD2-02 |

## Full-stack

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Desarrollador que cubre frontend y backend | — | UD1-02 |
| "Hace de todo" en una empresa pequeña (incluido despliegue, datos, soporte) | — | UD1-02 |
| Frontend que sabe montar una API (o al revés) | — | UD1-02 |
| Con IA asistida: "product engineer", de la idea al despliegue | — | UD1-02, UD1-09 |
| Un *stack* concreto (MERN, Spring + Angular) | "Full-stack Java" | — |

## Científico de datos / "los de datos"

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Científico de datos: modelos y análisis avanzado | — | UD2-07 |
| Analista de datos: informes, cuadros de mando, SQL | (a menudo contratado como "científico") | UD2-07 |
| Ingeniero de datos: tuberías, almacenes, calidad | — | UD2-07 |
| Ingeniero de ML / MLOps: modelos en producción | — | UD2-07 |
| Ingeniero de analítica: modelado en el almacén (dbt) | — | UD2-07 |
| Ingeniero de IA: aplicaciones sobre LLM | — | UD1-09, UD2-07 |

## Tiempo real

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Tiempo real duro (OT): respuesta garantizada dentro de un plazo, siempre | "El PLC responde en 10 ms" | UD1-03 |
| Tiempo real blando: "rápido", sin garantía | "Cuadro de mando en tiempo real" (cada 5 minutos) | UD1-06 |
| Comunicación en tiempo real: WebSocket, *streaming* | "Chat en tiempo real" | UD1-04 |
| Procesamiento en flujo frente a por lotes | "Ingesta en tiempo real" (Kafka) | UD2-08 |
| Sistema operativo de tiempo real (RTOS) | — | UD1-03 |

## Local / on-premise / en casa

| Acepción | Ejemplo | Dónde |
|---|---|---|
| En el equipo del usuario (frente a en el servidor) | "Se calcula en local" | UD2-05 |
| En servidores propios (frente a en la nube) | "Lo tenemos *on-premise*" | UD2-03 |
| En la planta o instalación (*edge*, *fog*) | "Un servidor local en la fábrica" | UD2-04 |
| Modelo de IA local (frente a por API) | "Un modelo local con Ollama" | UD2-04 |
| *Local-first*: la fuente de verdad en el cliente, con sincronización | — | UD2-05 |
| Entorno de desarrollo local (`localhost`) | "Funciona en local" | UD1-04 |

## Token

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Unidad de texto de un LLM, y unidad de cobro | "Cuesta 3 € por millón de tokens" | UD1-07, UD2-02 |
| Token de autenticación (JWT, *bearer token*) | "La API pide un token" | UD1-06 |
| Token de acceso a una API de un proveedor (secreto) | "No subas el token al repo" | UD1-10 |
| Token en un enlace firmado | "Enlace con token de un solo uso" | UD3-02 |
| Token en análisis léxico (compiladores) | — | UD1-04 |
| Token de blockchain / criptoactivo | — | UD2-01 |

## Contexto

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Ventana de contexto de un LLM: lo que cabe en una petición | "Se ha llenado el contexto" | UD1-07, UD1-09 |
| Lo que rodea a un dato y le da significado (información) | "Un dato sin contexto" | UD2-06 |
| Contexto de negocio: la situación de la empresa | "El contexto de la decisión" (ADR) | UD3-01 |
| Contexto en programación (objeto de contexto, contexto de ejecución) | — | — |
| Ingeniería de contexto: dar al agente lo que necesita (instrucciones, ficheros, herramientas) | — | UD1-09 |

## Abierto (open)

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Código abierto (licencia que permite usar, modificar, redistribuir) | "Postgres es *open source*" | — |
| Modelo de pesos abiertos (descargables) que puede no ser software libre | "Llama es abierto" (con licencia propia y restricciones) | UD2-04 |
| Estándar o protocolo abierto (MCP, OPC UA, OpenTelemetry) | — | UD1-09, UD1-03, UD1-06 |
| Datos abiertos (*open data*) | — | UD2-06 |
| Formato abierto (Parquet, Iceberg) frente a propietario | — | UD2-08 |

## Sistema

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Sistema informático concreto (el ERP, el CRM) | "Está en el sistema" | UD1-02 |
| Sistema operativo | — | UD2-03 |
| Sistema de control (OT) | "El sistema de seguridad de la planta" | UD1-03 |
| Sistema de información (departamento + proceso + software) | "Sistemas de información" (los de sistemas) | UD1-02 |
| Sistema ciberfísico | — | UD1-03, UD2-01 |
| Sistema de IA (AI Act: el producto que incorpora un modelo) | "Sistema de alto riesgo" | UD1-10 |
| Sistema distribuido / sistema conectado | "Las ventajas de la nube en sistemas conectados" | UD2-05 |

## Instancia

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Máquina virtual en la nube | "Una instancia con GPU" | UD2-03 |
| Copia en ejecución de una aplicación (detrás de un balanceador) | "Tres instancias de la API" | UD1-04 |
| Instancia de una base de datos gestionada | "Una instancia de RDS" | UD2-08 |
| Instancia de una clase (POO) | — | — |
| Instancia de un SaaS para un cliente (*tenant*) | "Vuestra instancia de Jira" | UD2-03 |

## Producto / pedido / lote / cita (términos de dominio)

No son términos técnicos, y por eso son los más peligrosos: cada departamento de una empresa usa el
suyo como si fuera el único. El diseño archivado del proyecto (una conservera con 15 áreas) se
construyó sobre diez de estas ambigüedades: *cliente*, *producto* (¿SKU, receta, formato o lote
físico?), *lote* (de materia prima, de producción o logístico, enlazados N:M), *unidades* (kg, latas,
cajas, con conversión no constante), *precio* (tarifa, pactado, promoción, *rappel* de fin de año),
*pedido* (de venta, de producción o de compra), *fechas* (captura, entrada, producción, caducidad,
expedición), *empleado* (fijo discontinuo: ¿un registro o uno nuevo por campaña?), *devolución*
(venta negativa, movimiento de almacén o incidencia de calidad) y *corrección tardía*. Se usa en
clase como caso de debate; para el proyecto propio, la sección 3 del informe es el glosario de estas
ambigüedades en la empresa elegida ([UD1-02](ud1-digitalizacion-ia-software/02-la-empresa-por-dentro.md),
[UD2-06](ud2-tecnologias-arquitectura/06-dato-informacion-ciclo-de-vida.md),
[UD3-02](ud3-proyecto/02-ejemplo-trabajado.md)).

## Industria 4.0 / 5.0, THD, KET

| Acepción | Ejemplo | Dónde |
|---|---|---|
| Industria 4.0: estrategia industrial alemana (2011); por extensión, la digitalización industrial | — | UD1-01 |
| Industria 5.0: reposicionamiento de la Comisión Europea (2021), centrado en la persona | — | UD1-01 |
| THD: lista de tecnologías de *Industria Conectada 4.0* (España) | — | UD2-01 |
| KET: lista distinta de la Comisión Europea, no digital | — | UD2-01 |
| Cualquiera de ellas como etiqueta de subvención o de marketing | — | UD2-01 |

---

## Términos añadidos durante el curso

Espacio para los que surjan en los debates. Formato: término, acepciones, quién las usa, en qué
sesión apareció.

| Término | Acepción 1 | Acepción 2 | Quién lo dijo / sesión |
|---|---|---|---|
| | | | |
