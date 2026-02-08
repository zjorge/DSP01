# Clase 03 | Miércoles 11

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 3. UX y arquitectura de información

## Objetivos de la sesión

- Construir arquitectura de información a partir de objetivos de negocio, audiencias reales y tareas observables del usuario.
- Diseñar sitemaps que reflejen prioridades, no organigramas internos.
- Crear flujos de usuario con puntos de decisión, caminos de error y estados intermedios.
- Definir navegación primaria y secundaria con criterios claros de agrupación y rotulado.
- Priorizar contenido y jerarquía visual en wireframes de baja fidelidad.
- Aplicar principios de escaneo, densidad informativa y revelación progresiva.

## Conceptos clave

### Arquitectura de información (AI)

La AI es la estructura invisible que organiza el contenido para que el usuario encuentre lo que busca y entienda dónde está. No es un sitemap — es el sistema de decisiones detrás del sitemap. Incluye: organización (cómo se agrupan las cosas), rotulado (cómo se nombran), navegación (cómo se mueve el usuario) y búsqueda (cómo encuentra algo específico).

Referencia: Richard Saul Wurman acuñó el término "arquitecto de información" en 1976. Peter Morville y Louis Rosenfeld lo formalizaron en *Information Architecture for the World Wide Web*.

### Objetivos → Audiencias → Tareas

Toda AI empieza con tres preguntas encadenadas:

1. **Objetivos del negocio**: ¿Qué necesita lograr este sitio/app? Vender, informar, captar leads, reducir soporte, fidelizar. Si no hay objetivo claro, no hay criterio para priorizar.
2. **Audiencias**: ¿Quién viene y por qué? No "todo el mundo" — segmentos con motivaciones distintas. Un e-commerce tiene compradores, curiosos y compradores recurrentes. Cada uno necesita caminos diferentes.
3. **Tareas**: ¿Qué hace cada audiencia? Tareas observables: "buscar un producto por categoría", "comparar dos planes", "recuperar contraseña". Las tareas se priorizan por frecuencia × importancia.

### Modelos mentales vs. modelo del sistema

El usuario tiene un modelo mental de cómo funciona algo. El sistema tiene su propia lógica. Cuando no coinciden, hay fricción. Ejemplo: un banco organiza por tipo de producto (cuentas, tarjetas, préstamos). El usuario piensa en tareas: "pagar una factura", "ver mi saldo", "transferir plata". La AI debe acercar el modelo del sistema al modelo mental del usuario.

Técnica clave: **card sorting** — pedir a usuarios reales que agrupen y nombren contenidos. Abierto (ellos crean categorías) o cerrado (categorías predefinidas). Herramientas: Optimal Workshop, Maze, post-its físicos.

### Sitemap

Un sitemap es un diagrama jerárquico que muestra las páginas/secciones y sus relaciones. No es un wireframe ni un flujo — es un mapa de territorio.

Reglas prácticas:
- **Ancho vs. profundidad**: máximo 7±2 ítems en navegación principal (Miller). Mejor 5 claros que 12 confusos.
- **Profundidad máxima**: 3 niveles. Si necesitás más, probablemente la estructura está mal. El usuario no debería hacer más de 3 clics para llegar a contenido importante.
- **Naming**: verbos para acciones ("Comprar", "Contactar"), sustantivos para secciones ("Productos", "Blog"). Evitar jerga interna.
- **Prioridad visual**: lo más importante va primero (izquierda en nav horizontal, arriba en vertical).

### Flujos de usuario

Un flujo es la secuencia de pasos que sigue un usuario para completar una tarea. A diferencia del sitemap (estático), el flujo es dinámico: tiene inicio, decisiones, acciones y fin.

Elementos de un flujo:
- **Inicio**: ¿de dónde viene el usuario? (link, búsqueda, email, directo)
- **Pasos**: cada pantalla o acción. Numerados.
- **Decisiones**: rombos. "¿Tiene cuenta?" → Sí/No. "¿Datos válidos?" → Sí/No.
- **Estados**: qué pasa en cada paso si hay error, si está vacío, si está cargando.
- **Fin**: éxito (confirmación + próximo paso) o abandono (¿por qué se fue?).

Errores comunes:
- Diseñar solo el "happy path" (todo sale bien). El 40-60% del diseño real es manejar lo que sale mal.
- No definir qué pasa cuando el usuario retrocede o abandona a mitad de camino.
- Olvidar estados intermedios: "procesando pago", "verificando email", "esperando respuesta del servidor".

### Navegación

La navegación es el sistema que permite al usuario moverse por el sitio. No es solo el menú — incluye breadcrumbs, links contextuales, búsqueda, filtros, paginación.

