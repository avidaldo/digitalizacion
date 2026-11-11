---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: "DAOSP · UD1-06 · Seguir un dato de punta a punta"
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

# Seguir un dato de punta a punta

La conexión IT/OT y su espejo en software

UD1 · apunte 06 · [texto completo](../06-extremo-a-extremo.md)

---

<!-- _class: idea -->

Para saber si una digitalización funciona, **se elige un dato y se sigue** desde que nace hasta la factura o el cuadro de mando.

En cada salto cambia de protocolo, de formato, de dueño, de ritmo y, a veces, de significado. Donde se copia a mano, se pierde o cambia de sentido sin que nadie lo sepa, **la conexión no existe**.

---

## El peso de una partida, nivel a nivel

```text
0    Báscula   señal eléctrica de la célula de carga (4-20 mA)
1    PLC       1 247,3 kg, cada 100 ms, por Modbus
2    SCADA     "pesada confirmada a las 06:42", con lote y operario
3    MES       entrada de materia prima: proveedor, peso neto, calidad
3.5  DMZ       fichero o API hacia el ERP
4    ERP       albarán: kg facturables, precio pactado, IVA
     ├─▶ factura del proveedor conciliada, asiento contable
     └─▶ BI: rendimiento por proveedor, merma por lote
```

Las paradas son los niveles del modelo de Purdue de [03](../03-it-y-ot.md).

---

## Qué cambia en cada salto, y dónde se rompe

| Salto | Cambia | Dónde se rompe |
| --- | --- | --- |
| Sensor → PLC | Naturaleza: señal → número | La báscula deriva y el error entra en todo lo de abajo |
| PLC → SCADA | Ritmo: ms → eventos | Qué lectura es "el peso": una regla de negocio escondida en OT |
| SCADA → MES | Contexto: lote, operario | El operario tiene que elegir bien el lote en una lista |
| MES → ERP | Semántica: neto → facturable | Bruto, neto y facturable: tres números llamados "peso" |
| ERP → factura | Dueño: operaciones → finanzas | El proveedor factura su peso, no el nuestro |
| ERP → BI | Agregación: registro → indicador | Días sin sincronizar: el indicador miente |

---

## Dónde está rota en una PYME real

- **El portapapeles.** El operario apunta el peso en una hoja y alguien lo teclea en el ERP por la tarde. La frontera IT/OT es una persona: errores de transcripción, horas de retraso, nadie sabe el stock real a mediodía.
- **El CSV nocturno por FTP.** Mejor, pero si un peso se corrige después de facturar, ¿se sobrescribe o se duplica? Es la **corrección tardía** de [UD2-06](../../ud2-tecnologias-arquitectura/06-dato-informacion-ciclo-de-vida.md).
- **Unidades que nadie ha acordado.** Lonja en kg, planta en latas, comercial en cajas y palés, y el factor de conversión no es constante.
- **Cada sistema tiene su "hoy".** El turno de noche produce a las 02:00 y contabiliza en el día anterior.

---

## Lo que se gana y lo que se arriesga

- **Se gana**: planificar con lo que hay en planta *ahora*; mantenimiento predictivo; trazabilidad automática (exigida en alimentación, farmacia, automoción); costes reales por lote, máquina y turno; y **cerrar el bucle**: la orden de fabricación llega a la máquina sin que nadie la reescriba.
- **Se arriesga el aislamiento.** Cada conexión es una puerta; la seguridad industrial (zonas y conductos de **IEC 62443**, DMZ, listas blancas de protocolos) existe para abrir puertas sin abrir la planta.
- **El gemelo digital** es la versión ambiciosa: un modelo de la planta, alimentado por OT, sobre el que IT simula antes de tocar la realidad. Solo vale si el flujo de abajo arriba es completo y fiable.

---

## El espejo: «confirmar pedido» en una tienda online

