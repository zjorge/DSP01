---
title: "DSP01 · Clase 02 · Teoría"
revealOptions:
  transition: none
  slideNumber: true
  hash: true
  controls: true
  progress: true
---

# DSP01
## Clase 02 · Teoría

Note:
Fundamentos técnicos que el diseñador debe dominar. Ritmo alto, muchos ejemplos cortos.

---

## Hoy
Fundamentos que el diseñador debe dominar

---

## HTML
No es código

---

## HTML
Es estructura

Note:
HTML no es "programar". Es definir qué ES cada cosa: un título, una lista, un formulario, un enlace.

---

## HTML semántico
El esqueleto de la página

Note:
Semántico = con significado. Cada etiqueta comunica qué rol tiene ese contenido.

---

## Landmarks
Las regiones de la página

---

## Landmarks
header · nav · main · footer

Note:
Los lectores de pantalla saltan entre landmarks. Sin ellos, un usuario ciego navega a ciegas (literalmente).

---

## Landmarks
section · article · aside

Note:
section: grupo temático con heading. article: contenido independiente (post, card de producto). aside: contenido relacionado pero secundario.

---

## Regla
Un `main` por página

---

## Headings
Orden lógico

---

## Headings
h1 → h2 → h3

Note:
Nunca saltar de h1 a h4. Un h1 por página. Los headings crean un outline navegable.

---

## Headings
Nunca saltar niveles

Note:
Si saltas de h2 a h4, el lector de pantalla pierde la estructura. Es como un libro sin capítulos.

---

## Formularios
El punto de fricción

Note:
Los formularios son donde el usuario trabaja. Son el componente más importante y el más ignorado.

---

## Label
Siempre visible, siempre asociado

Note:
Cada input necesita un label. El placeholder NO es un label — desaparece al escribir.

---

## Input type
email · tel · number · date

Note:
El type correcto cambia el teclado en móvil. email muestra @, tel muestra números, date muestra selector.

---

## Errores
Texto + posición + asociación

Note:
Mensaje de error debajo del campo, en texto (no solo color), asociado con aria-describedby.

---

## Elementos nativos
Antes de inventar

Note:
strong, em, code, blockquote, ul, ol, dl. Usar lo nativo antes de crear clases CSS custom.

---

## CSS
No es "estilos"

---

## CSS
Es un modelo mental

Note:
CSS no es una lista de propiedades. Es un sistema de reglas que define cómo fluye el contenido.

---

## Modelo mental
4 capas

---

## 1
Caja

---

## Box model
contenido + padding + border + margin

Note:
Todo en CSS es una caja. Siempre usar box-sizing: border-box para que padding no sume al ancho.

---

## 2
Flujo

---

## Flujo normal
Bloque vs Inline

Note:
Bloque: ocupa todo el ancho, apila vertical (div, p, h1). Inline: ocupa solo su contenido, fluye horizontal (span, a, strong).

---

## Display
Cambia todo

Note:
display es la propiedad más importante de CSS. Cambia cómo un elemento participa en el flujo.

---

## 3
Flex

---

## Flexbox
Un eje, una dirección

Note:
Flex trabaja en un eje principal (row o column). Ideal para barras, cards en fila, layouts lineales.

---

## Flex
gap · wrap · align · justify

Note:
gap: espacio entre items. wrap: permite que los items salten de línea. align: eje secundario. justify: eje principal.

---

## Flex
Navbar · Cards · Barras

---

## 4
Grid

---

## Grid
Dos ejes, filas y columnas

Note:
Grid trabaja en dos dimensiones. Ideal para layouts de página completa, rejillas de productos, dashboards.

---

## Grid
tracks · fr · minmax · gap

Note:
fr = fracción del espacio disponible. minmax(200px, 1fr) = mínimo 200px, máximo lo que sobre. auto-fit/auto-fill para grids responsivas sin media queries.

---

## Grid
Layouts · Rejillas · Páginas

---

## Flex vs Grid
No compiten

Note:
Flex: una dimensión (fila O columna). Grid: dos dimensiones (filas Y columnas). Flex para componentes, Grid para layouts.

---

## Escalas
No inventar medidas

---

## Espaciado
Base 4px u 8px

Note:
4, 8, 12, 16, 24, 32, 48, 64. Escala consistente. Si todo usa múltiplos de 4, el diseño se siente coherente sin esfuerzo.

---

## Tipografía
Steps coherentes

