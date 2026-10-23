# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Qué es

Página web personal en **un único archivo**: `index.html` (HTML + CSS + JS inline). No hay build, dependencias, tests ni linter. La única dependencia externa es Poppins desde Google Fonts. Junto a él está `vista-previa.png` (1200 × 630 px), la imagen que sale al compartir el enlace. Para verla en local, abrir `index.html` directamente en Chrome/Edge.

## Publicación

- Publicada con **GitHub Pages** en https://infoericms-code.github.io/ desde la rama `main` del repositorio público `infoericms-code/infoericms-code.github.io` (remoto `origin`).
- El hook `Stop` guarda los cambios en local, pero **no publica**. Publicar = `git push`, y solo cuando Eric lo pida. Tras el push, GitHub tarda uno o dos minutos en actualizar la web.
- La rama local `historial-local` guarda el historial antiguo (con textos de pruebas): **no subirla nunca**.
- Todo lo que hay en el repositorio es público: no añadir nada secreto.

## Estructura de `index.html`

- **`<head>`**: título y `meta description` para Google, y etiquetas Open Graph para la vista previa al compartir. `og:url`, `og:image` y `canonical` apuntan a la dirección publicada. Si se cambia la descripción, cambiar también `og:description`.
- **Cabecera**: avatar cuadrado (iniciales, sustituible por `<img>`), nombre, profesión y botón a LinkedIn (azul de LinkedIn con texto blanco, por contraste).
- **Sobre mí**: párrafos y chips de habilidades/intereses.
- **Qué puedo hacer por ti**: servicios que ofrece Eric (icono SVG, título y descripción en bloques con borde). Solo servicios reales.
- **Mis trabajos**: tarjetas fijas en HTML con los trabajos hechos (etiqueta tipo · año, título, descripción, tecnologías y botón «Ver web» opcional), el más reciente arriba. La web sirve para conseguir clientes: todo lo que aparece tiene que ser real.
- **Hablemos**: frase de invitación y dos botones de contacto con los datos reales de Eric: correo (`mailto:`) y WhatsApp (`wa.me` con un mensaje ya escrito). Debajo, un formulario de contacto que envía los mensajes a través de Web3Forms (servicio externo).
- JavaScript: pone el año actual en el pie y envía el formulario con `fetch`.

## Reglas

Las reglas detalladas están en `.claude/rules/`:
- `estilo-visual.md` — sistema visual brutalista oscuro (variables, sombras, interacción, layout).
- `contenido.md` — archivo único, idioma, marcadores `EDITA AQUÍ`, datos y enlaces del usuario.
- `formulario.md` — formulario de contacto con Web3Forms: clave, campos, seguridad y pruebas sin envíos reales.
- `verificacion.md` — cómo probar cambios en el navegador integrado.

## Skills

Las skills del proyecto están en `.claude/skills/`:
- `text-reviewer` — revisa los textos de `index.html` (ortografía, tono cercano, sin anglicismos) y propone correcciones; solo edita si el usuario las acepta.

## Agentes

Los agentes del proyecto están en `.claude/agents/`:
- `accesibilidad` — audita `index.html` (WCAG 2.2 AA) y lista mejoras de accesibilidad por prioridad. Usa el modelo Opus y solo tiene herramientas de lectura (`Read`, `Glob`, `Grep`): no edita nada.

## Hooks

Los hooks del proyecto están en `.claude/settings.json`:
- `Stop` — al terminar cada respuesta de Claude, si hay cambios sin guardar, hace `git add -A` y un commit automático («Cambios automáticos del …»). No hace nada si no hay cambios. Para desactivarlo, borrar el bloque `hooks` de ese archivo.

## MCP

Los servidores MCP del proyecto están en `.mcp.json`:
- `playwright` — controla un navegador para probar la web. Necesita Node (`npx`), instalado en este equipo (v24 LTS).

## Comandos

Los comandos personalizados están en `.claude/commands/`:
- `/trabajo <texto>` — convierte un trabajo terminado en una tarjeta nueva (arriba del todo) de la sección «Mis trabajos» de `index.html`; pregunta lo que falte y no inventa clientes, fechas ni enlaces.
