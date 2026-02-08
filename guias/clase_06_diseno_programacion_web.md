# Clase 06 | Lunes 23

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 6. Sistema de UI ligero

## Objetivos de la sesión

- Entender qué es un design system y por qué "ligero" es una decisión estratégica, no una limitación.
- Consolidar los componentes del proyecto en un sistema coherente con reglas explícitas de uso.
- Definir la anatomía de un componente documentado: nombre, propósito, variantes, propiedades, estados, do/don't.
- Crear documentación mínima pero suficiente para que otra persona implemente sin adivinar.
- Identificar deudas de diseño: qué falta, qué se deja fuera a propósito y por qué.
- Escribir criterios de aceptación para componentes clave usando Dado/Cuando/Entonces.

## Conceptos clave

### Qué es un design system

Un design system no es una librería de componentes. Es un conjunto de decisiones compartidas que incluye: principios (por qué diseñamos así), tokens (las constantes del sistema), componentes (las piezas reutilizables), patrones (cómo se combinan las piezas) y documentación (cómo se usan correctamente).

Ejemplos de referencia:
- **Material Design** (Google): exhaustivo, opinionado, con guías detalladas por componente.
- **Human Interface Guidelines** (Apple): principios + componentes nativos, menos prescriptivo.
- **Polaris** (Shopify): enfocado en e-commerce, con ejemplos de uso y anti-patrones.
- **Carbon** (IBM): enterprise, con tokens detallados y accesibilidad integrada.
- **Primer** (GitHub): developer-focused, pragmático.

### Por qué "ligero"

Un sistema ligero es una decisión consciente de alcance. No es un sistema incompleto — es un sistema que cubre el 80% del uso real con el 20% del esfuerzo. La diferencia:

| Sistema completo | Sistema ligero |
|-----------------|----------------|
| 50-100+ componentes | 8-15 componentes núcleo |
| Documentación exhaustiva | Documentación mínima suficiente |
| Equipo dedicado de mantenimiento | Mantenido por el mismo equipo de producto |
| Meses de desarrollo | Semanas de desarrollo |
| Cubre edge cases | Cubre casos principales + reglas para resolver el resto |

Un sistema ligero es ideal para: proyectos nuevos, equipos pequeños (1-5 personas), MVPs, y como punto de partida que crece con el producto.

Principio: **empezar con lo que necesitás hoy, no con lo que podrías necesitar algún día**. Un sistema que nadie usa porque es demasiado complejo es peor que no tener sistema.

### Anatomía de un componente documentado

Cada componente del sistema debe tener:

1. **Nombre**: claro, consistente, sin ambigüedad. "Button", no "CTA element" ni "action-box".
2. **Propósito**: una oración que explica para qué sirve. "Permite al usuario ejecutar una acción principal o secundaria."
3. **Anatomía visual**: diagrama que muestra las partes del componente (ícono, label, container, border).
4. **Variantes**: las versiones del componente. Para un botón: primary, secondary, ghost, destructive.
5. **Propiedades**: las perillas configurables. Tamaño (sm/md/lg), con/sin ícono, ancho fijo/fluido.
6. **Estados**: default, hover, focus, active, disabled, loading. Todos diseñados.
7. **Comportamiento**: qué pasa al interactuar. Click → feedback inmediato → acción. Loading → spinner reemplaza label → se deshabilita para evitar doble clic.
8. **Do / Don't**: ejemplos visuales de uso correcto e incorrecto. "Do: usar un solo botón primario por sección. Don't: poner 3 botones primarios juntos."
9. **Accesibilidad**: requisitos mínimos. Contraste, focus visible, label para screen readers, keyboard interaction.

### Componentes núcleo

Para la mayoría de proyectos web, estos 8-12 componentes cubren el 80% de la UI:

1. **Button**: la acción. Primary, secondary, ghost, destructive. Con ícono opcional.
2. **Input/TextField**: la entrada de datos. Con label, placeholder, helper text, error message.
3. **Select/Dropdown**: selección de una opción entre varias.
4. **Checkbox/Radio**: selección múltiple o única.
5. **Card**: contenedor de contenido agrupado. Con imagen opcional, título, descripción, acciones.
6. **Alert/Banner**: mensaje del sistema. Info, success, warning, error. Dismissible o persistente.
7. **Toast/Snackbar**: feedback temporal. Auto-dismiss.
8. **Modal/Dialog**: acción que requiere atención completa. Con overlay, título, contenido, acciones.
9. **Navbar/Header**: navegación global. Desktop y móvil.
10. **Badge/Tag/Chip**: metadata visual. Estado, categoría, filtro.
11. **Avatar**: representación de usuario. Con imagen, iniciales o placeholder.
12. **Skeleton/Loader**: estado de carga. Placeholder visual de la estructura.

No todos los proyectos necesitan los 12. Elegir los que el proyecto realmente usa.

### Propiedades bien definidas

Las propiedades de un componente son las "perillas" que se pueden ajustar sin romper el componente. Deben ser:

