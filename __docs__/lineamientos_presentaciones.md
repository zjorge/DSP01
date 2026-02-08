# Lineamientos de Presentaciones — Isthmus DSP01

> Guía de estilo visual, estructura y animaciones para todas las presentaciones del curso **Diseño y Programación Web**.

---

## 1. Filosofía general

Cada presentación debe sentirse como una experiencia de producto, no como un documento proyectado. Inspiración directa: keynotes de Apple, decks de Dash0, WeTransfer Ideas Report y portafolios de agencias como Alura.

- **Menos es más** — Un solo concepto por slide. Si necesitas explicar más, agrega otro slide.
- **El espacio en blanco es contenido** — El vacío dirige la mirada y da peso a lo que sí aparece.
- **Revelación progresiva** — La información aparece cuando el presentador la necesita, nunca antes.
- **Movimiento con propósito** — Cada animación comunica jerarquía o secuencia, nunca es decorativa.

---

## 2. Estética visual

### 2.1 Identidad tipográfica

| Propiedad       | Valor                                              |
| --------------- | -------------------------------------------------- |
| Familia         | **Montserrat** (Google Fonts)                      |
| Pesos usados    | 200 (thin), 300 (light), 400, 500, 600, 700, 800, 900 |
| Código          | `SF Mono`, `Fira Code`                             |
| Anti-aliasing   | `-webkit-font-smoothing: antialiased`              |

- Los títulos usan **tracking negativo** (`letter-spacing: -0.03em` a `-0.04em`) para lograr el look Apple de tipografía compacta y pesada.
- El cuerpo usa peso **300 (light)** para contraste con los headings.

### 2.2 Paleta de color

#### Modo claro (default)

| Token               | Hex       | Uso                              |
| -------------------- | --------- | -------------------------------- |
| `--r-background`     | `#e8e7e6` | Fondo general (gris cálido)      |
| `--r-heading-color`  | `#1d1d1f` | Títulos, texto principal         |
| `--color-muted`      | `#86868b` | Subtítulos, etiquetas, íconos    |
| `--color-subtle`     | `#d2d2d7` | Bordes, separadores, texto dimmed |
| `--color-surface`    | `#f5f5f7` | Fondos de tarjetas, código       |
| `--color-highlight`  | `#0071e3` | Links, acentos (azul Apple)      |
| `--color-warm`       | `#e84d3d` | Alertas, énfasis cálido          |

#### Modo oscuro (toggle con tecla `D`)

| Token               | Hex       |
| -------------------- | --------- |
| `--r-background`     | `#111112` |
| `--r-heading-color`  | `#f5f5f7` |
| `--color-muted`      | `#6e6e73` |
| `--color-subtle`     | `#424245` |
| `--color-surface`    | `#161617` |
| `--color-highlight`  | `#2997ff` |

### 2.3 Densidad de contenido

- **Máximo por slide**: 1 título + 1 subtítulo + 3-4 bullets, **o** 1 número grande + 1 etiqueta, **o** 1 cita + autor.
- **Nunca**: párrafos largos, tablas densas ni más de 4 columnas.
- **Regla de los 3 segundos**: si el alumno no puede captar la idea del slide en 3 segundos, tiene demasiado contenido.

### 2.4 Alineación y layout

- **Alineación izquierda** por defecto (como Apple). Centrado solo en slides de título y section dividers.
- **Padding**: `60px 80px` — generoso, respira.
- **Ancho máximo de texto**: `1100px` — evita líneas demasiado largas.
- **Grid**: sistema de columnas con `display: flex` y `gap: 3em`.

---

## 3. Tipos de slide

### 3.1 Title slide (`class="title-slide"`)
Centrado. Logo/código del curso + nombre de la clase. Tipografía máxima (4em, weight 900). Fondo limpio.

### 3.2 Section divider (`class="section-divider"`)
Centrado. Marca la transición entre bloques temáticos. Tipografía grande (3em, weight 800) + tag opcional.

