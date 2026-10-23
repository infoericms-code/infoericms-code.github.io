# Contenido y estructura

- **Un solo archivo**: todo vive en `index.html` (CSS en `<style>`, JS en `<script>`). No crear archivos `.css`/`.js` aparte ni añadir frameworks o pasos de build salvo que se pida. Las únicas excepciones son las imágenes `vista-previa.png` (1200 × 630 px, vista previa al compartir el enlace), `favicon.ico` (icono de la pestaña: 16, 32 y 48 px dentro de un solo archivo) y `apple-touch-icon.png` (180 px, iPhone), y la página `privacidad.html` (aviso legal y privacidad), que copia las variables y estilos básicos de `index.html` en su propio `<style>`.
- **Privacidad**: si se añade algo que recoja datos o use un servicio externo nuevo (formulario, analítica, vídeos incrustados…), actualizar `privacidad.html` y su fecha de «Última actualización». No es asesoramiento legal: recomendar al usuario que lo revise con una gestoría.
- **Idioma**: todo el texto visible, `aria-label`, placeholders y comentarios en español.
- **Marcadores editables**: el contenido personal está marcado con `<!-- EDITA AQUÍ: … -->`. Conservarlos y añadir uno nuevo junto a cualquier texto o enlace que el usuario deba personalizar.
- **No inventar datos personales** (nombre, profesión, ciudad, redes, enlaces). Si falta un dato, usar un marcador claro (`Tu Nombre`, `tu-usuario`) y decírselo al usuario.
- **Enlaces del usuario**: usar exactamente la URL que dio; no sustituirla por una URL deducida. El botón de LinkedIn de la cabecera aún tiene el enlace provisional `https://www.linkedin.com/in/tu-usuario`: cambiarlo solo por el que dé el usuario. El correo y el WhatsApp de «Hablemos» son datos reales que dio el usuario: no cambiarlos salvo que lo pida.
- Enlaces externos con `target="_blank" rel="noopener noreferrer"`.
