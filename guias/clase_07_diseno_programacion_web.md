# Clase 07 | Martes 24

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 7. Prototipado y comunicación con desarrollo

## Objetivos de la sesión

- Entender los niveles de fidelidad de un prototipo y elegir el correcto según el objetivo (explorar, validar, comunicar).
- Prototipar flujos completos incluyendo estados de contenido: vacío, cargando, error, éxito, datos largos.
- Preparar especificaciones de handoff que permitan a desarrollo implementar sin adivinar.
- Aplicar las 10 heurísticas de Nielsen como herramienta de evaluación rápida de prototipos.
- Escribir microcopy efectivo para errores, confirmaciones, placeholders y estados vacíos.
- Explorar diseño por contexto: plegables, voz y AR como ejercicios de claridad conceptual.

## Conceptos clave

### Prototipos: qué son y para qué sirven

Un prototipo es una simulación del producto que permite probar ideas antes de construirlas. No es el producto — es una pregunta materializada: "¿esto funciona?"

**Lo que un prototipo puede responder:**
- ¿El usuario entiende qué hacer? (claridad)
- ¿Puede completar la tarea? (eficacia)
- ¿El flujo tiene sentido? (lógica)
- ¿Falta algún estado o paso? (completitud)
- ¿Hay fricción innecesaria? (eficiencia)

**Lo que un prototipo NO puede responder:**
- ¿El producto va a tener éxito? (eso requiere datos reales)
- ¿La tecnología lo soporta? (eso requiere desarrollo)
- ¿El rendimiento será bueno? (eso requiere implementación)

### Niveles de fidelidad

| Nivel | Qué incluye | Para qué sirve | Herramienta |
|-------|-------------|-----------------|-------------|
| Baja | Cajas, texto, flujo básico | Explorar estructura y flujo | Papel, FigJam, Whimsical |
| Media | Componentes reales, contenido cercano al real, sin estilo final | Validar flujo y jerarquía con usuarios o equipo | Figma (wireframes interactivos) |
| Alta | UI final, microinteracciones, contenido real | Comunicar a desarrollo, testear con usuarios, presentar a stakeholders | Figma prototyping, Framer, ProtoPie |

Regla: **la fidelidad debe coincidir con la pregunta que querés responder**. Si querés saber si el flujo tiene sentido, un prototipo de baja fidelidad alcanza. Si querés saber si el microcopy es claro, necesitás media-alta. Si querés impresionar a un stakeholder, alta.

Error común: hacer prototipos de alta fidelidad demasiado pronto. Se invierte tiempo en detalles visuales antes de validar que la estructura funciona.

### Prototipos en Figma

Figma permite crear prototipos interactivos conectando frames con interacciones:

**Tipos de interacción:**
- **On click/tap**: la más común. Navegar a otra pantalla, abrir modal, cambiar estado.
- **On hover**: mostrar tooltip, cambiar estado de botón (solo desktop).
- **On drag**: arrastrar elementos (sliders, reordenar).
- **After delay**: transiciones automáticas (splash screen, auto-advance).
- **While pressing**: mantener presionado para acción (eliminar, grabar).

**Transiciones:**
- **Instant**: sin animación. Para cambios de estado rápidos.
- **Dissolve**: fade entre pantallas. La más segura y universal.
- **Smart Animate**: anima diferencias entre frames con el mismo nombre de capa. Poderoso pero requiere naming consistente.
- **Move in/out**: slide desde un borde. Para drawers, sheets, navegación.
- **Push**: una pantalla empuja a la otra. Para navegación horizontal (tabs, carousels).

**Overlays:**
- Modales, dropdowns, tooltips, bottom sheets.
- Se superponen a la pantalla actual sin reemplazarla.
- Configurar: posición, fondo oscurecido, cerrar al hacer clic fuera.

### Prototipar estados de contenido

El error más grave en prototipado es mostrar solo el "happy path" — todo funciona, hay datos perfectos, nada falla. En la realidad, el 40-60% de la experiencia son estados no ideales.

**Estados que debe incluir el prototipo:**

1. **Vacío (empty state)**: primera vez que el usuario llega. Sin datos. Debe comunicar qué es esto, qué puede hacer, y cómo empezar. Ejemplo: "Aún no tenés proyectos. Crear el primero →".
2. **Cargando (loading)**: skeleton screens > spinners. Mostrar la estructura de lo que viene reduce la percepción de espera. Para acciones largas: barra de progreso con porcentaje.
3. **Error**: el estado más ignorado y el más importante. Tipos:
   - Error de validación: campo específico, mensaje debajo, cómo corregir.
   - Error de servidor: "Algo salió mal. Intentá de nuevo." + botón de retry.
   - Error de red: "Sin conexión. Los cambios se guardarán cuando vuelvas a conectarte."
   - Error de permisos: "No tenés acceso a esto. Contactá al administrador."
