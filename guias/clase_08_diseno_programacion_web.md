# Clase 08 | Miércoles 25

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 8. Calidad básica de producto

## Objetivos de la sesión

- Aplicar accesibilidad práctica desde diseño: contraste, foco visible, navegación por teclado, labels, orden de lectura y alternativas textuales.
- Diseñar con performance en mente: peso de imágenes, tipografías, layout shifts, carga diferida y dependencias.
- Entender capacidades y límites de dispositivos: cámara, micrófono, sensores, red, energía y sus implicaciones de diseño.
- Diseñar con privacidad como principio: consentimiento, mínimos de recolección, transparencia.
- Diseñar experiencias con IA que mantengan control del usuario, transparencia sobre límites y mecanismos de corrección.
- Realizar una auditoría práctica del prototipo propio y aplicar correcciones.

## Conceptos clave

### Accesibilidad: por qué y para quién

La accesibilidad web (a11y) no es un extra ni un favor — es un requisito legal en muchos países (ADA en EE.UU., EN 301 549 en Europa, Ley 7600 en Costa Rica) y una decisión ética. El 15-20% de la población mundial tiene alguna discapacidad. Pero la accesibilidad beneficia a todos:

- **Discapacidad permanente**: ceguera, sordera, movilidad reducida.
- **Discapacidad temporal**: brazo roto, infección ocular, cirugía.
- **Discapacidad situacional**: sol en la pantalla, ambiente ruidoso, una mano ocupada con un bebé.

Diseñar accesible es diseñar robusto. Si funciona para alguien que navega con teclado, funciona mejor para todos.

### WCAG 2.2: los 4 principios

Las Web Content Accessibility Guidelines se organizan en 4 principios (POUR):

1. **Perceptible**: la información debe poder percibirse. Alternativas textuales para imágenes, subtítulos para video, contraste suficiente.
2. **Operable**: la interfaz debe poder operarse. Navegación por teclado, tiempo suficiente, sin contenido que cause convulsiones.
3. **Comprensible**: el contenido debe poder entenderse. Lenguaje claro, comportamiento predecible, ayuda para errores.
4. **Robusto**: el contenido debe funcionar con tecnologías asistivas. HTML semántico, ARIA cuando sea necesario, compatibilidad con lectores de pantalla.

Niveles de conformidad: A (mínimo), AA (estándar de la industria, el objetivo), AAA (ideal pero no siempre alcanzable).

### Contraste

El contraste es la diferencia de luminosidad entre el texto y su fondo. Sin contraste suficiente, el texto es ilegible para personas con baja visión, daltonismo o simplemente bajo sol directo.

**Requisitos WCAG AA:**
- Texto normal (< 18px o < 14px bold): ratio mínimo **4.5:1**.
- Texto grande (≥ 18px o ≥ 14px bold): ratio mínimo **3:1**.
- Elementos de UI (bordes de inputs, íconos funcionales): ratio mínimo **3:1** contra el fondo.

**Herramientas para verificar:**
- Stark (plugin Figma): verifica contraste en tiempo real.
- WebAIM Contrast Checker: https://webaim.org/resources/contrastchecker/
- Chrome DevTools: inspeccionar elemento → pestaña de accesibilidad.

**Errores comunes:**
- Texto gris claro sobre fondo blanco (estéticamente "elegante", funcionalmente ilegible).
- Placeholder text con contraste insuficiente (el placeholder no reemplaza al label).
- Texto sobre imágenes sin overlay oscuro.
- Botones disabled con contraste tan bajo que no se ven.

### Foco visible

Cuando un usuario navega con teclado (Tab para avanzar, Shift+Tab para retroceder, Enter para activar, Escape para cerrar), necesita ver claramente qué elemento está seleccionado. Eso es el indicador de foco.

**Requisitos:**
- Todo elemento interactivo (links, botones, inputs, selects, checkboxes) debe tener un indicador de foco visible.
- El indicador debe tener contraste suficiente (3:1 contra el fondo adyacente).
- No usar `outline: none` sin reemplazo. Si el outline por defecto es feo, diseñar uno mejor — nunca eliminarlo.

