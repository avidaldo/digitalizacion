---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: 'DAOSP · UD1-07 · Qué es "la IA"'
style: |
  section { font-size: 28px; padding: 48px 64px; }
  section.portada { justify-content: center; }
  section.portada h1 { font-size: 60px; }
  section.idea { justify-content: center; font-size: 34px; }
  table { font-size: 22px; }
  pre { font-size: 22px; }
  footer { font-size: 15px; }
---

<!-- _class: portada -->
<!-- _paginate: false -->

# Qué es "la IA"

IA simbólica, *machine learning*, *deep learning*, LLM — y cómo elegir modelo

UD1 · apunte 07 · [texto completo](../07-que-es-la-ia.md)

---

<!-- _class: idea -->

"Inteligencia artificial" es un paraguas que cambia de contenido cada década; hoy, en la calle, significa casi siempre **un LLM**.

Para un desarrollador importan menos las siglas que **cómo se comporta el software**: reglas escritas y deterministas, una función aprendida y estadística, o un generador de texto que no responde siempre lo mismo.

---

## Setenta años en una tabla

| Época | "La IA" era | Ejemplo |
| --- | --- | --- |
| 1956–1980 | Reglas escritas a mano (GOFAI) | Sistemas expertos, Prolog, ajedrez por búsqueda |
| 1990–2010 | *Machine learning*: la función se aprende de datos | Filtros de spam, árboles de decisión |
| 2012–2017 | *Deep learning* entrenado en GPU | AlexNet (2012), voz, traducción |
| 2017–2022 | *Transformers* que escalan con datos y cómputo | BERT, GPT-3 (2020) |
| 2022–2024 | IA generativa, LLM | ChatGPT (noviembre de 2022) |
| 2024–2026 | Agentes, razonamiento, multimodalidad | Agentes de código |

El ML clásico sigue siendo **la mayor parte de la IA en producción**.

---

## El "efecto IA"

- Cuando algo funciona, deja de llamarse IA: el ajedrez, el OCR, la ruta del GPS, el filtro de spam. Mañana, el autocompletado de código será "el editor".
- El término señala siempre **la frontera de lo que aún sorprende**.
- La IA clásica no ha desaparecido: el planificador de rutas de un almacén o el motor de reglas de una aseguradora siguen siendo IA simbólica, y la herramienta correcta. **Un LLM no sustituye a un algoritmo de optimización; en todo caso, lo llama.**

> El mismo fenómeno que "servidor" en [04](../04-front-back-cliente-servidor.md): la palabra se queda y el contenido se mueve.

---

## Las siglas anidadas

```text
IA: el campo
├── IA simbólica: reglas, búsqueda, planificación, lógica
└── Machine learning: el comportamiento se aprende de datos
    ├── ML clásico: regresión, árboles, SVM, k-means, gradient boosting
    └── Deep learning: redes neuronales de muchas capas
        ├── Visión (CNN)
        └── Transformers ── LLM, modelos multimodales
```

- Un programa de ML no clasifica gatos: **produce otro programa** — el modelo — que los clasifica.
- Un LLM se entrena para predecir el siguiente *token*; de ese objetivo emergen conversar, resumir, traducir y programar.

---

## Y las que no están anidadas

| Término | Qué es | Relación con la IA |
| --- | --- | --- |
| Big Data | Infraestructura para datos que no caben en una máquina | La IA moderna lo necesita para entrenarse; él no necesita IA → [08](../08-ia-datos-sectores-lenguajes.md) |
| Análisis / ciencia de datos | Extraer conclusiones con estadística, consultas, visualización | Un `GROUP BY` es análisis de datos y no es IA → [UD2-07](../../ud2-tecnologias-arquitectura/07-ciencia-de-datos.md) |
| Estadística | La regresión lineal es de 1805 | Se solapa tanto con el ML que la diferencia es en parte de tribu |

> En una empresa, los cuatro términos los usa el mismo departamento sobre los mismos datos, y la etiqueta depende **del presupuesto que quiere pedir**.

---

## Tres formas de comportarse

