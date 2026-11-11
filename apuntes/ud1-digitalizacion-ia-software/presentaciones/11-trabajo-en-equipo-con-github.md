---
marp: true
lang: es
theme: default
paginate: true
size: 16:9
footer: "DAOSP · UD1-11 · Trabajar en equipo con GitHub"
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

# Trabajar en equipo con GitHub

*Issues*, ramas, *pull requests* y revisión

UD1 · apunte 11 · [texto completo](../11-trabajo-en-equipo-con-github.md)

---

<!-- _class: idea -->

Git guarda la historia del código; la plataforma añade la capa con la que **un equipo se coordina**: la *issue* dice qué y por qué, la rama aísla el trabajo, la *pull request* lo propone para discutirlo, revisarlo y probarlo, y la fusión lo incorpora.

Es la digitalización del propio sector y, desde 2025, **la puerta por la que entran los agentes**.

---

## Git y la plataforma: dos capas

| Capa | Qué aporta | Dónde vive |
| --- | --- | --- |
| **Git** | Historia de versiones: *commits*, ramas, fusiones. Funciona sin red | En cada copia del repositorio |
| **Plataforma**: GitHub, GitLab, Bitbucket, Gitea, Forgejo | *Issues*, *pull requests*, revisión, permisos, automatización | En un servidor |

- Git es distribuido — cada copia es completa, como la app móvil de [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md) —, pero **la colaboración no**: clonar un proyecto trae su código y su historia, no sus discusiones.
- Los nombres se mueven: la *pull request* de GitHub (pedir al dueño que "tire" de tu rama) es la *merge request* de GitLab (pedir que se fusione); "repositorio" es la carpeta `.git`, el proyecto en GitHub o todo con sus *issues*.

---

## El flujo: de la *issue* a la fusión

```text
issue #12        qué hay que hacer y por qué
rama             12-buscador-por-nombre, a partir de main
commits          pequeños; el mensaje explica por qué
pull request     el diff, la conversación y "Closes #12"
revisión + CI    comentar, aprobar o pedir cambios ↺ más commits
fusión en main   solo aprobada y en verde; la issue se cierra sola
```

- `Closes`, `Fixes` o `Resolves #12` enlazan la *issue* y la cierran cuando la PR se fusiona en la rama por defecto.
- Al fusionar se elige la historia: un *commit* de fusión que conserva los de la rama, o *squash*, que los junta en uno.
- Si dos ramas cambiaron las mismas líneas hay **conflicto**, y se resuelve a mano → [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md).

---

## Buenas prácticas, pieza a pieza

| Pieza | Buena práctica |
| --- | --- |
| *Issue* | Título concreto; qué se quiere y por qué; **criterios de aceptación** comprobables; etiquetas y persona asignada |
| Rama | Una por *issue*, de vida corta, con un nombre que la identifique |
| *Commit* | Pequeño y con sentido propio; el mensaje explica *por qué*, porque el *diff* ya dice *qué* |
| *Pull request* | Qué cambia, por qué y cómo se ha probado; pequeña, para que se pueda revisar |
| Revisión | Comentarios concretos y verificables; comportamiento y casos límite, no solo estilo |
| CI y fusión | Pruebas, *linter* y compilación en cada *push* (GitHub Actions); `main` protegida |

---

## Rama o *fork*

- **Dentro del equipo**: cada uno crea ramas en el repositorio común.
- **En un proyecto ajeno** en el que no se tiene permiso de escritura — el caso del software libre —: se hace un ***fork***, una copia del repositorio en la cuenta propia; se trabaja en una rama del *fork*, y la *pull request* se abre hacia el repositorio original.
- El flujo de revisión es el mismo.

---

## Por qué el sector trabaja así

