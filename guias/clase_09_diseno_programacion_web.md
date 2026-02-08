# Clase 09 | Jueves 26

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 9. Contenido y plataformas

## Objetivos de la sesión

- Entender el ecosistema de plataformas web y los criterios para elegir la correcta según el tipo de proyecto, equipo y presupuesto.
- Distinguir entre website builders, plataformas de e-commerce, CMS headless y arquitectura moderna (JAMstack, SSR, SSG).
- Diseñar pensando en contenido dinámico: tipos de contenido, campos, fuentes, responsables y frecuencia de actualización.
- Diseñar vistas complejas tipo SaaS: dashboards, tablas de datos, filtros, permisos y roles.
- Entender la arquitectura conceptual de un producto web: frontend, backend, CMS, APIs y bases de datos.
- Definir eventos de analítica que permitan medir el éxito del producto después del lanzamiento.

## Conceptos clave

### El ecosistema de plataformas web

No todo se construye desde cero. La mayoría de proyectos web usan alguna plataforma o framework como base. Elegir bien ahorra meses de trabajo; elegir mal genera deuda técnica y frustración.

**Categorías principales:**

| Categoría | Ejemplos | Ideal para | Limitaciones |
|-----------|----------|------------|-------------|
| Website builders | Webflow, Framer, Squarespace, Wix, ReadyMag | Sitios informativos, portfolios, landing pages, sitios de 5-20 páginas | Personalización limitada, dependencia del vendor, escalabilidad |
| E-commerce | Shopify, WooCommerce, BigCommerce | Tiendas online, catálogos, checkout | Restricciones de diseño en checkout, costos por transacción, temas |
| CMS headless | Sanity, Contentful, Strapi, Payload, Directus | Contenido dinámico, multi-canal, equipos con desarrolladores | Requiere desarrollo frontend, más complejidad inicial |
| Frameworks | Next.js, Nuxt, Astro, SvelteKit, Remix | Apps complejas, SaaS, dashboards, productos a medida | Requiere equipo de desarrollo, más tiempo de setup |
| No-code/Low-code | Bubble, Retool, Airtable, Notion | MVPs rápidos, herramientas internas, prototipos funcionales | Escalabilidad, performance, vendor lock-in |

### Criterios de selección de plataforma

La plataforma correcta depende del contexto, no de la moda. Evaluar con estos criterios:

1. **Tipo de contenido**: ¿es estático (about, servicios) o dinámico (blog, productos, usuarios)? ¿Quién lo actualiza y con qué frecuencia?
2. **Complejidad de interacción**: ¿es informativo (leer) o transaccional (comprar, reservar, gestionar)? ¿Hay formularios complejos, dashboards, permisos?
3. **Equipo disponible**: ¿hay desarrolladores? ¿Solo diseñadores? ¿El cliente va a mantenerlo solo?
4. **Presupuesto**: builders son baratos al inicio pero caros al escalar. Desarrollo custom es caro al inicio pero flexible a largo plazo.
5. **Tiempo**: ¿cuándo necesita estar listo? Un builder puede estar en 2 semanas. Un desarrollo custom puede tomar 2-3 meses.
6. **Escalabilidad**: ¿va a crecer? ¿Más páginas, más usuarios, más funcionalidades? ¿La plataforma lo soporta?
7. **SEO y performance**: ¿importa el posicionamiento en buscadores? ¿La plataforma genera HTML limpio y rápido?
8. **Integraciones**: ¿necesita conectarse con otros servicios? (pasarelas de pago, CRM, email marketing, analytics)

### Website builders en detalle

**Webflow**
- Diseño visual con output de código limpio (HTML/CSS/JS).
- CMS integrado para contenido dinámico (blog, portfolio, catálogo).
- Hosting incluido con CDN.
- Ideal para: diseñadores que quieren control total sin escribir código.
- Limitación: lógica compleja (autenticación, permisos, cálculos) requiere integraciones externas.

**Framer**
- Enfocado en diseño interactivo y animaciones.
- Integración directa con Figma.
- Bueno para: landing pages, sitios de producto, portfolios con mucha animación.
- Limitación: CMS básico, no ideal para sitios con mucho contenido dinámico.

**Squarespace / Wix**
- Templates prediseñados, editor drag-and-drop.
- Ideal para: clientes no técnicos que necesitan un sitio rápido y lo van a mantener solos.
- Limitación: personalización limitada, código generado pesado, difícil de migrar.

**ReadyMag**
- Enfocado en diseño editorial y creativo.
- Ideal para: portfolios de diseño, revistas digitales, presentaciones interactivas.
- Limitación: no es para apps ni e-commerce.

### E-commerce: Shopify como caso práctico

