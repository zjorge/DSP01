# Clase 01 | Lunes 9

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 1. Web actual y roles

## Objetivos de la sesión

- Ubicar el rol del diseñador en un equipo web y sus responsabilidades reales frente a producto, desarrollo, QA, contenido y analítica.
- Entender qué se entrega y cómo se evalúa una entrega profesional: archivo Figma organizado, assets exportados, especificación de estados, criterios de aceptación escritos.
- Identificar las tres restricciones técnicas que más afectan decisiones de diseño: performance (peso, imágenes, tipografías), accesibilidad (teclado, contraste, foco, lectura) y responsive (reflow, prioridad, breakpoints).
- Introducir el framework Dado/Cuando/Entonces para escribir criterios de aceptación desde diseño.
- Definir el proyecto del curso con alcance realista.

## Conceptos clave

### La web como máquina de decisiones

La web no es un lienzo en blanco. Es un sistema con reglas técnicas, usuarios reales con contextos diversos y objetivos de negocio medibles. Cada decisión visual tiene consecuencias: peso de página, tiempo de carga, accesibilidad, costo de mantenimiento. Diseñar para web es negociar entre intención creativa y restricción técnica.

### Diseño ≠ decoración

Diseño es tomar decisiones informadas sobre jerarquía (qué ve primero el usuario), estructura (cómo se organiza la información), interacción (qué pasa cuando el usuario actúa) y criterio (por qué esta solución y no otra). Un botón grande y rojo no es "diseño". Un botón que comunica la acción principal, tiene contraste suficiente, es alcanzable con el pulgar y tiene estados de hover, focus, disabled y loading — eso es diseño.

### Producto como hipótesis

Un producto digital es una apuesta: creemos que cierto grupo de personas tiene un problema, y que nuestra solución les aporta valor. Esa apuesta se valida con datos, no con opiniones. "Creemos que los freelancers necesitan generar facturas rápido desde el celular" es una hipótesis testeable. "Hagamos una app bonita" no lo es.

### Tres preguntas antes de diseñar

1. **¿Qué problema resolvemos?** — Si no podés articularlo en una oración, no estás listo para diseñar.
2. **¿Para quién?** — Siempre hay un usuario primario. Edad, contexto, nivel técnico, dispositivo probable, motivación.
3. **¿En qué contexto?** — ¿Está en el bus con una mano? ¿En la oficina con doble monitor? ¿Tiene prisa?

### Contexto real del usuario

- Pantalla pequeña: más del 60% del tráfico web global es móvil.
- Red inestable: en Latinoamérica, muchos navegan con 3G o WiFi compartido. Una imagen de 2MB puede tardar 8 segundos.
- Tiempo limitado: el usuario promedio decide en 3-5 segundos si se queda o se va. Google encontró que el 53% de visitas móviles se abandonan si la página tarda más de 3 segundos.

### El trabajo del diseñador web

- **Reducir fricción**: cada clic extra, cada campo innecesario es fricción. Amazon patentó el "1-Click" por algo.
- **Aumentar claridad**: si el usuario tiene que pensar "¿esto qué es?", fallaste. El diseño debe ser auto-explicativo.
- **Evitar errores**: no solo prevenirlos — cuando ocurren, guiar al usuario de vuelta. Un formulario que dice "Error" sin explicar qué pasó es hostil.

### Roles en un equipo web

| Rol | Responsabilidad |
|-----|----------------|
| Producto | Define el qué y el por qué. Prioriza features, habla con stakeholders, mide resultados. |
| Diseño | Define cómo se ve, se siente y se usa. Traduce necesidades en interfaces. |
| Desarrollo | Construye. Frontend (lo visible), backend (la lógica), infraestructura. |
| QA | Verifica que lo construido funcione como se especificó. Encuentra bugs y edge cases. |
| Contenido | Escribe el copy, define el tono, estructura la información. El texto ES interfaz. |
| Analítica | Mide qué pasa después del lanzamiento. Funnels, conversión, retención. |

