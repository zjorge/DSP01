# Clase 10 | Viernes 27

Curso: Diseño y Programación Web (DSP01)

Duración: 6 horas presenciales (3h mañana, 3h tarde). Descansos: 10 min por sesión.

Distribución sugerida del día: 2h teoría, 4h práctica. Trabajo independiente: 1h.

Tema guía del programa: Tema 10. De idea a release

## Objetivos de la sesión

- Cerrar el alcance del proyecto con criterios de éxito medibles y realistas.
- Preparar el archivo Figma como entrega final profesional: sistema de componentes, tokens, prototipo, spec de handoff y documentación.
- Entender el ciclo de vida post-lanzamiento: publicación, medición, iteración y mantenimiento.
- Aplicar principios de privacidad y seguridad desde el nivel de diseño.
- Presentar el proyecto con defensa fundamentada de decisiones de diseño.
- Dar y recibir crítica constructiva como práctica profesional.

## Conceptos clave

### De idea a release: el ciclo completo

El diseño no termina cuando se entrega el archivo Figma. El ciclo completo es:

1. **Descubrimiento**: entender el problema, el usuario y el contexto (clase 01).
2. **Estructura**: arquitectura de información, flujos, navegación (clase 03).
3. **Diseño**: patrones, componentes, sistema de UI (clases 04-06).
4. **Validación**: prototipado, heurísticas, accesibilidad, performance (clases 07-08).
5. **Especificación**: handoff, criterios de aceptación, documentación (clases 05-07).
6. **Implementación**: desarrollo construye basándose en la spec (fuera del curso, pero el diseñador acompaña).
7. **Lanzamiento**: publicar, medir, observar.
8. **Iteración**: analizar datos, identificar mejoras, diseñar cambios, repetir.

El diseñador participa en todo el ciclo, no solo en los pasos 2-5. Después del lanzamiento, los datos reemplazan a las opiniones.

### Alcance final y criterios de éxito

Antes de entregar, definir con precisión:

**Alcance (qué se entrega):**
- Lista explícita de pantallas/flujos incluidos.
- Lista explícita de lo que queda fuera (y por qué).
- Versión del sistema de componentes (v1, con deudas documentadas).
- Plataforma objetivo y restricciones consideradas.

**Criterios de éxito (cómo se mide):**
Los criterios deben ser SMART: específicos, medibles, alcanzables, relevantes y con tiempo definido.

Ejemplos:
- "El 70% de los usuarios completa el flujo de registro en menos de 3 minutos" (medible con analítica).
- "El score de accesibilidad en Lighthouse es ≥ 90" (medible con herramienta).
- "El tiempo de carga en 3G es < 4 segundos" (medible con PageSpeed).
- "La tasa de error en el formulario de checkout se reduce un 30% vs. la versión anterior" (medible con analytics).
- "El NPS post-compra es ≥ 40" (medible con encuesta).

No todos los criterios son cuantitativos. También vale: "El equipo de desarrollo puede implementar la pantalla de producto sin hacer preguntas sobre estados o comportamiento" (medible con observación).

### Publicación y lanzamiento

El lanzamiento no es un evento — es un proceso. Consideraciones:

**Antes del lanzamiento:**
- Verificar que la spec de handoff está completa y actualizada.
- Revisar que los assets están exportados (íconos SVG, imágenes optimizadas, fuentes).
- Confirmar que los criterios de aceptación están escritos y compartidos con desarrollo y QA.
- Definir qué eventos de analítica deben estar implementados antes del lanzamiento.
- Preparar contenido real (no lorem ipsum) para las pantallas principales.

**Durante el lanzamiento:**
- Lanzamiento gradual (si es posible): primero un porcentaje pequeño de usuarios, luego todos. Permite detectar problemas antes de que afecten a todos.
- Monitorear métricas clave en tiempo real: errores, tiempos de carga, conversión.
- Tener un plan de rollback: si algo sale muy mal, poder volver a la versión anterior.

**Después del lanzamiento:**
- Primeras 24-48 horas: monitoreo intensivo. ¿Hay errores? ¿Los embudos funcionan?
- Primera semana: análisis de datos iniciales. ¿Los usuarios hacen lo que esperábamos?
- Primer mes: evaluación contra criterios de éxito. ¿Se cumplieron? ¿Qué ajustar?

### Iteración basada en datos

Después del lanzamiento, el diseño se basa en evidencia, no en intuición.

**Fuentes de datos:**
- **Analítica cuantitativa**: Google Analytics, Mixpanel, Amplitude. Qué hacen los usuarios (números).
- **Analítica cualitativa**: Hotjar, FullStory, grabaciones de sesión. Cómo lo hacen (comportamiento).
- **Feedback directo**: encuestas, entrevistas, soporte al cliente. Por qué lo hacen (motivación).
- **Pruebas A/B**: comparar dos versiones de un diseño con usuarios reales. Cuál funciona mejor (evidencia).