Shopify es la plataforma de e-commerce más usada para tiendas pequeñas y medianas. Entender sus restricciones es clave para diseñar dentro de lo posible.

**Páginas clave de un e-commerce:**
1. **Home**: hero, categorías destacadas, productos populares, propuesta de valor.
2. **Colección/Categoría**: grid de productos con filtros (precio, talla, color, disponibilidad) y ordenamiento.
3. **Producto**: imágenes, título, precio, variantes (talla, color), descripción, reviews, "Agregar al carrito".
4. **Carrito**: lista de productos, cantidades editables, subtotal, botón de checkout.
5. **Checkout**: datos de envío, método de pago, resumen del pedido, confirmación. En Shopify, el checkout tiene personalización limitada (solo Shopify Plus permite cambios profundos).
6. **Cuenta de usuario**: pedidos, direcciones, wishlist.
7. **Búsqueda**: resultados con filtros, sugerencias, "no encontramos resultados".

**Restricciones de diseño en Shopify:**
- El checkout estándar tiene diseño fijo (colores y logo, pero no layout).
- Los temas usan Liquid (lenguaje de templates propio). Personalización requiere conocer Liquid.
- Las secciones son modulares: el cliente puede reordenar bloques en el editor de temas.
- Performance depende del tema: temas pesados con muchas apps = sitio lento.

### CMS headless

Un CMS headless separa el contenido (backend) de la presentación (frontend). El contenido se gestiona en el CMS y se consume vía API desde cualquier frontend (web, app, kiosko, reloj).

**Ventajas:**
- Contenido reutilizable en múltiples canales.
- Frontend con total libertad de diseño y tecnología.
- Mejor performance (se puede usar SSG o SSR).
- Escalabilidad: el CMS escala independientemente del frontend.

**Desventajas:**
- Requiere desarrollo frontend (no es drag-and-drop).
- Más complejidad inicial de setup.
- El cliente necesita una interfaz de edición (el CMS la provee, pero hay que configurarla).

**Ejemplos:**
- **Sanity**: flexible, schema en código, real-time editing, generoso free tier.
- **Contentful**: enterprise, API robusta, buena documentación.
- **Strapi**: open source, self-hosted, personalizable.
- **Payload**: open source, TypeScript-first, integrado con Next.js.

### Arquitectura conceptual para diseñadores

Un diseñador no necesita saber programar, pero sí entender cómo se conectan las piezas:

```
[Usuario] → [Browser] → [Frontend (lo que se ve)]
                              ↕
                         [API / Backend (la lógica)]
                              ↕
                    [Base de datos + CMS (el contenido)]
```

**Frontend**: lo que el usuario ve e interactúa. HTML, CSS, JavaScript. Frameworks: React, Vue, Svelte. Meta-frameworks: Next.js, Nuxt, Astro.

**Backend / API**: la lógica del negocio. Autenticación, permisos, procesamiento de pagos, envío de emails. El frontend le "pide" datos al backend vía API (endpoints).

**Base de datos**: donde se guardan los datos. Usuarios, productos, pedidos, contenido. El diseñador no la toca, pero debe saber qué datos existen para diseñar las vistas.

**CMS**: donde el equipo de contenido edita textos, imágenes, productos. Puede ser parte del backend (WordPress, Shopify) o separado (headless).

**CDN**: red de distribución de contenido. Sirve imágenes, fuentes y archivos estáticos desde servidores cercanos al usuario. Reduce latencia.

### Contenido como sistema

El contenido no es "lo que va en la página" — es un sistema con estructura, reglas y responsables.

**Mapa de contenido:**

Para cada tipo de contenido, definir:

| Campo | Ejemplo: Producto | Ejemplo: Artículo de blog |
|-------|-------------------|--------------------------|
| Nombre del tipo | Producto | Artículo |
| Campos | título, descripción, precio, imágenes, categoría, variantes, SKU, stock | título, autor, fecha, cuerpo, imagen destacada, categoría, tags |
| Fuente | equipo de producto / importación CSV | equipo de contenido / editor |
| Responsable | product manager | content manager |
| Frecuencia de cambio | semanal (precios, stock) | 2-3 por semana |
| Restricciones | título máx 80 chars, descripción máx 500 chars, mín 1 imagen | título máx 100 chars, imagen 16:9, mín 300 palabras |

Este mapa es esencial para diseñar: si sabés que el título puede tener 80 caracteres, diseñás para 80 caracteres (no para "Producto X").

### Diseño de dashboards y vistas SaaS

Un dashboard es una vista que muestra datos agregados y permite tomar decisiones. Es el tipo de interfaz más complejo porque combina alta densidad de información con necesidad de claridad.

