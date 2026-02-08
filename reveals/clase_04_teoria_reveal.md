---
title: "DSP01 · Clase 04 · Teoría"
revealOptions:
  transition: none
  slideNumber: true
  hash: true
  controls: true
  progress: true
---

# DSP01
## Clase 04 · Teoría

Note:
UI: patrones y componentes. La clase más visual hasta ahora. Foco en estados completos y reglas de uso.

---

## Hoy
UI: patrones y componentes

---

## Patrón ≠ Componente

Note:
El patrón es el problema. El componente es la solución visual.

---

## Patrón
Solución recurrente a un problema de interacción

---

## Componente
Implementación visual del patrón

Note:
"Selección múltiple con filtro" es un patrón. Checkboxes con búsqueda, chips, o dropdown multi-select son componentes.

---

## Patrones de navegación

---

## Tabs
2-7 secciones del mismo nivel

---

## Bottom nav
3-5 destinos principales

---

## Hamburger
Último recurso

Note:
Oculta opciones = reduce descubrimiento. Usar solo si no caben en bottom nav.

---

## Patrones de contenido

---

## Cards
Exploración · Contenido heterogéneo

---

## Listas
Escaneo rápido · Contenido homogéneo

---

## Tablas
Comparación · Datos estructurados

---

## Patrones de acción

---

## Modales
Atención completa · Confirmación

Note:
No abusar. Siempre con X, Escape y clic fuera para cerrar.

---

## Toasts
Feedback temporal · No bloqueante

Note:
"Guardado", "Copiado". Auto-dismiss en 3-5 segundos.

---

## Drawers
Contenido secundario · Desde el borde

---

## Estados
La otra mitad del diseño

---

## 9 estados

---

## Default · Hover · Focus
Active · Disabled · Loading
Error · Success · Empty

---

## Focus
Siempre visible

Note:
Es la única forma en que usuarios de teclado saben dónde están. Nunca outline: none sin reemplazo.

---

## Feedback
El usuario necesita saber que el sistema respondió

---

## Inmediato
< 100ms · Hover, press, toggle

---

## Progresivo
1-10s · Loading bar, skeleton

---

## Confirmatorio
Toast, checkmark, cambio de estado

---

## Correctivo
Qué salió mal + cómo arreglarlo

---

## Formularios
Donde más se pierde al usuario

---

## Menos campos
Más conversiones

---

## Labels
Siempre visibles, siempre asociados

---

## Validación progresiva
Al salir del campo, no al enviar

---

## Mensajes de error
Específicos · Debajo del campo · Con ícono

Note:
"Este campo es obligatorio" < "Ingresa tu email" < "El formato debe ser nombre@dominio.com"

---

## Botón de envío
Dice qué va a pasar

Note:
"Crear cuenta" > "Enviar" > "Submit"

---

## No perder datos
Si falla, preservar lo escrito

---

## Vistas de datos
Vacío · Pocos · Muchos · Largos

---

## Multimodalidad
IA y voz

---

## IA en UI
Transparencia · Control · Límites · Fallback

Note:
El usuario siempre puede editar, rechazar o ignorar. Nunca auto-aplicar sin confirmación.

---

## Voz
Turnos cortos · Confirmación · Fallback a pantalla

---

## Mini-checklist

---

- Cada componente tiene estados completos
- Los formularios tienen labels visibles
- El focus es visible en todo elemento interactivo

---

## Pausa
10 minutos

Note:
Cierre teórico. Después: construir kit de componentes en Figma con estados completos.

---
