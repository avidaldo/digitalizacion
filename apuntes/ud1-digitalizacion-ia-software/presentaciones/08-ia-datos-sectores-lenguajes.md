---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: "DAOSP · UD1-08 · IA, datos, sectores y lenguajes"
style: |
  section { font-size: 28px; padding: 48px 64px; }
  section.portada { justify-content: center; }
  section.portada h1 { font-size: 56px; }
  section.idea { justify-content: center; font-size: 34px; }
  table { font-size: 22px; }
  pre { font-size: 22px; }
  footer { font-size: 15px; }
---

<!-- _class: portada -->
<!-- _paginate: false -->

# IA, datos, sectores y lenguajes

Por qué la IA necesita datos, dónde se aplica y con qué se programa

UD1 · apunte 08 · [texto completo](../08-ia-datos-sectores-lenguajes.md)

---

<!-- _class: idea -->

Un modelo de ML es **una función aprendida de datos**: sin datos no hay modelo, y con datos malos el modelo es malo.

Por eso la IA moderna llegó *después* del Big Data, y por eso la ventaja de una empresa suele estar en **sus datos, no en su algoritmo**. Y para *usar* IA desde una aplicación no hace falta cambiar de lenguaje: es **una petición HTTP**.

---

## Por qué la IA necesita datos

- Entrenar es ajustar millones o billones de parámetros para que la salida se parezca a los ejemplos. Con pocos, el modelo **memoriza** (*sobreajuste*); con muchos y variados, **generaliza**.
- **Leyes de escala** (2020): en *deep learning*, el rendimiento mejora de forma predecible con el tamaño del modelo, los datos y el cómputo.
- Los LLM se entrenan con billones de *tokens*, una fracción sustancial del texto público de Internet. ¿Qué pasa cuando ese texto se agota, o se llena de salidas de otros modelos?

---

## Cuatro matices

| Matiz | Consecuencia |
| --- | --- |
| Calidad antes que cantidad | Un millón de etiquetas mal puestas enseña los errores; limpiar datos se come el proyecto → [UD2-07](../../ud2-tecnologias-arquitectura/07-ciencia-de-datos.md) |
| Rendimientos decrecientes | Doblar los datos no dobla la calidad: hacen falta datos *distintos* |
| Sesgo | El modelo aprende las injusticias del histórico; seleccionar personal es alto riesgo → [10](../10-seguridad-y-regulacion.md) |
| No siempre se entrena | Con un LLM, los datos de la empresa van **en el contexto** (RAG): de "datos para entrenar" a "datos para consultar" |

---

## El volante de datos, y el lema del petróleo

```text
más usuarios → más datos → mejor modelo → mejor producto → más usuarios
```

- Es como se consolidan los líderes en búsqueda, recomendación y mapas.
- "Los datos son el nuevo petróleo", y por qué falla: el petróleo se consume y los datos no; el petróleo vale en bruto y los datos solo refinados; almacenar petróleo no genera obligaciones legales sobre personas.

> Almacenar datos que no se usan no es un activo: es **un coste y un riesgo** → RGPD en [10](../10-seguridad-y-regulacion.md).

---

## Cómo se convierte en dinero

| Mecanismo | Ejemplos | Dónde está el dinero |
| --- | --- | --- |
| **Predecir mejor** | Demanda, mantenimiento predictivo, fraude, abandono (*churn*) | Menos stock inmovilizado, menos paradas, menos fraude, clientes retenidos |
| **Automatizar** | Tickets de soporte, extracción de facturas y contratos, código | Horas de persona por tarea |
| **Personalizar** | Recomendación, precios dinámicos, publicidad dirigida | Ventas y margen; el negocio entero de Google y Meta |

> Predecir que una máquina fallará el jueves no vale nada si mantenimiento no tiene ventana el miércoles ni la pieza en almacén. Sin **un proceso que actúe sobre la predicción**, el proyecto no sale del piloto.

---

## Big Data: las V

| V | Qué mide | Ejemplo |
| --- | --- | --- |
| Volumen | No cabe en una máquina | Terabytes de registros de acceso al día |
| Velocidad | Ritmo de llegada y de respuesta | Aprobar una transacción de tarjeta en 100 ms |
| Variedad | Formatos heterogéneos | Correos, PDF, fotos de incidencias y la base del ERP, juntos |
| Veracidad | Ruido, incoherencia | Sensores descalibrados, formularios mal rellenados |
| Valor | Lo que se puede extraer | La única que importa al negocio, y la que justifica las demás |

Las tres primeras son la definición original (Laney, 2001); el resto, añadidos posteriores. Hay listas de diez V: inflación terminológica.

---

## "Big" es relativo a las herramientas

- Un CSV de 10 GB **no** es Big Data: cabe en un portátil con pandas o DuckDB.
- 10 TB diarios de logs **sí**: exigen almacenamiento y procesamiento distribuidos.

```text
2010 Hadoop  →  2014 Spark  →  hoy BigQuery, Snowflake, Databricks
```

- La palabra pasó de moda hacia 2018, no la tecnología: la nube hizo que lo grande dejara de ser un problema especial. Hoy se dice "datos", "plataforma de datos" o *lakehouse*, con el mismo contenido → [UD2-08](../../ud2-tecnologias-arquitectura/08-almacenamiento-y-cloud-computing.md).

---

## Sectores: madurez, no titulares