- **Ortogonales**: cada propiedad controla una dimensión independiente. "Size" no debe afectar "hierarchy".
- **Exhaustivas para el uso real**: cubrir las combinaciones que se necesitan, no todas las posibles.
- **Nombradas con claridad**: `size: sm | md | lg`, no `size: 1 | 2 | 3` ni `size: small | medium | big`.

Ejemplo para Button:
| Propiedad | Valores | Descripción |
|-----------|---------|-------------|
| hierarchy | primary, secondary, ghost, destructive | Importancia visual |
| size | sm, md, lg | Tamaño del componente |
| state | default, hover, focus, active, disabled, loading | Estado de interacción |
| iconPosition | none, left, right | Posición del ícono |
| width | auto, full | Ancho fijo al contenido o 100% del contenedor |

### Documentación mínima suficiente

La documentación no es un libro — es una referencia rápida. Debe responder tres preguntas en menos de 30 segundos:

1. **¿Qué es esto?** → Nombre + propósito en una oración.
2. **¿Cómo lo uso?** → Variantes + propiedades + ejemplo visual.
3. **¿Qué NO debo hacer?** → Do/Don't con ejemplos.

Formatos de documentación:
- **Dentro de Figma**: página dedicada con componentes organizados, ejemplos y notas. Ventaja: todo en un lugar. Desventaja: puede ser difícil de navegar.
- **Página web (Storybook, ZeroHeight, Notion)**: más estructurada, con búsqueda. Ventaja: accesible para todo el equipo. Desventaja: requiere mantenimiento separado.
- **README en el repo**: junto al código. Ventaja: desarrollo lo encuentra fácil. Desventaja: diseño no lo actualiza.

Para este curso: documentación dentro de Figma es suficiente.

### Deuda de diseño

Así como existe deuda técnica, existe deuda de diseño: decisiones que se posponen conscientemente. La clave es que sea consciente y documentada.

Tipos de deuda:
- **Componentes faltantes**: "No tenemos componente de tabla porque el MVP no tiene tablas. Si se agrega, hay que diseñarlo."
- **Estados incompletos**: "El componente de upload no tiene estado de error de red. Se agrega en v2."
- **Responsive pendiente**: "El dashboard solo está diseñado para desktop. Móvil es deuda."
- **Accesibilidad parcial**: "Los contrastes están verificados, pero el orden de tabulación no."

Documentar la deuda evita que se olvide y permite priorizarla. Formato simple: qué falta + por qué se pospuso + cuándo se debería resolver.

### Criterios de aceptación para componentes

Aplicar el formato Dado/Cuando/Entonces (de clase 01) a componentes:

**Ejemplo: Button**
- Dado que el botón está en estado default, cuando el usuario hace hover, entonces el fondo cambia a `color/primary/hover` con transición de 150ms ease.
- Dado que el botón está en estado loading, cuando el usuario hace clic, entonces no se dispara ninguna acción (prevenir doble envío).
- Dado que el botón es de tipo destructive, cuando el usuario hace clic, entonces se muestra un modal de confirmación antes de ejecutar la acción.

**Ejemplo: Input**
- Dado que el input tiene un error de validación, cuando el usuario corrige el valor y sale del campo (blur), entonces el mensaje de error desaparece y el borde vuelve al estado default.
- Dado que el input es de tipo password, cuando el usuario hace clic en el ícono de ojo, entonces el texto se muestra/oculta alternadamente.

Estos criterios son el puente entre diseño y desarrollo. Eliminan ambigüedad.

## Agenda

### Mañana (3h)

**Bloque 1: Design systems — concepto y alcance (40 min)**
- Qué es un design system vs. una librería de componentes vs. una guía de estilo.
- Ejemplos de referencia: Material Design, Polaris, Carbon, Primer.
- Por qué "ligero": decisión estratégica de alcance. Tabla comparativa.
- Los 8-12 componentes núcleo que cubren el 80% de la UI.

**Bloque 2: Anatomía y propiedades (50 min)**
- Anatomía de un componente documentado: nombre, propósito, variantes, propiedades, estados, do/don't, accesibilidad.
- Propiedades bien definidas: ortogonales, exhaustivas, nombradas con claridad.
- Demo: documentar un botón completo en vivo (10 minutos, paso a paso).
- Ejercicio: cada estudiante elige un componente de su kit y lo documenta con la anatomía completa.

Descanso: 10 min

**Bloque 3: Documentación y deuda (40 min)**
- Documentación mínima suficiente: las 3 preguntas en 30 segundos.
- Formatos: dentro de Figma, web, README. Pros y contras.
- Deuda de diseño: tipos, cómo documentarla, cuándo resolverla.
- Ejercicio: cada estudiante lista 3 deudas de su sistema y las prioriza.

**Bloque 4: Criterios de aceptación para componentes (40 min)**
- Dado/Cuando/Entonces aplicado a componentes (repaso de clase 01).
- Ejemplos: Button, Input, Modal, Toast.
- Ejercicio: escribir 3 criterios de aceptación para 2 componentes del proyecto.
- Por qué esto importa: el criterio es el contrato entre diseño y desarrollo.