**Proceso de iteración:**
1. **Observar**: ¿qué dicen los datos? ¿Dónde se pierden usuarios? ¿Qué genera errores?
2. **Hipótesis**: "Creemos que si simplificamos el formulario de 8 a 4 campos, la tasa de completado subirá un 20%."
3. **Diseñar**: proponer el cambio en Figma con spec y criterios.
4. **Implementar**: desarrollo construye la variante.
5. **Medir**: ¿la hipótesis se confirmó? ¿Subió la tasa?
6. **Decidir**: si sí, adoptar. Si no, aprender y probar otra cosa.

### Mantenimiento del sistema de diseño

Un sistema de diseño no es un entregable estático — es un producto vivo que requiere mantenimiento.

**Tareas de mantenimiento:**
- **Agregar componentes**: cuando el producto crece, surgen necesidades nuevas. Evaluar si es un componente nuevo o una variante de uno existente.
- **Deprecar componentes**: cuando un componente ya no se usa, marcarlo como deprecated antes de eliminarlo.
- **Actualizar tokens**: si cambia la paleta de colores o la tipografía, actualizar las variables y verificar que todo sigue funcionando.
- **Resolver deuda**: ir pagando la deuda de diseño documentada según prioridad.
- **Sincronizar con código**: verificar periódicamente que los componentes en Figma coinciden con los componentes en código.

**Gobernanza:**
- ¿Quién puede agregar componentes al sistema? ¿Cualquiera o solo el equipo de diseño?
- ¿Cómo se proponen cambios? ¿Hay un proceso de revisión?
- ¿Con qué frecuencia se revisa el sistema? Trimestral es un buen punto de partida.

### Privacidad y seguridad desde diseño

Repaso y profundización de lo visto en clase 08, aplicado al proyecto final:

**Privacidad (lo que se recolecta):**
- Auditar el proyecto: ¿qué datos se piden? ¿Todos son necesarios?
- Consentimiento: ¿es claro, informado y no manipulativo?
- Retención: ¿cuánto tiempo se guardan los datos? ¿Se pueden eliminar?
- Terceros: ¿se comparten datos con servicios externos? (analytics, ads, CRM) ¿El usuario lo sabe?

**Seguridad (cómo se protege):**
- Contraseñas: nunca mostrar en texto plano. Indicador de fortaleza. Requisitos claros.
- Datos sensibles: tarjetas de crédito enmascaradas (•••• •••• •••• 4242). Datos personales ocultos por defecto.
- Sesiones: timeout después de inactividad. Opción de cerrar sesión en todos los dispositivos.
- Permisos: principio de mínimo privilegio. Cada rol ve solo lo que necesita.
- HTTPS: todo el sitio debe usar HTTPS. No es decisión de diseño, pero sí verificable.

**Checklist de privacidad para el proyecto:**
- ¿Cada dato pedido tiene una justificación clara?
- ¿El usuario puede ver, editar y eliminar sus datos?
- ¿Los mensajes de consentimiento son honestos y comprensibles?
- ¿Los datos sensibles están protegidos visualmente?
- ¿Se documentó qué terceros reciben datos del usuario?

### Presentación y defensa de decisiones

Presentar un proyecto de diseño no es mostrar pantallas bonitas — es defender decisiones con fundamento.

**Estructura de presentación recomendada (10-15 minutos):**

1. **Problema** (1-2 min): ¿Qué problema resuelve? ¿Para quién? ¿En qué contexto? Conectar con la definición de clase 01.
2. **Investigación** (1-2 min): ¿Qué descubriste? Auditoría, casos de estudio, supuestos validados.
3. **Arquitectura** (1-2 min): Sitemap, flujos principales, decisiones de navegación. Por qué esta estructura.
4. **Sistema de diseño** (2-3 min): Tokens, componentes clave, variantes. Mostrar la lógica, no cada componente.
5. **Prototipo** (2-3 min): Demo del flujo principal. Mostrar happy path + al menos 1 estado de error. Destacar microcopy y estados.
6. **Calidad** (1-2 min): Hallazgos de la auditoría (accesibilidad, performance). Correcciones aplicadas. Deuda documentada.
7. **Plataforma y medición** (1 min): Plataforma elegida y por qué. Eventos de analítica y embudo. Criterios de éxito.
8. **Próximos pasos** (1 min): Qué haría si tuviera 2 semanas más. Riesgos identificados.