| Idea | Dónde se vio | Cómo aparece en el flujo |
| --- | --- | --- |
| El dato se captura una vez y fluye | [01](../01-que-es-digitalizar.md) | Quién hace qué, y en qué estado está, se ve en *issues* y PR sin preguntar a nadie |
| Nunca confíes en lo que cruza la frontera | [04](../04-front-back-cliente-servidor.md) | Nada llega a `main` sin revisión ni pruebas, aunque venga del propio equipo |
| Ley de Conway | [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md) | Quién revisa qué copia la estructura del equipo (`CODEOWNERS`); tres equipos, tres conversaciones |
| Iterar en pasos pequeños | [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md) | Una rama que vive tres meses es una cascada escondida que acaba en un conflicto enorme |
| Trazabilidad | [06](../06-extremo-a-extremo.md) | De una línea en producción se llega a su PR, a su revisión y a la *issue* que la pidió |

---

## Dónde entra el agente

Los agentes asíncronos de [09](../09-ia-para-el-desarrollo-de-software.md) usan **exactamente este flujo**: reciben una *issue*, trabajan en una rama dentro de un entorno aislado y abren una PR que revisa una persona; si se les comenta, vuelven a trabajar sobre ella.

1. **La *issue* es la especificación.** "Arreglar el buscador" produce una PR que arregla *algo*; con criterios de aceptación, una que se puede comprobar: SDD a escala de tarea.
2. **La revisión pasa a ser el trabajo.** El tamaño de una tarea lo marca lo que se puede revisar de verdad, no lo que el agente puede escribir.
3. **Una *issue* es contenido no confiable.** Leerla, acceder al repositorio y poder publicar es la tríada letal de [10](../10-seguridad-y-regulacion.md); proteger `main` es la última barrera.

---

## Lo mínimo para practicar

```bash
gh issue create --title "Buscar pokémon por nombre"  # el cuerpo, con los criterios
git switch -c 12-buscador-por-nombre                  # rama nueva desde main
git add . && git commit -m "Muestra 'No encontrado' cuando la API devuelve 404"
git push -u origin 12-buscador-por-nombre
gh pr create --fill                 # y "Closes #12" en la descripción
gh pr checkout 15                   # traer la PR de otra persona para revisarla
gh pr review 15 --approve           # o --request-changes / --comment
gh pr merge 15 --squash --delete-branch
```

Todo se puede hacer también desde la web o desde VS Code; la terminal enseña exactamente qué ocurre, y es lo que ejecuta un agente.

---

## Cómo se conecta

| Con | La relación |
| --- | --- |
| [09](../09-ia-para-el-desarrollo-de-software.md) IA para el desarrollo | El agente asíncrono vive dentro de este flujo; una *issue* con criterios es SDD |
| [10](../10-seguridad-y-regulacion.md) Seguridad | Una *issue* pública es contenido no confiable; proteger `main` es defensa en profundidad |
| [UD2-01](../../ud2-tecnologias-arquitectura/01-tecnologias-habilitadoras.md) Informe THD | El informe colaborativo se hace con este flujo: rama, PR y revisión de un compañero |
| [Proyecto](../../../proyecto/README.md) de la UD3 | El historial del repositorio forma parte de la nota |

---

## Para debatir

- Un agente entrega en diez minutos una PR de 2000 líneas que pasa todas las pruebas. ¿Se aprueba? ¿Cómo se revisa? Si falla en producción, ¿quién responde: quien la pidió, quien la aprobó o el agente?
- "Arreglar el buscador" frente a la misma *issue* con criterios de aceptación. ¿Qué haría con cada una un compañero recién llegado? ¿Y un agente?
- Si todo el equipo es de confianza, ¿para qué proteger `main`? Argumentar con "nunca confíes en el cliente" de [04](../04-front-back-cliente-servidor.md) y la defensa en profundidad de [10](../10-seguridad-y-regulacion.md).
- Un equipo que se coordina por WhatsApp y se pasa el código en un ZIP: aplicar el test de cinco preguntas de [01](../01-que-es-digitalizar.md). ¿Qué pieza del flujo arregla cada "no"?
