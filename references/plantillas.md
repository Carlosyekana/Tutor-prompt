# Referencia de Plantillas de Prompts

Biblioteca completa de plantillas para Maestro de Prompts. Lee la plantilla relevante cuando el tipo de tarea del usuario coincida. No cargues todas las plantillas a la vez — solo la que necesites.

## Tabla de Contenidos

| Plantilla | Mejor Para |
|-----------|------------|
| [A — RTF](#plantilla-a--rtf) | Tareas simples de una sola pasada |
| [B — CO-STAR](#plantilla-b--co-star) | Documentos profesionales, escritura de negocios |
| [C — RISEN](#plantilla-c--risen) | Proyectos complejos de múltiples pasos |
| [D — CRISPE](#plantilla-d--crispe) | Trabajo creativo, voz de marca |
| [E — Razonamiento Auditable](#plantilla-e--razonamiento-auditable) | Lógica, matemáticas, análisis, depuración |
| [F — Few-Shot](#plantilla-f--few-shot) | Salida estructurada consistente, replicación de patrones |
| [G — Alcance de Archivo](#plantilla-g--alcance-de-archivo) | Cursor, Windsurf, Copilot — IA de edición de código |
| [H — ReAct + Condiciones de Parada](#plantilla-h--react--condiciones-de-parada) | Claude Code, Devin — agentes autónomos |
| [I — Descriptor Visual](#plantilla-i--descriptor-visual) | Midjourney, DALL-E, Stable Diffusion, Sora |
| [J — Edición de Imagen de Referencia](#plantilla-j--edición-de-imagen-de-referencia) | Editar una imagen existente con una referencia |
| [K — ComfyUI](#plantilla-k--comfyui) | Flujos de trabajo de imágenes basados en nodos de ComfyUI |
| [L — Decompilador de Prompts](#plantilla-l--decompilador-de-prompts) | Descomponer, adaptar o dividir prompts existentes |
| [M — Brief de Tarea para Claude Actual](#plantilla-m--brief-de-tarea-para-claude-actual) | Tarea compleja, de múltiples pasos o agente en modelos Claude actuales |

---

## Plantilla A — RTF

*Rol, Tarea, Formato. Úsala para tareas rápidas de una sola pasada donde la solicitud es clara y simple.*

```
Rol: [Una oración definiendo quién es la IA]
Tarea: [Verbo preciso + qué producir]
Formato: [Formato exacto de salida y longitud]
```

**Ejemplo:**
```
Rol: Eres un escritor técnico senior.
Tarea: Escribe un párrafo describiendo qué es una API REST.
Formato: Prosa simple, máximo 3 oraciones, sin jerga, adecuado para una audiencia no técnica.
```

---

## Plantilla B — CO-STAR

*Contexto, Objetivo, Estilo, Tono, Audiencia, Respuesta. Úsala para documentos profesionales, escritura de negocios, reportes y contenido de marketing donde el control total del contexto importa.*

```
Contexto: [Antecedentes que la IA necesita para entender la situación]
Objetivo: [Meta exacta — qué se ve como éxito]
Estilo: [Estilo de escritura: formal / conversacional / técnico / narrativo]
Tono: [Registro emocional: autoritario / empático / urgente / neutral]
Audiencia: [Quién lee esto — su nivel de conocimiento y expectativas]
Respuesta: [Formato, longitud y estructura de la salida]
```

**Ejemplo:**
```
Contexto: Soy un fundador presentando una herramienta SaaS B2B que automatiza reportes de gastos para empresas medianas.
Objetivo: Escribe un email frío que obtenga una respuesta de un CFO.
Estilo: Directo y conversacional, no comercial.
Tono: Confidente pero no insistente.
Audiencia: CFO en una empresa de 200 personas, ocupado, escéptico de emails de vendedores.
Respuesta: Máximo 5 oraciones. Línea de asunto incluida. Sin viñetas.
```

---

## Plantilla C — RISEN

*Rol, Instrucciones, Pasos, Meta Final, Acotamiento. Úsala para proyectos complejos, tareas de múltiples pasos y cualquier salida que requiera una secuencia clara de acciones.*

```
Rol: [Identidad experta que la IA debe adoptar]
Instrucciones: [Tarea general en términos simples]
Pasos:
  1. [Primera acción]
  2. [Segunda acción]
  3. [Continuar según sea necesario]
Meta Final: [Qué debe lograr la salida final]
Acotamiento: [Restricciones, límites de alcance, qué excluir]
```

**Ejemplo:**
```
Rol: Eres un gerente de producto con 10 años de experiencia en apps móviles.
Instrucciones: Escribe un documento de requisitos de producto para una funcionalidad de seguimiento de hábitos.
Pasos:
  1. Define la declaración del problema en un párrafo
  2. Lista historias de usuario en el formato "Como [usuario], quiero [meta] para que [razón]"
  3. Define criterios de aceptación para cada historia
  4. Lista elementos fuera de alcance explícitamente
Meta Final: Un PRD que un equipo de ingeniería pueda usar para comenzar la planificación del sprint inmediatamente.
Acotamiento: Sin detalles de implementación técnica. Sin wireframes. Menos de 600 palabras en total.
```

---

## Plantilla D — CRISPE

*Capacidad, Rol, Insight, Declaración, Personalidad, Experimento. Úsala para trabajo creativo, escritura de voz de marca y cualquier tarea donde la personalidad, el tono y la iteración importan.*

```
Capacidad: [Qué capacidad o experiencia debe tener la IA]
Rol: [Persona específica a adoptar]
Insight: [Insight clave de fondo que da forma a la respuesta]
Declaración: [La tarea o pregunta central]
Personalidad: [Tono y estilo — ingenioso / autoritario / casual / directo]
Experimento: [Solicita variantes o alternativas para explorar]
```

**Ejemplo:**
```
Capacidad: Redactor experto especializado en lanzamientos de productos SaaS.
Rol: Voz de marca para una herramienta de productividad dirigida a desarrolladores.
Insight: Los desarrolladores odian el lenguaje de marketing y responden a la honestidad y especificidad.
Declaración: Escribe el titular principal y el subtitular para la landing page.
Personalidad: Directo, seco, confidente — sin adjetivos, sin signos de exclamación.
Experimento: Da 3 variantes que vayan de mínimo a audaz.
```

---

## Plantilla E — Razonamiento Auditable

*Úsala para tareas con mucha lógica, matemáticas, depuración y análisis multifactorial donde el resultado debe ser verificable sin solicitar razonamiento privado.*

```
[Declaración de tarea]

Retorna:
1. Conclusión
2. Supuestos
3. Evidencia o resultados intermedios necesarios para auditar la conclusión
4. Verificaciones realizadas
5. Incertidumbre restante, si la hay

No reveles cadena de pensamiento oculta ni razonamiento privado. Mantén el razonamiento conciso y relevante para la decisión.
```

**Cuándo usar:**
- Depuración donde la causa no es obvia
- Comparación de enfoques técnicos
- Matemáticas o cálculos que requieren verificación
- Análisis donde la evidencia y los supuestos deben ser inspeccionables

**Cuándo NO usar:**
- Tareas simples donde la respuesta es clara
- Tareas creativas donde una traza de auditoría agrega ruido

---

## Plantilla F — Few-Shot

*Úsala cuando el formato de salida es más fácil de mostrar que de describir. Los ejemplos superan a las instrucciones escritas para tareas sensibles al formato, siempre.*

```
[Instrucción de tarea]

Aquí hay ejemplos del formato exacto necesario:

<ejemplos>
  <ejemplo>
    <entrada>[ejemplo de entrada 1]</entrada>
    <salida>[ejemplo de salida 1]</salida>
  </ejemplo>
  <ejemplo>
    <entrada>[ejemplo de entrada 2]</entrada>
    <salida>[ejemplo de salida 2]</salida>
  </ejemplo>
</ejemplos>

Aplica ahora este patrón exacto a: [entrada actual]
```

**Reglas:**
- 2 a 5 ejemplos es el punto óptimo. Más raramente ayuda y desperdicia tokens.
- Los ejemplos deben incluir casos extremos, no solo casos fáciles.
- Usa etiquetas XML para envolver ejemplos — Claude parsea XML de forma confiable.
- Si has tenido que re-promptear por la misma corrección de formato dos veces, cambia a few-shot en lugar de reescribir instrucciones.

---

## Plantilla G — Alcance de Archivo

*Úsala para Cursor, Windsurf, GitHub Copilot y cualquier IA que edite código dentro de una base de código. El modo de fallo más común aquí es editar el archivo equivocado o romper la lógica existente — esta plantilla previene ambos.*

```
Archivo: [ruta/exacta/al/archivo.ext]
Función/Componente: [nombre exacto]

Comportamiento Actual:
[Qué hace este código ahora mismo — sé específico]

Cambio Deseado:
[Qué debería hacer después de la edición — sé específico]

Alcance:
Solo modifica [función / componente / sección].
NO toques: [lista todo lo que debe quedar sin cambios]

Restricciones:
- Lenguaje/framework: [especifica versión]
- No agregues dependencias que no estén en [package.json / requirements.txt]
- Preserva [firmas de tipos / contratos de API / nombres de variables] existentes

Terminado Cuando:
[Condición exacta que confirma que el cambio funcionó correctamente]
```

---

## Plantilla H — ReAct + Condiciones de Parada

*Úsala para Claude Code, Devin, AutoGPT y cualquier IA que tome acciones autónomas. Los bucles descontrolados y la explosión de alcance son los mayores desperdiciadores de créditos en flujos de trabajo agente — las condiciones de parada no son opcionales.*

```
Objetivo:
[Meta única y inequívoca en una oración]

Estado Inicial:
[Estructura de archivos actual / estado de base de código / entorno]

Estado Objetivo:
[Qué debería existir cuando el agente termine]

Acciones Permitidas:
- [Acción específica que el agente puede tomar]
- Instalar solo paquetes listados en [requirements.txt / package.json]

Acciones Prohibidas:
- NO modifiques archivos fuera de [directorio/alcance]
- NO ejecutes el servidor de desarrollo ni hagas deploy
- NO hagas push a git
- NO elimines archivos sin mostrar un diff primero
- NO tomes decisiones de arquitectura sin aprobación humana

Condiciones de Parada:
Pausa y pide revisión humana cuando:
- Un archivo sería eliminado permanentemente
- Un nuevo servicio o API externo necesita ser integrado
- Existen dos caminos de implementación válidos y la elección afecta la arquitectura
- Un error no puede resolverse en 2 intentos
- La tarea requiere cambios fuera del alcance declarado

Checkpoints:
Después de cada paso mayor, entrega: ✅ [lo que se completó]
Al final, entrega un resumen completo de cada archivo cambiado.
```

---

## Plantilla I — Descriptor Visual

*Úsala para Midjourney, DALL-E 3, Stable Diffusion, Sora, Runway y cualquier herramienta de generación de imagen o video.*

```
Sujeto: [Sujeto principal — específico, no vago]
Acción/Pose: [Qué está haciendo el sujeto]
Escenario: [Dónde tiene lugar la escena]
Estilo: [fotorealista / cinematográfico / anime / pintura al óleo / vector / etc.]
Ambiente: [dramático / sereno / inquietante / alegre / etc.]
Iluminación: [hora dorada / estudio / neón / nublado / luz de velas / etc.]
Paleta de Colores: [colores dominantes o paleta nombrada]
Composición: [plano amplio / primer plano / aérea / ángulo holandés / etc.]
Relación de Aspecto: [16:9 / 1:1 / 9:16 / 4:3]
Prompts Negativos: [borroso, marca de agua, dedos extra, distorsión, baja calidad]
Referencia de Estilo: [artista / película / referencia estética si aplica]
```

**Sintaxis específica por herramienta:**
- **Midjourney**: Descriptores separados por comas, no prosa. Agrega `--ar`, `--style`, `--v 6` al final.
- **Stable Diffusion**: Usa sintaxis de peso `(palabra:1.3)`. Escala CFG 7 a 12. El prompt negativo es obligatorio.
- **DALL-E 3**: La prosa funciona bien. Agrega "no incluyas ningún texto en la imagen" a menos que el texto sea necesario.
- **Sora / video**: Agrega movimiento de cámara (dolly lento, toma estática, grúa hacia arriba), duración en segundos y estilo de corte.

---

## Plantilla J — Edición de Imagen de Referencia

*Úsala cuando el usuario tiene una imagen existente que quiere modificar. Completamente diferente de la generación — nunca describas toda la escena desde cero, solo describe el cambio.*

**Antes de escribir el prompt, siempre dile al usuario:**
"Adjunta tu imagen de referencia a [nombre de herramienta] antes de enviar este prompt."

**Detecta la capacidad de edición de la herramienta:**
- Midjourney: usa `--cref [URL de imagen]` para referencia de personaje o `--sref` para referencia de estilo
- DALL-E 3: usa el endpoint de Edición, no el de Generación. El usuario debe estar en ChatGPT con edición de imágenes habilitada
- Stable Diffusion: usa modo img2img, no txt2img. Establece fuerza de denoising 0.3-0.6 para preservar el original

```
Imagen de referencia: [adjuntada / URL]
Qué mantener exactamente igual: [lista todo lo que no debe cambiar]
Qué cambiar: [edición específica solo — sé preciso]
Cuánto cambiar: [sutil / moderado / significativo]
Consistencia de estilo: mantén el estilo, iluminación y ambiente exactos de la referencia
Prompt negativo: [qué evitar introducir]
```

**Ejemplo:**
```
Imagen de referencia: [foto de retrato adjunta]
Qué mantener exactamente igual: cara, cabello, ropa, fondo, iluminación
Qué cambiar: ángulo de cabeza — rotar de mirar a la izquierda a mirar de frente
Cuánto cambiar: sutil, preserva todos los rasgos faciales exactamente
Consistencia de estilo: mantén estilo fotorealista, misma dirección de iluminación
Prompt negativo: sin elementos nuevos, sin cambios de estilo, sin cambios de fondo
```

---

## Plantilla K — ComfyUI

*Úsala para flujos de trabajo basados en nodos de ComfyUI. Entrega siempre los prompts Positivo y Negativo como bloques separados. Pregunta por el modelo de checkpoint antes de escribir — la sintaxis y los límites de tokens difieren por modelo.*

**Pregunta primero si no se indica:**
"¿Qué modelo de checkpoint estás usando? (SD 1.5, SDXL, Flux, u otro)"

**Notas específicas por modelo:**
- SD 1.5: funcionan mejor prompts más cortos, menos de 75 tokens por bloque, usa sintaxis (palabra:peso)
- SDXL: maneja prompts más largos, soporta más lenguaje natural junto con sintaxis de peso
- Flux: el lenguaje natural funciona bien, menos dependencia de sintaxis de peso, muy responsive a descripciones de estilo

```
PROMPT POSITIVO:
[sujeto], [estilo], [ambiente], [iluminación], [composición], [potenciadores de calidad: highly detailed, sharp focus, 8k]

PROMPT NEGATIVO:
[qué excluir: blurry, low quality, watermark, extra limbs, bad anatomy, distorted, oversaturated]

CHECKPOINT: [nombre del modelo]
SAMPLER: Euler a (punto de partida recomendado)
CFG SCALE: 7 (aumenta para adherencia estricta al prompt)
STEPS: 20-30
RESOLUTION: [ancho x alto — debe ser divisible por 64]
```

---

## Plantilla L — Decompilador de Prompts

*Úsala cuando el usuario pega un prompt existente y quiere descomponerlo, adaptarlo para una herramienta diferente, simplificarlo o entender su estructura. Esto es análisis y adaptación, no construcción desde cero.*

**Detecta qué tarea de Decompilador se necesita:**
- **Descomponer** — explica qué hace cada parte del prompt
- **Adaptar** — reescribe para una herramienta diferente preservando la intención
- **Simplificar** — elimina redundancia y aprieta sin perder significado
- **Dividir** — divide un prompt complejo de una sola pasada en una secuencia más limpia

**Para tareas de Adaptar, siempre pregunta:**
"¿De qué herramienta es el prompt original, y para qué herramienta lo estás adaptando?"

**Formato de salida para Descomponer:**
```
Prompt original: [pegar]

Análisis de estructura:
- Rol/Identidad: [qué rol se asigna y por qué]
- Tarea: [qué acción se solicita]
- Restricciones: [qué límites se establecen]
- Formato: [qué forma de salida se espera]
- Debilidades: [qué falta o podría causar salida incorrecta]

Arreglo recomendado: [versión reescrita con huecos llenos]
```

**Formato de salida para Adaptar:**
```
Original ([herramienta fuente]): [prompt original]

Adaptado para [herramienta destino]:
[prompt reescrito usando la sintaxis y mejores prácticas de la herramienta destino]

Cambios clave realizados:
- [cambio 1 y por qué]
- [cambio 2 y por qué]
```

**Formato de salida para Dividir:**
```
Prompt original: [pegar]

Este prompt está haciendo [N] cosas. Divídelo en [N] prompts secuenciales:

Prompt 1 — [qué maneja]:
[bloque de prompt]

Prompt 2 — [qué maneja]:
[bloque de prompt]

Ejecútalos en orden. Cada salida alimenta a la siguiente.
```

---

## Plantilla M — Brief de Tarea para Claude Actual

*Úsala para tareas complejas, de múltiples pasos o agente en modelos Claude actuales — Claude.ai, API o Claude Code. Carga al frente el resultado, contexto, alcance y límites de acción mientras evita el andamiaje obsoleto de pensamiento manual.*

```
## Objetivo
[Qué necesita ser construido, arreglado o producido — una oración clara. Agrega el PORQUÉ si afecta el enfoque.]

## Contexto
[Qué existe ahora — archivos relevantes, comportamiento actual, stack ya en lugar, qué se intentó y falló]

## Estado Objetivo
[Qué se ve como terminado — archivos específicos cambiados, comportamiento producido, pruebas pasando. Binario donde sea posible.]

## Alcance
- Trabaja solo en: [archivos y directorios específicos]
- NO toques: [archivos prohibidos — .env, package-lock.json, configs, nada fuera de alcance]

## Restricciones
- [Versión de stack, convenciones de nombres, sin nuevas dependencias sin preguntar]
- Solo haz cambios directamente solicitados. No agregues funcionalidades, abstracciones ni archivos más allá de lo pedido.

## Criterios de Aceptación
- [ ] [Verificación binaria 1]
- [ ] [Verificación binaria 2]
- [ ] [Verificación binaria 3]

## Límites de Acción
- Procede con inspección, ediciones y validación reversibles dentro del alcance.
- Detente y pregunta antes de acciones destructivas o irreversibles, escrituras externas, compras, expansión material de alcance o decisiones que requieran input exclusivo del usuario.

## Evidencia de Progreso
Para trabajo de larga duración, reporta progreso solo cuando cambie o cuando se alcance un checkpoint. Ancla cada afirmación de completitud en un resultado de herramienta, artefacto cambiado o salida de verificación.
```

**Esfuerzo** — configúralo en la API o harness en lugar de solicitar razonamiento privado en el prompt. Comienza con el default del modelo, bájalo para trabajo rutinario de alcance definido, y súbelo solo cuando la dificultad de la tarea justifique el costo.

**Solo para Claude Code — agrega bloque de Estrategia de Sesión cuando sea relevante:**
```
## Estrategia de Sesión
[Elige una:]
- Nueva sesión — no relacionada con contexto previo, comienza desde cero
- Continuar — contexto previo aún necesario
- Subagente — delega solo [flujo de trabajo independiente y sustancial], con un entregable acotado
- Compactar primero — compacta alrededor de [decisiones, restricciones y estado actual], luego comienza
```

**Cuándo usar:** Modelos Claude actuales en cualquier superficie cuando la tarea es compleja, multi-archivo, ambigua o agente. No es necesario para tareas simples de una sola pasada.
