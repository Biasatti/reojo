# REOJO / 003

Prototipo PWA para iPhone de cámara con duotono y estelas temporales, desarrollado en HTML, CSS, JavaScript y WebGL. No utiliza servidores para procesar los videos.

## Para probar en iPhone

1. Subí **todo el contenido de esta carpeta** a un repositorio público de GitHub, en la raíz.
2. En GitHub, abrí **Settings → Pages → Deploy from a branch → main / (root)** y guardá.
3. Abrí la dirección HTTPS publicada con **Safari** en tu iPhone.
4. Tocá **ABRIR CÁMARA** y autorizá el permiso.
5. Opcional: Compartir → **Agregar a pantalla de inicio**.

La cámara requiere HTTPS. Abrir `index.html` desde Archivos o mediante `file://` no sirve. En una computadora podés probar con un servidor local (`python -m http.server 8000` y `http://localhost:8000`).

## Uso

- Deslizamiento horizontal sobre el centro/izquierda de la imagen: balance del duotono.
- Deslizamiento vertical en el 23% derecho de la imagen: cantidad de estela.
- **ECO**: fotogramas anteriores semitransparentes, condicionados por cambios visuales.
- **PSY**: retroalimentación acumulativa y persistencia.
- Dos círculos de color: elegir tono de sombras y luces.
- Botón rojo central: grabar/detener la imagen procesada (sin audio).
- Botón de cámara inferior izquierdo: sacar una foto PNG con el duotono y las estelas visibles en ese instante.
- Flecha hacia abajo: compartir o guardar la última foto o grabación (la más reciente).
- Botón de flecha circular en la parte superior: alternar cámara trasera/frontal.
- Botón superior junto a cambiar cámara: reiniciar controles.

## Limitaciones de este primer prototipo

- La grabación desde un canvas depende de `HTMLCanvasElement.captureStream` y `MediaRecorder`; algunos Safari/iOS no ofrecen una combinación funcional o no generan el formato esperado. La app informa si falta soporte.
- El formato final se negocia con el navegador (preferentemente MP4, y WebM como alternativa). Algunos videos WebM podrían no abrirse directamente en Fotos del iPhone.
- No hay micrófono ni audio en esta versión.
- La calidad de procesamiento se fija internamente en 960 px de alto / 30 fps como objetivo; el rendimiento depende del dispositivo.
- Para compartir, iOS normalmente presenta la hoja nativa de compartir. No podemos escribir directamente en Fotos sin acción del usuario.
- El modo ECO mezcla dos muestras históricas, aproximadamente a 3 y 8 fotogramas de distancia; PSY acumula el resultado de la imagen previa.
- Esta versión no guarda configuraciones entre sesiones.

## Próxima iteración

Probar especialmente en Safari/iPhone la captura y la exportación. Una vez validada, calibrar el delay para movimientos reales, ajustar el tratamiento cromático y mejorar los estados de grabación.

## Versión 2: encuadre y zoom

- El encuadre base **1×** muestra el fotograma completo de la cámara en lugar de recortarlo para llenar la pantalla. Puede dejar pequeñas bandas oscuras si la proporción de la cámara no coincide con la pantalla.
- Botón superior derecho **1× / 2×** para activar o desactivar el zoom digital; funciona con las dos cámaras y también durante una grabación.
- Al cambiar entre cámara frontal y trasera, el zoom vuelve a **1×** para evitar acercamientos inesperados.
- El aumento **2× es digital**: no garantiza seleccionar el teleobjetivo físico del iPhone. No puede alejar más que el campo de visión real de la cámara seleccionada.
- La cámara solicita formato vertical 9:16 cuando el navegador lo permite, pero iOS decide el formato y sensor disponibles.

Para actualizar GitHub Pages, reemplazá los archivos del repositorio por esta versión. Si abrís la app desde un ícono antiguo, cerrala y reabrila para recibir la actualización del service worker.

## Versión 3: fotos y marca

- Nombre REOJO en título HTML, nombre del ícono de inicio, encabezado y exportaciones.
- Se actualizó el indicador visible de versión a 003 y el caché offline a `reojo-v3`.
- Se agregó botón fotográfico abajo a la izquierda. Captura el resultado WebGL ya procesado, con ambos modos y el duotono.
- La captura se exporta como PNG, sin controles de interfaz.
- Guardar/compartir utiliza la última captura, sea foto o video. No hay galería interna.
- Para conservar los fotogramas previos visibles, la foto se toma desde el framebuffer de composición y se invierte verticalmente para su exportación.

**Importante:** reemplazar los archivos en GitHub Pages actualiza la web publicada. No podemos confirmar su contenido remoto sin revisar la URL. Si ya tenés un ícono instalado, puede ser necesario cerrar y reabrir la PWA, o eliminarla y volverla a agregar para renovar el nombre/ícono según iOS.
