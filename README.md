# YoutubeStylus


Temas de [Stylus](https://github.com/openstyles/stylus) para **YouTube** y **YouTube Music** con fondo personalizado, barra de reproducción translúcida y una Kafka animada en la barra de progreso.

| Archivo | Para qué sitio |
|---|---|
| `Youtube.css` | `www.youtube.com` |
| `youtube-music.css` | `music.youtube.com` |

> Si tus archivos tienen otro nombre, ajusta la tabla. Lo importante es que son **dos estilos separados**.

---

## Instalación

1. Instala Stylus (Firefox, Chrome, Edge, LibreWolf).
2. Crea **dos estilos nuevos**, uno por archivo, y pega el código de cada uno.
3. En **"Se aplica a"** de cada estilo, usa **"URLs que comienzan con"**:

| Estilo | Se aplica a |
|---|---|
| `Youtube.css` | `https://www.youtube.com/` |
| `youtube-music.css` | `https://music.youtube.com/` |

**Importante:** no uses "URLs en el dominio `youtube.com`" para el primero. Stylus cuenta los subdominios, así que el tema de YouTube también se aplicaría a YouTube Music y los dos se pisarían.

---

## Usar los dos temas a la vez

Funcionan sin problema juntos, porque cada uno se activa solo en su sitio. Solo asegúrate de haber puesto bien el "Se aplica a" como en la tabla de arriba.

Si quieres que ambos usen **el mismo fondo**, pon la misma URL de imagen en los dos (ver siguiente sección).

---

## Cambiar las imágenes

Las imágenes están en este repositorio: [`XDertZX/Pictures`](https://github.com/XDertZX/Pictures). El CSS las carga con URLs de este tipo:

```
https://raw.githubusercontent.com/XDertZX/Pictures/refs/heads/main/NOMBRE.ext
```

### Opción A: reemplazar el archivo (no tocas el CSS)

1. Sube tu imagen a tu propio repositorio de GitHub con **exactamente el mismo nombre y extensión** que la original.
2. Si es en el mismo repo, sobrescribe el archivo.
3. Recarga con **Ctrl+Shift+R**. GitHub puede tardar unos 5 minutos en servir la versión nueva.

### Opción B: usar otra URL (la más flexible)

Sube tu imagen a tu repo, copia su URL `raw.githubusercontent.com/...` y reemplázala en el CSS.

### Dónde está cada imagen en el código

**`Youtube.css`**

| Qué es | Dónde buscarlo |
|---|---|
| Fondo de la página | La regla `html { background: url("...") ... }` al inicio del archivo |
| Kafka de la barra de progreso | La regla `.ytp-scrubber-button.ytp-swatch-background-color` (aparece dos veces: normal y `:hover`; cambia **ambas**) |

**`youtube-music.css`** (todo está arriba, en `:root`)

| Variable | Qué es |
|---|---|
| `--r-bg-kafka` | Fondo de toda la página |
| `--r-banner-img` | GIF del menú lateral (arriba a la izquierda) |
| `--r-scrubber-icon` | Kafka pequeña de la barra de progreso |
| `--r-scrubber-size` | Tamaño de esa Kafka (por defecto `30px`) |

Ejemplo, cambiar el fondo de YouTube Music:

```css
:root {
    --r-bg-kafka: url("https://raw.githubusercontent.com/TU-USUARIO/TU-REPO/main/mi-fondo.png");
}
```

### Consejos para las imágenes

- **Fondo:** no necesita ser más grande que tu pantalla (1920×1080 sobra). Un JPG con calidad 85 a 90 se ve igual y pesa muy poco.
- **Kafka de la barra:** se muestra a 30 px. Un GIF de unos 60×60 px es suficiente y carga mucho más rápido.
- **GIF del menú lateral:** se muestra a unos 228×140 px, no necesita ser más grande.
- Los GIF y fondos muy pesados pueden hacer más lento el navegador. Si notas lentitud, revisa en F12 → Red cuánto pesa cada imagen.

---

## Hacer que el disco deje de girar (YouTube Music)

El disco de la portada gira mientras suena la música y se pausa cuando pausas.

**Apagarlo por completo:** en el `:root` del principio, cambia esta línea:

```css
--r-rotate: rotate 12s linear infinite;
```

por esta:

```css
--r-rotate: none;
```

**Cambiar la velocidad:** modifica los `12s`. Menos segundos gira más rápido (`6s`), más segundos gira más lento (`30s`).

**Apagar solo uno de los dos discos:** deja `--r-rotate` como está y agrega esto **al final del archivo**.

Solo el disco pequeño de la barra de abajo:

```css
#layout[player-ui-state] ytmusic-player-bar .middle-controls .thumbnail-image-wrapper {
    animation: none;
}
```

Solo el disco grande de la página del reproductor:

```css
#layout #player:is([player-ui-state="PLAYER_PAGE_OPEN"], [player-ui-state="MINIPLAYER"]) #song-image #thumbnail {
    animation: none;
}
```

---

## Mostrar la Kafka de la barra solo al pasar el mouse (YouTube Music)

Por defecto está siempre visible. Para que solo aparezca al pasar el mouse, busca el bloque `Kafka del scrubber: siempre visible` y reemplaza esto:

```css
#progress-bar #sliderKnob {
    visibility: visible !important;
    opacity: 1 !important;
}
```

por esto:

```css
#progress-bar #sliderKnob { visibility: hidden; }
#progress-bar:hover #sliderKnob { visibility: visible; }
```

---

## Otras cosas útiles

**Quitar la intro con el texto "музыка"** (YouTube Music): borra el bloque que empieza en `/* ---------- Intro al cargar ---------- */`, incluyendo su `@keyframes swipe`.

**Hacer el fondo más oscuro o más claro:**
- YouTube: en `html::before`, cambia el `0.35` de `rgba(0, 0, 0, 0.35)`.
- YouTube Music: en `body::before`, cambia los dos `.25` de `rgba(0, 0, 0, .25)`.

**Quitar el desenfoque** (si el navegador va lento): borra o comenta las líneas `backdrop-filter: ...`. Es lo que más recursos gasta.

---

## Problemas comunes

| Problema | Solución |
|---|---|
| El tema no se ve | Revisa que el estilo esté activado en Stylus y que el "Se aplica a" sea el correcto. |
| La imagen nueva no aparece | Recarga con **Ctrl+Shift+R** y espera unos minutos si la reemplazaste en GitHub. |
| El preview de los videos aparece corrido | No pongas `position` ni `z-index` en `body` ni en `ytd-app`. |
| Los dos temas se mezclan | Cambia el "Se aplica a" de `Youtube.css` a "URLs que comienzan con" `https://www.youtube.com/`. |
| Todo va más lento | Usa imágenes más livianas y reduce los `backdrop-filter`. |
