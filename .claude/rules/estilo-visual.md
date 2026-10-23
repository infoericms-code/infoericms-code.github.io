# Estilo visual (brutalista oscuro)

El diseño copia el estilo de una referencia que dio el usuario. Todo elemento nuevo debe encajar en él.

- **Colores solo con variables** de `:root` (`--bg`, `--text`, `--text-muted`, `--ink`, `--blue`, `--orange`, `--red`, `--green`, `--gray`, `--linkedin`, `--whatsapp`, `--shadow`, `--shadow-hover`). Si hace falta un color nuevo, añadir una variable; no escribir hex sueltos en las reglas.
- **Solo tema oscuro.** No añadir modo claro ni `prefers-color-scheme` salvo que se pida.
- **Esquinas rectas**: nada de `border-radius` en bloques, botones ni campos.
- **Bloques de color plano** con texto oscuro (`color: var(--ink)`) y **sombra blanca desplazada** (`box-shadow: var(--shadow)`), sin difuminado ni degradados.
- **Interacción estándar** para todo lo clicable con sombra:
  - hover: `transform: translate(-2px, -2px)` + `box-shadow: var(--shadow-hover)`
  - active: `transform: translate(2px, 2px)` + `box-shadow: 2px 2px 0 var(--text)`
  - foco: `outline: 2px solid var(--blue); outline-offset: 3px` en `:focus-visible`
- **Tipografía**: Poppins. Títulos y nombre en peso 800; botones y etiquetas en 600. Si se usa un peso nuevo, añadirlo a la URL de Google Fonts.
- **Paleta rotatoria** para series de bloques (chips, tarjetas de trabajos): naranja → rojo → verde → azul, en ese orden.
- **Layout**: una columna, `max-width: 560px`, 16px de margen lateral. Todo debe verse sin scroll horizontal a 375px de ancho.
- Los iconos van como **SVG inline** con `fill="currentColor"` y `aria-hidden="true"`; no cargar librerías de iconos.
