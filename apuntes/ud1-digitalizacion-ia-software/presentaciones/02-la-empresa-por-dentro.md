---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: "DAOSP · UD1-02 · La empresa por dentro"
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

# La empresa por dentro

Departamentos, sistemas y roles

UD1 · apunte 02 · [texto completo](../02-la-empresa-por-dentro.md)

---

<!-- _class: idea -->

Cada departamento acaba teniendo un sistema que refleja **cómo trabaja**.

Hacer que esos sistemas se hablen es imposible sin cambiar cómo se hablan los departamentos: **tecnología y organización se determinan mutuamente**.

---

## Cada departamento, su sistema

| Departamento | Sistema típico |
| --- | --- |
| Finanzas, compras | **ERP** (módulos financiero y de compras) |
| Comercial | **CRM** |
| Producción | **MES**, SCADA (la frontera con OT → [03](../03-it-y-ot.md)) |
| Almacén | **WMS / SGA** |
| Recursos humanos | **HRIS**, nóminas |
| Soporte | *Ticketing* |
| Dirección | **BI**: cuadros de mando sobre todo lo anterior |

No se trata de memorizar siglas, sino de ver el patrón: **cada herramienta refleja una forma de trabajar**, y lo difícil empieza cuando tienen que compartir datos y reglas.

---

## El ERP: el sistema que obliga a ponerse de acuerdo

- Integra finanzas, compras, ventas, inventario y a menudo producción **sobre una base de datos común**.
- Implantarlo obliga a unificar procesos: si contabilidad y almacén usaban códigos de producto distintos, **alguien tiene que ceder**.
- Por eso los proyectos de ERP fracasan más por organización que por técnica (casos en [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md)).

Es el paso del peldaño 3 al 4 de [01](../01-que-es-digitalizar.md), con nombre comercial: SAP, Dynamics, Odoo, Sage.

---

## Qué departamentos son entornos IT

IT y OT clasifican **tecnologías**, no departamentos. Criterio: los sistemas que usa cada uno.

| Entorno | Departamentos | Por qué |
| --- | --- | --- |
| **IT** | Finanzas, RRHH, comercial, marketing, atención al cliente, compras | Todos sus sistemas son de información: ERP, CRM, HRIS, *ticketing* |
| **Mixto** | Producción, mantenimiento; logística y calidad si están automatizadas | Sistemas IT (GMAO, WMS, LIMS) sobre equipos **OT** (PLC, robots, AGV) → [03](../03-it-y-ot.md) |

- **El departamento de IT no coincide con los entornos IT**: en la industria, la OT suele depender de ingeniería o mantenimiento.
- En una empresa de software, casi todo es entorno IT, también el departamento que "produce".

---

## Los roles de un equipo de desarrollo

| Para qué | Roles |
| --- | --- |
| Decidir qué se construye | *Product owner* / *product manager*, UX/UI |
| Construirlo | Frontend, backend, móvil, *full-stack* |
| Que funcione y siga funcionando | QA, DevOps / SRE / plataforma |
| Los datos | Ingeniero de datos, científico o analista, ML / AI engineer |
| Las decisiones técnicas | Arquitecto, *tech lead* |

Los nombres se mueven: "DevOps" nació como cultura y acabó siendo un puesto; "*full-stack*" va de "hace de todo en una *startup*" a "frontend que sabe montar una API".

---

## La IA difumina las fronteras entre roles

- Con un agente de código, un desarrollador de frontend puede montar una API razonable, y al revés.
- En equipos pequeños crece el "*product engineer*", que cubre de la idea al despliegue; la especialización profunda queda en equipos grandes.
- Lo que **no** se difumina: hay que *entender* ambos lados para revisar lo que el agente produce → [09](../09-ia-para-el-desarrollo-de-software.md).

---

## La tecnología cambia la organización

- **El ERP unifica procesos**: alguien cede su código de producto.
- **Aparecen roles**: CIO, CTO, CDO (dos puestos distintos con la misma sigla), DPO (obligatorio por RGPD en ciertos casos → [10](../10-seguridad-y-regulacion.md)).
- **Cambian las tareas**: desaparece teclear facturas, aparece revisar excepciones.
- **Cambia el canal**: de la llamada al ticket, de la reunión al panel.

---

## La organización condiciona la tecnología

- **Silos que no se hablan → sistemas que no se hablan.** La integración técnica no arregla que nadie haya acordado qué es un "pedido".
- ***Shadow IT***: si IT es lenta, cada departamento se compra su SaaS con la tarjeta de empresa, y aparecen datos de clientes en herramientas que nadie controla.
- **IT centralizada** (coherente, lenta) frente a **descentralizada** (ágil, fragmentada): una decisión de organización que fija qué arquitectura es posible.
- **El modelo de negocio dicta el modelo de datos**: facturar por proyecto o por suscripción organiza el software en torno al proyecto o al cliente.

---

## Ejemplo integrador: la cadena de clínicas dentales

- Compran un software de gestión. La recepcionista sigue con la agenda en papel; los dentistas dictan y una auxiliar transcribe al final del día; los informes mensuales se hacen a mano en Excel.
- **Diagnóstico:** la tecnología se implantó sin cambiar la organización. Nadie decidió que la agenda de papel desaparece, ni formó a nadie, ni definió que el informe se genera solo.
- Lo que falta no es mejor software: es **una decisión organizativa y formación**.

> El software está, pero el proceso no cambió: es el fallo más común que aparecerá en el proyecto.

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [01](../01-que-es-digitalizar.md) Qué es digitalizar | El salto del peldaño 3 al 4 es un acuerdo entre departamentos |
| [03](../03-it-y-ot.md) IT y OT | La segunda lectura de "IT" define, por contraste, qué es OT |
| [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md) Ley de Conway | El organigrama de quien construye determina el sistema que sale |
| [09](../09-ia-para-el-desarrollo-de-software.md) IA para el desarrollo | Los roles se difuminan; la capacidad de revisar, no |
| [10](../10-seguridad-y-regulacion.md) Seguridad | *Shadow IT* y DPO: la organización también decide la seguridad |

Para el proyecto: **el organigrama de la empresa cliente es parte del análisis técnico**, no un dato administrativo.

---

## Para debatir

- Si "cliente" significa cosas distintas en cinco departamentos, ¿la base de datos tiene una tabla `Cliente` o cinco? ¿Quién lo decide?
- ¿Debe IT elegir las herramientas de toda la empresa (coherencia) o cada departamento las suyas (rapidez)? Buscar un caso en el que cada opción haya fallado.
- En una empresa de 15 personas, ¿qué roles de la tabla existen de verdad y cuáles hace la misma persona? ¿Qué se pierde?