**Principios de defensa:**
- **Fundamentar, no justificar**: "Elegí 4 columnas en móvil porque el contenido es texto corto y necesita espacio para respirar" > "Me pareció que se veía mejor así".
- **Reconocer limitaciones**: "No tuve tiempo de diseñar el flujo de recuperación de contraseña. Está documentado como deuda." Es más profesional que pretender que no existe.
- **Conectar con datos**: "El 53% del tráfico es móvil, por eso prioricé mobile-first" > "Hice mobile-first porque es la tendencia".
- **Aceptar crítica**: "Buen punto, no lo había considerado. Lo agregaría como mejora en la siguiente iteración."

### Crítica constructiva

Dar y recibir feedback es una habilidad profesional. Reglas:

**Al dar feedback:**
- Ser específico: "El contraste del texto secundario en la card no cumple 4.5:1" > "No me gusta el color".
- Ser accionable: "Sugiero aumentar el peso del texto a medium para mejorar legibilidad" > "Hay que arreglarlo".
- Balancear: empezar con algo que funciona bien, luego lo que se puede mejorar.
- Preguntar antes de asumir: "¿Consideraste el estado de error aquí?" > "Falta el estado de error".

**Al recibir feedback:**
- Escuchar sin defender inmediatamente.
- Anotar todo. Evaluar después con calma.
- Preguntar para clarificar: "¿Podés darme un ejemplo de lo que querés decir?"
- No tomarlo personal. El feedback es sobre el trabajo, no sobre vos.

## Agenda

### Mañana (3h)

**Bloque 1: Cierre de alcance y criterios de éxito (40 min)**
- Revisar el alcance del proyecto: ¿qué se entrega y qué queda fuera?
- Definir criterios de éxito SMART para el proyecto.
- Verificar que la deuda de diseño está documentada y priorizada.
- Ejercicio: cada estudiante escribe 3 criterios de éxito medibles para su proyecto.

**Bloque 2: Publicación, iteración y mantenimiento (45 min)**
- El ciclo completo: de idea a release y vuelta.
- Antes, durante y después del lanzamiento. Qué monitorear.
- Iteración basada en datos: observar → hipótesis → diseñar → medir → decidir.
- Mantenimiento del sistema de diseño: agregar, deprecar, actualizar, sincronizar.
- Gobernanza: quién decide qué entra al sistema.

Descanso: 10 min

**Bloque 3: Privacidad, seguridad y checklist final (40 min)**
- Repaso de privacidad y seguridad aplicado al proyecto final.
- Checklist de privacidad: datos necesarios, consentimiento, retención, terceros.
- Seguridad visual: contraseñas, datos sensibles, sesiones, permisos.
- Checklist final de handoff: ¿el archivo está listo para entregar?

**Bloque 4: Preparación de presentación (35 min)**
- Estructura de presentación: problema, investigación, arquitectura, sistema, prototipo, calidad, plataforma, próximos pasos.
- Principios de defensa: fundamentar, reconocer limitaciones, conectar con datos, aceptar crítica.
- Reglas de crítica constructiva: específica, accionable, balanceada.
- Tiempo para preparar la presentación (inicio).

### Tarde (3h)

**Bloque 5: Checklist final y pulido (45 min)**
- Cada estudiante revisa su archivo Figma con el checklist final:
  - ¿Las páginas están organizadas? (Cover, Tokens, Components, UI, Flows, Handoff)
  - ¿Los componentes tienen variantes y estados completos?
  - ¿Los tokens están aplicados consistentemente?
  - ¿La spec de handoff tiene medidas, tokens, responsive, estados, microcopy, criterios?
  - ¿La documentación del sistema es navegable?
  - ¿La deuda está documentada?
  - ¿Los criterios de aceptación están escritos?
- Aplicar ajustes finales.

Descanso: 10 min

**Bloque 6: Presentaciones (90 min)**
- Cada estudiante presenta su proyecto (10-15 minutos según tamaño del grupo):
  - Presentación siguiendo la estructura recomendada.
  - Demo del prototipo en vivo.
  - Defensa de decisiones.
- Después de cada presentación:
  - 2-3 preguntas del grupo.
  - Feedback breve del instructor: 1 fortaleza + 1 mejora.

**Bloque 7: Cierre del curso (15 min)**
- Reflexión grupal: ¿qué aprendimos? ¿Qué cambió en cómo pensamos el diseño web?
- Recursos para seguir aprendiendo.
- Evaluación del curso (si aplica).
- Cierre: "Diseñar para web es negociar entre intención creativa y restricción técnica. Ahora tienen las herramientas para hacerlo con criterio."

## Trabajo independiente (1h)

- Pulir el archivo Figma para entrega final: limpieza de capas, organización de páginas, naming consistente, documentación completa.
- Escribir 1 página de cierre del proyecto:
  - **Riesgos identificados**: qué podría salir mal en implementación y cómo mitigarlo.
  - **Próximos pasos**: qué haría con 2 semanas más de trabajo (priorizado).
  - **Medición a 30 días**: qué métricas revisaría un mes después del lanzamiento y qué decisiones tomaría según los resultados.