| Sector | Consolidado | En despliegue (2024–2026) |
| --- | --- | --- |
| Software | Búsqueda, recomendación | Agentes de código |
| Finanzas y seguros | Fraude, *scoring*, tarificación | Análisis de documentos |
| Comercio | Recomendación, demanda, logística | Búsqueda conversacional |
| Sanidad | Imagen médica, fármacos | Apoyo al diagnóstico (alto riesgo) |
| Industria | Inspección visual, mantenimiento predictivo | Gemelos digitales con IA |
| Transporte | Asistencia a la conducción, rutas | Conducción autónoma, en pocas ciudades |

En software, la implantación es la más profunda → [09](../09-ia-para-el-desarrollo-de-software.md).

---

## Lenguajes: tres capas

```text
APLICACIÓN  consumir IA desde un producto, en cualquier lenguaje:
            Java, Kotlin, C#, TypeScript, Swift, Python, vía HTTP o SDK
MODELADO    entrenar, evaluar, experimentar:
            Python (PyTorch, JAX, scikit-learn, pandas), R, Julia
MOTOR       los cálculos que hacen posible lo anterior:
            C++, CUDA, Rust, Triton (llama.cpp, ONNX Runtime, vLLM)
```

- "La IA se hace en Python" es verdad e incompleto: Python es **el pegamento** que llama a bibliotecas escritas en C++ y CUDA.
- SQL es imprescindible, porque los datos viven en bases de datos; Kotlin y Swift llevan modelos al dispositivo móvil.

---

## Lo que significa para un alumno de DAM

- No hace falta cambiar de lenguaje para "hacer IA": integrar un LLM en Kotlin, Java o C# es **una llamada HTTP**, o un SDK oficial.
- Con las técnicas de cualquier integración — errores, tiempos de espera, reintentos, coste — y las cautelas propias de [10](../10-seguridad-y-regulacion.md).
- La "ingeniería de IA" de 2024–2026 es en buena parte **desarrollo backend ordinario alrededor de un componente no determinista**.
- Python aparece al entrenar, evaluar o analizar datos, y es fácil de añadir a un perfil de DAM.

---

## La llamada a un LLM es una petición REST

La de PokeAPI en [04](../04-front-back-cliente-servidor.md), con tres diferencias: `POST` con cuerpo, una **clave de API** que identifica a quien paga y una respuesta que dice cuántos *tokens* se han gastado. OpenAI y Google usan la misma forma.

```http
POST https://api.anthropic.com/v1/messages
x-api-key: <clave secreta: vive en el servidor, nunca en el cliente>
anthropic-version: 2026-10-21
content-type: application/json

{ "model": "claude-haiku-5-5", "max_tokens": 1000,
  "system": "Clasifica: pedido, incidencia o spam. Solo la categoría.",
  "messages": [
    { "role": "user", "content": "El pedido 4512 llegó con una lata abollada." } ] }
```

---

## La respuesta, y lo que enseña

```json
{ "role": "assistant", "model": "claude-haiku-5-5",
  "content": [ { "type": "text", "text": "incidencia" } ],
  "stop_reason": "end_turn",
  "usage": { "input_tokens": 48, "output_tokens": 4 } }
```

| Campo | Lo que enseña |
| --- | --- |
| `x-api-key` | La clave vive en el backend: en el navegador o el móvil es pública → [04](../04-front-back-cliente-servidor.md) |
| `messages` | La API no recuerda: se reenvía la conversación entera, y cada turno cuesta más → [07](../07-que-es-la-ia.md) |
| `usage`, `model` | La factura: entrada y salida a precios distintos, según la gama → [UD2-02](../../ud2-tecnologias-arquitectura/02-sostenibilidad-coste-y-mercados.md) |
| `content` | Se busca el bloque `text` (antes puede llegar uno `thinking`) y se **valida** la categoría → [10](../10-seguridad-y-regulacion.md) |

---

## ¿Es el *prompt* un lenguaje de programación?

- **No en sentido estricto**: no tiene sintaxis formal ni semántica definida, y el mismo texto da resultados distintos con modelos distintos.
- **Pero hay un continuo**: los *prompts* se versionan, se prueban y se componen como código; hay bibliotecas (DSPy) que los optimizan solas; y las **salidas estructuradas** — JSON con un esquema — convierten la respuesta en algo que el código procesa de forma fiable.

> El *prompt* no es código, pero **se gestiona como código**.

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [01](../01-que-es-digitalizar.md) Qué es digitalizar | La IA vive en los peldaños 5 y 6, y no se llega sin integrar los datos |
| [04](../04-front-back-cliente-servidor.md) Front/back | La llamada al LLM es REST; la clave es lógica que vive en el servidor |
| [06](../06-extremo-a-extremo.md) Seguir un dato | La IA es el último eslabón de la cadena |
| [07](../07-que-es-la-ia.md) Qué es la IA | Gama, *tokens* y falta de memoria, vistos en una petición real |
| [10](../10-seguridad-y-regulacion.md) Seguridad | Sesgo, alto riesgo y datos que salen hacia un proveedor |
| [UD2-08](../../ud2-tecnologias-arquitectura/08-almacenamiento-y-cloud-computing.md) Almacenamiento y nube | Dónde viven los datos cuando "big" deja de ser especial |

---

## Para debatir

- Una PYME con ocho años de ventas en un ERP quiere "poner IA para predecir ventas". ¿Qué hay que preguntar antes de aceptar el encargo? ¿Qué proyecto es en realidad?
- Si los LLM se han entrenado con "todo Internet", ¿por qué siguen necesitando *los datos de la empresa*? ¿Qué relación con los datos es esa?
- "Python es lento, así que la IA debería hacerse en C++." ¿Por qué es y no es verdad?
- El modelo responde "Creo que es una incidencia" en vez de "incidencia". ¿Qué debe hacer el código? ¿Qué tiene que ver con "nunca confíes en el cliente"?