Tipos:
- **Global/Primaria**: presente en todas las páginas. Máximo 5-7 ítems. Las tareas más frecuentes o importantes.
- **Local/Secundaria**: dentro de una sección. Sidebar, tabs, sub-menú.
- **Contextual**: links dentro del contenido. "Ver también", "Productos relacionados".
- **Utilitaria**: login, idioma, carrito, ayuda. Esquina superior derecha por convención.
- **Breadcrumbs**: rastro de migas. Útil en sitios con más de 2 niveles. Formato: Home > Categoría > Subcategoría > Página actual.

Principio de Krug: "No me hagas pensar". Si el usuario duda sobre dónde hacer clic, la navegación falló. El rotulado debe ser auto-explicativo, no creativo.

### Jerarquía visual y contenido

Jerarquía visual es el orden en que el ojo recorre la página. Se controla con:
- **Tamaño**: lo más grande se ve primero.
- **Peso**: bold > regular > light.
- **Contraste**: oscuro sobre claro destaca; gris se percibe como secundario.
- **Posición**: arriba-izquierda primero (en culturas LTR). El patrón F de lectura web (Nielsen, 2006).
- **Espacio**: más espacio alrededor = más importancia percibida. Apple usa esto magistralmente.
- **Color**: un acento de color guía la atención. Más de 2-3 colores de acento = ruido.

### Patrones de lectura web

- **Patrón F**: el usuario escanea la primera línea, baja, escanea una segunda línea más corta, y luego baja por el lado izquierdo. Implicación: las primeras palabras de cada línea son críticas.
- **Patrón Z**: en páginas con poco texto (landing pages). Arriba-izquierda → arriba-derecha → abajo-izquierda → abajo-derecha.
- **Escaneo, no lectura**: el 79% de los usuarios escanea; solo el 16% lee palabra por palabra (Nielsen). Implicación: títulos claros, párrafos cortos, listas, negritas en palabras clave.

### Densidad informativa

¿Cuánta información cabe en una pantalla? Depende del contexto:
- **Dashboard**: alta densidad, usuario experto, tareas repetitivas. Ejemplo: Google Analytics.
- **Landing page**: baja densidad, usuario nuevo, una acción principal. Ejemplo: Stripe.
- **E-commerce**: densidad media, balance entre exploración y decisión. Ejemplo: Amazon (alta) vs. Apple Store (baja).

Regla: la densidad debe coincidir con la experiencia del usuario y la frecuencia de uso. Un usuario diario tolera más densidad que un visitante nuevo.

### Revelación progresiva

No mostrar todo de golpe. Revelar información según el usuario la necesita:
- **Acordeones**: FAQ, detalles de producto.
- **Tabs**: secciones dentro de una página sin recargar.
- **Tooltips**: información complementaria al hacer hover/focus.
- **Modales**: acciones que requieren atención completa (confirmaciones, formularios cortos).
- **Drill-down**: de lista general a detalle específico.

Principio: cada pantalla debe tener un propósito claro y una acción principal. Si tiene 5 acciones igualmente prominentes, no tiene ninguna.

### Wireframes

Un wireframe es un boceto estructural de baja fidelidad. Muestra qué va dónde, no cómo se ve. Sin color, sin imágenes reales, sin tipografía final.

Niveles:
- **Baja fidelidad**: cajas y líneas. Papel o Figma rápido. Para explorar opciones.
- **Media fidelidad**: estructura definida, contenido real (o cercano), jerarquía clara. Para validar con el equipo.
- **Alta fidelidad**: ya es UI. No es wireframe.

Qué debe mostrar un wireframe:
- Jerarquía de contenido (qué es más importante).
- Estructura de la página (header, contenido, sidebar, footer).
- Ubicación de elementos clave (CTA, navegación, formularios).
- Comportamiento responsive (cómo cambia en móvil).
- Anotaciones: notas sobre comportamiento, estados, interacciones.

Error común: hacer wireframes "bonitos". Un wireframe bonito distrae de su propósito: validar estructura. Usar gris, cajas y texto real.

## Agenda

### Mañana (3h)

**Bloque 1: Fundamentos de AI (45 min)**
- Qué es arquitectura de información y por qué importa antes de diseñar.
- Objetivos → Audiencias → Tareas: la cadena de decisiones.
- Modelos mentales vs. modelo del sistema. Card sorting como técnica.
- Ejemplo: reorganizar la navegación de un sitio real aplicando estos principios.

**Bloque 2: Sitemap y navegación (50 min)**
- Sitemap como mapa de territorio: jerarquía, ancho vs. profundidad, naming.
- Tipos de navegación: global, local, contextual, utilitaria, breadcrumbs.
- Principio de Krug: rotulado auto-explicativo.
- Ejercicio rápido: dado un brief, proponer sitemap de 2 niveles en 10 minutos.

Descanso: 10 min

