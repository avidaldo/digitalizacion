# Presentaciones de la UD1

Una presentación por apunte, para las sesiones de clase. Cada una recoge los conceptos centrales del apunte y, sobre todo, **cómo se relacionan** entre sí y con los demás apuntes; no sustituye al apunte, que es donde están los matices, los ejemplos y los casos límite. Todas siguen el mismo orden: la idea en una frase, una diapositiva por concepto, una tabla «Cómo se conecta» y las preguntas de «Para debatir».

| Presentación | Apunte |
| --- | --- |
| [01 Qué es digitalizar](01-que-es-digitalizar.md) | [01](../01-que-es-digitalizar.md) |
| [02 La empresa por dentro](02-la-empresa-por-dentro.md) | [02](../02-la-empresa-por-dentro.md) |
| [03 IT y OT](03-it-y-ot.md) | [03](../03-it-y-ot.md) |
| [04 Frontend/backend y cliente/servidor](04-front-back-cliente-servidor.md) | [04](../04-front-back-cliente-servidor.md) |
| [05 Ciclos de vida, Conway y el caso móvil](05-ciclos-de-vida-conway-y-el-caso-movil.md) | [05](../05-ciclos-de-vida-conway-y-el-caso-movil.md) |
| [06 Seguir un dato de punta a punta](06-extremo-a-extremo.md) | [06](../06-extremo-a-extremo.md) |
| [07 Qué es "la IA"](07-que-es-la-ia.md) | [07](../07-que-es-la-ia.md) |
| [08 IA, datos, sectores y lenguajes](08-ia-datos-sectores-lenguajes.md) | [08](../08-ia-datos-sectores-lenguajes.md) |
| [09 IA para el desarrollo de software](09-ia-para-el-desarrollo-de-software.md) | [09](../09-ia-para-el-desarrollo-de-software.md) |
| [10 Seguridad y regulación](10-seguridad-y-regulacion.md) | [10](../10-seguridad-y-regulacion.md) |
| [11 Trabajar en equipo con GitHub](11-trabajo-en-equipo-con-github.md) | [11](../11-trabajo-en-equipo-con-github.md) |

## Cómo verlas

Están escritas en Markdown con [Marp](https://marp.app/): cada `---` separa una diapositiva. En GitHub se leen como texto; para verlas como diapositivas:

- **En VS Code**, con la extensión *Marp for VS Code* (`marp-team.marp-vscode`): abrir el fichero y la vista previa.
- **Exportarlas** a PDF, PPTX o HTML con la línea de comandos (necesita Node.js y, para PDF y PPTX, Chrome o Chromium instalado):

```bash
npx @marp-team/marp-cli@4.1.2 01-que-es-digitalizar.md --pdf --allow-local-files
npx @marp-team/marp-cli@4.1.2 01-que-es-digitalizar.md --pptx --allow-local-files
```

Los ficheros exportados no se suben al repositorio: se generan cuando hacen falta a partir del Markdown, que es la fuente.
