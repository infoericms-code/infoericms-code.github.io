---
description: Convierte un trabajo terminado en una tarjeta nueva (tipo y año, título, descripción, tecnologías y enlace opcional) en la sección "Mis trabajos" de index.html
argument-hint: <qué has hecho, escrito como te salga>
---

Convierte el trabajo que cuenta el usuario en una tarjeta nueva de la sección **Mis trabajos** de `index.html`. Esta sección la ven posibles clientes: todo lo que ponga tiene que ser verdad.

Trabajo recibido: $ARGUMENTS

## Paso 1 · Entender el trabajo

- Si está vacío, pregunta en una sola frase: «¿Qué trabajo quieres añadir?» y espera la respuesta. No inventes ninguno.
- Necesitas saber: **qué es** (tipo: web de negocio, tienda, landing…), **para quién** (o si es propio), **año**, **tecnologías** y si tiene **enlace** público. Si falta algo de esto, pregúntalo todo junto en **un** mensaje corto. Si el usuario no lo sabe o no quiere ponerlo, se deja fuera.
- No inventes clientes, nombres de negocios, resultados, cifras, fechas ni enlaces. Usa el enlace exactamente como lo dé.

## Paso 2 · Proponer la tarjeta

Redacta en español, con tono cercano y sin jerga ni anglicismos:

- **Etiqueta**: `Tipo · Año` (por ejemplo «Web de restaurante · 2027»).
- **Título**: 2–6 palabras, empieza en mayúscula, sin punto final.
- **Descripción**: 1–2 frases, máximo ~160 caracteres: qué se hizo y para qué sirve. Sin relleno ni promesas.
- **Tecnologías**: 2–4 etiquetas cortas (HTML, CSS, JavaScript…).
- **Enlace**: solo si el usuario lo ha dado.

Muestra la propuesta así y pregunta si la añades o quiere cambiar algo:

```
{Tipo · Año}
{Título}
{Descripción}
Tecnologías: {A}, {B}, {C}
Enlace: {url o «sin enlace»}
```

Espera la respuesta. Si pide cambios, ajusta y vuelve a mostrarla. No edites ningún archivo antes de que confirme.

## Paso 3 · Añadirla a `index.html`

Respeta `.claude/rules/estilo-visual.md` y `.claude/rules/contenido.md`. Lee `index.html` antes de editar. El CSS de las tarjetas (`.work-card`, `.work-link`…) ya existe: no añadas estilos nuevos.

**Escapa el texto** al pasarlo a HTML (`&` → `&amp;`, `<` → `&lt;`, `>` → `&gt;`).

Añade el `<li>` nuevo **al principio** de `<ul class="works">` (el trabajo más reciente va arriba). No toques las demás tarjetas. Estructura:

```html
<li class="work-card">
  <p class="work-meta">Tipo · Año</p>
  <h3>Título del trabajo</h3>
  <p class="work-desc">Descripción del trabajo.</p>
  <ul class="work-tags" aria-label="Tecnologías">
    <li>HTML</li>
    <li>CSS</li>
  </ul>
  <a class="work-link" href="URL-EXACTA" target="_blank" rel="noopener noreferrer">Ver web<span class="visually-hidden"> (se abre en una pestaña nueva)</span></a>
</li>
```

- **Sin enlace**: en lugar del `<a>`, deja este marcador: `<!-- EDITA AQUÍ: añade el botón «Ver web» cuando tengas el enlace -->`.
- Si el usuario da el enlace de un trabajo que ya está en la lista (por ejemplo «Mi web personal»), sustituye su marcador por el `<a>` en esa misma tarjeta, en vez de crear otra.

## Paso 4 · Comprobar

Sigue `.claude/rules/verificacion.md`: captura de la tarjeta nueva en escritorio y en móvil (375px), comprueba que `document.documentElement.scrollWidth === document.documentElement.clientWidth` y vuelve el panel a `desktop`. Si hay enlace, comprueba que el `href` es exactamente el que dio el usuario. Si el texto se corta o desborda, arréglalo.

## Paso 5 · Responder

Dile al usuario, en español y en pocas líneas, qué tarjeta se añadió y que puede cambiar el texto a mano en `index.html` dentro de `<ul class="works">`. Dile qué has comprobado y qué no.
