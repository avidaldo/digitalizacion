---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: "DAOSP · UD1-01 · Qué es digitalizar"
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

# Qué es digitalizar

El dato se captura **una vez** y **fluye**

UD1 · apunte 01 · [texto completo](../01-que-es-digitalizar.md)

---

<!-- _class: idea -->

Digitalizar un proceso es **rediseñarlo** para que el dato se capture una sola vez, donde nace, y llegue sin teclearlo de nuevo a cada sitio donde se necesita.

Tener ordenadores no basta. Escanear papel tampoco.

---

## Tres palabras que en español son una

| Término | Qué es | ¿Cambia el proceso? |
| --- | --- | --- |
| *Digitization* (digitización) | Pasar de analógico a digital: escanear una factura | No: cambia el soporte |
| *Digitalization* (digitalización) | Rediseñar el proceso con tecnología: la factura llega por API al ERP | Sí: cambia el flujo |
| *Digital transformation* | Cambiar el negocio: vender horas de máquina en vez de máquinas | Sí: cambia qué se vende |

"Hemos digitalizado el archivo": ¿cuál de las tres?

---

## El caso: una gestoría "con ordenadores"

```text
ANTES    PDF por correo → se lee y se teclea → Excel
         → otra persona lo copia → contabilidad
         el estado vive en la cabeza de alguien

DESPUÉS  portal o API → OCR valida el NIF
         → asiento pendiente de revisión
         → panel con el estado de cada cliente
```

- Antes: el mismo importe se teclea **tres veces**; cada tecleo es un error posible.
- Después: la persona que tecleaba **revisa excepciones**.
- Todos los datos eran digitales antes. Nada estaba digitalizado.

---

## Test rápido: ¿está digitalizado?

1. ¿Algún dato se introduce a mano más de una vez?
2. ¿Hay un papel, un PDF o un correo que alguien tiene que *leer* para que el proceso avance?
3. ¿Se sabe el estado del proceso sin preguntar a una persona?
4. ¿Sigue el proceso si quien lo lleva está de baja?
5. ¿Se pueden analizar los datos en conjunto sin copiarlos a otro sitio?

Dos "sí" en 1–2, o dos "no" en 3–5: no está digitalizado, tenga los ordenadores que tenga.

---

## La escalera de madurez

```text
1  Papel y procesos manuales
2  Ofimática aislada (Excel, correo)
3  Sistemas por departamento: islas
4  Integración: ERP, API, dato único   ← el salto difícil
5  Dato como activo: analítica, IA
6  Modelo de negocio digital
```

- La mayoría de las PYMES está entre el **2 y el 3**.
- El salto difícil es del **3 al 4**: exige acordar qué es un cliente, un pedido, un producto, y quién manda sobre cada dato. Es organización antes que tecnología.
- La IA vive en el **5 y el 6**, y no se llega sin pasar por el 4.

---

## La relación que más se repite en el módulo

> "Vamos a poner IA" en una empresa en el peldaño 2 es, en la práctica, **un proyecto de integración de datos disfrazado**.

- Un modelo de demanda necesita el histórico de ventas limpio, único y accesible → [08](../08-ia-datos-sectores-lenguajes.md).
- Ese histórico existe solo si los departamentos se han puesto de acuerdo → [02](../02-la-empresa-por-dentro.md).

---

## Industria 4.0: qué cambia de verdad

| Revolución | Tecnología | Qué cambió |
| --- | --- | --- |
| 3ª (años 70) | Electrónica, PLC, informática | La máquina se automatiza, pero **aislada** |
| 4ª (2011–) | IoT, nube, datos, IA | La máquina produce **datos que salen de la planta** |

- "Industria 4.0" es una estrategia industrial (Alemania, 2011), no un estándar técnico; "5.0" es sobre todo un reposicionamiento político.
- El dato que sale de la planta es la frontera IT/OT de [03](../03-it-y-ot.md).

---

## El sector del software también sube la escalera

| Antes | Ahora | Qué se digitaliza |
| --- | --- | --- |
| Copiar por FTP a mano | Git | El dato del sector: el código y su historia |
| Coordinarse en persona | *Issues* y *pull requests* | Quién hace qué y en qué estado está → [11](../11-trabajo-en-equipo-con-github.md) |
| Pruebas con un Word | Integración continua | Las pruebas |
| "Desplegar el viernes" | Despliegue continuo, infraestructura como código | La entrega y el servidor |
| — | IA generativa | El peldaño 5 aplicado al propio sector → [09](../09-ia-para-el-desarrollo-de-software.md) |

---

## Casos límite: digitalizar no es un valor en sí mismo

- **Un proceso malo, digitalizado, falla más rápido.** Cuatro firmas en papel → cuatro aprobaciones electrónicas. Primero se simplifica, luego se digitaliza.
- **A veces el papel gana:** la lista quirúrgica, la comanda en hora punta, el operario con guantes a −20 °C.
- **Digital no es *online*:** una depuradora digitalizada y sin Internet, por seguridad.
- **Dependencia:** un ERP o una nube únicos dan eficiencia y quitan autonomía.
- **Sin dato no hay digitalización completa:** el kiosco que imprime el pedido y no lo guarda.

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [02](../02-la-empresa-por-dentro.md) La empresa por dentro | El salto del 3 al 4 es un acuerdo entre departamentos antes que un proyecto técnico |
| [03](../03-it-y-ot.md) IT y OT | En la 4ª revolución el dato sale de la planta y cruza la frontera |
| [06](../06-extremo-a-extremo.md) Seguir un dato | El método para encontrar dónde se teclea dos veces y dónde se rompe |
| [08](../08-ia-datos-sectores-lenguajes.md) IA y datos | La IA necesita datos integrados: peldaños 5 y 6 |
| [11](../11-trabajo-en-equipo-con-github.md) GitHub | El propio equipo de desarrollo también se digitaliza |

La pregunta de fondo en todo el módulo: **¿dónde se captura el dato y por dónde fluye?**

---

## Para debatir

- Un kiosco de autopedido que imprime en cocina y no guarda nada: ¿es digitalización? ¿Qué faltaría para llegar al peldaño 5?
- El gasto que exige cuatro firmas porque nadie se fía de nadie. ¿Se digitaliza tal cual? ¿Qué cambia si ahora se puede medir cuánto tarda?
- Aplicar el test de cinco preguntas a un proceso real del instituto: una falta de asistencia, una nota, una compra.
