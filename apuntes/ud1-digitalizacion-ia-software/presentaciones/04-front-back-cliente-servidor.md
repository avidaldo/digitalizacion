---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: "DAOSP · UD1-04 · Frontend/backend y cliente/servidor"
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

# Frontend/backend y cliente/servidor

Dos ejes que se confunden, y la API que los une

UD1 · apunte 04 · [texto completo](../04-front-back-cliente-servidor.md)

---

<!-- _class: idea -->

**Cliente/servidor** es una *relación*: uno pide, otro responde.

**Frontend/backend** es una *responsabilidad*: uno presenta, otro guarda y decide.

Coinciden en la web de los años 2010 por accidente histórico. Separarlos es lo que permite decidir **dónde vive cada pieza de lógica**.

---

## Cliente/servidor es un rol, no una máquina

```text
navegador ──HTTP──▶ servidor web / API ──SQL──▶ base de datos
                         │
                         ├──DNS──▶ servidor DNS
                         └──HTTP─▶ pasarela de pago
```

- El servidor web es *servidor* del navegador y *cliente* de la base de datos, del DNS y de la pasarela.
- En la misma máquina puede haber un servidor (Postgres en el puerto 5432) y su cliente.
- La alternativa existe: *peer-to-peer* (BitTorrent, Git entre repositorios). Cliente/servidor es una elección, no una ley.

---

## "Servidor": siete acepciones en uso

| Se dice | Es en realidad |
| --- | --- |
| "Está en el armario del sótano" | Una máquina física |
| "Arranca el servidor con `npm run dev`" | Un proceso que escucha en un puerto |
| "Postgres actúa como servidor" | Un rol en una conversación |
| "Levantamos tres servidores en AWS" | Máquinas virtuales alquiladas |
| "Cada microservicio en su servidor" | Contenedores |
| "Un servidor *serverless*" | Funciones bajo demanda: hay servidores, pero no son tuyos |
| "Pregúntale al servidor si existe" | El backend entero, esté donde esté |

---

## Frontend/backend sin red

- **Editor de fotos**: la ventana y los menús frente al motor que aplica los filtros. Un solo proceso.
- **Compilador**: el *frontend* entiende el lenguaje fuente; el *backend* genera código para la máquina. LLVM: muchos *frontends* (C, Rust, Swift) sobre un *backend* común.
- **"Backend de almacenamiento"**: la implementación intercambiable de una interfaz (disco, S3, memoria).

> La palabra describe **una posición en un flujo**, no una tecnología.

---

## Cuando los ejes se separan

| Situación | Frontend corre en | Backend corre en |
| --- | --- | --- |
| Web clásica (PHP, plantillas) | **Servidor** (genera HTML) | Servidor |
| SPA (React, Vue, Angular) | Navegador | Servidor |
| SSR (Next.js, Nuxt) | Servidor **y** navegador | Servidor |
| App móvil nativa | Dispositivo | Servidor **y una capa local** → [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md) |
| *Edge functions* | — | Cientos de puntos de la red |
| *Local-first* | Local | Local; el servidor solo replica |

Ante cualquier código, **dos preguntas separadas**: ¿qué responsabilidad tiene? ¿dónde se ejecuta?

---

## La frontera con nombre: la API

Entre frontend y backend — y entre dos sistemas cualesquiera — hay un **contrato**: qué se puede pedir, en qué formato, qué se recibe. En la web: **REST sobre HTTP con JSON**.

| | Petición | Respuesta |
| --- | --- | --- |
| Primera línea | `GET /api/v2/pokemon/pikachu` | `200 OK` |
| Cabeceras | `Accept: application/json` | `Content-Type: application/json` |
| Cuerpo | Vacío en un `GET`; JSON en un `POST` | El recurso, en JSON |

- HTTP es **sin estado**: el servidor no recuerda la petición anterior.
- REST: cada **recurso** tiene una URL, se manipula con los métodos de HTTP y viaja su **representación**.

---

## Métodos y códigos de estado

| Método | Significado | ¿Repetirlo cambia algo más? |
| --- | --- | --- |
| `GET` | Leer | No: seguro e idempotente |
| `POST` | Crear o lanzar una acción | Sí: dos `POST`, dos pedidos |
| `PUT` / `PATCH` | Sustituir / modificar en parte | `PUT` no; `PATCH`, depende |
| `DELETE` | Borrar | No: idempotente |

`2xx` bien · `3xx` está en otro sitio · `4xx` error del **cliente** (`400`, `401`, `403`, `404`, `429`) · `5xx` error del **servidor**

---

## El ejemplo de clase: PokeAPI

```bash
curl https://pokeapi.co/api/v2/pokemon/pikachu
```

