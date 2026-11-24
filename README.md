# Águila: Colecciona la Navidad (prototipo)

Micrositio de campaña: 4 momentos (Velitas, La Novena, La Parranda, El 31), escaneo de QR, portal y formulario de concurso.

## Estructura
```
index.html        Estructura y vistas
css/styles.css    Estilos
js/config.js      CONFIG, códigos DEMO (SOLO prototipo)
js/app.js         Lógica de la app
vendor/jsQR.js    Lector de QR (MIT)
```

## Ejecutar en VS Code
1. Abrir la carpeta en VS Code.
2. Instalar la extensión **Live Server** (se sugiere sola) y pulsar "Go Live".
   Alternativa: `npx serve .`
3. La cámara solo funciona en `localhost` o con **HTTPS**. Para probar en el celular, publica en un hosting con HTTPS.

## Subir a un repositorio
```
git init
git add .
git commit -m "Prototipo Águila Colecciona la Navidad"
git branch -M main
git remote add origin <URL_DEL_REPOSITORIO>
git push -u origin main
```

## Demostrativo vs. requiere backend
Todo lo marcado con `TODO` en `js/config.js` y `js/app.js`.

| Funcionalidad | Hoy | Producción |
|---|---|---|
| Registro / login | localStorage, sin contraseña | Autenticación real (OTP, JWT/OAuth) |
| Validación de QR | Tabla `DEMO_CODES` en el cliente | `POST /api/codes/redeem`: QR únicos y firmados; el servidor decide validez, momento y repetición |
| Colección | localStorage | Base de datos (users, collections, entries) |
| Desbloqueo del portal | Conteo local | Verificación en servidor de los 4 momentos |
| Inscripción al concurso | localStorage | `POST /api/contest/entries` |
| Términos y condiciones | Enlace `#` | `CONFIG.contestTermsUrl` con el texto oficial |

**Antes de publicar:** poner `CONFIG.DEMO = false` y eliminar `DEMO_CODES`. En el prototipo, cualquiera con esos códigos puede completar la colección.