**Diseño de foco recomendado:**
- Outline de 2-3px con color de alto contraste (azul, negro).
- Offset de 2px para que no se pegue al elemento.
- Consistente en todo el sitio.
- Ejemplo CSS: `outline: 2px solid #005FCC; outline-offset: 2px;`

### Navegación por teclado

Todo lo que se puede hacer con mouse debe poder hacerse con teclado. Esto incluye:

- **Tab**: mover el foco al siguiente elemento interactivo.
- **Shift+Tab**: mover el foco al elemento anterior.
- **Enter/Space**: activar botones, links, checkboxes.
- **Escape**: cerrar modales, dropdowns, tooltips.
- **Flechas**: navegar dentro de componentes (tabs, radio groups, menús).

**Orden de tabulación**: debe seguir el orden visual de lectura (izquierda a derecha, arriba a abajo en LTR). Si el orden de Tab no coincide con el orden visual, hay un problema de diseño o de código.

**Trampas de teclado**: el foco no debe quedar "atrapado" en un elemento sin forma de salir. Excepción: modales — el foco debe quedar dentro del modal hasta que se cierre.

### Labels y alternativas textuales

- **Labels de formulario**: cada input debe tener un `<label>` asociado. El placeholder NO es un label (desaparece al escribir, no es leído consistentemente por lectores de pantalla).
- **Alt text en imágenes**: 
  - Imágenes informativas: describir qué muestra. "Gráfico de barras mostrando ventas por trimestre, Q3 es el más alto."
  - Imágenes decorativas: `alt=""` (vacío, no ausente). El lector de pantalla las ignora.
  - Imágenes con texto: el alt debe contener el texto de la imagen.
- **Íconos funcionales**: si un ícono es el único contenido de un botón (ej: ícono de papelera para eliminar), necesita un `aria-label="Eliminar"`.
- **Links**: el texto del link debe describir el destino. "Leer más sobre accesibilidad" > "Clic aquí" > "Más".

### Orden de lectura

Los lectores de pantalla leen el contenido en el orden del DOM (código HTML), no en el orden visual. Si el diseño reorganiza elementos visualmente (con CSS Grid o Flexbox) pero el orden del DOM es diferente, la experiencia para usuarios de lector de pantalla será confusa.

Implicación para diseño: al definir layouts, considerar que el orden visual debe coincidir con el orden lógico de lectura. Si no coincide, documentarlo en la spec de handoff.

### Performance desde diseño

El diseñador no controla el código, pero sí toma decisiones que impactan directamente en el rendimiento:

**Imágenes (50-70% del peso de una página):**
- **Formato**: WebP reduce 30-50% vs. PNG/JPEG. AVIF reduce aún más pero tiene menos soporte. SVG para íconos y gráficos vectoriales.
- **Tamaño**: no servir una imagen de 4000px para un contenedor de 400px. Definir tamaños por breakpoint.
- **Lazy loading**: imágenes fuera del viewport inicial se cargan cuando el usuario hace scroll. Reducción significativa del tiempo de carga inicial.
- **Placeholder**: mientras carga, mostrar un color sólido, blur o skeleton. No dejar espacio vacío que cause layout shift.

**Tipografías (20-100KB por peso):**
- Cada peso de fuente (regular, bold, italic) es un archivo separado (~20-50KB).
- Máximo 2-3 pesos por fuente. Si usás Montserrat en 200, 400, 500, 600, 700, 900 — son 6 archivos × ~30KB = ~180KB solo en fuentes.
- `font-display: swap`: muestra texto con fuente del sistema mientras carga la custom. Evita "flash of invisible text" (FOIT).
- Considerar fuentes variables: un solo archivo con todos los pesos.

