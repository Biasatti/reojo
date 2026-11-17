# REOJO / 009 — FX

Versión experimental para iPhone. Incluye la galería temporal de v8, cámara frontal/trasera, fotos y video sin audio, selector 9:16 / 4:5 / 16:9, ECO / PSY, control gestual de trail y duotono.

## Nuevo en 009

- Los dos colores y el botón **DUO · ON/OFF** siguen en la pantalla principal.
- Nuevo botón visible **FX** en la franja superior. Abre un panel inferior con vista parcial de la cámara.
- **GRAIN / RUIDO**: slider de 0 a 100%, por defecto 25%. El ruido se incorpora a fotos y videos; no es una simple superposición visual.
- **RGB REACTIVO**: ON/OFF. El RGB aparece en las regiones de movimiento y puede combinarse con duotono o color natural.
- Tocar fuera del panel o la flecha hacia abajo lo cierra. Reset restaura grain 25% y RGB ON.

## Instalación

Subí el contenido del ZIP a la raíz del repositorio GitHub Pages. Abrí la dirección HTTPS desde Safari y autorizá la cámara. Podés agregarla a la pantalla de inicio. Se usa almacenamiento local de Safari (IndexedDB) para guardar capturas temporalmente hasta 24 horas, pero no es infalible; exportá cualquier video importante. Si la actualización no aparece, cerrá y reabrí la PWA.

**Pendiente de prueba en iPhone real:** calidad del nuevo grano, rendimiento, exportación y disposición del panel FX.
