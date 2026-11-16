# Entre tiempo · Brandbook (prototipo)

Sitio de una sola página en HTML/CSS/JS vanilla. Sin build ni dependencias.

    index.html   → todo el CSS y JS inline (vistas: #home, #sobre, #comunicamos, #signos)
    assets/      → imágenes raster (fotos, tiles, teléfonos, medidas)

Abrir `index.html` directo en el navegador (funciona con file://) o servir la carpeta con cualquier servidor estático.

## Cómo está armado
- Navegación por hash; `show(v)` alterna las vistas. Cada página escala con `zoom` según el ancho (base 1280).
- Bloques fijos al scroll: `.pin.full` + `.stick`; `pin(sel, fn)` recibe el progreso t∈[0,1]. Helpers: `stack`, `goPin`, `steps`, `lit`.
- Logos: vectores. El path de Entre tiempo está en `<symbol id="sy-et">` (se usa con `<use>`); el resto vive como máscaras SVG en base64 en el bloque `/*MASKS*/…/*/MASKS*/` (variables `--k-et`, `--k-vert`, `--k-iso`, `--k-movida`, `--k-apuro`, `--k-desvio`, `--k-kaisen`, `--k-gadnic`, `--k-giant`). Se recolorean con `.mk` + `currentColor`.
- Usos incorrectos: los 12 ejemplos se generan en JS (array `BAD`), no son imágenes.

## Pendiente: calidad de imágenes
Las imágenes de `assets/` están exportadas a 1x desde Figma (archivo `iq4xYoSzLlfEnHCzyObg8F`) y se ven pixeladas en pantallas retina. Reemplazarlas por exportaciones **3x (PNG o WebP)** con el MISMO nombre de archivo; el tamaño en pantalla lo fija el CSS, no hace falta tocar código:
`tile-*.png`, `phone-1..5.png`, `apuro-*/desvio-*.png`, `con-*.png`, `ver-*.png`, `sub-*.png`.
Giant (colaboraciones) es raster en Figma: exportarlo en SVG o PNG 3x y regenerar `--k-giant`.
