---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: "DAOSP · UD1-05 · Ciclos de vida, Conway y el caso móvil"
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

# Ciclos de vida, ley de Conway y el caso móvil

Digitalizar de extremo a extremo es organización y método, no solo tecnología

UD1 · apunte 05 · [texto completo](../05-ciclos-de-vida-conway-y-el-caso-movil.md)

---

<!-- _class: idea -->

Que el dato fluya sin cortes de punta a punta tiene ventajas enormes. Conseguirlo exige **elegir cómo se construye** — de golpe o por iteraciones — y aceptar que el sistema **reproducirá la estructura de quien lo construya**.

Y cuando un extremo es un móvil que no siempre está conectado, cliente/servidor deja de encajar.

---

## Ventajas y riesgos de ir de extremo a extremo

| Ventajas | Riesgos |
| --- | --- |
| **Dato único**: el mismo peso en producción, almacén y factura | **Fracasos a lo grande**: Lidl abandonó SAP en 2018 tras 7 años y unos 500 M€ |
| **Sin reintroducción**: nadie teclea lo que ya está en el sistema | **Acoplamiento**: un fallo se propaga (Colonial Pipeline → [03](../03-it-y-ot.md)) |
| **Trazabilidad**: de la lata a la captura | **Dependencia** del proveedor que lo integra todo |
| **Base para la IA** → [08](../08-ia-datos-sectores-lenguajes.md) | **Rigidez**: las excepciones hay que programarlas |

El patrón de los fracasos: **implantar de golpe** (*big bang*). La pregunta del apunte: ¿cómo se construye sin *big bang*?

---

## Ciclos de vida

| Ciclo | Cómo funciona | Nota |
| --- | --- | --- |
| **Cascada** | Requisitos → diseño → construcción → pruebas → entrega, en secuencia | Royce (1970) la presentó como *arriesgada* y proponía iterar; la industria copió el diagrama |
| **Modelo en V** | Cada fase de construcción tiene enfrente su prueba | Automoción, aeronáutica, sanidad |
| **Iterativo, espiral** | Versión pequeña que funciona → aprender → ampliar | Boehm (1986) añade riesgos en cada vuelta |
| **Ágil** (2001) | Entregas frecuentes; requisitos que cambian | Scrum (*sprints*), Kanban (flujo continuo) |
| **DevOps, entrega continua** | La iteración llega hasta producción | Cada cambio puede desplegarse el mismo día |

---

## No todo es ágil

| Favorece cascada o V | Favorece iterativo o ágil |
| --- | --- |
| Requisitos estables y verificables (una norma, un contrato) | Requisitos que se descubren usando el producto |
| Error caro e irreversible (un marcapasos) | Error barato y reversible (una web) |
| Regulación que exige documentar antes de operar | Sin regulación de proceso |
| Contrato a precio cerrado | Equipo interno, tiempo y materiales |

**La misma empresa, dos ciclos**: la trazabilidad sanitaria de una conservera, en V; su tienda online, iterativa. La realidad tiene nombre irónico: *water-scrum-fall*.

---

## Ágil e IA: el cuello de botella se mueve

- Un agente de código genera en una tarde lo que antes llevaba un *sprint*.
- El cuello de botella pasa a ser **saber exactamente qué se quiere**.
- De ahí el ***spec-driven development***: una especificación previa, de aspecto "cascada", dentro de un bucle de iteración de minutos → [09](../09-ia-para-el-desarrollo-de-software.md).

> No es una vuelta a la cascada: construir se ha abaratado tanto que vuelve a compensar **pensar antes**.

---

## La ley de Conway

> Las organizaciones que diseñan sistemas están condenadas a producir diseños que copian sus estructuras de comunicación. — Melvin Conway, 1968

**Si cuatro equipos construyen un compilador, sale un compilador de cuatro pasadas.**

Una interfaz entre módulos solo puede ser tan buena como la conversación entre las personas que los hacen.

---

## Consecuencias de Conway

| Organización | Sistema que sale |
| --- | --- |
| Departamentos que no se hablan → [02](../02-la-empresa-por-dentro.md) | Sistemas que no se integran: el "dato único" exige acordar qué es un pedido |
| "Los de front" y "los de back" → [04](../04-front-back-cliente-servidor.md) | Una API con la fricción de ambos equipos en medio |
| Equipos pequeños y autónomos | Microservicios: Conway aplicado a propósito |
| Equipos organizados para la arquitectura que se quiere | La **maniobra inversa de Conway** (*Team Topologies*, 2019) |

Para el proyecto: **el organigrama de la empresa es un dato de arquitectura**.

---

## El caso móvil: qué rompe el modelo clásico

1. **Conectividad intermitente**: tiene que funcionar con datos locales (SQLite, Room, Core Data).
2. **Sincronización y conflictos**: dos dispositivos cambian lo mismo sin red; "gana el último", registro de operaciones, CRDT.
3. **El servidor inicia la conversación**: las notificaciones *push* pasan por un tercero (FCM, APNs).
4. **No se despliega cuando se quiere**: conviven versiones durante meses → API compatible hacia atrás y versionada.
5. **Recursos limitados** y **cómputo local** cada vez más capaz (modelos en el dispositivo).

---

## A qué se parece una app móvil bien hecha

```text
DISPOSITIVO                              SERVIDOR
interfaz → lógica local → BD local
               │
       motor de sincronización ◀──▶ API → BD central
               ▲                     │
               └──── aviso push ◀────┘ (vía FCM / APNs)
```

- Tiene **su propia capa de datos y su propia lógica**; el servidor es un punto de encuentro, no la única fuente de verdad.
- "Se conecta a la API" **no es una arquitectura**: hay que decir qué vive en el dispositivo, cómo se sincroniza y qué pasa en conflicto.

---

## La analogía que ya conocéis: Git

| Git | App móvil bien hecha |
| --- | --- |
| Cada copia es completa y funciona sin red (*commit* local) | Datos y lógica en el dispositivo |
| Sincronización explícita (*push*, *pull*) | Motor de sincronización cuando hay red |
| Los conflictos se resuelven al fusionar (*merge*) | Estrategia de conflictos decidida por el dominio |
| GitHub es un punto de encuentro, no el dueño | El servidor replica y coordina |

Lo que Git no resuelve — quién hace qué, quién revisa — lo añade la plataforma: *issues* y *pull requests* → [11](../11-trabajo-en-equipo-con-github.md).

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [01](../01-que-es-digitalizar.md) Qué es digitalizar | Subir de peldaño sin *big bang*: iterar |
| [02](../02-la-empresa-por-dentro.md) La empresa por dentro | Conway: el organigrama se copia en el sistema |
| [04](../04-front-back-cliente-servidor.md) Front/back | El móvil tiene frontend *y* una capa de backend local |
| [09](../09-ia-para-el-desarrollo-de-software.md) IA para el desarrollo | SDD recupera la especificación previa dentro de la iteración |
| [11](../11-trabajo-en-equipo-con-github.md) GitHub | Git es el modelo del móvil; la plataforma añade la coordinación |

---

## Para debatir

- El repartidor marca "entregado" sin cobertura y, antes de que sincronice, el cliente cancela desde la web. ¿Qué gana? ¿Quién decide? ¿Es un problema técnico o de negocio?
- Un agente genera en una tarde lo que llevaba un *sprint*. ¿Sigue teniendo sentido un *sprint* de dos semanas? ¿Qué parte del ciclo de vida pasa a ser el cuello de botella?
- Un hospital digitaliza la historia clínica de punta a punta: ¿cascada o ágil, y para qué parte? ¿Qué hace la ley de Conway entre servicios médicos que no se hablan?