- Verificar que todos los entregables del curso están completos y organizados.

## Lecturas y recursos

### Obligatorias
- Krug, S. *Don't Make Me Think* — capítulo 9 (pruebas de usabilidad rápidas y baratas).
- Google: "HEART Framework" para métricas de UX — https://research.google/pubs/pub36299/

### Recomendadas
- Croll, A. & Yoskovitz, B. *Lean Analytics* — capítulos 1-3 (métricas que importan, vanity metrics vs. actionable metrics).
- Intercom: "Intercom on Product Management" — https://www.intercom.com/books/product-management
- Nielsen Norman Group: "How to Present UX Research and Design Work" — https://www.nngroup.com/articles/presenting-ux-research/

### Herramientas
- Google Analytics 4 para medición post-lanzamiento.
- Hotjar para mapas de calor y grabaciones.
- Loom para grabar presentaciones de diseño asíncronas.
- Notion o Confluence para documentación de proyecto a largo plazo.

## Entregables del día (entrega final del curso)

1. **Archivo Figma completo**:
   - Sistema de componentes con variantes, propiedades y tokens.
   - Variables/tokens documentados (color, tipografía, espaciado, radius, sombra).
   - Prototipo navegable del flujo principal con estados (happy path + error + empty + loading).
   - Spec de handoff para pantallas clave (medidas, tokens, responsive, estados, microcopy).
   - Página de documentación del sistema (nombre, propósito, variantes, do/don't por componente).
2. **Reporte heurístico y de accesibilidad final** (1-2 páginas): hallazgos con severidad, correcciones aplicadas, deuda documentada.
3. **Lista de criterios de aceptación** por pantalla o flujo principal (Dado/Cuando/Entonces).
4. **Mapa de contenido** con tipos, campos, fuentes, responsables y restricciones.
5. **Eventos de analítica** y embudo principal con métricas anticipadas.
6. **Página de cierre**: riesgos, próximos pasos y plan de medición a 30 días.

## Checklist de calidad (entrega final)

- [ ] El archivo Figma tiene estructura de páginas clara y organizada.
- [ ] Los componentes tienen variantes completas y estados diseñados (no solo descritos).
- [ ] Los tokens están aplicados consistentemente en todo el archivo.
- [ ] El prototipo incluye happy path, estados de error, empty state y loading.
- [ ] La spec de handoff permite implementar sin adivinar (medidas, tokens, responsive, estados, microcopy, criterios).
- [ ] La documentación del sistema responde "¿qué es?", "¿cómo lo uso?" y "¿qué no debo hacer?" por componente.
- [ ] El reporte de auditoría tiene hallazgos con severidad y correcciones aplicadas.
- [ ] Los criterios de aceptación son específicos y testeables (Dado/Cuando/Entonces).
- [ ] El mapa de contenido tiene restricciones de longitud/formato por tipo.
- [ ] Los eventos de analítica cubren el flujo principal con nombre, trigger y datos.
- [ ] La deuda de diseño está documentada explícitamente (no es invisible).
- [ ] La propuesta respeta privacidad: datos mínimos, consentimiento claro, sin dark patterns.
- [ ] La presentación defiende decisiones con fundamento, no con opiniones.

## Notas para el instructor

- Esta es la clase de cierre. El tono debe ser de celebración y consolidación, no de presión. Los estudiantes han trabajado 10 sesiones intensivas — reconocer el esfuerzo.
- En el bloque de alcance y criterios, verificar que los criterios de éxito sean realmente medibles. "Que se vea profesional" no es medible. "Score de Lighthouse ≥ 90" sí.
- En publicación e iteración, ser realistas: la mayoría de los proyectos del curso no se van a lanzar. Pero el proceso mental es el mismo y es lo que importa.
- En las presentaciones, mantener el tiempo estricto (10-15 min por persona). Usar timer visible. Las preguntas deben ser constructivas, no interrogatorios.
- Dar feedback específico y accionable después de cada presentación. Evitar generalidades como "muy bien" o "falta trabajo". Mejor: "La decisión de usar bottom nav con 4 ítems está bien fundamentada. Sugiero agregar el estado de loading en la tabla de pedidos."
- Si el grupo es grande (>8), considerar presentaciones en paralelo o reducir a 8 minutos por persona.
- Cerrar con energía y conexión: "Hace 10 sesiones no sabían qué era un criterio de aceptación ni por qué importa el contraste. Hoy entregan un sistema completo con fundamento. Eso es crecimiento real."
- Recordar que la evaluación se basa en implementabilidad: ¿se puede construir lo que entregaron sin adivinar? Esa es la señal de madurez profesional.

