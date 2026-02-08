# Clase 05 | Viernes 13

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 5. Figma para sistemas

## Objetivos de la sesión

- Dominar Auto Layout como herramienta fundamental para componentes que escalan sin romperse.
- Entender constraints y grillas responsivas para simular comportamiento real de CSS Flex/Grid en Figma.
- Crear y organizar variables (design tokens) para color, tipografía, espaciado, radio y sombra.
- Convertir elementos sueltos en componentes con variantes y propiedades configurables.
- Establecer convenciones de naming, estructura de archivo y prácticas de colaboración.
- Preparar el archivo Figma como artefacto de handoff legible para desarrollo.

## Conceptos clave

### Auto Layout

Auto Layout es la feature más importante de Figma para diseño sistemático. Simula el comportamiento de CSS Flexbox: los elementos hijos se distribuyen automáticamente según reglas definidas.

**Conceptos fundamentales:**
- **Dirección**: horizontal (row) o vertical (column). Como `flex-direction` en CSS.
- **Gap**: espacio entre elementos hijos. Uniforme o independiente. Como `gap` en CSS.
- **Padding**: espacio interno del contenedor. Puede ser uniforme o por lado (top, right, bottom, left).
- **Alignment**: cómo se alinean los hijos en el eje principal y secundario. Como `justify-content` y `align-items`.
- **Resizing**: 
  - *Fixed*: tamaño fijo en píxeles.
  - *Hug contents*: el contenedor se ajusta al contenido (como `width: fit-content`).
  - *Fill container*: el hijo ocupa todo el espacio disponible (como `flex: 1`).

**Por qué importa:**
- Un botón con Auto Layout se adapta al texto sin romperse. Sin Auto Layout, cambiar "OK" por "Confirmar pedido" rompe el diseño.
- Un card con Auto Layout reorganiza su contenido si el título tiene 2 líneas en vez de 1.
- Un formulario con Auto Layout mantiene espaciado consistente entre campos sin ajustar manualmente.

**Errores comunes:**
- Usar frames sin Auto Layout y posicionar todo manualmente. Funciona para un mockup, se rompe para un sistema.
- No definir resizing correctamente: todo en "Fixed" hace que nada se adapte.
- Anidar demasiados Auto Layouts sin necesidad. Mantener la estructura lo más plana posible.

### Constraints

Constraints definen cómo se comporta un elemento cuando su contenedor padre cambia de tamaño. Útil para elementos que no están en Auto Layout (overlays, elementos posicionados absolutamente).

- **Left/Right/Top/Bottom**: el elemento mantiene distancia fija a ese borde.
- **Left and Right**: el elemento se estira horizontalmente (como `position: absolute; left: 0; right: 0`).
- **Center**: el elemento se mantiene centrado.
- **Scale**: el elemento escala proporcionalmente.

Uso típico: un ícono de cerrar (X) que siempre está en la esquina superior derecha de un modal, sin importar el tamaño del modal.

### Grillas responsivas en Figma

Figma permite definir grillas de layout que simulan el comportamiento responsive:

- **Columnas**: 4 (móvil), 8 (tablet), 12 (desktop). Con gutter y margin definidos.
- **Stretch**: las columnas se adaptan al ancho del frame.
- **Center**: las columnas tienen ancho fijo y se centran (como `max-width` + `margin: auto`).

Configuración recomendada:
| Breakpoint | Columnas | Gutter | Margin | Ancho frame |
|------------|----------|--------|--------|-------------|
| Móvil | 4 | 16px | 16px | 375px |
| Tablet | 8 | 24px | 32px | 768px |
| Desktop | 12 | 24px | 64px | 1440px |

Las grillas no son decorativas — son la estructura que garantiza alineación y consistencia. Desarrollo las traduce directamente a CSS Grid o Flexbox.

### Design tokens (variables en Figma)

Un design token es una decisión de diseño almacenada como variable reutilizable. En vez de usar `#007AFF` directamente, usás `color/primary/500`. Si cambia el azul, cambia en todo el sistema.

**Categorías de tokens:**

**Color**
- Primitivos: `blue/500`, `gray/100`, `red/600`. La paleta base.
- Semánticos: `color/primary`, `color/error`, `color/surface`, `color/text-primary`, `color/text-secondary`. Lo que se usa en componentes.
- Regla: los componentes nunca usan primitivos directamente. Siempre semánticos. Esto permite temas (light/dark) sin rediseñar.

**Tipografía**
- Escala: definir 5-7 tamaños con nombre semántico. Ejemplo: `text/xs` (12px), `text/sm` (14px), `text/base` (16px), `text/lg` (18px), `text/xl` (24px), `text/2xl` (32px), `text/3xl` (48px).
- Pesos: regular (400), medium (500), semibold (600), bold (700). Máximo 3-4 pesos por proyecto.
- Line-height: 1.2 para headings, 1.5 para body. Nunca "auto" sin verificar.

**Espaciado**
- Escala base 4px o 8px. Ejemplo: `space/1` (4px), `space/2` (8px), `space/3` (12px), `space/4` (16px), `space/6` (24px), `space/8` (32px), `space/12` (48px), `space/16` (64px).
- Usar la escala para padding, margin, gap. No inventar valores intermedios (13px, 17px, 22px).