4. **Éxito**: confirmación clara + próximo paso. "Pedido confirmado. Te enviamos un email con los detalles. Ver mis pedidos →".
5. **Datos parciales**: solo algunos campos llenos, perfil incompleto, lista con 1 ítem.
6. **Datos extremos**: título de 200 caracteres, lista de 500 ítems, imagen muy alta o muy ancha.

### Spec de handoff

La especificación de handoff es el documento (o conjunto de anotaciones) que le dice a desarrollo exactamente qué construir. Un buen handoff elimina reuniones innecesarias.

**Qué incluir en una spec:**

1. **Medidas y espaciados**: Figma Dev Mode los muestra automáticamente si el archivo está limpio. Pero verificar que los valores coincidan con los tokens del sistema.
2. **Tokens utilizados**: no "este azul" sino `color/primary/500`. No "16px de padding" sino `space/4`.
3. **Comportamiento responsive**: 
   - Qué cambia en cada breakpoint (columnas, visibilidad, orden).
   - Reglas de reflow: "3 columnas en desktop → 2 en tablet → 1 en móvil".
   - Elementos que desaparecen o cambian de posición.
4. **Estados de componentes**: todos los estados diseñados, no solo el default. Desarrollo necesita saber qué pasa en hover, focus, error, loading, disabled.
5. **Interacciones y transiciones**: qué pasa al hacer clic, cuánto dura la animación, qué easing usa.
6. **Microcopy**: texto exacto de labels, placeholders, mensajes de error, confirmaciones, tooltips. No "algo como..." sino el texto final.
7. **Assets**: íconos en SVG, imágenes con formato y tamaño definidos, fuentes.
8. **Lógica condicional**: "Si el usuario no tiene foto de perfil, mostrar iniciales. Si no tiene nombre, mostrar email."
9. **Orden de tabulación**: en qué orden se navega con Tab. Especialmente importante en formularios.
10. **Criterios de aceptación**: Dado/Cuando/Entonces para los flujos principales.

**Lo que NO incluir:**
- Cómo implementarlo técnicamente (eso lo decide desarrollo).
- Detalles de backend o base de datos (a menos que afecten la UI directamente).
- Opiniones sin fundamento ("creo que quedaría mejor si...").

### Heurísticas de Nielsen

Las 10 heurísticas de usabilidad de Jakob Nielsen son una herramienta rápida para evaluar interfaces. No reemplazan pruebas con usuarios, pero detectan problemas evidentes.

1. **Visibilidad del estado del sistema**: ¿el usuario sabe qué está pasando? Loading indicators, progress bars, confirmaciones.
2. **Coincidencia con el mundo real**: ¿el lenguaje es familiar? ¿Los conceptos son reconocibles? Usar palabras del usuario, no jerga técnica.
3. **Control y libertad del usuario**: ¿puede deshacer? ¿Puede volver atrás? ¿Hay salida de emergencia? Undo, cancel, back.
4. **Consistencia y estándares**: ¿los mismos elementos se comportan igual en todo el sitio? ¿Se siguen convenciones de la plataforma?
5. **Prevención de errores**: ¿el diseño evita que el usuario cometa errores? Confirmaciones antes de acciones destructivas, validación en tiempo real.
6. **Reconocimiento sobre recuerdo**: ¿la información necesaria está visible? ¿O el usuario tiene que recordar algo de una pantalla anterior?
7. **Flexibilidad y eficiencia**: ¿hay atajos para usuarios expertos? ¿Se puede personalizar?
8. **Diseño estético y minimalista**: ¿hay información irrelevante compitiendo con la relevante? Cada elemento extra reduce la visibilidad de los demás.
9. **Ayuda al usuario a reconocer, diagnosticar y recuperarse de errores**: ¿los mensajes de error son claros? ¿Dicen qué pasó y cómo arreglarlo?
10. **Ayuda y documentación**: ¿hay ayuda contextual? ¿Tooltips, FAQ, onboarding?

**Formato de evaluación heurística:**
| # | Heurística violada | Pantalla | Descripción del problema | Severidad (0-4) | Recomendación |
|---|-------------------|----------|-------------------------|-----------------|---------------|

Severidad: 0 = no es problema, 1 = cosmético, 2 = menor, 3 = mayor, 4 = catastrófico.

### Microcopy

Microcopy es el texto pequeño de la interfaz que guía al usuario: labels, placeholders, mensajes de error, confirmaciones, tooltips, botones, estados vacíos. Es diseño, no decoración.

