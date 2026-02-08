---
title: "DSP01 · Clase 05 · Teoría"
revealOptions:
  transition: none
  slideNumber: true
  hash: true
  controls: true
  progress: true
---

# DSP01
## Clase 05 · Teoría

Note:
Figma para sistemas. Clase técnica y práctica. Minimizar teoría, maximizar Figma.

---

## Hoy
Figma para sistemas

---

## De piezas sueltas
A un sistema

Note:
Ayer construimos componentes. Hoy los convertimos en un sistema: Auto Layout, variables, librería.

---

## Auto Layout
La feature más importante de Figma

---

## Auto Layout
Simula CSS Flexbox

Note:
Los elementos hijos se distribuyen automáticamente según reglas definidas.

---

## Dirección
Horizontal (row) · Vertical (column)

---

## Gap
Espacio entre elementos hijos

---

## Padding
Espacio interno del contenedor

---

## Resizing
Fixed · Hug · Fill

Note:
Fixed: tamaño fijo. Hug: se ajusta al contenido. Fill: ocupa todo el espacio disponible.

---

## Hug vs Fill
La diferencia clave

Note:
Hug = el contenedor se adapta al contenido. Fill = el hijo se adapta al contenedor. Confundirlos rompe todo.

---

## Sin Auto Layout
Cambiar "OK" por "Confirmar pedido" rompe el diseño

---

## Con Auto Layout
Se adapta solo

---

## Constraints
Posicionamiento relativo

---

## Constraints
Left · Right · Top · Bottom · Center · Scale

Note:
Para elementos fuera de Auto Layout. Ej: ícono de cerrar siempre en esquina superior derecha del modal.

---

## Grillas responsivas

---

## Móvil
4 columnas · 16px gutter · 375px

---

## Tablet
8 columnas · 24px gutter · 768px

---

## Desktop
12 columnas · 24px gutter · 1440px

---

## Grillas
No son decorativas — son estructura

Note:
Desarrollo las traduce directamente a CSS Grid o Flexbox.

---

## Design tokens
Variables reutilizables

---

## Token
Una decisión de diseño con nombre

Note:
No #007AFF sino color/primary. Si cambia el azul, cambia en todo el sistema.

---

## Color
Primitivos → Semánticos

Note:
Primitivos: blue/500, gray/100. Semánticos: color/primary, color/error. Componentes solo usan semánticos.

---

## Tipografía
5-7 tamaños con nombre

Note:
text/xs (12), text/sm (14), text/base (16), text/lg (18), text/xl (24), text/2xl (32).

---

## Espaciado
Base 4px u 8px

Note:
4, 8, 12, 16, 24, 32, 48, 64. No inventar valores intermedios.

---

## Radius y sombra
También son tokens

---

## Componentes con variantes

---

## Variantes
Hierarchy · Size · State · Icon

Note:
Botón: primary/secondary/ghost × sm/md/lg × default/hover/focus/disabled × none/left/right.

---

## Component Properties
Boolean · Instance swap · Text

---

## Atomic Design
De lo simple a lo complejo

---

## Átomos → Moléculas → Organismos

Note:
Átomos: botón, input, ícono. Moléculas: campo de formulario (label + input + error). Organismos: header, card de producto.

---

## Estructura del archivo

---

## Páginas
Cover · Tokens · Components · UI · Flows · Handoff

Note:
Si alguien abre tu archivo por primera vez, debe entender la estructura en 2 minutos.

---

## Naming
btn/primary/default, no Frame 847

---

## Handoff
Del diseño al código

---

## Handoff
¿Se puede implementar sin preguntarte?

Note:
Medidas, tokens, responsive, estados, assets exportables, anotaciones.

---

## Mini-checklist

---

- Todo usa Auto Layout
- No hay colores hex sueltos
- Las capas tienen nombres descriptivos

---

## Pausa
10 minutos

Note:
Cierre teórico breve. Después: refactorizar componentes con Auto Layout, crear variables, organizar archivo.

---
