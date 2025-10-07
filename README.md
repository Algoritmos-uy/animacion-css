# Animaciones y transiciones (explicaciones)

Este repositorio contiene una hoja de estilos de ejemplo que muestra cómo usar
transiciones y animaciones en CSS. Aquí están las explicaciones separadas y
didácticas para cada regla, además de recomendaciones de accesibilidad y
rendimiento.

## Resumen rápido

- `transition`: anima cambios entre dos estados (por ejemplo, hover) de forma suave.
- `animation` + `@keyframes`: define animaciones complejas que se repiten o no.
- Prefiere usar `transform` (por ejemplo `translateX`, `rotate`) en animaciones por
  rendimiento en lugar de propiedades como `left` o `top`.
- Respeta la preferencia del usuario `prefers-reduced-motion` para evitar
  animaciones no deseadas.

## Reglas principales (explicadas)

- `body`:

  - Contenedor principal con `display: flex` y `flex-direction: column` para
    centrar y espaciar los elementos en la demo.
  - `padding` grande para separar el contenido del borde de la ventana en los
    ejemplos.

- `.boton` y `.boton:hover`:

  - `transition: background-color 0.3s ease, transform 0.3s ease;` hace que
    el cambio de color y el escalado sean suaves al pasar el ratón.
  - En `:hover` se cambia el color, se escala con `transform: scale(1.1)` y se
    añade un borde para feedback visual.

- `.caja` + `@keyframes mover`:

  - `.caja` es un cuadrado que se desplaza horizontalmente usando
    `transform: translateX(...)` dentro de `@keyframes`.
  - Usar `transform` produce animaciones más suaves y con menos repintados.

- `.circulo` / `.circulo-2` + `@keyframes girar` / `girar-2`:

  - Círculos que rotan continuamente en sentidos opuestos (horario y
    antihorario).

- `hr` y clases `.hr2`–`.hr5`:

  - Líneas cortas usadas como elementos gráficos; se rotan con
    `transform: rotate(...)` para crear diagonales.

- `.box` + `@keyframes moveAcross`:
  - Un bloque que cruza horizontalmente la pantalla.
  - Refactorizado para usar `transform: translateX(...)` en vez de `left` para
    mejorar el rendimiento. La animación se reinicia mediante un salto
    rápido en el 50% del ciclo para crear un flujo continuo.

## Accesibilidad

Es importante respetar a las personas que prefieren menos movimiento. Por eso
en el CSS se incluye:

```css
@media (prefers-reduced-motion: reduce) {
  /* detener animaciones/transiciones para usuarios que lo prefieren */
}
```

Esto evita mareos o distracciones innecesarias.

## Rendimiento

- Evita animar propiedades que provoquen reflow/layout (por ejemplo `left`,
  `top`, `width`), porque son más costosas.
- Prefiere `transform` y `opacity` para animaciones fluidas.

## Cómo probar

1. Abrir `index.html` en un navegador moderno.
2. Observar los elementos con clases `.boton`, `.caja`, `.circulo`, `.box`.
3. En las DevTools puedes desactivar `prefers-reduced-motion` para probar ambos
   comportamientos (o cambiar la configuración de accesibilidad del SO).

## Cambios realizados

- Se movieron las explicaciones largas fuera de `styles.css` y se colocaron en
  este `README.md` para mantener el CSS limpio.
- Se refactorizó la animación `.box` para usar `transform` y mejorar rendimiento.
- Se añadió soporte para `prefers-reduced-motion`.

## Siguientes pasos sugeridos

- Añadir un ejemplo visual en el README con GIF o una pequeña demo HTML.
- Incluir notas sobre accesibilidad adicional (contraste, tamaños clicables).
- Añadir variantes con `prefers-reduced-motion: no-preference` explicadas.

Si quieres, genero una página de ejemplo `demo.html` con los elementos ya
colocados para visualizar todo con facilidad.

---

Archivo generado automáticamente con explicaciones.

# animacion-css

Proyecto didáctico explicativo de animación en css