**Border radius**
- `radius/none` (0), `radius/sm` (4px), `radius/md` (8px), `radius/lg` (12px), `radius/xl` (16px), `radius/full` (9999px para píldoras/círculos).

**Sombra**
- `shadow/sm`: sutil, para elevación mínima (cards, dropdowns).
- `shadow/md`: media, para modales y popovers.
- `shadow/lg`: fuerte, para elementos flotantes prominentes.

### Componentes con variantes

En Figma, un componente puede tener variantes que representan sus diferentes estados y configuraciones. Esto evita duplicar componentes y mantiene todo sincronizado.

**Estructura recomendada de variantes:**

Para un botón:
- **Hierarchy**: primary, secondary, ghost, destructive
- **Size**: sm, md, lg
- **State**: default, hover, focus, active, disabled, loading
- **Icon**: none, left, right, only

Esto genera una matriz de combinaciones. No todas son necesarias — diseñar las que se usan realmente (regla 80/20).

**Propiedades de componente (Component Properties):**
- **Boolean**: mostrar/ocultar elementos (ícono, badge, avatar).
- **Instance swap**: cambiar un sub-componente (ícono izquierdo por otro ícono).
- **Text**: contenido editable sin entrar al componente.

### Atomic Design

Concepto de Brad Frost para organizar componentes por nivel de complejidad:

1. **Átomos**: elementos indivisibles. Botón, input, label, ícono, avatar.
2. **Moléculas**: combinaciones simples de átomos. Campo de formulario (label + input + mensaje de error). Barra de búsqueda (input + botón).
3. **Organismos**: secciones completas. Header (logo + nav + search + avatar). Card de producto (imagen + título + precio + botón).
4. **Templates**: layouts de página con placeholders. La estructura sin contenido real.
5. **Páginas**: templates con contenido real. Lo que se entrega como mockup final.

No es necesario seguir Atomic Design al pie de la letra, pero el principio es valioso: construir de lo simple a lo complejo, reutilizando piezas.

### Estructura del archivo Figma

Un archivo Figma bien organizado es un acto de respeto hacia el equipo. Estructura recomendada:

**Páginas:**
1. **Cover**: nombre del proyecto, fecha, versión, responsable.
2. **Tokens/Styles**: paleta de colores, tipografía, espaciado, íconos.
3. **Components**: librería de componentes organizados por categoría.
4. **Wireframes**: estructura de baja fidelidad.
5. **UI**: diseño de alta fidelidad por pantalla.
6. **Flows**: prototipos y flujos conectados.
7. **Handoff**: pantallas listas para desarrollo con anotaciones.
8. **Archive**: versiones anteriores, exploración descartada.

**Naming de capas:**
- Descriptivo: `btn/primary/default`, no `Frame 847`.
- Consistente: siempre el mismo patrón (tipo/variante/estado).
- Sin frames anónimos: cada frame tiene nombre con propósito.

**Regla de oro**: si alguien abre tu archivo por primera vez, debe entender la estructura en 2 minutos sin preguntarte.

### Handoff: del diseño al código

Handoff es el proceso de entregar el diseño a desarrollo de forma que puedan implementarlo sin adivinar. Figma Dev Mode facilita esto, pero el diseñador debe preparar el archivo.

**Qué debe quedar explícito:**
- Medidas y espaciados (Figma los muestra automáticamente si el archivo está limpio).
- Colores como tokens, no como valores hex sueltos.
- Tipografía como estilos, no como propiedades manuales.
- Comportamiento responsive: qué cambia en cada breakpoint y por qué.
- Estados de componentes: todos diseñados, no solo el default.
- Assets exportables: íconos en SVG, imágenes con formatos y tamaños definidos.
- Anotaciones: notas sobre animaciones, transiciones, lógica condicional.

**Lo que desarrollo necesita saber:**
- ¿Este elemento es fijo o se adapta al contenido?
- ¿Qué pasa cuando el texto es más largo de lo esperado?
- ¿Cuál es el orden de tabulación?
- ¿Qué animación tiene esta transición? (ease, duration, delay)
- ¿De dónde vienen los datos? (estático, API, CMS)

## Agenda

### Mañana (3h)

**Bloque 1: Auto Layout a fondo (50 min)**
- Repaso rápido: dirección, gap, padding, alignment, resizing.
- Demo en vivo: construir un botón, un campo de formulario y un card con Auto Layout desde cero.
- Anidamiento: cuándo anidar y cuándo mantener plano.
- Ejercicio: tomar un componente del kit de clase 04 y reconstruirlo con Auto Layout correcto.

**Bloque 2: Constraints, grillas y responsive (45 min)**
- Constraints para elementos posicionados (overlays, íconos fijos, FABs).
- Grillas de layout: configuración para móvil, tablet y desktop.
- Demo: diseñar un layout que funcione en 3 breakpoints usando grillas y Auto Layout.
- Relación directa con CSS: Figma Auto Layout ≈ Flexbox, Figma Grid ≈ CSS Grid.