```json
{ "id": 25, "name": "pikachu", "height": 4, "weight": 60,
  "types": [ { "slot": 1, "type": { "name": "electric",
      "url": "https://pokeapi.co/api/v2/type/13/" } } ] }
```

- **Los recursos enlazan a recursos**: el tipo llega como URL, y el cliente la sigue si la necesita.
- **Las unidades son parte del contrato**: `60` son hectogramos (6 kg), `4` son decímetros (0,4 m).
- **Las listas se paginan** (`?limit=3&offset=0` → `count`, `results`, `next`) y **los errores son respuestas** (`/pokemon/noexiste` → `404`).

---

## "REST" también se mueve

| Quién lo dice | Qué significa |
| --- | --- |
| Fielding (2000) | Recursos, métodos, sin estado **y** navegación por los enlaces que da el servidor; casi nadie lo cumple entero |
| Uso corriente | Recursos con URL, métodos HTTP y JSON |
| "Tenemos una API REST" | A veces, `POST /api` con un campo `accion`: llamadas a procedimiento remoto sobre HTTP |

Alternativas con nombre propio: GraphQL (el cliente elige los campos), gRPC (binario, entre servicios), WebSocket (canal abierto, tiempo real).

---

## Dónde vive cada lógica

| Lógica | Dónde | Por qué |
| --- | --- | --- |
| Validación de formato | Cliente **y** servidor | En cliente, por rapidez; en servidor, porque cualquiera llama a la API con `curl` |
| Autorización | Servidor, siempre | En cliente se salta editando el JavaScript |
| Precios y totales | Servidor | Un precio calculado en cliente lo elige el usuario |
| Secretos, claves de API | Servidor, nunca en cliente | Todo lo que llega al navegador es público |
| Estado de la interfaz | Cliente | No le importa a nadie más |

> **"Nunca confíes en el cliente"** es la DMZ industrial de [03](../03-it-y-ot.md): lo que cruza la frontera se valida.

---

## Monolito, microservicios y la vuelta al monolito

- **Monolito**: simple de desarrollar y depurar; el equipo entero pisa el mismo código.
- **Microservicios**: despliegue y escalado independientes, a cambio de red, consistencia difícil y coste operativo.
- **Monolito modular**: un despliegue con fronteras internas estrictas; lo más recomendado para empezar.

Prime Video (2023) fusionó en un proceso un servicio de monitorización distribuido y **bajó su coste en torno a un 90 %**: las fronteras entre procesos se pagan, y solo compensan cuando compran algo. Los microservicios son, ante todo, una forma de organizar **equipos** → ley de Conway en [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md).

---

## El paralelo, explícito

| | IT / OT | Frontend / backend |
| --- | --- | --- |
| Prioridades distintas | Seguridad física, disponibilidad / confidencialidad | Experiencia, latencia / integridad, consistencia |
| Una frontera con nombre | DMZ (nivel 3.5), entre MES y ERP | API, BFF, capa de red |
| La frontera se mueve | IIoT y *edge* llevan IT a la planta | SSR y *edge* mueven front y back |
| Lo que cruza se valida | Cortafuegos, DMZ | "Nunca confíes en el cliente" |
| Culturas distintas | Ingeniería frente a sistemas | "Los de front" frente a "los de back" |

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [03](../03-it-y-ot.md) IT y OT | El mismo patrón de dos entornos y una frontera móvil |
| [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md) Conway y el caso móvil | Equipos de front y de back producen una API con fricción; el móvil añade una capa local |
| [06](../06-extremo-a-extremo.md) Seguir un dato | Una petición HTTP de punta a punta; las unidades que nadie acordó |
| [08](../08-ia-datos-sectores-lenguajes.md) IA y lenguajes | Llamar a un LLM es la misma petición REST, con clave y factura por *tokens* |
| [UD2-05](../../ud2-tecnologias-arquitectura/05-donde-vive-la-logica.md) Dónde vive la lógica | El debate central de la UD2 parte de esta tabla |

---

## Para debatir

- Un formulario calcula el total en JavaScript para mostrarlo al instante. ¿Lo recalcula el servidor? ¿Qué pasa si llega un total distinto? ¿Qué significa aquí "el cliente"?
- PokeAPI devuelve `"weight": 60`. ¿60 qué? ¿Dónde debería estar escrito? ¿Qué pasa si una app de nutrición lo lee como kilos?
- `POST /api` con `{"accion": "borrarPedido", "id": 7}`: ¿es REST? ¿Qué se pierde frente a `DELETE /pedidos/7`?
- Un equipo de 4 personas quiere arrancar con 12 microservicios "para que escale". Argumentar en contra, y a favor en el único caso en que tendría sentido.
