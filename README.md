# REOJO / 006

Prototipo PWA para iPhone de cámara experimental con foto, video, formatos variables, modos ECO/PSY, RGB reactivo al movimiento y duotono opcional. Está hecho en HTML, CSS, JavaScript y WebGL, y procesa la imagen en el dispositivo.

## Para probar en iPhone

1. Subí **todo el contenido de esta carpeta** a un repositorio público de GitHub.
2. En GitHub, abrí **Settings → Pages → Deploy from a branch → main / (root)**.
3. Abrí la URL HTTPS publicada con **Safari** en tu iPhone.
4. Tocá **ABRIR CÁMARA** y autorizá el permiso.
5. Opcional: Compartir → **Agregar a pantalla de inicio**.

> La cámara requiere HTTPS. Abrir `index.html` desde Archivos o con `file://` no sirve.

## Uso actual

- Deslizamiento horizontal sobre la imagen: balance del duotono.
- Deslizamiento vertical en el sector derecho: intensidad de estela.
- **ECO**: rastros más legibles, tipo eco de movimiento.
- **PSY**: persistencia más abstracta y acumulativa.
- Dos círculos de color: elegir color A y color B del duotono.
- Botón **ON/OFF** junto a “DUOTONO”: prender o apagar el duotono.
  - **ON**: la imagen usa el mapeo de dos colores.
  - **OFF**: la imagen conserva sus colores naturales, pero siguen funcionando ECO/PSY, trail y RGB reactivo.
- Botón central: grabar / detener video procesado (sin audio por ahora).
- Botón de cámara: sacar foto PNG con el efecto aplicado.
- Flecha hacia abajo: guardar o compartir la última captura.
- Botón superior de formato: alterna **9:16 → 4:5 → 16:9**.
- Botón superior ↺: restablecer controles.
- Botón superior ⟳: cambiar entre cámara trasera y frontal.

## Novedades en 006

- Se agregó interruptor **DUOTONO ON/OFF**.
- El duotono ya no es obligatorio: ahora se puede probar el tratamiento **RGB reactivo** sobre color natural.
- El reinicio de controles vuelve a dejar el duotono activado.
- Cache de la PWA actualizado a `reojo-v6`.

## Limitaciones actuales

- No hay grabación con micrófono en esta versión.
- La grabación depende de `captureStream` y `MediaRecorder`; algunos iPhone/Safari pueden limitar formatos o compatibilidad.
- La calidad y fluidez dependen del dispositivo.
- No se guardan ajustes entre sesiones.

## Próximo ajuste pendiente

- Confirmar en iPhone real el comportamiento de **DUOTONO OFF + RGB reactivo** y evaluar luego audio, botón sorpresa y “congelar el tiempo”.