### 3.3 Contenido simple
Título h2 + subtítulo h3 (uppercase, muted) + párrafo lead o lista corta. Ícono hero opcional (Lucide, stroke-width 1, 3em).

### 3.4 Lista con revelación
Items con `fragment fade-up` (aparecen uno a uno desde abajo) o `fragment semi-out` (todos visibles pero atenuados, el actual destaca).

### 3.5 Big number / Stat
Número grande (6em, weight 800) + etiqueta. Ideal para datos impactantes. Usar `data-auto-animate` para morphing entre números.

### 3.6 Columnas (`class="cols"`)
2-3 columnas con flex. Cada columna puede tener big-number + label, o ícono + texto. Fragments opcionales.

### 3.7 Stack diagram
Capas apiladas verticalmente. Cada capa aparece con `fragment fade-up`. La capa activa se invierte (fondo oscuro, texto claro).

### 3.8 Código
Bloque `<pre><code>` con fondo surface, border-radius 12px, borde sutil. Máximo 8-10 líneas por slide.

### 3.9 Cita / Blockquote
Borde izquierdo azul (3px). Texto italic, weight 300, tamaño 1.3em. Autor debajo en small + muted.

### 3.10 Checklist
Lista con `□` como marcador. Ideal para criterios de evaluación o pasos a seguir.

### 3.11 Wireframe placeholder
Cajas con borde dashed para representar layouts. Estilo blueprint minimalista.

### 3.12 Pausa
Slide de título centrado con "Pausa" + duración en muted. Marca el descanso.

---

## 4. Animaciones y transiciones

### 4.1 Principios

- **Suavidad** — Todo movimiento usa `cubic-bezier(0.25, 0.1, 0.25, 1)` (ease-in-out suave, similar a Apple).
- **Velocidad** — Transiciones rápidas (`transitionSpeed: 'fast'`). Duración de auto-animate: `0.6s`. Fragments: `0.4s`.
- **Consistencia** — Todas las transiciones entre slides son `fade`. Sin slides, flips ni zooms.
- **Intención** — Cada animación tiene un porqué: revelar secuencia, mostrar jerarquía o conectar estados.

### 4.2 Tipos de fragment

| Clase              | Comportamiento                                                                 |
| ------------------ | ------------------------------------------------------------------------------ |
| `fragment fade-up` | Aparece desde 24px abajo con fade. Ideal para listas y columnas.               |
| `fragment semi-out` | Todos visibles desde el inicio en color sutil. El actual se destaca (JS).      |
| `fragment dim-out` | Similar a semi-out pero manejado por CSS. El actual se ilumina.                |
| `fragment highlight-current` | Todos visibles en sutil, el actual en heading-color.                |

### 4.3 Auto-animate (morphing)

- Usar `data-auto-animate` en slides consecutivos para transiciones fluidas entre estados.
- Elementos que deben morphear comparten `data-id`.
- Easing: `cubic-bezier(0.25, 0.1, 0.25, 1)`.
- Duración: `0.6s`.
- `autoAnimateUnmatched: false` — solo anima lo que tiene match explícito.

### 4.4 Lo que NO hacer

- Nunca usar `slide`, `convex`, `concave` ni `zoom` como transición.
- Nunca animar todo el slide completo con bounce o spring.
- Nunca usar delays largos (>0.5s) que hagan sentir la presentación lenta.
- Nunca usar animaciones de entrada en el primer elemento visible de un slide.

---

## 5. Iconografía

- **Librería**: Lucide Icons (CDN, última versión).
- **Stroke-width**: 1.5 para inline, 1 para hero icons.
- **Tamaños**: inline (1em), lg (1.5em), xl (2em), hero (3em).
- **Color**: heredado del contexto. Usar clases `icon-muted`, `icon-subtle`, `icon-highlight`.
- **Estilo**: line icons únicamente. Nunca filled, nunca ilustraciones complejas.

---

## 6. Notas del presentador