| | Software tradicional | ML clásico | LLM |
| --- | --- | --- | --- |
| Se construye | Se programa | Se entrena con datos etiquetados | Se preentrena con texto y se ajusta |
| Mismo input, mismo output | Sí | Sí, una vez entrenado | En la práctica, no |
| Fuera de lo previsto | Error definido | Predicción mala, sin aviso | Texto plausible y falso: **alucinación** |
| Se prueba con | Pruebas unitarias | Métricas sobre datos de prueba | ***Evals***: salidas aceptables, no "la" salida |
| Se cambia | Editando el código | Reentrenando | *Prompt*, contexto, herramientas, *fine-tuning* |

---

## Lo que la experiencia del chat esconde

- **El modelo no recuerda nada.** La aplicación guarda el historial y lo reenvía entero en cada petición; el **contexto** es lo máximo que cabe en una.
- **No es determinista.** Cada *token* se elige por muestreo entre los probables, y aun con el azar al mínimo hay variación por detalles numéricos del hardware y del procesamiento en lote.
- **Su conocimiento está congelado** en la fecha de corte del entrenamiento: lo posterior tiene que llegarle en el contexto → RAG en [09](../09-ia-para-el-desarrollo-de-software.md).
- **La alucinación es estructural**, no un fallo que corregirá la próxima versión.
- **La superficie de ataque es nueva**: inyección de *prompt* → [10](../10-seguridad-y-regulacion.md).

---

## Taxonomía mínima del ML clásico

| Tipo | Aprende | Ejemplo |
| --- | --- | --- |
| Supervisado | De ejemplos etiquetados: *clasificación* y *regresión* | ¿Spam o no? ¿Cuánto venderemos mañana? |
| No supervisado | Estructuras, sin etiquetas | Segmentar clientes, detectar anomalías |
| Por refuerzo | Por prueba y error, con recompensas | Robótica, juegos y la fase final de los LLM (RLHF) |

**Discriminativo** (esto es un gato) frente a **generativo** (aquí tienes un gato): los LLM y los modelos de imagen son generativos; casi todo el ML en producción es discriminativo.

---

## Cuándo un LLM y cuándo no

| Problema | Herramienta correcta |
| --- | --- |
| Conceder un crédito con 30 variables numéricas | Reglas o *gradient boosting*: explicable y auditable |
| Extraer campos de facturas en PDF de formatos variados | LLM multimodal |
| Responder sobre la documentación interna | LLM con RAG |
| La ruta de 40 furgonetas | Investigación operativa: hay un óptimo |
| El IVA de una factura | Código |

> **Si el problema tiene una respuesta correcta calculable, se calcula.** El LLM entra donde la entrada es lenguaje o imagen con una variedad imposible de enumerar.

---

## Qué LLM: cuatro ejes

- **Gama**: capacidad frente a coste y velocidad.
- **Esfuerzo**: cuánto razona antes de responder.
- **Contexto**: cuánto texto se le da.
- **Dónde se ejecuta**: la API de un proveedor o un modelo local.

| Pesos cerrados: solo por API o en sus productos | Familias con modelos de pesos abiertos |
| --- | --- |
| OpenAI (GPT), Anthropic (Claude), Google (Gemini), xAI (Grok) | Meta (Llama), Mistral, Alibaba (Qwen), DeepSeek, Moonshot (Kimi): se descargan y corren en local → [UD2-04](../../ud2-tecnologias-arquitectura/04-edge-fog-mist.md) |

Los nombres cambian cada pocos meses; la estructura de la elección se mantiene desde 2023.

---

## Gama: más grande no siempre es mejor

| Gama | Ejemplos | Para qué |
| --- | --- | --- |
| Pequeña y rápida | Haiku, Gemini Flash, las variantes *mini* y *nano* de GPT | Clasificar, extraer, resumir; subagentes que leen mucho |
| Intermedia | Sonnet y equivalentes | El trabajo diario de programación con alcance claro |
| Grande | Opus, Fable, las gamas altas de GPT y Gemini | Fallos difíciles, arquitectura, tareas largas con poca supervisión |

- El precio cambia en **dos órdenes de magnitud**: en la API de Anthropic, de 0,10 a 10 dólares por millón de *tokens* de entrada (noviembre de 2026).
- Se compara el **coste por tarea terminada**: un modelo barato que necesita tres intentos no sale barato.
- Un intermedio de hoy suele superar al grande de hace un año.

---

## Esfuerzo: cuánto piensa antes de responder

Los modelos con razonamiento generan texto interno (*thinking*) antes de la respuesta. Más esfuerzo rinde en lo difícil, a cambio de *tokens* — que se pagan como salida aunque no se vean — y de espera; con rendimientos decrecientes y riesgo de "pensar de más" en lo sencillo.