**Layout shifts (CLS — Cumulative Layout Shift):**
- Cuando un elemento cambia de posición después de que la página se renderizó. Ejemplo: una imagen sin dimensiones definidas que "empuja" el contenido al cargar.
- Causa: imágenes sin width/height, anuncios que se insertan, fuentes que cambian el tamaño del texto.
- Solución desde diseño: definir dimensiones exactas para imágenes, reservar espacio para contenido dinámico, usar skeleton screens.

**Dependencias y complejidad:**
- Cada carousel, animación compleja, mapa interactivo o video embebido agrega peso y complejidad.
- Pregunta antes de diseñar algo pesado: "¿Esto aporta valor suficiente para justificar su costo?"
- Un carousel de 5 imágenes pesa más y tiene más bugs que una sola imagen bien elegida.

### Capacidades del dispositivo

No todos los dispositivos pueden lo mismo. Diseñar considerando:

- **Cámara**: escaneo de QR, foto de documento, AR. Pedir permiso explícito. Fallback si no hay cámara o el usuario niega permiso.
- **Micrófono**: búsqueda por voz, notas de audio. Indicador claro de que está grabando. Fallback a texto.
- **Geolocalización**: "Tiendas cerca de mí". Pedir permiso con contexto ("Para mostrarte tiendas cercanas, necesitamos tu ubicación"). Fallback: búsqueda manual por dirección.
- **Sensores**: acelerómetro (shake to undo), giroscopio (AR), biometría (Face ID, huella). No depender de ellos como única vía.
- **Red**: diseñar para conexiones lentas o intermitentes. Offline-first cuando sea posible. Indicar estado de conexión.
- **Batería**: animaciones pesadas y GPS constante consumen batería. Ofrecer modo de bajo consumo si aplica.
- **Almacenamiento**: PWAs y apps que guardan datos localmente. Respetar límites y permitir limpiar.

Principio: **pedir permiso con contexto, ofrecer fallback siempre, no depender de una sola capacidad**.

### Privacidad como diseño

La privacidad no es un checkbox legal — es una decisión de diseño que afecta la confianza del usuario.

**Principios de Privacy by Design:**
1. **Mínimo necesario**: no pedir datos que no necesitás. Si no usás la fecha de nacimiento, no la pidas.
2. **Consentimiento informado**: explicar qué datos se recolectan, para qué y con quién se comparten. En lenguaje humano, no legal.
3. **Control del usuario**: permitir ver, editar y eliminar sus datos. Derecho al olvido.
4. **Transparencia**: si usás cookies, tracking o IA, decirlo claramente.
5. **Seguridad visual**: no mostrar datos sensibles por defecto (contraseñas, tarjetas). Usar máscaras y toggles.
6. **Dark patterns a evitar**: 
   - Pre-seleccionar casillas de marketing.
   - Hacer que "Aceptar todo" sea más visible que "Configurar".
   - Dificultar la eliminación de cuenta.
   - Usar lenguaje confuso para obtener consentimiento.

### Diseño con IA: control y confianza

La IA en productos es una herramienta poderosa pero imperfecta. Diseñar con IA requiere honestidad sobre sus límites.

**Principios de diseño con IA:**

1. **Explicar qué hace**: "Este resumen fue generado por IA." No ocultar que es IA.
2. **Mostrar confianza del modelo**: si es posible, indicar nivel de certeza. "Creemos que esto es spam (95% de confianza)."
3. **Permitir corrección**: el usuario siempre puede editar, rechazar o reportar un resultado de IA.
4. **No ocultar incertidumbre**: si la IA no sabe, decirlo. "No tengo suficiente información para responder esto."
5. **Degradación elegante**: si la IA falla, el producto debe seguir funcionando. La IA es mejora, no dependencia.
6. **Sesgo y equidad**: la IA puede amplificar sesgos de los datos de entrenamiento. Diseñar mecanismos de revisión y feedback.