```text
clic → JavaScript → fetch POST /api/pedidos con JSON
  → DNS → TLS en la CDN o el balanceador → proxy: elige instancia
  → middleware: token, límites, registro
  → controlador: valida el JSON → servicio: stock, precio, fraude
  → ORM: SQL dentro de una transacción → base de datos
  → 201 + JSON → la interfaz se actualiza
  └─▶ cola: "pedido creado" → correo, almacén, analítica
```

La forma de la petición — método, cabeceras, JSON, código de estado — es la de PokeAPI en [04](../04-front-back-cliente-servidor.md).

---

## La correspondencia es exacta

| Cadena OT → IT | Cadena HTTP | Lo que cambia |
| --- | --- | --- |
| Señal → número | Clic → JSON | Naturaleza |
| Modbus → OPC UA → API | HTTP → SQL → mensaje en cola | Protocolo |
| Peso → entrada de materia prima → albarán | JSON → objeto → fila → evento | Formato y semántica |
| Planta → operaciones → finanzas | Cliente → API → base de datos → otros servicios | Dueño |
| Milisegundos → eventos → días | Navegador → transacción → correo minutos después | Ritmo |
| DMZ | "Nunca confíes en el cliente" | Seguridad |

---

## Y se rompe por los mismos sitios

| En la planta | En la tienda |
| --- | --- |
| El portapapeles: un dato cruza la frontera sin verificar | El JavaScript calcula el total y el servidor lo acepta sin recalcularlo |
| El CSV nocturno | Un *cron* sincroniza con el almacén cada hora: el pedido cancelado en ese intervalo se prepara igual |
| Tres "pesos" con el mismo nombre | "Confirmado" en la tienda, "pagado" en la pasarela, "en preparación" en el almacén: tres "pedidos" que no coinciden |

---

## Observabilidad: la trazabilidad del software

En OT, seguir el dato se llama **trazabilidad** y lo exige la regulación. En software se llama **observabilidad** y lo exige operar un sistema distribuido.

| Pilar | Responde |
| --- | --- |
| Logs | Qué pasó, en texto, en cada componente |
| Métricas | Cuánto y con qué frecuencia: peticiones por segundo, latencia, errores |
| Trazas | Por dónde pasó **una** petición, unida por un *trace ID* que se propaga |

Estándar abierto: **OpenTelemetry** (Jaeger, Grafana Tempo, Datadog). Sin trazas, el microservicio lento se busca a ciegas entre veinte: es la pregunta de calidad cuando una partida sale mal, *¿en qué paso se estropeó?*

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [01](../01-que-es-digitalizar.md) Qué es digitalizar | El test de cinco preguntas, aplicado salto a salto |
| [03](../03-it-y-ot.md) IT y OT | Los niveles de Purdue son las paradas del recorrido |
| [04](../04-front-back-cliente-servidor.md) Front/back | Una petición HTTP hace el mismo viaje; la DMZ es "nunca confíes en el cliente" |
| [08](../08-ia-datos-sectores-lenguajes.md) IA y datos | La IA es el último eslabón: sin los anteriores, no sale del piloto |
| [11](../11-trabajo-en-equipo-con-github.md) GitHub | De una línea en producción a su PR y su *issue* |
| [UD2-06](../../ud2-tecnologias-arquitectura/06-dato-informacion-ciclo-de-vida.md) Ciclo de vida del dato | Corrección tardía: ¿actualizar el histórico o añadir un evento? |

Para el proyecto: este diagrama para **un dato de la empresa elegida**, marcando dónde se copia a mano hoy.

---

## Para debatir

- Elegir un dato del instituto — una nota, una falta de asistencia, una compra — y dibujar su recorrido. ¿Cuántas veces se teclea? ¿Cuántos sistemas lo tocan? ¿Cambia de nombre por el camino?
- La báscula corrige un peso después de facturar. ¿Modificar el registro o añadir un evento de corrección? ¿Qué prefiere finanzas? ¿Y calidad? ¿Y quien tiene que reproducir un error?
- En una API, ¿dónde va el *trace ID*? ¿Sobrevive al paso por una cola de mensajes? ¿Y a una llamada a un proveedor externo de LLM?