Descanso: 10 min

**Bloque 3: Variables y tokens (45 min)**
- Qué es un design token y por qué importa para consistencia y temas.
- Crear variables en Figma: color (primitivos + semánticos), tipografía, espaciado, radius, sombra.
- Naming conventions: `/` como separador, semántico sobre descriptivo.
- Demo: crear un tema light y un tema dark con las mismas variables semánticas.

**Bloque 4: Componentes con variantes (30 min)**
- Variantes: hierarchy, size, state, icon. Matriz de combinaciones.
- Component Properties: boolean, instance swap, text.
- Cuándo crear una variante vs. un componente separado.
- Atomic Design como modelo mental: átomos → moléculas → organismos.

### Tarde (3h)

**Bloque 5: Refactor del kit (75 min)**
- Tomar los componentes de clase 04 y convertirlos en componentes Figma con:
  - Auto Layout correcto (no posicionamiento manual).
  - Variantes para estados y configuraciones.
  - Variables/tokens aplicados (no colores hex sueltos).
  - Naming consistente.
- Priorizar: botones, inputs, cards, alertas, navbar.

Descanso: 10 min

**Bloque 6: Librería y estructura (40 min)**
- Organizar el archivo con la estructura de páginas recomendada.
- Crear página de tokens/styles con la paleta visual.
- Definir convenciones de naming para capas y componentes.
- Publicar componentes como librería interna del proyecto.

**Bloque 7: Handoff y revisión (40 min)**
- Preparar 1 pantalla para handoff: anotaciones, estados, responsive.
- Activar Dev Mode y verificar que la información es correcta y completa.
- Peer review: intercambiar archivos y evaluar con la pregunta "¿podría implementar esto sin preguntarte nada?"
- Feedback grupal: 3 hallazgos comunes.

## Trabajo independiente (1h)

- Limpiar el archivo Figma completo: renombrar capas anónimas, eliminar frames sueltos, organizar páginas.
- Verificar que todos los componentes usan variables/tokens (no valores hardcodeados).
- Escribir 1 página de guía del archivo: estructura de páginas, convenciones de naming, cómo agregar un componente nuevo, cómo colaborar sin romper nada.
- Probar el archivo en Dev Mode: ¿se ven los tokens correctos? ¿Las medidas son coherentes?

## Lecturas y recursos

### Obligatorias
- Documentación oficial de Figma: Auto Layout — https://help.figma.com/hc/en-us/articles/5731482952599-Using-auto-layout
- Documentación oficial de Figma: Variables — https://help.figma.com/hc/en-us/articles/15339657135383-Guide-to-variables-in-Figma

### Recomendadas
- Frost, B. *Atomic Design* — capítulos 1-2 (concepto de átomos a plantillas) — https://atomicdesign.bradfrost.com/
- Figma: Component Properties — https://help.figma.com/hc/en-us/articles/5579474826519-Create-and-use-component-properties
- Design Tokens W3C Community Group — https://www.w3.org/community/design-tokens/

### Herramientas
- Figma Dev Mode para inspección y handoff.
- Tokens Studio for Figma (plugin) para gestión avanzada de tokens.
- Figma Autoname (plugin) para renombrar capas automáticamente.

## Entregables del día

1. **Librería de componentes refactorizada** en Figma con Auto Layout, variantes y variables aplicadas.
2. **Sistema de tokens** documentado: color (primitivos + semánticos), tipografía, espaciado, radius, sombra.
3. **Guía del archivo** (1 página): estructura, convenciones, cómo colaborar.

## Checklist de calidad

- [ ] Todos los componentes usan Auto Layout (no posicionamiento manual).
- [ ] Los componentes se adaptan correctamente al cambiar contenido (texto más largo, sin imagen, etc.).
- [ ] No hay estilos duplicados ni colores hex sueltos — todo usa variables/tokens.
- [ ] Las variables tienen nombres semánticos consistentes (`color/primary`, no `blue-500` en el componente).
- [ ] La escala de espaciado es coherente (base 4px u 8px, sin valores arbitrarios).
- [ ] Las capas tienen nombres descriptivos (no "Frame 847", "Group 12").
- [ ] La estructura del archivo tiene páginas claras y organizadas.
- [ ] Al menos 1 pantalla está preparada para handoff con anotaciones.

## Notas para el instructor

- Esta clase es técnica y práctica. Minimizar teoría, maximizar tiempo en Figma.
- En Auto Layout, el error más común es no entender "Hug" vs. "Fill". Hacer una demo visual lado a lado.
- En variables, empezar con color (es lo más intuitivo) y luego espaciado. Tipografía puede ser más compleja — mantenerlo simple.
- En el refactor, muchos van a querer empezar de cero. Redirigir: "Refactorizar es más valioso que rehacer. En el mundo real, siempre heredás archivos ajenos."
- En handoff, hacer la prueba del "¿podría implementar esto sin preguntarte?" en vivo. Es revelador.
- Cerrar conectando con clase 6: "Hoy organizamos las piezas. La próxima clase las consolidamos en un sistema de UI coherente con documentación real."

