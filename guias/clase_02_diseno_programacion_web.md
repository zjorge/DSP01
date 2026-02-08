# Clase 02 | Martes 10

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 2. Fundamentos que el diseñador debe dominar

## Objetivos de la sesión

- Usar HTML semántico como herramienta de diseño: jerarquía, landmarks, formularios accesibles.
- Aplicar CSS como modelo mental (caja → flujo → flex → grid) para tomar decisiones de layout y responsive.
- Entender JavaScript mínimo para diseño: eventos, estados, validación y JSON como contrato de datos.
- Diseñar con contexto: responsive real (breakpoints definidos) + casos especiales (plegables y voz).
- Aterrizar estos fundamentos en el proyecto del curso (grilla + estructura semántica de una pantalla clave).

## Conceptos clave

### HTML semántico

- Landmarks: `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`. Ayudan a SEO y accesibilidad (lectores de pantalla saltan por landmarks).
- Headings: orden lógico h1→h6. Nunca saltar de h1 a h4. Un h1 por página (contexto principal), subsecciones con h2/h3.
- Listas: `ul/ol` para colecciones; `dl` para pares término/definición.
- Formularios: `label` asociado, `input type` correcto (email, number, tel), `fieldset/legend` para grupos, `aria-invalid` y `aria-describedby` para mensajes de error.
- Texto: usar elementos nativos (`strong`, `em`, `code`, `blockquote`) antes de inventar clases.

### CSS como modelo mental

- Caja: contenido + padding + border + margin; `box-sizing: border-box` como base.
- Flujo normal: bloque vs inline; por qué `display` importa para reflow.
- Flex: eje principal/secundario, `gap`, `wrap`, `align/justify`. Útil para barras, cards, layouts lineales.
- Grid: tracks, fracciones, `minmax`, `auto-fit/auto-fill`, `gap`. Útil para rejillas adaptables.
- Escalas: espaciamiento y tipografía coherente (8px/4px; steps de font-size). Tokens de diseño.

### Responsive en serio

- Breakpoints definidos por contenido (no por dispositivo). Referencias: ~480, ~768, ~1024, ~1280; ajustarlos según dónde se rompe tu layout.
- Estrategia mobile-first vs desktop-first. Ventaja de mobile-first: fuerza a priorizar.
- Reflow: 3 cols → 2 → 1; navbar a hamburger; tablas a listas.
- Imágenes: tamaños adaptativos (`srcset`, `sizes`), WebP/AVIF, lazy loading.

### JavaScript mínimo para diseño

- Eventos: click, input, change, submit, focus/blur.
- Estados: loading, success, error; flags comunes (`isLoading`, `hasError`).
- Validación: nativa (required, pattern) + mensajes claros y accesibles.
- JSON: contrato front-back. Claves claras, tipos conocidos. Ej.: `{ "name": "", "email": "", "plan": "pro" }`.

### Contextos especiales

- Plegables: continuidad al cambiar postura; “bisagra” en el medio; safe areas; decidir qué pane va en cada pantalla.
- Voz: intents simples, confirmación explícita, errores con fallback. Diseño de diálogos breves.

## Agenda

### Mañana (3h)

**Bloque 1: HTML semántico (45 min)**
- Landmarks y headings como esqueleto de la página.
- Formularios accesibles: labels, type correcto, mensajes de error.
- Ejemplo guiado: convertir un mockup en estructura semántica.

**Bloque 2: CSS mental model (50 min)**
- Caja y flujo; por qué `display` cambia todo.
- Flex vs Grid: cuándo usar cada uno. Ejemplos rápidos con casos típicos (navbar, cards, layout de producto).
- Escalas de espacio y tipo: cómo no inventar medidas al azar.

Descanso: 10 min

**Bloque 3: Responsive y assets (45 min)**
- Breakpoints por contenido. Ejercicio: detectar dónde se rompe un layout.
- Imágenes y tipografías: peso, formatos, carga diferida.
- Micro-ejemplos de reflow (3→2→1), nav a hamburger.