**Bloque 3: Flujos, jerarquía y contenido (45 min)**
- Flujos de usuario: inicio, pasos, decisiones, estados, fin.
- El happy path no es suficiente: diseñar error, vacío, carga, abandono.
- Jerarquía visual: tamaño, peso, contraste, posición, espacio, color.
- Patrones de lectura: F, Z, escaneo. Implicaciones para diseño.
- Densidad informativa y revelación progresiva.

**Bloque 4: Wireframes (30 min)**
- Qué es y qué no es un wireframe. Niveles de fidelidad.
- Qué debe mostrar: jerarquía, estructura, ubicación, responsive, anotaciones.
- Demo rápida: wireframe de una pantalla en 5 minutos (papel o Figma).

### Tarde (3h)

**Bloque 5: Sitemap y navegación del proyecto (60 min)**
- Cada estudiante crea el sitemap de su proyecto (versión 1).
- Definir navegación primaria (máximo 5-7 ítems) y secundaria.
- Justificar agrupación y naming con criterios explícitos.
- Revisión en parejas: ¿el sitemap refleja tareas del usuario o estructura interna?

Descanso: 10 min

**Bloque 6: Flujos principales (50 min)**
- Dibujar 2 flujos principales del proyecto con:
  - Puntos de decisión (rombos).
  - Estados de error y recuperación.
  - Estados intermedios (cargando, procesando, verificando).
  - Confirmación de éxito con próximo paso.
- Peer review: ¿qué pasa si el usuario retrocede? ¿Y si abandona?

**Bloque 7: Wireframes de pantallas clave (50 min)**
- Wireframes de baja-media fidelidad de 2-3 pantallas clave del proyecto.
- Foco en jerarquía de contenido, no en estética.
- Incluir anotaciones: qué cambia en móvil, qué estados tiene cada sección.
- Presentación rápida: 2 minutos por persona, feedback del grupo.

## Trabajo independiente (1h)

- Refinar sitemap y flujos incorporando feedback de clase. Documentar 3 supuestos explícitos sobre el usuario (ejemplo: "asumimos que el usuario ya tiene cuenta creada").
- Tomar 5 capturas de un caso de estudio (sitio/app real) y anotar decisiones de jerarquía: ¿qué se ve primero? ¿Cómo se agrupa? ¿Qué patrón de lectura sugiere?
- Escribir los labels de navegación del proyecto y justificar cada uno en una oración.

## Lecturas y recursos

### Obligatorias
- Krug, S. *Don't Make Me Think* — capítulos 6-7 (navegación y rotulado).
- Rosenfeld, L. & Morville, P. *Information Architecture for the World Wide Web* — capítulo 1 (qué es AI).

### Recomendadas
- Steane, J. *Fundamentos del diseño interactivo* — secciones sobre navegación y estructura.
- Nielsen, J. "F-Shaped Pattern of Reading on the Web" — https://www.nngroup.com/articles/f-shaped-pattern-reading-web-content/
- Optimal Workshop: guía de card sorting — https://www.optimalworkshop.com/learn/card-sorting/

### Herramientas
- FigJam o Miro para sitemaps y flujos colaborativos.
- Optimal Workshop para card sorting remoto.
- Whimsical para wireframes y flujos rápidos.

## Entregables del día

1. **Sitemap del proyecto** (versión 1) con navegación primaria y secundaria justificada.
2. **2 flujos principales** con puntos de decisión, estados de error/vacío/carga y confirmación.
3. **Wireframes de 2-3 pantallas clave** con anotaciones de jerarquía y comportamiento responsive.

## Checklist de calidad

- [ ] La navegación prioriza tareas del usuario, no secciones por costumbre o estructura interna.
- [ ] El sitemap no tiene más de 3 niveles de profundidad.
- [ ] Los labels de navegación son auto-explicativos (sin jerga interna ni creatividad confusa).
- [ ] Los flujos incluyen caminos de error, no solo el happy path.
- [ ] Cada flujo define qué pasa en error, vacío, carga y éxito.
- [ ] Los wireframes muestran jerarquía de contenido sin depender de color ni decoración.
- [ ] Hay anotaciones sobre comportamiento responsive en los wireframes.
- [ ] Los supuestos sobre el usuario están documentados explícitamente.

## Notas para el instructor

- Esta clase es el puente entre lo conceptual (clase 1-2) y lo visual (clase 4). Insistir en que la estructura viene antes que la estética.
- En el ejercicio de sitemap, el error más común es replicar la estructura interna de la empresa. Preguntar: "¿esto es lo que el usuario busca o lo que vos organizarías?"
- En flujos, forzar a pensar en errores: "¿qué pasa si el pago falla?", "¿y si no hay resultados?", "¿y si el usuario cierra el browser a mitad del checkout?"
- En wireframes, vigilar que no se pongan a "diseñar". Si empiezan a elegir colores o tipografías, redirigir: "eso es clase 4, hoy es estructura".
- Cerrar conectando con la siguiente clase: "Hoy definimos el esqueleto. Mañana le ponemos piel: patrones de UI y componentes."