| Nivel | Cuándo |
| --- | --- |
| `low` | Lluvia de ideas, primer borrador, renombrar algo |
| `medium` | El trabajo diario con alcance claro |
| `high` | Cuando importa verificar o hay casos límite: arreglar un fallo |
| `xhigh`, `max` | Problemas difíciles que el agente resuelve solo; `max` puede pensar de más |

---

## Contexto: más grande no es más fácil

Muchos modelos admiten ya **un millón de *tokens***: varios libros. Llenarlo tiene tres costes:

1. **Cada vuelta lo reenvía todo**: el coste y la espera crecen con la conversación.
2. **El modelo encuentra peor** lo relevante entre material irrelevante: "perdido en el medio" (Liu et al., 2023).
3. **Al llenarse, la herramienta compacta** — resume — y los detalles se pierden.

La práctica: una conversación por tarea; los ficheros pertinentes, no el repositorio entero; conversación nueva al cambiar de tema; revisar los resúmenes antes de seguir.

---

## Dónde se elige (noviembre de 2026)

| | GitHub Copilot | Claude Code |
| --- | --- | --- |
| Modelo | Selector en el chat; en Free y Student, siempre **Auto** | `/model`: `haiku`, `sonnet`, `opus`, `fable` |
| Esfuerzo | Configurable en los modelos que lo admiten | `/effort`, de `low` a `max`; `ultrathink` solo para un *prompt* |
| Contexto | Hasta un millón de *tokens* en algunos modelos | `/context` lo muestra, `/compact` lo resume, `/clear` lo vacía |
| Coste | Créditos mensuales (*GitHub AI Credits*) según modelo y *tokens* | Suscripción con límites, o pago por *token* con una clave de API |

> **La gama y el esfuerzo suben cuando el problema es difícil y equivocarse cuesta más que esperar; el contexto se mantiene pequeño y pertinente siempre.**

---

## Presente y futuro, con la medida justa

- **Presente**: IA generativa masiva en oficinas, software y atención al cliente; ML clásico en recomendación, riesgo y fraude.
- **Tres futuros que se defienden en serio**:
  - *Aceleración*: agentes cada vez más capaces; AlphaFold (Nobel de 2024).
  - *Meseta*: mejoras decrecientes, alucinación persistente, burbuja parcial, como la de las telecomunicaciones de 2000, que dejó fibra útil.
  - *Riesgos*: concentración de poder, desinformación, empleo, uso militar → [10](../10-seguridad-y-regulacion.md).
- **La posición práctica**: el trabajo pasa de *escribir* a *especificar, revisar y decidir* → [09](../09-ia-para-el-desarrollo-de-software.md).

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [04](../04-front-back-cliente-servidor.md) Front/back | "Servidor" e "IA": palabras que se quedan mientras su contenido se mueve |
| [08](../08-ia-datos-sectores-lenguajes.md) IA y datos | Sin datos no hay modelo; llamar a un LLM es una petición HTTP |
| [09](../09-ia-para-el-desarrollo-de-software.md) IA para el desarrollo | Agentes, RAG y *skills* existen para gestionar el contexto y la falta de memoria |
| [10](../10-seguridad-y-regulacion.md) Seguridad | La inyección de *prompt* nace de que instrucciones y datos son el mismo texto |
| [UD2-02](../../ud2-tecnologias-arquitectura/02-sostenibilidad-coste-y-mercados.md) Coste | El *token* es la unidad de la factura |
| [UD2-07](../../ud2-tecnologias-arquitectura/07-ciencia-de-datos.md) Ciencia de datos | Analizar datos no es hacer IA |

---

## Para debatir

- "Nuestro termostato tiene IA." ¿Un LLM, un modelo de ML clásico, una regla *si-entonces* o marketing? ¿Cómo se sabría?
- Un motor de ajedrez venció en 1997 al campeón del mundo. ¿Era IA entonces? ¿Lo es ahora? ¿Qué dice eso del término?
- Si un LLM responde distinto cada vez, ¿cómo se prueba una función que lo llama? ¿Qué se prueba realmente?
- Renombrar una variable en 40 ficheros; encontrar por qué una prueba falla una vez de cada diez; resumir un PDF de 200 páginas. ¿Qué gama, qué esfuerzo y cuánto contexto para cada tarea?