**Patrones de UI para IA:**
- **Sugerencia editable**: texto generado que el usuario puede modificar antes de confirmar.
- **Clasificación con override**: la IA clasifica automáticamente, pero el usuario puede cambiar la clasificación.
- **Explicación bajo demanda**: "¿Por qué me recomiendas esto?" con respuesta clara.
- **Feedback loop**: "¿Fue útil esta respuesta?" para mejorar el modelo.
- **Indicador de IA**: badge o label que identifica contenido generado por IA.

## Agenda

### Mañana (3h)

**Bloque 1: Accesibilidad práctica (55 min)**
- Por qué accesibilidad: legal, ético y práctico. Discapacidad permanente, temporal y situacional.
- WCAG 2.2: los 4 principios (POUR) y nivel AA como objetivo.
- Contraste: requisitos, herramientas, errores comunes. Demo con Stark en Figma.
- Foco visible: requisitos, diseño recomendado, por qué nunca `outline: none`.
- Navegación por teclado: Tab, Enter, Escape, flechas. Orden de tabulación.
- Labels, alt text, íconos funcionales, orden de lectura.

**Bloque 2: Performance desde diseño (40 min)**
- Imágenes: formato (WebP/AVIF/SVG), tamaño, lazy loading, placeholders.
- Tipografías: pesos, font-display, fuentes variables.
- Layout shifts: causas y soluciones desde diseño.
- Dependencias: el costo real de un carousel, un mapa, un video.
- Demo: analizar un sitio en PageSpeed Insights y conectar resultados con decisiones de diseño.

Descanso: 10 min

**Bloque 3: Capacidades, privacidad e IA (45 min)**
- Capacidades del dispositivo: cámara, micrófono, geo, sensores, red, batería. Permisos y fallbacks.
- Privacidad como diseño: mínimo necesario, consentimiento, control, dark patterns a evitar.
- Diseño con IA: explicar, mostrar confianza, permitir corrección, no ocultar incertidumbre.
- Patrones de UI para IA: sugerencia editable, clasificación con override, explicación bajo demanda.

**Bloque 4: Preparación para auditoría (30 min)**
- Formato de reporte de hallazgos: hallazgo, categoría (a11y/performance/privacidad/IA), severidad, pantalla, ajuste propuesto.
- Checklist de auditoría: qué revisar en cada categoría.
- Distribución de la auditoría de la tarde.

### Tarde (3h)

**Bloque 5: Auditoría de accesibilidad (60 min)**
- Cada estudiante audita su propio prototipo:
  - Contraste de todos los textos y elementos de UI (usar Stark).
  - Foco visible en todos los elementos interactivos.
  - Labels en todos los inputs (no solo placeholders).
  - Orden de tabulación lógico en formularios.
  - Alt text previsto para imágenes.
  - Mensajes de error que no dependen solo de color (ícono + texto).
- Documentar hallazgos en el formato de reporte.

Descanso: 10 min

**Bloque 6: Auditoría de performance y privacidad (40 min)**
- Checklist de performance:
  - ¿Las imágenes tienen formato y tamaño definidos?
  - ¿Cuántos pesos de fuente se usan?
  - ¿Hay componentes pesados que podrían simplificarse?
  - ¿Se definieron dimensiones para evitar layout shifts?
- Checklist de privacidad:
  - ¿Se piden solo los datos necesarios?
  - ¿El consentimiento es claro y no manipulativo?
  - ¿Los datos sensibles están protegidos visualmente?
- Documentar hallazgos adicionales.

**Bloque 7: Correcciones y revisión (50 min)**
- Aplicar correcciones en Figma basadas en los hallazgos de la auditoría.
- Priorizar: severidad 3-4 primero, luego 2, luego 1.
- Peer review: intercambiar reportes y verificar que las correcciones se aplicaron.
- Si hay propuesta de IA en el proyecto: verificar que cumple los principios (transparencia, control, corrección, honestidad).
- Presentación rápida: 2 minutos por persona, hallazgo más importante y corrección aplicada.

## Trabajo independiente (1h)

