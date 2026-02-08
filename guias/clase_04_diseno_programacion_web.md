# Clase 04 | Jueves 12

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 4. UI: patrones y componentes

## Objetivos de la sesión

- Identificar patrones de UI recurrentes y entender por qué existen (problema que resuelven, no solo cómo se ven).
- Convertir patrones en componentes reutilizables con estados completos: default, hover, focus, active, disabled, loading, error, empty.
- Diseñar formularios accesibles con prevención de errores, validación progresiva y mensajes claros.
- Diseñar vistas de datos (listas, tablas, cards) con criterios de densidad, filtrado y paginación.
- Introducir multimodalidad: UI asistida por IA (sugerencias, autocompletado, límites éticos) y voz (turnos, confirmación, fallback).
- Construir el kit inicial de componentes del proyecto del curso.

## Conceptos clave

### Patrones de UI

Un patrón de UI es una solución recurrente a un problema de interacción. No es un componente — es la lógica detrás del componente. El componente es la implementación visual del patrón.

Ejemplo: el patrón "selección múltiple con filtro" puede implementarse como checkboxes con barra de búsqueda, como chips seleccionables, o como un dropdown multi-select. El patrón es el mismo; el componente cambia según el contexto.

Referencia: Jenifer Tidwell, *Designing Interfaces* — catálogo de patrones organizados por problema, no por componente.

### Patrones comunes y cuándo usarlos

**Navegación**
- **Tabs**: 2-7 secciones del mismo nivel, sin necesidad de ver varias a la vez. No usar para pasos secuenciales.
- **Sidebar**: navegación secundaria persistente. Útil en dashboards y apps con muchas secciones.
- **Breadcrumbs**: sitios con más de 2 niveles de profundidad. No en apps de una sola página.
- **Bottom nav (móvil)**: 3-5 destinos principales. Más de 5 = confusión. Menos de 3 = innecesario.
- **Hamburger**: último recurso. Oculta opciones = reduce descubrimiento. Usar solo si no caben en bottom nav.

**Contenido**
- **Cards**: contenido heterogéneo con imagen + texto + acción. Buenas para exploración. Malas para comparación (usar tabla).
- **Listas**: contenido homogéneo, escaneo rápido. Con o sin thumbnail. Ordenables y filtrables.
- **Tablas**: datos estructurados que se comparan. Columnas = atributos, filas = ítems. Responsive: colapsar columnas secundarias o convertir a cards.
- **Grid de imágenes**: contenido visual dominante (portfolio, galería, e-commerce). Lazy loading obligatorio.

**Acciones**
- **Modales**: acciones que requieren atención completa y confirmación. No abusar — interrumpen el flujo. Siempre con forma de cerrar (X, Escape, clic fuera).
- **Drawers/Sheets**: contenido secundario que no merece página propia. Desde el borde (derecho en desktop, inferior en móvil).
- **Toasts/Snackbars**: feedback temporal no bloqueante. "Guardado", "Copiado", "Enviado". Auto-dismiss en 3-5 segundos.
- **Dropdowns**: selección de una opción entre varias. Máximo 10-15 ítems visibles; más = agregar búsqueda.

**Filtros y búsqueda**
- **Filtros**: reducir un conjunto grande. Sidebar de filtros (desktop), bottom sheet de filtros (móvil). Mostrar cantidad de resultados en tiempo real.
- **Búsqueda**: encontrar algo específico. Autocompletado, sugerencias, resultados recientes. Siempre mostrar qué se buscó y cuántos resultados hay.

### Estados de componentes

Cada componente interactivo tiene múltiples estados. Diseñar solo el estado default es como construir un auto sin frenos.