**Bloque 4: JS mínimo para diseño (30 min)**
- Eventos y estados (loading/error/success).
- Validación nativa + mensajes accesibles.
- JSON como contrato; naming claro.

### Tarde (3h)

**Bloque 5: Aplicación al proyecto (75 min)**
- Mapear una pantalla clave del proyecto a HTML semántico (paper/figma → estructura real).
- Definir breakpoints y grilla base (móvil, tablet, escritorio) con reglas escritas.
- Redactar tokens básicos: espaciado, tipografía, border radius.

Descanso: 10 min

**Bloque 6: Casos especiales (40 min)**
- Plegables: continuidad, bisagra, dual screen, safe areas.
- Voz: intents, confirmación, errores y fallback.

**Bloque 7: Taller guiado (50 min)**
- Ajustar la pantalla del proyecto con grilla + breakpoints + estados (loading/error/empty) documentados.
- Peer review en parejas: checklist de headings, labels, breakpoints escritos.

## Trabajo independiente (1h)

- Documentar grilla y breakpoints del proyecto en una página de Figma (móvil, tablet, escritorio) con reglas de uso.
- Redactar estructura semántica de la pantalla clave (landmarks + headings + formularios con labels y mensajes).
- Buscar 2 ejemplos reales de plegables: captura + nota de cómo resuelven continuidad y postura.
- Escribir un mini guion de voz para una tarea del proyecto: intent, confirmación, error y fallback.

## Lecturas y recursos

### Obligatorias
- MDN Web Docs: HTML semántico y estructuras básicas — https://developer.mozilla.org/es/docs/Learn/HTML
- MDN Web Docs: Flexbox — https://developer.mozilla.org/es/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox
- MDN Web Docs: Grid — https://developer.mozilla.org/es/docs/Web/CSS/CSS_grid_layout
- W3C WAI: Conceptos básicos de accesibilidad — https://www.w3.org/WAI/fundamentals/accessibility-intro/

### Recomendadas
- Niederst Robbins, J. *Aprender diseño web* (HTML/CSS intro).
- Resources sobre plegables (Foldables): https://learn.microsoft.com/en-us/dual-screen/web/
- Voz (Voice UX) guía breve: https://developers.google.com/assistant/design

### Herramientas
- Stark (contraste) y Able (accesibilidad) en Figma.
- Responsively App o devtools para probar breakpoints.
- Lighthouse/PageSpeed para peso y performance.

## Entregables del día

1. **Grilla y breakpoints del proyecto** (móvil, tablet, escritorio) con reglas escritas.
2. **Estructura semántica** propuesta para 1 pantalla clave (landmarks, headings, formularios con labels y mensajes de error).
3. **Notas de casos especiales**: 2 ejemplos de plegables + mini guion de voz para una tarea.

## Checklist de calidad

- [ ] Los headings siguen un orden lógico (sin saltos arbitrarios).
- [ ] Hay un `main` y landmarks claros; `nav` se usa solo para navegación real.
- [ ] Formularios con `label` asociado y mensajes de error previstos (texto + asociación `aria-describedby`).
- [ ] Breakpoints escritos (ancho + qué cambia) y coherentes con el contenido.
- [ ] Grilla documentada (columnas, gutter, margin, comportamiento por breakpoint).
- [ ] Imágenes/recursos con formato y peso considerado (WebP/AVIF donde aplique, lazy fuera del fold).
- [ ] Estados mínimos cubiertos: loading, empty, error, success.

## Notas para el instructor

- Mantener el ritmo alto, como en clase 01: muchos ejemplos cortos + aplicación inmediata en el proyecto.
- En HTML semántico, insistir en landmarks y headings. Hacer una demo en vivo en devtools mostrando regiones y outline.
- En CSS, contrastar flex vs grid con ejemplos muy breves. Hacer al menos un ejercicio de reflow 3→2→1.
- En JS, no enseñar a programar: solo mostrar eventos/estados/validación y por qué importan para diseño.
- En casos especiales, ser breves: 15-20 min plegables + 15-20 min voz, solo principios accionables.
- Revisar que todos salgan con breakpoints escritos y una estructura semántica clara para su pantalla clave.