En equipos pequeños, una persona cubre 2-3 roles. En la práctica, el diseñador termina haciendo un poco de todo: escribir copy, pensar en edge cases, negociar con desarrollo.

### El ecosistema técnico

Tu interfaz vive dentro de capas que no controlás: Servicios (APIs, CDNs) → Red (WiFi, 4G, 3G) → Dispositivo (desde iPhone 15 Pro hasta Android de $80) → OS (iOS, Android, Windows) → Browser (Chrome, Safari, Firefox). Cada capa puede fallar. Si falla, también es diseño — ejemplo: Spotify offline muestra tu biblioteca descargada, no un error.

### Entregables profesionales

Un "pantallazo bonito" no es una entrega. Una entrega profesional incluye:

1. **Especificación**: medidas, colores, tipografías, espaciados. Extraíble desde Figma Dev Mode.
2. **Criterios de aceptación**: condiciones que definen cuándo algo está "terminado".
3. **Activos listos**: imágenes en formatos correctos (WebP, SVG), íconos, fuentes. No "después te los paso".
4. **Comportamiento definido**: hover, focus, active, disabled, loading, error, empty, overflow. Cada estado documentado.

### Figma como contrato visual

Figma no es el fin — es un contrato visual. Como un plano arquitectónico: preciso, organizado y legible para alguien que no es diseñador. Cada componente debe responder tres preguntas: ¿Qué es esto? ¿Cómo se usa? ¿Qué pasa si algo sale mal?

### Tres entregables típicos

1. **Estructura**: jerarquía + contenido + navegación. Sitemap y wireframes de baja fidelidad.
2. **Componentes**: piezas reutilizables con estados (default, hover, active, focus, disabled, loading, error, empty) y reglas de uso.
3. **Flujos**: tareas completas del usuario de principio a fin, incluyendo decisiones y caminos de error.

### Criterios de aceptación (Dado/Cuando/Entonces)

Formato del mundo de testing (BDD) adaptado para diseño:

- **Dado** un estado inicial → "Dado que el usuario está en la página de login"
- **Cuando** hago una acción → "Cuando ingresa un email inválido y presiona Enviar"
- **Entonces** obtengo un resultado → "Entonces se muestra un mensaje de error debajo del campo email"

Ejemplo completo para un login:
- Si el email es inválido → borde rojo + mensaje "Ingresá un email válido" debajo del campo.
- Si falta contraseña → botón de envío deshabilitado (gris, no clickeable).
- Si credenciales fallan → "Email o contraseña incorrectos. ¿Olvidaste tu contraseña?" con link a recuperación.

### Costo del diseño

Cada decisión de diseño tiene precio: tiempo de desarrollo, bugs potenciales, carga de soporte, impacto en conversión. Un carousel tiene más bugs que una lista estática. Un checkout confuso pierde ventas. Amazon estima que 100ms de latencia extra les cuesta 1% de ventas.

### Restricciones básicas

**Performance**
- Página web promedio: ~2.5MB. En 3G tarda 8-12 segundos.
- Imágenes: 50-70% del peso. WebP reduce 30-50% vs PNG. Lazy loading para fuera del viewport.
- Tipografías: cada peso ~20-50KB. Máximo 2-3 pesos por fuente.
- Animaciones: CSS es barato, JS puede bloquear el hilo principal.
- Herramienta: PageSpeed Insights de Google.

**Accesibilidad**
- 15% de la población mundial tiene alguna discapacidad. En muchos países es ley (ADA, EN 301 549).
- Teclado: todo lo que se hace con mouse debe funcionar con Tab, Enter y Escape.
- Contraste: ratio mínimo 4.5:1 texto normal, 3:1 texto grande (WCAG AA). Plugin: Stark para Figma.
- Lectura: mínimo 16px en móvil, líneas de 45-75 caracteres, interlineado 1.5.
- Foco visible: al navegar con Tab, debe verse claramente qué elemento está seleccionado.