**Principios de buen microcopy:**
- **Claro antes que creativo**: "Guardar cambios" > "¡Listo!" > "Persistir modificaciones".
- **Específico**: "Ingresá un email válido (ejemplo: nombre@dominio.com)" > "Error en el campo".
- **Orientado a la acción**: "Crear cuenta" > "Enviar" > "Submit".
- **Empático en errores**: "No encontramos resultados para 'xyz'. Probá con otros términos." > "0 resultados".
- **Breve**: cada palabra extra es fricción. Si podés decirlo en 5 palabras, no uses 15.
- **Consistente**: si en un lugar decís "Cancelar", no digas "Descartar" en otro para la misma acción.

**Microcopy por contexto:**
- **Placeholder**: ejemplo del formato esperado, no repetición del label. "nombre@dominio.com", no "Ingresá tu email".
- **Helper text**: información adicional antes de que haya error. "Mínimo 8 caracteres, al menos una mayúscula."
- **Error**: qué salió mal + cómo arreglarlo. "La contraseña debe tener al menos 8 caracteres."
- **Éxito**: confirmación + próximo paso. "Cuenta creada. Revisá tu email para verificar."
- **Empty state**: qué es esto + qué hacer. "Aún no tenés favoritos. Explorá productos y guardá los que te gusten."
- **Loading**: solo si tarda más de 2-3 segundos. "Procesando tu pedido..." con indicador visual.

### Diseño por contexto: plegables, voz y AR

Diseñar para contextos no convencionales es un ejercicio de claridad. Si tu diseño funciona en un plegable, en voz y en AR, probablemente funciona bien en cualquier contexto.

**Plegables (foldables):**
- Dos pantallas físicas con una bisagra en el medio. El contenido no debe quedar cortado por la bisagra.
- Posturas: cerrado (una pantalla), abierto plano (pantalla grande), semi-abierto (como laptop).
- Continuidad: si el usuario abre el dispositivo, la tarea debe continuar sin perder estado.
- Oportunidad: usar la segunda pantalla para contenido complementario (lista + detalle, mapa + info).

**Voz:**
- Sin pantalla (o pantalla secundaria). Todo se comunica con audio.
- Turnos cortos: sistema habla → usuario responde → sistema confirma.
- Confirmación explícita antes de acciones irreversibles.
- Fallback: "No entendí. ¿Podés repetirlo?" o "Te muestro opciones en pantalla."

**AR (Realidad Aumentada):**
- Capas de información sobre el mundo real a través de la cámara.
- Gestos: tap en objeto, arrastrar, pellizcar para escalar.
- Información contextual: apuntar a un producto y ver precio, reviews, disponibilidad.
- Límites: batería, procesamiento, precisión del tracking, iluminación.
- Principio: la AR debe agregar valor que la pantalla sola no puede dar. Si la misma info funciona mejor en una lista, no uses AR.

## Agenda

### Mañana (3h)

**Bloque 1: Prototipos — concepto y fidelidad (40 min)**
- Qué es un prototipo y qué preguntas puede (y no puede) responder.
- Niveles de fidelidad: baja, media, alta. Cuándo usar cada uno.
- Prototipos en Figma: interacciones, transiciones, overlays, Smart Animate.
- Error común: alta fidelidad demasiado pronto.

**Bloque 2: Estados de contenido (45 min)**
- Los 6 estados que todo prototipo debe cubrir: vacío, cargando, error, éxito, parcial, extremo.
- Demo: prototipar un flujo con happy path + error + empty state en Figma.
- Ejercicio rápido: identificar estados faltantes en un prototipo de ejemplo.

Descanso: 10 min

**Bloque 3: Spec de handoff (45 min)**
- Los 10 elementos de una spec completa: medidas, tokens, responsive, estados, interacciones, microcopy, assets, lógica, tabulación, criterios.
- Demo: preparar una pantalla para handoff en Figma Dev Mode.
- Qué incluir y qué NO incluir. La línea entre diseño y desarrollo.

**Bloque 4: Heurísticas y microcopy (40 min)**
- Las 10 heurísticas de Nielsen: repaso rápido con ejemplos visuales.
- Formato de evaluación heurística: tabla con severidad.
- Microcopy: principios, ejemplos por contexto (placeholder, error, éxito, empty).
- Ejercicio: reescribir 5 mensajes de error malos → buenos.

### Tarde (3h)

**Bloque 5: Prototipar el flujo principal (70 min)**
- Cada estudiante prototipa el flujo principal de su proyecto en Figma:
  - Happy path completo (inicio → fin).
  - Al menos 2 estados de error con mensajes y recuperación.
  - Estado vacío / primera vez.
  - Estado de carga (skeleton o spinner).