- Completar el reporte de hallazgos (1-2 páginas): cada hallazgo con categoría, severidad, pantalla afectada y ajuste propuesto. Mínimo 8 hallazgos.
- Aplicar todas las correcciones de severidad 3-4 en Figma. Documentar las de severidad 1-2 como deuda de diseño.
- Si el proyecto incluye IA: escribir los textos de transparencia ("Generado por IA", "¿Fue útil?", "Puedo equivocarme") y diseñar los componentes correspondientes.
- Verificar que el prototipo actualizado (versión 2) refleja las correcciones de accesibilidad.

## Lecturas y recursos

### Obligatorias
- W3C. *Web Content Accessibility Guidelines (WCAG) 2.2* — resumen ejecutivo — https://www.w3.org/TR/WCAG22/
- WebAIM: "Introduction to Web Accessibility" — https://webaim.org/intro/

### Recomendadas
- MDN: "Web Performance" — https://developer.mozilla.org/en-US/docs/Web/Performance
- Google: "Web Vitals" (LCP, FID, CLS) — https://web.dev/vitals/
- Smashing Magazine: "Designing for Accessibility" — https://www.smashingmagazine.com/2021/03/complete-guide-accessible-front-end-components/
- Google PAIR: "People + AI Guidebook" — https://pair.withgoogle.com/guidebook/

### Herramientas
- Stark (plugin Figma): contraste y simulación de daltonismo.
- WAVE Web Accessibility Evaluator — https://wave.webaim.org/
- PageSpeed Insights — https://pagespeed.web.dev/
- Lighthouse (Chrome DevTools): auditoría automática de a11y y performance.
- axe DevTools: auditoría de accesibilidad en el browser.

## Entregables del día

1. **Reporte de auditoría** (borrador 1): hallazgos de accesibilidad, performance y privacidad con severidad y ajuste propuesto (mínimo 8 hallazgos).
2. **Prototipo corregido** (versión 2): correcciones de severidad 3-4 aplicadas en Figma.
3. **Componentes de IA** (si aplica): textos de transparencia y mecanismos de corrección diseñados.

## Checklist de calidad

- [ ] Todos los textos cumplen ratio de contraste mínimo (4.5:1 normal, 3:1 grande).
- [ ] El foco es visible en todos los elementos interactivos con contraste suficiente.
- [ ] Todos los inputs tienen label visible asociado (no solo placeholder).
- [ ] Los mensajes de error no dependen exclusivamente de color (usan ícono + texto).
- [ ] Las imágenes tienen formato optimizado (WebP/SVG) y tamaño definido por breakpoint.
- [ ] Se usan máximo 3-4 pesos de fuente en todo el proyecto.
- [ ] No se piden datos innecesarios en formularios.
- [ ] El consentimiento de datos es claro, no manipulativo (sin dark patterns).
- [ ] Si hay IA: se indica claramente qué es generado por IA y se permite corrección.
- [ ] El reporte tiene al menos 8 hallazgos con severidad asignada.

## Notas para el instructor

- Esta clase es de "verificación de calidad". El tono cambia de "construir" a "evaluar y mejorar". Algunos estudiantes pueden frustrarse al encontrar muchos problemas en su trabajo — normalizar: "Encontrar problemas es el objetivo. Un diseñador que no encuentra problemas en su propio trabajo no está mirando bien."
- En accesibilidad, la demo con Stark es muy impactante. Mostrar cómo un diseño "bonito" puede ser ilegible para alguien con baja visión o daltonismo.
- En performance, PageSpeed Insights es revelador. Analizar un sitio conocido (Amazon, gobierno local, universidad) y mostrar cómo las decisiones de diseño afectan los números.
- En privacidad, mostrar ejemplos de dark patterns reales (cookie banners manipulativos, flujos de eliminación de cuenta de Facebook/Amazon). Genera discusión.
- En IA, ser pragmáticos. No todos los proyectos tendrán IA — para los que no, el ejercicio es identificar dónde podría agregarse y dónde no debería.
- Cerrar conectando con clase 9: "Hoy verificamos calidad. Mañana pensamos en dónde vive esto: plataformas, contenido y arquitectura técnica."