### Tarde (3h)

**Bloque 5: Construcción del sistema — componentes núcleo (75 min)**
- Cada estudiante construye 8-12 componentes núcleo de su proyecto en Figma:
  - Con variantes completas (hierarchy, size, state).
  - Con propiedades configurables (boolean, instance swap, text).
  - Con tokens/variables aplicados.
  - Con naming consistente.
- Priorizar los componentes que el proyecto realmente necesita (no los 12 genéricos).

Descanso: 10 min

**Bloque 6: Documentación en Figma (40 min)**
- Crear página de documentación del sistema dentro de Figma:
  - Cada componente con: nombre, propósito, variantes mostradas, do/don't.
  - Tokens visualizados: paleta de colores, escala tipográfica, espaciado.
  - Reglas generales: cuándo usar cada jerarquía, cuándo usar modal vs. toast, etc.

**Bloque 7: Revisión cruzada (40 min)**
- Intercambiar sistemas con un compañero.
- Evaluar con checklist:
  - ¿Puedo entender cada componente en 30 segundos?
  - ¿Las propiedades son claras y no se solapan?
  - ¿Los do/don't son útiles o genéricos?
  - ¿Qué deuda de diseño identifico que no está documentada?
- Feedback escrito: 3 fortalezas + 3 mejoras concretas.

## Trabajo independiente (1h)

- Hacer una lista completa de deudas del sistema: qué falta, qué se deja fuera a propósito y por qué. Priorizar: qué se resolvería primero si hubiera tiempo.
- Escribir criterios de aceptación (Dado/Cuando/Entonces) para 2 componentes clave del proyecto: al menos 3 criterios por componente, cubriendo estados de error y edge cases.
- Incorporar el feedback del peer review: aplicar al menos 2 de las 3 mejoras sugeridas.
- Revisar que la página de documentación en Figma sea navegable y comprensible para alguien que no participó en la clase.

## Lecturas y recursos

### Obligatorias
- Kholmatova, A. *Design Systems* — capítulos 3-4 (documentación, consistencia y gobernanza).
- Shopify Polaris: revisar la documentación de 3 componentes (Button, TextField, Card) — https://polaris.shopify.com/components

### Recomendadas
- Material Design 3: componentes y tokens — https://m3.material.io/
- Nathan Curtis: "Documenting Components" — https://medium.com/eightshapes-llc/documenting-components-9fe59b80c015
- Brad Frost: "Interface Inventory" — https://bradfrost.com/blog/post/interface-inventory/

### Herramientas
- Figma: páginas de documentación con frames organizados.
- ZeroHeight o Supernova para documentación externa (referencia).
- Notion como alternativa ligera para documentación de sistema.

## Entregables del día

1. **Sistema de UI ligero** (versión 1): 8-12 componentes núcleo con variantes, propiedades y tokens aplicados.
2. **Página de documentación** en Figma: cada componente con nombre, propósito, variantes, do/don't.
3. **Lista de deudas de diseño** documentada y priorizada.
4. **Criterios de aceptación** para 2 componentes clave (mínimo 3 criterios cada uno).

## Checklist de calidad

- [ ] Las variantes cubren el 80% del uso real del proyecto (no variantes teóricas que nunca se usan).
- [ ] Las propiedades son ortogonales: cada una controla una dimensión independiente sin solapamiento.
- [ ] Cada componente tiene nombre, propósito en una oración, y al menos 1 do/don't.
- [ ] Los tokens están aplicados consistentemente (no hay colores hex sueltos en componentes).
- [ ] La documentación responde "¿qué es?", "¿cómo lo uso?" y "¿qué no debo hacer?" en menos de 30 segundos.
- [ ] La deuda de diseño está documentada explícitamente (no es deuda invisible).
- [ ] Los criterios de aceptación cubren estados de error, no solo el happy path.
- [ ] El peer review fue incorporado: al menos 2 mejoras aplicadas.

## Notas para el instructor

- Esta clase marca el inicio de la segunda semana. Recordar lo hecho en la primera semana y conectar: "Semana 1 fue exploración y construcción. Semana 2 es consolidación y calidad."
- En design systems, evitar que se vuelva teórico. El foco es construir, no estudiar sistemas ajenos. Los ejemplos de referencia son inspiración, no modelo a copiar.
- En documentación, el error más común es escribir demasiado. Insistir: "Si tu documentación necesita documentación, es demasiado compleja."
- En deuda de diseño, normalizar que tener deuda es profesional. Lo no profesional es tener deuda invisible. Preguntar: "¿Qué decidiste NO hacer y por qué?"
- En criterios de aceptación, verificar que sean específicos y testeables. "El botón se ve bien" no es un criterio. "El fondo cambia a #color con transición de 150ms" sí lo es.
- Cerrar conectando con clase 7: "Hoy consolidamos el sistema. Mañana lo ponemos a prueba: prototipado y comunicación con desarrollo."

