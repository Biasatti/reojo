# RASTRO / 001

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
- Botón rojo: grabar/detener la imagen procesada (sin audio).
- Flecha hacia abajo: compartir o guardar la última grabación.
- Botón de flecha circular en la parte superior: alternar cámara trasera/frontal.
- Botón inferior izquierdo: reiniciar controles.

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
