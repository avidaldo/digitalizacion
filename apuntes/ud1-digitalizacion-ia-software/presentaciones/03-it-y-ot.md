---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: "DAOSP · UD1-03 · IT y OT"
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

# IT y OT

Dos mundos con una frontera que se mueve

UD1 · apunte 03 · [texto completo](../03-it-y-ot.md)

---

<!-- _class: idea -->

**IT** gestiona información. **OT** controla procesos físicos.

Fueron mundos separados durante cuarenta años; digitalizar la industria es **conectarlos**, y la frontera entre ambos se desplaza con cada tecnología nueva.

Es también el molde de un contraste que un desarrollador maneja a diario: **frontend/backend**.

---

## Qué hay en cada lado

```text
OT (planta)              FRONTERA            IT (negocio)
sensores, actuadores     MES                 ERP, CRM
PLC, DCS                 DMZ industrial      BI, analítica
SCADA, HMI, historian    pasarelas           web, apps, portales
```

- **PLC**: ordenador industrial que lee entradas, aplica lógica y escribe salidas en ciclos de milisegundos.
- **SCADA / HMI**: la supervisión: pantallas de la planta, alarmas, históricos.
- **MES**: recibe órdenes del ERP, las reparte a las máquinas y devuelve lo producido. Software de IT que habla con OT.

---

## El modelo de Purdue: la frontera tiene número

| Nivel | Qué hay | Escala de tiempo | Mundo |
| --- | --- | --- | --- |
| 0–1 | Sensores, actuadores; PLC, DCS | Milisegundos | OT |
| 2 | SCADA, HMI | Segundos | OT |
| 3 | MES, historian, planificación | Minutos–horas | Frontera |
| 3.5 | DMZ industrial | — | Frontera |
| 4–5 | ERP, correo, BI; red corporativa | Horas–días | IT |

Dos lecciones, no una lista: **el tiempo que importa es distinto en cada nivel** (un PLC que tarda 2 s es un accidente; un ERP que tarda 2 s es normal), y **la frontera es el nivel 3**, que la digitalización va engrosando.

---

## Las diferencias que importan

| | IT | OT |
| --- | --- | --- |
| Prioridad de seguridad | Confidencialidad → integridad → disponibilidad | **Personas** → disponibilidad → integridad → confidencialidad |
| Si falla | Datos, dinero, reputación | Lesiones, contaminación, explosión |
| Vida del equipo | 3–5 años | 15–30 años |
| Actualizar | Frecuente; se reinicia | En paradas planificadas |
| Tiempo | *Best effort* | Determinista: siempre dentro de plazo |
| Cultura | "Muévete rápido" | "No toques lo que funciona" |

---

## Por qué convergen

- **Ambos son software en ordenadores**: SCADA es una aplicación con base de datos; OPC UA, una arquitectura cliente/servidor con cifrado y certificados.
- **Ambos usan la misma red**: Ethernet industrial, MQTT en planta y en la nube.
- **Ambos se atacan**: con la conexión desapareció el aislamiento físico (*air gap*).
- **Ambos convergen en el dato**: lo que produce y consume cada máquina vale en el negocio → [06](../06-extremo-a-extremo.md).

> Colonial Pipeline (2021): el *ransomware* entró en IT y el oleoducto paró, porque no se podía garantizar que OT estuviera a salvo. **La frontera ya no aísla.**

---

## La frontera se mueve

| Época | Dónde está la frontera |
| --- | --- |
| Años 80–90 | Nítida: OT eléctrica y neumática, IT en la oficina; no se hablan |
| 2000–2010 | Una pasarela: aparece el MES, SCADA pasa a Windows y Ethernet |
| 2010–2020 | IIoT y nube: ¿dónde está la frontera si el historian está en AWS? |
| 2020–2026 | *Edge* e IA en planta: un modelo de visión corre al pie de la línea, pero se entrena en la nube y se despliega con contenedores |

**La frontera ya no es un lugar: es una decisión de diseño.**

---

## El mismo patrón en el software

| Año | Navegador | Servidor |
| --- | --- | --- |
| 1995 | Muestra HTML | Hace todo |
| 2015 | Ejecuta la aplicación entera | Datos y reglas |
| 2026 | Parte del "frontend" se ejecuta en el servidor | Parte del "backend" se ejecuta en el borde de la red |

Dos entornos, prioridades distintas, una frontera con nombre que se valida y que se mueve con la tecnología: se desarrolla en [04](../04-front-back-cliente-servidor.md).

---

## Tecnologías: basta con saber de qué lado está cada una

| Planta (OT) | Negocio (IT) |
| --- | --- |
| PLC, DCS, SCADA, HMI, MES | ERP, CRM, BI |
| Sensores IIoT y pasarelas (*retrofit*) | Ofimática y colaboración en la nube |
| Robots, *cobots*, AGV/AMR | Comercio electrónico, portales |
| Visión artificial, mantenimiento predictivo | RPA, factura y firma electrónicas |
| Gemelo digital, fabricación aditiva | Analítica e IA, ciberseguridad |

La columna de negocio es, para un desarrollador, **la lista de sistemas con los que tendrá que integrarse** una aplicación nueva.

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [01](../01-que-es-digitalizar.md) Qué es digitalizar | La 4ª revolución es esto: el dato sale de la planta |
| [02](../02-la-empresa-por-dentro.md) La empresa por dentro | "IT" como entorno define, por contraste, qué es OT |
| [04](../04-front-back-cliente-servidor.md) Front/back | El mismo patrón: dos entornos, una frontera que se mueve |
| [06](../06-extremo-a-extremo.md) Seguir un dato | El peso de la báscula, nivel a nivel, hasta la factura |
| [10](../10-seguridad-y-regulacion.md) Seguridad | La tríada CIA cambia de orden; la segmentación es la DMZ |

---

## Para debatir

- La bomba de infusión conectada a la red de un hospital: ¿IT u OT? ¿Y el monitor que envía alarmas al móvil de la enfermera? ¿Qué prioridad de seguridad aplica?
- Un coche con decenas de unidades de control y una pantalla con apps en la misma red interna: ¿dónde va la DMZ? ¿Qué pasó con el Jeep Cherokee en 2015?
- ¿Tiene sentido hablar de OT en una empresa de software? ¿Qué sería lo más parecido? ¿Comparte la cultura de "no toques lo que funciona"?
