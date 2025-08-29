# API Key Usage Checker (Meme)

Página web de broma (single-file) que “escanea” si alguien más está usando tu API key. La interfaz está en inglés, pero todo corre 100% en el navegador: no hay backend y nada se envía a ningún servidor (salvo cargar el CSS de Tailwind vía CDN y la imagen de avatar desde Unavatar).

> Obviamente es una broma — no pegues claves reales en ninguna parte.

## Demo local

- Abre `index.html` en tu navegador. No necesita build ni servidor.
- Requiere conexión para cargar Tailwind (CDN) y los avatares (Unavatar). Sin conexión, la página funciona pero se verá sin estilos y sin avatar.

## Características

- Validación de formato de API keys (no verificación real): OpenAI y Anthropic.
- Simulación de escaneo con barra de progreso y resultado final.
- Resultado aleatorio: en ocasiones “alguien más” aparece con su handle de X/Twitter y avatar.
- Lista fija de posibles usuarios: `levelsio`, `theo`, `plbiojout`, `rauchg`, `leerob`, `shadcn`, `gnukeith`, `nicolasoulianov`.
- Aviso flotante diminuto que aparece en una posición aleatoria al recargar la página.

## Cómo funciona

- Todo es client-side. La clave que pegues nunca sale del navegador.
- Se valida el patrón (formato) de la key, no su validez real. Si el formato no coincide con OpenAI/Anthropic, se muestra feedback y no se inicia el “escaneo”.
- Si “alguien más” la usa (probabilidad configurable), se elige un usuario al azar de tu lista y se muestra su avatar (`unavatar.io`) y un link a `twitter.com/<handle>`.

## Personalización rápida

- Lista de usuarios sospechosos: edita `SUSPECT_USERS` en `index.html:61`.
- Probabilidad de “alguien más la usa”: edita `PROB_USED_BY_SOMEONE` en `index.html:63`.
- Patrones de keys reconocidos: amplía `KEY_PATTERNS` en `index.html:65`.
- Aviso flotante (texto/posición): elemento `#floatingNote` en `index.html:223` y script de posicionamiento justo debajo.

## Validación de claves (aproximada)

- OpenAI: patrones como `sk-live-…`, `sk-test-…`, `sk-proj-…`, y `sk-…` alfanumérico largo.
- Anthropic: patrones `sk-ant-…`.
- Para añadir otro proveedor, agrega un objeto en `KEY_PATTERNS` con tu `vendor` y una función `match(key)` con tu RegExp.

## Dependencias y red

- CSS: Tailwind vía CDN (`https://cdn.tailwindcss.com`).
- Avatares: Unavatar (`https://unavatar.io/x/<handle>` con fallback a `https://unavatar.io/<handle>`).
- En modo offline, la página carga pero sin estilos CDN y sin avatares.

## Seguridad y privacidad

- No pegues API keys reales. Este proyecto es humorístico.
- El input no se envía a ninguna parte; solo vive en memoria del navegador.
- Si quieres máxima tranquilidad, desconecta internet y abre el archivo; verás que funciona “sin red”, solo sin estilos/avatares.

## Créditos

- Tailwind CSS (CDN).
- Unavatar para las imágenes de perfil.

---

Made for fun. Use responsibly. 😄