| Estado | Descripción | Señal visual |
|--------|-------------|--------------|
| Default | Estado inicial, sin interacción | Base del componente |
| Hover | Mouse encima (solo desktop) | Cambio sutil de fondo o borde |
| Focus | Seleccionado con teclado (Tab) | Outline visible, alto contraste |
| Active/Pressed | Durante el clic/tap | Feedback inmediato (escala, color) |
| Disabled | No disponible | Gris, opacidad reducida, cursor not-allowed |
| Loading | Procesando | Spinner o skeleton, no bloquear toda la UI |
| Error | Algo salió mal | Borde rojo + mensaje descriptivo |
| Success | Acción completada | Confirmación visual temporal |
| Empty | Sin datos | Mensaje útil + CTA para llenar |

Regla de oro: **focus debe ser siempre visible**. Es la única forma en que usuarios de teclado saben dónde están. El outline por defecto del browser es feo pero funcional — si lo quitás, reemplazalo con algo mejor, nunca con nada.

### Feedback y microinteracciones

El usuario necesita saber que el sistema respondió. Sin feedback, repite la acción (doble clic, doble envío).

Tipos de feedback:
- **Inmediato**: hover, press, toggle. < 100ms.
- **Progresivo**: loading bar, skeleton, porcentaje. Para acciones de 1-10 segundos.
- **Confirmatorio**: toast, checkmark, cambio de estado. Después de completar.
- **Correctivo**: mensaje de error con instrucción. Qué salió mal + cómo arreglarlo.

