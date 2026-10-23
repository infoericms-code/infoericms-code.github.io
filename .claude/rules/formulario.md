# Formulario de contacto (Web3Forms)

- **Servicio externo**: los mensajes los recibe Web3Forms (`https://api.web3forms.com/submit`) y los reenvía al correo del usuario. Plan gratuito: 250 mensajes al mes. No cambiar la dirección de envío ni de servicio salvo que se pida.
- **Clave (`access_key`)**: es pública por diseño; puede ir en el HTML. Ya está puesta la clave real que dio el usuario: no cambiarla salvo que lo pida. Si se volviera a poner `TU-CLAVE-DE-WEB3FORMS`, el JS no envía nada y avisa de usar correo o WhatsApp. No darse de alta en Web3Forms en nombre del usuario.
- **Campos**: `name` y `email` se llaman así porque Web3Forms los usa para el remitente y el «responder a». El resto (`telefono`, `servicio`, `mensaje`) aparecen con ese nombre en el correo. `botcheck` es la casilla trampa contra spam: siempre oculta.
- **Seguridad**: los mensajes de estado se ponen con `textContent`. Nunca `innerHTML` ni plantillas de cadena con datos del visitante.
- **Teléfono**: solo números, espacios y un `+` inicial. El JS borra al momento cualquier otro carácter y el `pattern` exige entre 6 y 19 cifras/espacios; sigue siendo opcional.
- La validación la hace el navegador (`required`, `type="email"`); el evento `submit` solo llega si los campos son válidos.
- **Nada de envíos reales de prueba sin permiso del usuario**: llegan a su correo y cuentan para el límite. Para probar, simular `fetch` (ver `verificacion.md`).