Note:
No inventar tamaños: 12, 14, 16, 18, 20, 24, 32, 40, 48. Cada step tiene un propósito (caption, body, subtitle, title, hero).

---

## Tokens
Nombres, no valores

Note:
No "16px" sino "spacing-md". No "#333" sino "color-text-primary". Los tokens son el contrato entre diseño y código.

---

## Responsive
No es "se achica"

---

## Responsive
Es adaptación al contexto

Note:
Responsive no es hacer lo mismo más chico. Es reorganizar, repriorizar y a veces quitar.

---

## Breakpoints
Definidos por contenido

Note:
No por dispositivo. No "iPhone" ni "iPad". Donde tu contenido se rompe → ahí va un breakpoint.

---

## Referencias
~480 · ~768 · ~1024 · ~1280

Note:
Son referencias, no reglas. Siempre validar con tu contenido. A veces necesitas uno a 600px porque tu sidebar no cabe.

---

## Mobile-first
Priorizar primero

Note:
Empezar por móvil obliga a decidir qué es esencial. Después expandir para desktop — no recortar.

---

## Reflow
3 → 2 → 1

Note:
Columnas que colapsan. Grid de 3 productos → 2 en tablet → 1 en móvil. Navbar horizontal → hamburger.

---

## Imágenes
El mayor peso

Note:
50-70% del peso de una página. WebP reduce 30-50% vs PNG/JPEG. Lazy loading fuera del viewport. srcset para tamaños adaptativos.

---

## Tipografías
Cada peso cuesta

Note:
Cada peso de fuente = ~20-50KB. 6 pesos de Montserrat = ~180KB solo en fuentes. Máximo 2-3 pesos.

---

## JavaScript
Mínimo para diseño

Note:
No vamos a programar. Vamos a entender qué necesita saber un diseñador sobre JS para comunicarse con desarrollo.

---

## Eventos
Lo que el usuario hace

---

## Eventos
click · input · change · submit · focus · blur

Note:
click: toca algo. input: escribe en un campo. change: cambia un select. submit: envía un formulario. focus/blur: entra/sale de un campo.

---

## Estados
Lo que el sistema muestra

---

## Estados
isLoading · hasError · isSuccess

Note:
Flags booleanos que controlan qué se muestra. Si isLoading es true → skeleton. Si hasError → mensaje de error. Si isSuccess → confirmación.

---

## Validación
Nativa primero

Note:
required, pattern, type. El browser ya sabe validar emails, números, campos obligatorios. Usar lo nativo antes de inventar.

---

## JSON
El contrato front-back

Note:
JSON es cómo el frontend y el backend se hablan. Claves claras, tipos conocidos. El diseñador debe saber qué datos existen para diseñar las vistas.

---

## Ejemplo
```json
{
  "name": "Ana López",
  "email": "ana@mail.com",
  "plan": "pro"
}
```

Note:
Esto es lo que el frontend recibe del backend. Si sabes que "name" puede tener 100 caracteres, diseñas para 100 caracteres.

---

## Contextos especiales
Más allá de la pantalla

---

## Plegables
Continuidad

Note:
Dispositivos plegables: la app debe mantener continuidad al cambiar de postura. La bisagra divide la pantalla — decidir qué va en cada lado.

---

## Plegables
Bisagra · Safe areas · Dual screen

Note:
Safe areas: no poner contenido sobre la bisagra. Dual screen: una pantalla para navegación, otra para contenido.

---

## Voz
Intents simples

Note:
Diseño de voz: el usuario dice algo (intent), el sistema confirma, ejecuta o pide aclaración. Siempre fallback a texto.

---

## Voz
Confirmación · Error · Fallback

Note:
"¿Quieres agendar para el martes a las 3?" → Confirmación explícita. Si no entiende → "No entendí, ¿puedes repetir?" Si falla → "Puedes hacerlo desde la app."

---

## Hoy entrenamos

---

## 1
Estructura semántica

---

## 2
Modelo mental de CSS

---

## 3
Diseño con restricciones reales

---

## Mini-checklist
Antes de entregar

---

- Los headings siguen orden lógico
- Hay landmarks claros
- Los formularios tienen labels
- Los breakpoints están escritos

Note:
Si alguna respuesta es "no", la entrega no está lista. Esto aplica para todo el curso.

---

## Pausa
10 minutos

Note:
Cierre del bloque teórico. Después: aplicación al proyecto — mapear pantalla a HTML semántico, definir grilla y breakpoints.

---