Principio de Jakob Nielsen: "El sistema debe mantener al usuario informado sobre lo que está pasando, a través de feedback apropiado en un tiempo razonable." (Heurística #1: Visibilidad del estado del sistema).

### Formularios

Los formularios son donde más se pierde a los usuarios. Cada campo extra reduce la tasa de conversión. Cada error mal manejado genera abandono.

**Principios de diseño de formularios:**

1. **Menos campos = más conversiones**. Pedir solo lo necesario. ¿Realmente necesitás el teléfono? ¿El apellido por separado?
2. **Labels siempre visibles**: no usar placeholder como label (desaparece al escribir). Label arriba del campo, alineado a la izquierda.
3. **Tipos de input correctos**: `email` muestra teclado con @, `tel` muestra teclado numérico, `date` muestra date picker nativo. Cada tipo correcto reduce errores.
4. **Agrupación lógica**: fieldsets para datos relacionados (datos personales, dirección, pago). Progresión lógica de arriba a abajo.
5. **Validación progresiva**: validar al salir del campo (onblur), no al enviar. El usuario corrige en contexto, no después de 10 campos.
6. **Mensajes de error específicos**: "Este campo es obligatorio" < "Ingresá tu email" < "El formato debe ser nombre@dominio.com". Siempre debajo del campo, en rojo, con ícono.
7. **Prevención > corrección**: si el formato es específico, mostrar ejemplo. Si hay restricciones, decirlas antes (no después de fallar).
8. **Botón de envío claro**: "Crear cuenta" > "Enviar" > "Submit". El label del botón debe decir qué va a pasar.
9. **No perder datos**: si el formulario falla, no borrar lo que el usuario ya escribió. Preservar el estado.

**Patrones de formulario:**
- **Single column**: un campo por línea. Más lento pero menos errores. Ideal para móvil y formularios largos.
- **Multi-step**: dividir en pasos con indicador de progreso. Para formularios de más de 6-8 campos.
- **Inline editing**: editar directamente en la vista de datos. Para configuraciones y perfiles.

### Vistas de datos

Cuando el contenido es dinámico (viene de una base de datos, API, CMS), el diseño debe contemplar:

- **Vacío**: primera vez, sin datos. No pantalla en blanco — mensaje + CTA ("Aún no tenés proyectos. Crear el primero →").
- **Pocos datos**: 1-3 ítems. ¿Se ve raro con tanto espacio vacío? Ajustar layout.
- **Muchos datos**: paginación, infinite scroll o "cargar más". Paginación para datos que se consultan (e-commerce); infinite scroll para feeds (redes sociales).
- **Datos largos**: texto que se trunca, nombres de 200 caracteres, descripciones extensas. Definir reglas de truncado (ellipsis, "ver más").
- **Filtrado y ordenamiento**: ¿qué filtros son más usados? Ponerlos visibles. Los demás, en "más filtros". Siempre mostrar filtros activos y forma de limpiarlos.

### Multimodalidad: UI asistida por IA

La IA en interfaces no es magia — es una herramienta con límites. Diseñar con IA requiere:

- **Transparencia**: el usuario debe saber cuándo algo es generado por IA. "Sugerido por IA" como label.
- **Control**: el usuario siempre puede editar, rechazar o ignorar la sugerencia. Nunca auto-aplicar sin confirmación.
- **Límites honestos**: "Puedo equivocarme. Verificá la información." No prometer certeza.
- **Fallback**: si la IA no puede responder, ofrecer alternativa humana o manual.
- **Confianza progresiva**: empezar con sugerencias opcionales, no con acciones automáticas.

Ejemplos prácticos:
- **Autocompletado inteligente**: Gmail Smart Compose. Sugerencia en gris, Tab para aceptar.
- **Clasificación automática**: etiquetar emails, categorizar productos. Siempre editable.
- **Resumen de contenido**: "Este artículo en 3 puntos". Útil pero debe ser verificable.
- **Detección de errores**: "¿Quisiste decir...?" en búsqueda. Sugerencia, no corrección forzada.

### Multimodalidad: voz

Diseñar para voz es diseñar conversaciones, no pantallas. Principios:

- **Turnos cortos**: el sistema habla poco, pregunta claro, espera respuesta.
- **Confirmación explícita**: "Entendí que querés reservar para 2 personas el viernes. ¿Correcto?"
- **Errores con gracia**: "No entendí. ¿Podés repetirlo?" > "Error de reconocimiento".
- **Fallback a pantalla**: si la voz no funciona, ofrecer alternativa visual.
- **Sin menús largos**: "Presione 1 para ventas, 2 para soporte, 3 para..." es hostil. Mejor: "¿En qué te puedo ayudar?"

## Agenda

### Mañana (3h)

**Bloque 1: Patrones de UI (50 min)**
- Qué es un patrón vs. un componente. El patrón es el problema; el componente es la solución.
- Recorrido por patrones comunes: navegación, contenido, acciones, filtros y búsqueda.
- Cuándo usar cada uno: contexto, cantidad de datos, dispositivo, frecuencia de uso.
- Ejercicio rápido: dado un escenario, elegir el patrón correcto y justificar.

**Bloque 2: Estados y feedback (45 min)**
- Los 9 estados de un componente interactivo. Tabla de estados.
- Focus visible como requisito no negociable.
- Feedback y microinteracciones: inmediato, progresivo, confirmatorio, correctivo.
- Demo: recorrer un componente real (botón, input, card) y mapear todos sus estados.

Descanso: 10 min

**Bloque 3: Formularios (45 min)**
- Los 9 principios de diseño de formularios. Ejemplos buenos y malos.
- Validación progresiva vs. validación al enviar. Demo en vivo.
- Patrones: single column, multi-step, inline editing.
- Mensajes de error: anatomía (ícono + texto + posición + color + asociación aria).

**Bloque 4: Vistas de datos y multimodalidad (30 min)**
- Diseñar para datos dinámicos: vacío, pocos, muchos, largos.
- Filtrado y ordenamiento: visibilidad y limpieza.
- IA en UI: transparencia, control, límites, fallback. Ejemplos prácticos.
- Voz: turnos, confirmación, errores, fallback a pantalla.

### Tarde (3h)

**Bloque 5: Kit de componentes — parte 1 (60 min)**
- Cada estudiante diseña su kit inicial en Figma:
  - Botones: primario, secundario, ghost, destructivo. Con estados.
  - Inputs: text, email, password, textarea. Con label, placeholder, error, disabled.
  - Selects y checkboxes/radios.
- Foco en estados completos, no en estética perfecta.

Descanso: 10 min

**Bloque 6: Kit de componentes — parte 2 (50 min)**
- Continuar el kit:
  - Cards: con imagen, sin imagen, horizontal, con acciones.
  - Alertas/Toasts: info, success, warning, error.
  - Navbar: desktop y móvil.
  - Chips/Tags: seleccionables, removibles.
- Definir reglas de uso por componente: cuándo sí, cuándo no.

**Bloque 7: Integración y revisión (50 min)**
- Aplicar componentes del kit a los wireframes de clase 03.
- Verificar que cada componente tiene estados mínimos diseñados (no solo descritos).
- Peer review: intercambiar kits y buscar estados faltantes, inconsistencias de naming, componentes sin regla de uso.
- Presentación rápida: 2 minutos por persona, 2 hallazgos del peer review.

## Trabajo independiente (1h)

- Elegir 5 componentes del kit y escribir reglas de uso formales: cuándo usar, cuándo no usar, errores comunes a evitar, y ejemplo de uso correcto vs. incorrecto.
- Anotar 3 puntos del proyecto donde una ayuda de IA podría aportar valor (ejemplo: autocompletado de dirección, sugerencia de categoría) y 2 donde estorbaría o generaría desconfianza.
- Revisar que todos los inputs del proyecto tengan: label visible, tipo correcto, mensaje de error previsto y estado disabled definido.

## Lecturas y recursos

### Obligatorias
- Tidwell, J. *Designing Interfaces* — capítulos sobre formularios, listas y feedback.
- Nielsen, J. "10 Usability Heuristics for User Interface Design" — https://www.nngroup.com/articles/ten-usability-heuristics/

### Recomendadas
- Kholmatova, A. *Design Systems* — principios de consistencia y documentación de componentes.
- Wroblewski, L. *Web Form Design* — el libro definitivo sobre formularios.
- Google Material Design: componentes y guías — https://m3.material.io/components
- Apple Human Interface Guidelines: componentes — https://developer.apple.com/design/human-interface-guidelines/components

### Herramientas
- Figma: componentes con variantes y propiedades.
- Stark para verificar contraste en estados de error.
- Storybook (referencia): cómo desarrollo documenta componentes con estados.

## Entregables del día

1. **Kit de componentes inicial** en Figma (versión 1): botones, inputs, selects, cards, alertas, navbar, chips. Con estados completos.
2. **Reglas de uso** por componente: cuándo sí, cuándo no, errores comunes (texto breve en el archivo Figma o documento aparte).
3. **Wireframes actualizados** con componentes del kit aplicados.

## Checklist de calidad

- [ ] Cada componente tiene naming consistente (tipo/variante/estado).
- [ ] Los estados están diseñados visualmente, no solo descritos en texto.
- [ ] Todos los inputs tienen label visible (no solo placeholder).
- [ ] Los formularios tienen mensajes de error específicos debajo de cada campo.
- [ ] El focus es visible en todos los elementos interactivos.
- [ ] Las cards, listas o tablas contemplan estado vacío y estado con datos largos/truncados.
- [ ] Hay reglas de uso escritas para al menos 5 componentes.
- [ ] Los componentes de IA indican claramente que son sugerencias, no certezas.

## Notas para el instructor

- Esta clase es la más "visual" hasta ahora. Los estudiantes van a querer hacer cosas bonitas — redirigir hacia estados completos y reglas de uso. La estética se pule en clase 5-6.
- En patrones de UI, usar ejemplos reales: mostrar cómo Airbnb usa cards, cómo Notion usa sidebar, cómo Stripe usa formularios. Capturas en vivo.
- En formularios, hacer una demo de validación progresiva vs. validación al enviar. El contraste es muy claro y convence rápido.
- En multimodalidad, ser breves (15-20 min total). El objetivo es que sepan que existe y tengan criterio básico, no que diseñen un asistente de voz completo.
- En el peer review, insistir en buscar estados faltantes: "¿qué pasa si este botón está disabled?", "¿y si el input tiene un error?", "¿y si la card no tiene imagen?"
- Cerrar conectando con clase 5: "Hoy construimos piezas sueltas. Mañana las convertimos en un sistema: Auto Layout, variables, librería."