**Responsive**
- No es "se achica" — es adaptación al contexto. A veces implica quitar, reorganizar, cambiar interacción.
- Reflow: 3 columnas → 2 → 1. Grid → stack.
- Prioridad: en móvil, ¿qué se queda y qué se va?
- Breakpoints: no son arbitrarios — se definen donde el contenido se rompe. Referencia: ~480, ~768, ~1024, ~1280.
- Mobile-first: empezar por móvil obliga a priorizar.

### Estados de diseño

Un diseño no es una foto fija. Estados mínimos:
- **Vacío**: primera vez, sin datos. Mensaje útil + CTA, no pantalla en blanco.
- **Cargando**: skeleton screens > spinners. Mostrar estructura reduce percepción de espera.
- **Error**: el más ignorado y el más importante. Debe enseñar y permitir corregir sin perder progreso.
- **Éxito**: confirmación clara con próximos pasos.

Referencia: "The Nine States of Design" de Vince Speelman.

### Copy como diseño

El texto de la interfaz es diseño. "Enviar" vs. "Confirmar pedido" — la diferencia es enorme en claridad. Microcopy (placeholders, tooltips, mensajes de error) guía al usuario en cada paso. Referencia: "Microcopy: The Complete Guide" de Kinneret Yifrah.

## Agenda

### Mañana (3h)

**Bloque 1: La web y el equipo (45 min)**
- Presentación del curso: 10 sesiones, proyecto real, evaluación basada en implementabilidad.
- La web como máquina de decisiones. Diseño ≠ decoración. Producto como hipótesis.
- Las tres preguntas: ¿Qué problema? ¿Para quién? ¿En qué contexto?
- Contexto real del usuario: pantalla pequeña, red inestable, tiempo limitado.
- El trabajo del diseñador: reducir fricción, aumentar claridad, evitar errores.

**Bloque 2: Equipo y ecosistema (30 min)**
- Roles en un equipo web: producto, diseño, desarrollo, QA, contenido, analítica.
- La realidad: todo se mezcla. El diseñador como puente.
- El ecosistema técnico: servicios → red → dispositivo → OS → browser.
- Si falla, también es diseño.

**Bloque 3: Entregables y Figma (45 min)**
- Qué es una entrega profesional vs. "un pantallazo bonito".
- Los cuatro componentes: especificación, criterios de aceptación, activos listos, comportamiento definido.
- Figma como contrato visual. Las tres preguntas por componente.
- Evaluación: se evalúa lo que se puede implementar. Señal de madurez = menos ambigüedad.
- Los tres entregables típicos: estructura, componentes, flujos.
- Lo que no sirve ("se entiende", "después lo vemos") vs. lo que sí (explícito, medible, repetible).

Descanso: 10 min

**Bloque 4: Criterios, costo y restricciones (50 min)**
- Criterios de aceptación: Dado/Cuando/Entonces. Ejemplo con login.
- El costo del diseño: tiempo de dev, bugs, soporte, conversión.
- Restricciones básicas: performance, accesibilidad, responsive (detalle de cada una).
- Estados de diseño: vacío, cargando, error, éxito.
- Copy como parte del diseño.
- Mini-checklist antes de entregar.

### Tarde (3h)

**Bloque 5: Setup del curso (45 min)**
- Crear archivo maestro en Figma con estructura de páginas por entregable.
- Estructura sugerida: Cover, Sitemap, Wireframes, UI, Componentes, Flujos, Assets.
- Convenciones de nombrado y organización.
- Demostración: cómo usar auto-layout, componentes con variantes, Dev Mode.

Descanso: 10 min

**Bloque 6: Ejercicio de auditoría (60 min)**
- Cada estudiante elige un sitio o app conocida.
- Auditar la interfaz respondiendo:
  1. ¿Cuál es el flujo principal? Describilo paso a paso.
  2. ¿Qué decisiones de diseño implican costo técnico? (animaciones, imágenes pesadas, interacciones complejas)
  3. ¿Qué estados de error encontrás? ¿Están bien resueltos?
  4. ¿Cómo se comporta en móvil vs. desktop? ¿Qué cambia?
  5. ¿Podés navegar solo con teclado? ¿El contraste es suficiente?