**Principios de diseño de dashboards:**
1. **Priorizar por acción**: ¿qué necesita hacer el usuario? Los datos más accionables arriba.
2. **Jerarquía de información**: KPIs grandes arriba, detalles en tablas abajo, filtros accesibles.
3. **Filtros visibles**: los más usados siempre visibles. Los demás en "más filtros". Mostrar filtros activos y forma de limpiarlos.
4. **Tablas bien diseñadas**: 
   - Alineación: texto a la izquierda, números a la derecha, fechas consistentes.
   - Columnas ordenables (clic en header).
   - Filas con hover highlight.
   - Acciones por fila (editar, eliminar, ver detalle) al final o en menú contextual.
   - Responsive: colapsar columnas secundarias o convertir a cards en móvil.
5. **Paginación o scroll**: paginación para datos que se consultan, infinite scroll para feeds.
6. **Estados**: vacío ("No hay datos para este período"), loading (skeleton de tabla), error ("No pudimos cargar los datos. Reintentar.").
7. **Permisos**: no todos ven lo mismo. Admin ve todo, editor ve su contenido, viewer solo lee. Diseñar las variaciones.

### Analítica: medir para iterar

Diseñar sin medir es adivinar. La analítica permite saber si las decisiones de diseño funcionan.

**Tipos de eventos:**
- **Pageview**: el usuario llegó a una página. Básico pero esencial.
- **Click**: el usuario hizo clic en algo específico (CTA, link, botón).
- **Form submit**: el usuario envió un formulario.
- **Scroll depth**: hasta dónde scrolleó (25%, 50%, 75%, 100%).
- **Error**: algo falló (formulario con error, 404, timeout).
- **Conversión**: el usuario completó una tarea clave (compra, registro, reserva).
- **Engagement**: tiempo en página, interacciones, vistas de contenido.

**Embudo (funnel):**
Un embudo es la secuencia de pasos que lleva a una conversión. Ejemplo para e-commerce:
1. Home → 2. Categoría → 3. Producto → 4. Agregar al carrito → 5. Checkout → 6. Confirmación

En cada paso se pierde un porcentaje de usuarios. Medir dónde se pierden más indica dónde mejorar el diseño.

**Eventos del proyecto:**
Definir 8-10 eventos clave del flujo principal. Para cada evento:
- Nombre del evento (ej: `product_view`, `add_to_cart`, `checkout_start`)
- Cuándo se dispara (ej: "cuando el usuario hace clic en Agregar al carrito")
- Qué datos incluye (ej: `product_id`, `price`, `quantity`)
- Por qué importa (ej: "mide intención de compra")

## Agenda

### Mañana (3h)

**Bloque 1: Ecosistema de plataformas (50 min)**
- Panorama: builders, e-commerce, CMS headless, frameworks, no-code.
- Criterios de selección: tipo de contenido, complejidad, equipo, presupuesto, tiempo, escalabilidad, SEO, integraciones.
- Website builders en detalle: Webflow, Framer, Squarespace, Wix, ReadyMag. Pros, contras, cuándo usar cada uno.
- Demo rápida: recorrer un sitio hecho en Webflow y uno en Framer. Analizar output.

**Bloque 2: E-commerce y CMS headless (45 min)**
- Shopify como caso práctico: páginas clave, restricciones de diseño, temas, checkout.
- CMS headless: Sanity, Contentful, Strapi, Payload. Qué resuelven y qué exigen.
- Arquitectura conceptual: frontend → API → backend → base de datos → CMS → CDN.
- Ejercicio: dado un brief de proyecto, elegir plataforma y justificar con 5 criterios.

Descanso: 10 min

**Bloque 3: Contenido como sistema (40 min)**
- Mapa de contenido: tipos, campos, fuentes, responsables, frecuencia de cambio, restricciones.
- Por qué importa para diseño: si el título puede tener 200 caracteres, diseñá para 200 caracteres.
- Contenido estático vs. dinámico. Contenido editable vs. fijo.
- Ejercicio: crear mapa de contenido para 3 tipos del proyecto propio.

**Bloque 4: Analítica y medición (35 min)**
- Por qué medir: diseñar sin datos es adivinar.
- Tipos de eventos: pageview, click, form submit, scroll, error, conversión, engagement.
- Embudos: secuencia de pasos hacia conversión. Dónde se pierden usuarios.
- Ejercicio: definir 8 eventos clave del flujo principal del proyecto.

### Tarde (3h)

**Bloque 5: Decisión de plataforma (45 min)**
- Cada estudiante elige la plataforma objetivo para su proyecto.
- Justificar con al menos 5 criterios documentados.
- Identificar restricciones de la plataforma que afectan el diseño.
- Revisión en parejas: ¿la plataforma elegida es realista para el alcance y equipo?

Descanso: 10 min

