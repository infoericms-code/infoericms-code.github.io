# Verificación de cambios

No hay tests automáticos; los cambios se comprueban en el navegador integrado (el archivo se muestra solo tras editarlo).

- Tras un cambio visual: captura en escritorio y en móvil (`resize_window` preset `mobile`, 375px) y comprobar `document.documentElement.scrollWidth === document.documentElement.clientWidth`. Volver a `desktop` al terminar.
- Revisar que la consola no tenga errores y que el año del pie aparezca.
- Si se añade o cambia un enlace, comprobar que el `href` es exactamente el que dio el usuario.
- **Formulario**: probar sin enviar nada de verdad, sustituyendo `fetch` antes de pulsar «Enviar» (y poniendo una clave cualquiera en `access_key` si sigue la provisional):
  ```js
  window.fetch = async () => ({ ok: true, json: async () => ({ success: true }) }); // para el error: success: false
  ```
  Comprobar: enviar vacío (el navegador marca los obligatorios), aviso con la clave provisional, mensaje verde y formulario vacío si va bien, mensaje rojo y botón activo si falla.
- El panel abre el archivo como `data:` URL: ahí `localStorage` lanza error. Ahora la web no lo usa; si algún día se añade algo que guarde datos, habrá que simularlo antes de probar.
- **Alternativa con Playwright** (MCP del proyecto, ver `.mcp.json`): bloquea `file:`, así que hay que servir la web por `http://127.0.0.1`. Con Node (instalado en este equipo) basta un servidor mínimo en segundo plano, apuntando a la carpeta del proyecto:
  ```powershell
  node -e "require('http').createServer((q,r)=>require('fs').readFile('index.html',(e,d)=>{r.writeHead(e?500:200,{'Content-Type':'text/html; charset=utf-8'});r.end(d)})).listen(8765,'127.0.0.1')"
  ```
  Al terminar: parar el servidor (puerto 8765) y borrar las capturas y la carpeta `.playwright-mcp` que cree Playwright en el proyecto.
- `python` es el alias de la Microsoft Store: no usarlo para servidores locales.