- Conectar pantallas con interacciones y transiciones.

Descanso: 10 min

**Bloque 6: Spec de handoff (40 min)**
- Preparar spec de handoff para 2 pantallas del proyecto:
  - Medidas, espaciados, tokens.
  - Comportamiento responsive (qué cambia en móvil).
  - Estados de componentes.
  - Microcopy final.
  - Criterios de aceptación (Dado/Cuando/Entonces).

**Bloque 7: Contextos y revisión (40 min)**
- Ejercicio breve de diseño por contexto (elegir 1):
  - Plegable: ¿cómo se vería el flujo principal en un dispositivo plegable?
  - Voz: escribir un diálogo de 5 turnos para la tarea principal del proyecto.
  - AR: ¿qué información del proyecto se beneficiaría de una capa AR?
- Peer review del prototipo: navegar el flujo del compañero y anotar 5 hallazgos.
- Feedback grupal: patrones comunes de problemas encontrados.

## Trabajo independiente (1h)

- Aplicar una evaluación heurística rápida al prototipo propio: 10 hallazgos con heurística violada, pantalla, descripción y severidad (0-4). Usar la tabla de formato.
- Refinar microcopy de errores y confirmaciones en al menos 2 pantallas del proyecto. Verificar que cada mensaje dice qué pasó y cómo arreglarlo.
- Incorporar al menos 3 hallazgos del peer review en el prototipo.
- Verificar que la spec de handoff de las 2 pantallas está completa (medidas, tokens, responsive, estados, microcopy, criterios).

## Lecturas y recursos

### Obligatorias
- Nielsen, J. "10 Usability Heuristics for User Interface Design" — https://www.nngroup.com/articles/ten-usability-heuristics/
- Nielsen, J. "How to Conduct a Heuristic Evaluation" — https://www.nngroup.com/articles/how-to-conduct-a-heuristic-evaluation/

### Recomendadas
- Yifrah, K. *Microcopy: The Complete Guide* — capítulos sobre errores y confirmaciones.
- WCAG 2.2: requisitos de foco visible, labels y navegación por teclado — https://www.w3.org/TR/WCAG22/
- Figma: prototyping guide — https://help.figma.com/hc/en-us/articles/360040314193-Guide-to-prototyping-in-Figma
- Microsoft: diseño para plegables — https://learn.microsoft.com/en-us/dual-screen/

### Herramientas
- Figma Prototyping para flujos interactivos.
- Stark para verificar accesibilidad en el prototipo.
- Maze o UserTesting para pruebas remotas con prototipos.

## Entregables del día

1. **Prototipo navegable** del flujo principal (versión 1): happy path + errores + empty state + loading.
2. **Spec de handoff** para 2 pantallas: medidas, tokens, responsive, estados, microcopy, criterios de aceptación.
3. **Evaluación heurística** del prototipo propio: 10 hallazgos con severidad.

## Checklist de calidad

- [ ] El prototipo incluye estados de contenido reales, no solo el caso ideal (happy path).
- [ ] Hay al menos 2 estados de error con mensajes específicos y forma de recuperación.
- [ ] El estado vacío comunica qué es, qué hacer y cómo empezar.
- [ ] El handoff indica breakpoints y reglas de reflow para cada pantalla.
- [ ] Los tokens del sistema están referenciados en la spec (no valores hex sueltos).
- [ ] El microcopy de errores dice qué pasó y cómo arreglarlo (no solo "Error").
- [ ] La evaluación heurística tiene severidad asignada a cada hallazgo.
- [ ] El orden de tabulación está definido para formularios.

## Notas para el instructor

- Esta clase es el punto de inflexión del curso: de construir a evaluar y comunicar. Enfatizar que un prototipo sin estados de error es un prototipo incompleto.
- En la demo de prototipos, mostrar Smart Animate con un ejemplo simple (cambio de estado de un botón). Es impresionante pero requiere naming consistente — conectar con clase 05.
- En handoff, hacer la prueba en vivo: mostrar una pantalla en Dev Mode y preguntar "¿qué falta para implementar esto?" Las respuestas revelan gaps.
- En heurísticas, no profundizar en cada una — dar el resumen y que las apliquen. La práctica enseña más que la teoría aquí.
- En microcopy, el ejercicio de reescribir mensajes malos es muy efectivo. Usar ejemplos reales de sitios conocidos.
- En contextos (plegables/voz/AR), ser breves (15-20 min). El objetivo es ampliar la perspectiva, no dominar cada contexto.
- Cerrar conectando con clase 8: "Hoy probamos y especificamos. Mañana verificamos calidad: accesibilidad, performance y diseño con IA."