- Presentación breve: 2 minutos por persona, 3 hallazgos principales.

**Bloque 7: Definición del proyecto (60 min)**
- Cada estudiante define su proyecto del curso usando esta plantilla:

```
PROYECTO: [nombre]
PROBLEMA: [qué problema resuelve, en una oración]
USUARIO: [quién es, en 2 oraciones]
CONTEXTO: [dónde y cómo lo usa]
TAREAS: [3-5 tareas principales del usuario, como acciones observables]
PANTALLAS: [3-5 pantallas o secciones mínimas]
HIPÓTESIS: [qué medirías para saber si funciona]
```

- Revisión en parejas: cada uno revisa el proyecto del otro y hace 3 preguntas.
- Ajustes finales basados en feedback.

## Trabajo independiente (1h)

- Elegir un caso de estudio diferente al del ejercicio en clase (sitio o app) y escribir 8-10 observaciones sobre:
  - Jerarquía visual: ¿qué ves primero? ¿Qué segundo?
  - Flujo principal: ¿cuántos pasos tiene? ¿Hay fricción innecesaria?
  - Estados: ¿encontrás estados vacíos, de carga, de error?
  - Responsive: ¿cómo cambia entre desktop y móvil?
  - Accesibilidad: ¿funciona con teclado? ¿El contraste es suficiente?
- Crear bitácora inicial (1 página): decisiones tomadas sobre el proyecto, dudas pendientes, próximos pasos.

## Lecturas y recursos

### Obligatorias
- Krug, S. *Don't Make Me Think* — capítulos 1-3 (usabilidad básica, cómo realmente usamos la web).
- Speelman, V. "The Nine States of Design" — https://medium.com/swlh/the-nine-states-of-design-5bfe9b3d6d85

### Recomendadas
- Tidwell, J. *Designing Interfaces* — introducción y patrones básicos.
- Yifrah, K. *Microcopy: The Complete Guide* — capítulo 1 (qué es microcopy y por qué importa).
- MDN Web Docs: introducción a HTML y fundamentos web — https://developer.mozilla.org/es/docs/Learn
- Google PageSpeed Insights — https://pagespeed.web.dev/ (probar con 3 sitios diferentes).

### Herramientas para explorar
- Figma Dev Mode (inspección de diseños).
- Stark (plugin Figma para contraste y accesibilidad).
- WAVE Web Accessibility Evaluator — https://wave.webaim.org/

## Entregables del día

1. **Documento de alcance del proyecto** usando la plantilla proporcionada (problema, usuario, contexto, tareas, pantallas, hipótesis).
2. **Auditoría de interfaz** del ejercicio en clase (5 hallazgos documentados).
3. **Bitácora inicial** (1 página con decisiones, dudas y próximos pasos).

## Checklist de calidad

- [ ] El problema está articulado en una oración clara.
- [ ] El usuario está descrito sin usar "cualquier persona" o "todo el mundo".
- [ ] Las tareas están redactadas como acciones observables ("el usuario puede..." no "el sitio tiene...").
- [ ] El alcance cabe en 10 sesiones (3-5 pantallas, no 20).
- [ ] Hay una hipótesis simple de éxito (qué medirías al final).
- [ ] La auditoría incluye al menos 1 observación de performance, 1 de accesibilidad y 1 de responsive.

## Notas para el instructor

- Esta es la sesión más conceptual del curso. A partir de la clase 2, todo es más práctico.
- Ritmo alto en la teoría: muchos slides cortos, no dejar que se estanque.
- Fomentar preguntas durante toda la sesión, no solo al final.
- En el ejercicio de auditoría, circular por los equipos y hacer preguntas provocadoras: "¿y si no hay internet?", "¿y si el título tiene 200 caracteres?", "¿cuánto pesa esa imagen?".
- En la definición del proyecto, el error más común es alcance demasiado ambicioso. Insistir en que menos es más.
- Cerrar con energía: "Hoy vimos el mapa completo. A partir de mañana, empezamos a construir."

