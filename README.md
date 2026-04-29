# Portadas de revistas

Pequeña interfaz para previsualizar plantillas de portadas y gestionar la generación/descarga de imágenes.

## Descripción
Esta página permite seleccionar una "plantilla" (Modelo 1..7), ver una miniatura y editar un "system prompt" que describe la portada. Las miniaturas se leen desde la carpeta `images/` (archivos `modelo1.png`, `modelo2.png`, ...).

## Uso rápido
- Coloca las miniaturas en `images/modelo1.png` ... `images/modelo7.png`.
- Abre `index.html` en tu navegador (sitio estático).
- Selecciona una plantilla en la lista de miniaturas.
- El "System prompt (editable)" se genera automáticamente; puedes editarlo y usar el botón "Copiar" para copiarlo al portapapeles.
- Si quieres generar una imagen final con la API, introduce tu API key y pulsa "Generar imagen" (la app usa la API remota si se suministra la clave).
- Puedes descargar la imagen mostrada usando el botón "Descargar imagen".

## Estructura de archivos
- `index.html` — interfaz principal.
- `styles.css` — estilos.
- `script.js` — lógica de la UI: carga de plantillas, generación de prompts, carga de miniaturas desde `images/modeloN.png`, copia del prompt.
- `images/` — carpeta donde deben colocarse las miniaturas `modelo1.png`..`modelo7.png`.
- `JSON.txt`, `modelos.txt` — datos de plantillas y modelos (si existen).

## Notas de desarrollo
- Las miniaturas se cargan desde `images/modelo{N}.png` en lugar de generarse por IA. Si falta una imagen, la vista mostrará un fondo gris y el atributo `alt` mostrará "No preview".
- El botón de copia usa la API `navigator.clipboard` cuando está disponible y un fallback con `document.execCommand('copy')` si no lo está.
- Para cambiar el número de plantillas mostradas, edita la función `renderTemplateThumbnails()` en `script.js`.