- Cada slide **debe** tener `<aside class="notes">` con contenido guía explicativo y detallado para el presentador. No críptico, explicativo y detallado.
- Las notas incluyen: puntos clave a mencionar, ejemplos verbales, preguntas para el grupo, tiempos sugeridos.
- Las notas no se proyectan (activar con `S` para speaker view).
- Redactar en tono conversacional, como recordatorios rápidos.

---

## 7. Estructura de una clase típica

```
01. Title slide — Nombre de la clase
02. Agenda / Objetivos — Lista con fade-up
03. Section divider — Bloque 1
04-12. Contenido del bloque 1 (6-8 slides)
13. Section divider — Bloque 2
14-22. Contenido del bloque 2 (6-8 slides)
23. Pausa — 10 minutos
24. Section divider — Bloque 3 / Práctica
25-32. Contenido del bloque 3
33. Resumen / Checklist
34. Cierre — Próxima clase + tarea
```

- **Rango ideal**: 40-80 slides por clase de 2 horas.
- **Ritmo**: 30s a 3 minutos por slide (incluyendo fragments).
- **Pausas**: una pausa de 10 a 15 minutos a la mitad.

---

## 8. Stack técnico

| Componente     | Tecnología                                    |
| -------------- | --------------------------------------------- |
| Motor          | Reveal.js v5.1.0 (CDN, sin build)             |
| Theme base     | `white.css` + override `theme-isthmus.css`     |
| Íconos         | Lucide Icons (CDN)                             |
| Tipografía     | Google Fonts (Montserrat)                      |
| Servidor local | `python3 -m http.server 8765` desde `clases/` |
| Plugins        | RevealNotes (speaker view)                     |

### Configuración Reveal.js

```javascript
{
  width: 1920,
  height: 1080,
  margin: 0,
  hash: true,
  history: true,
  controls: true,
  controlsLayout: 'bottom-right',
  progress: true,
  slideNumber: 'c/t',          // solo en speaker view
  showSlideNumber: 'speaker',
  center: false,                // alineación top-left
  transition: 'fade',
  transitionSpeed: 'fast',
  backgroundTransition: 'fade',
  autoAnimateEasing: 'cubic-bezier(0.25, 0.1, 0.25, 1)',
  autoAnimateDuration: 0.6,
  autoAnimateUnmatched: false,
}
```

---

## 9. Clases CSS utilitarias

| Clase       | Efecto                                    |
| ----------- | ----------------------------------------- |
| `.muted`    | Color gris medio (`--color-muted`)        |
| `.accent`   | Color azul highlight                      |
| `.warm`     | Color rojo/naranja cálido                 |
| `.thin`     | Font-weight 200                           |
| `.light`    | Font-weight 300                           |
| `.medium`   | Font-weight 500                           |
| `.bold`     | Font-weight 700                           |
| `.heavy`    | Font-weight 800                           |
| `.small`    | Font-size 0.7em                           |
| `.tiny`     | Font-size 0.55em                          |
| `.uppercase`| Uppercase + tracking amplio + weight 600  |
| `.lead`     | Texto grande (1.8em), weight 300          |
| `.tag`      | Pill/badge con borde, uppercase           |

---

## 10. Checklist pre-publicación

Antes de dar por terminada una presentación, verificar:

- [ ] Cada slide tiene máximo 1 idea principal
- [ ] Todos los slides tienen `data-transition="fade"`
- [ ] Las listas usan fragments (`fade-up` o `semi-out`)
- [ ] Los auto-animate tienen `data-id` consistentes
- [ ] Cada slide tiene `<aside class="notes">` con contenido útil
- [ ] No hay párrafos de más de 3 líneas en pantalla
- [ ] Los íconos Lucide están correctamente referenciados
- [ ] El slide de título tiene el número de clase correcto
- [ ] Hay al menos un section divider por bloque temático
- [ ] La presentación funciona en modo oscuro (tecla `D`)
- [ ] El total de slides está entre 40-80
- [ ] Se probó con `python3 -m http.server 8765`