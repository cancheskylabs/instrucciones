# Landing Page Prompt — Luxury Editorial

Crea una landing page completa usando **HTML, Tailwind CSS (vía CDN) y JavaScript vanilla**. El stack debe ser un único archivo `.html` autocontenido.

## Stack visual y estilo

Diseño **luxury editorial** — oscuro, sofisticado, sin emojis y sin exceso de iconos. Paleta basada en negro profundo (`#0a0a0a`), crema/marfil (`#f5f0e8`) y un acento dorado (`#c9a84c`). Tipografía: una fuente serif elegante para titulares (ej. *Playfair Display* o *Cormorant Garamond* via Google Fonts) y una sans-serif refinada para cuerpo (ej. *DM Sans* o *Jost*).

## Secciones requeridas

1. **Hero fullscreen** — imagen de fondo de alta calidad (usa Unsplash con URL directa), titular grande centrado con animación de entrada (fade + slide), subtítulo y un CTA con borde dorado.
2. **About / Propuesta de valor** — layout asimétrico: imagen a la izquierda ocupando 50% de alto, texto a la derecha con 3 puntos clave en tipografía elegante. Sin bullets ni iconos excesivos.
3. **Galería / Showcase** — grid de 3 imágenes (Unsplash) con efecto hover: escala suave + overlay oscuro con texto que aparece.
4. **Testimonial** — sección minimalista centrada, una cita grande en serif cursiva con nombre y cargo debajo.
5. **CTA final** — franja oscura con titular impactante y botón prominente.
6. **Footer** — simple, logo/nombre del negocio, links y copyright.

## Interactividad JS requerida

- Navbar que cambia de fondo al hacer scroll (transparente → negro sólido con transición suave).
- Animaciones de entrada al hacer scroll usando `IntersectionObserver` (elementos que aparecen con fade-in + translateY).
- Efecto parallax sutil en la imagen hero.

## Restricciones de diseño

- Cero emojis. Iconos solo si son absolutamente necesarios (máximo 2-3, SVG inline discretos).
- Espaciado generoso, respiración visual premium.
- Hover states en todos los elementos interactivos.
- Totalmente responsive (mobile-first).
- Bordes y líneas decorativas finas en lugar de sombras pesadas.

El resultado debe sentirse como el sitio web de una marca de lujo internacional: **sobrio, denso en impacto visual, impecable en detalles tipográficos**.