**Bloque 6: Dashboard y vistas complejas (60 min)**
- Diseñar una vista tipo SaaS para el proyecto (si aplica) o un ejercicio genérico:
  - Dashboard con KPIs, tabla de datos, filtros.
  - Permisos básicos: qué ve admin vs. editor vs. viewer.
  - Estados: vacío, loading, error, datos extremos (1000 filas).
- Principios de diseño de tablas: alineación, ordenamiento, acciones, responsive.

**Bloque 7: Mapa de contenido y analítica (45 min)**
- Completar mapa de contenido del proyecto: todos los tipos de contenido con campos, fuentes, responsables y restricciones.
- Completar lista de eventos de analítica: 8-10 eventos con nombre, trigger, datos y justificación.
- Definir el embudo principal del proyecto: pasos, métricas esperadas, dónde se anticipan pérdidas.
- Presentación rápida: 2 minutos por persona, plataforma elegida + embudo principal.

## Trabajo independiente (1h)

- Escribir el mapa de contenido completo del proyecto: todos los tipos de contenido con campos, fuentes, responsables, frecuencia de cambio y restricciones de longitud/formato.
- Definir 8-10 eventos de analítica del flujo principal con nombre, trigger, datos incluidos y justificación.
- Dibujar el embudo principal del proyecto: pasos, conversión esperada por paso, y dónde se anticipan los mayores abandonos.
- Documentar las restricciones de la plataforma elegida que afectan decisiones de diseño (ej: "el checkout de Shopify no se puede personalizar en layout").

## Lecturas y recursos

### Obligatorias
- Shopify Polaris: componentes de tabla y filtros — https://polaris.shopify.com/components/tables
- MDN: "Using Fetch" (visión conceptual de cómo frontend pide datos) — https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch

### Recomendadas
- Webflow University: introducción — https://university.webflow.com/
- Sanity.io: documentación y conceptos — https://www.sanity.io/docs
- Google Analytics 4: guía de eventos — https://support.google.com/analytics/answer/9322688
- Shopify: guía de diseño de temas — https://shopify.dev/docs/themes

### Herramientas
- Webflow o Framer para prototipos funcionales sin código.
- Sanity Studio o Contentful para explorar interfaces de CMS.
- Google Analytics 4 o Mixpanel para analítica de producto.
- Hotjar o FullStory para mapas de calor y grabaciones de sesión.

## Entregables del día

1. **Decisión de plataforma** con justificación de al menos 5 criterios y restricciones documentadas.
2. **Mapa de contenido** (versión 1): todos los tipos de contenido con campos, fuentes, responsables y restricciones.
3. **Lista de eventos de analítica** (versión 1): 8-10 eventos con nombre, trigger, datos y justificación.
4. **Embudo principal** del proyecto con pasos y métricas anticipadas.

## Checklist de calidad

- [ ] La plataforma elegida coincide con el alcance, equipo y presupuesto del proyecto.
- [ ] Las restricciones de la plataforma están documentadas y consideradas en el diseño.
- [ ] El mapa de contenido separa contenido de presentación (los campos son datos, no estilos).
- [ ] Cada tipo de contenido tiene restricciones de longitud/formato definidas.
- [ ] Los eventos de analítica cubren el flujo principal completo (no solo pageviews).
- [ ] El embudo tiene pasos claros con métricas anticipadas.
- [ ] Si hay dashboard: las tablas tienen alineación correcta, filtros visibles y estados definidos.
- [ ] Si hay permisos: las variaciones por rol están diseñadas (no solo descritas).

## Notas para el instructor

- Esta clase es un cambio de perspectiva: de "cómo se ve" a "dónde vive y cómo se mide". Algunos estudiantes pueden sentir que no es "diseño" — enfatizar que elegir la plataforma correcta y definir el contenido ES diseño.
- En plataformas, evitar ser dogmático. No hay plataforma "mejor" — hay plataformas más adecuadas para cada contexto. Webflow no es mejor que Shopify; resuelven problemas diferentes.
- En Shopify, si hay estudiantes con proyectos de e-commerce, profundizar en las restricciones reales del checkout y los temas. Es donde más chocan diseño e implementación.
- En CMS headless, mantenerlo conceptual. No es una clase de desarrollo — es entender qué es posible y qué requiere.
- En analítica, el error más común es definir eventos vagos. "El usuario interactúa" no es un evento. "El usuario hace clic en Agregar al carrito en la página de producto" sí lo es.
- En dashboards, usar ejemplos reales: Google Analytics, Shopify Admin, Notion. Mostrar cómo manejan densidad, filtros y estados.
- Cerrar conectando con clase 10: "Hoy definimos dónde vive el producto y cómo lo medimos. Mañana cerramos: entrega final, presentación y defensa de decisiones."

