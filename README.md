# Maestro de Prompts

Un skill de Claude que escribe los prompts precisos para cualquier herramienta de IA. Cero tokens ni créditos desperdiciados. Retención completa de contexto y memoria. Se acabó el re-promptear hasta obtener la respuesta que debiste recibir en el primer intento.

**Funciona con:** Claude, ChatGPT, Codex, Grok, Gemini, o1/o3, MiniMax, Cursor, Claude Code, GitHub Copilot, Windsurf, Bolt, v0, Lovable, Devin, Perplexity, Midjourney, DALL-E, Stable Diffusion, ComfyUI, Sora, Runway, ElevenLabs, Zapier, Make y cualquier otra herramienta de IA que le lances.

---

## 🚀 Instalación

### Recomendado — Claude.ai (navegador)

1. Descarga este repositorio como ZIP
2. Ve a **claude.ai → Barra lateral → Personalizar → Skills → Subir un skill**

### Alternativa — Claude Code

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Carlosyekana/Tutor-prompt.git ~/.claude/skills/maestro-de-prompts
```

### Otras plataformas — ChatGPT, Gemini, Copilot, Mistral…

Abre [`portable/prompt-portable.md`](portable/prompt-portable.md), copia todo lo que va a partir de la primera línea de guiones y pégalo como primer mensaje. Es la skill entera en un archivo, sin remisiones a nada externo. Después escribe tu solicitud.

La carpeta `portable/` no es parte de la skill: si instalaste clonando, puedes borrarla sin consecuencias.

---

## 🔥 El problema que resuelve

Todos los usuarios de IA desperdician créditos de la misma manera:

> Escribes un prompt vago → obtienes una salida incorrecta → reformulas → te acercas → reformulas de nuevo → finalmente obtienes lo que querías en el intento 4

Eso son 3 llamadas desperdiciadas. Multiplica por 50 prompts al día: es dinero y tiempo reales perdidos.

### La idea clave

> "El mejor prompt no es el más largo. Es aquel donde cada palabra carga peso."

La mayoría de los "generadores de prompts" hacen los prompts más largos. Este skill los hace más afilados.

---

## 🎯 Uso

En Claude, puedes invocar el skill con lenguaje natural:

```
Escríbeme un prompt para Cursor para refactorizar mi módulo de autenticación
```

```
Necesito un prompt para Claude Code para construir una API REST — pregúntame lo que necesites saber
```

```
Aquí hay un prompt malo que escribí para GPT-4o, arréglalo: [pega el prompt]
```

```
Genera un prompt de Midjourney para una ciudad cyberpunk de noche
```

```
Tengo una imagen de referencia — ayúdame a escribir un prompt para editar solo el ángulo de la cabeza
```

```
Descompón este prompt y adáptalo para Stable Diffusion
```

O invócalo explícitamente:

```
/maestro-de-prompts

Quiero pedirle a Claude Code que construya una app de tareas con React y Supabase
```

---

## ⚙️ Cómo funciona

Maestro de Prompts ejecuta un pipeline estructurado en cada solicitud:

1. **Detecta la herramienta objetivo** — identifica para qué sistema de IA es el prompt y enruta silenciosamente al enfoque correcto
2. **Extrae 9 dimensiones de intención** — tarea, entrada, salida, restricciones, contexto, audiencia, memoria, criterios de éxito y ejemplos
3. **Hace preguntas aclaratorias enfocadas** — máximo 3 si falta información crítica, nunca más
4. **Enruta a la plantilla correcta** — elige y aplica la arquitectura de prompt adecuada de forma automática, sin mostrarte el nombre del framework
5. **Aplica solo técnicas seguras** — asignación de rol, ejemplos few-shot, estructura XML, anclajes de grounding y bloque de memoria, según corresponda
6. **Verifica la vigencia del modelo** — contrasta modelos exactos y controles con la documentación oficial del proveedor cuando la solicitud depende de "el más reciente"
7. **Ejecuta una auditoría de eficiencia de tokens** — elimina cada palabra que no cambia el resultado
8. **Entrega el prompt** — un bloque limpio y copiable con una nota de estrategia de una línea
9. **Te explica qué cambió** — en lenguaje llano: qué le faltaba a tu pedido, qué hace cada parte del prompt que te entregó, por qué esa forma y no la obvia, y dos o tres consejos para la próxima. Nunca nombres de frameworks ni de niveles

---

## 🖼️ Ejemplo completo #1: prompts para imágenes

### Entrada del usuario

```
Escríbeme un prompt de Midjourney para un samurái realista parado bajo la lluvia de noche
```

### Prompt generado

```
lone samurai standing in heavy rain at night, traditional armor, 
neon reflections on wet cobblestone street, cinematic lighting, 
dramatic shadows, fog, ultra detailed, photorealistic, 
shallow depth of field --ar 16:9 --v 6 --style raw

negative: blurry, low quality, watermark, cartoon, anime, extra limbs
```

**🎯 Objetivo:** Midjourney · **💡** descriptores separados por comas en lugar de prosa, iluminación y ambiente anclados desde el inicio, relación de aspecto y versión fijadas, y prompt negativo que previene la deriva de estilo.

**Qué cambié y por qué**

- **Qué le faltaba:** el pedido era una frase en prosa, sin luz, sin encuadre y sin decir qué NO querías ver.
- **Qué le puse:** la escena en descriptores sueltos —sujeto, luz, ambiente, encuadre— porque Midjourney lee listas, no oraciones; y una lista de lo que debe evitar, que es lo que frena las manos de seis dedos y las marcas de agua.
- **Para la próxima:** escribe primero el sujeto y después la luz; son las dos palancas que más cambian la imagen.

---

## 💻 Ejemplo completo #2: prompts para código

### Entrada del usuario

```
Construye un prompt de Claude Code para una landing page de un 
business dashboard que se vea y se sienta exactamente como Notion — 
animaciones suaves, UI limpia
```

### Prompt generado

```
Objective:
Build a fully detailed, production-quality static landing page for a 
business dashboard product. Design must match Notion's exact aesthetic — 
clean, minimal, typographic, with smooth animations throughout.

Stack:
Single HTML file with embedded CSS and vanilla JS. No frameworks. 
No external dependencies except Google Fonts (Inter).

Design Spec — match these exactly:
- Background: #ffffff
- Primary text: #1a1a1a
- Secondary text: #6b7280
- Border color: #e5e7eb
- Accent: #000000
- Font: Inter, weights 400 / 500 / 600 / 700
- Base spacing unit: 8px
- Border radius: 6px on cards, 4px on buttons
- Box shadows: 0 1px 3px rgba(0,0,0,0.08) only — no dramatic shadows
- Buttons: black fill, white text, no border radius above 6px

Sections to build in order:
1. Navbar — logo left, nav links center, "Get started free" CTA right. 
   Sticky on scroll, adds subtle border-bottom on scroll with JS.
2. Hero — large left-aligned heading (max 3 lines), subtext, two CTAs 
   (primary black + secondary outlined), hero screenshot mockup 
   placeholder (gray rounded card, 16:9 ratio).
3. Logos bar — "Trusted by teams at..." with 5 placeholder company names 
   in muted gray, centered.
4. Features — 3-column grid. Each card: icon (use emoji), bold title, 
   2-line description. Hover state: border darkens to #d1d5db, 
   translateY(-2px), transition 200ms ease.
5. How it works — alternating left/right layout, 3 steps. Number badge, 
   heading, description, placeholder screenshot card.
6. Pricing — 2 tiers side by side. Free tier: outlined card. Pro tier: 
   black background, white text, "Most popular" badge. List 4 features 
   each with checkmarks.
7. CTA banner — full-width dark section, centered heading, subtext, 
   single CTA button.
8. Footer — 4-column links, copyright line, minimal.

Animations — implement all of these:
- Fade-in + translateY(20px) to translateY(0) on scroll for every section, 
  using IntersectionObserver. Threshold 0.15. Duration 500ms ease-out.
- Staggered animation on feature cards: 100ms delay between each card.
- Navbar CTA button: background transitions from black to #333 on hover, 
  200ms ease.
- Hero CTA primary: same hover transition. Secondary: background goes from 
  transparent to #f3f4f6 on hover.
- Smooth scroll on all anchor links.
- Navbar border-bottom fades in on scroll past 60px using JS scroll event.

Constraints:
- Single file only — all CSS and JS embedded, no external files
- No dependencies except Google Fonts via CDN link tag
- All placeholder images replaced with styled gray div elements
- Must be pixel-perfect at 375px mobile and 1440px desktop
- No CSS frameworks, no utility classes from external sources

Done When:
- All 8 sections render correctly at both breakpoints
- All animations trigger on scroll without layout shift
- Navbar sticks and border appears on scroll
- Hover states work on all interactive elements
- Opens in browser with zero console errors
```

**🎯 Objetivo:** Claude Code · **💡** cada pista estética vaga traducida a valores hexadecimales exactos y especificaciones en píxeles — Claude Code no tiene que adivinar. Las animaciones se definen con duración, método y disparador exactos, sin margen de interpretación.

**Qué cambié y por qué**

- **Qué le faltaba:** "que se vea como Notion" y "animaciones suaves" son gustos, no instrucciones: nada ahí se puede verificar.
- **Qué le puse:** traduje cada gusto a un número —color en hexadecimal, espaciado en píxeles, duración en milisegundos— y agregué dónde debe parar, porque un agente sin criterio de terminado sigue inventando pantallas.
- **Para la próxima:** antes de pedir, pregúntate cómo comprobarías que quedó bien; eso que responderías es el criterio que le falta al prompt.

---

## 🤝 Funciona con cualquier herramienta de IA

Maestro de Prompts incluye perfiles específicos para más de 30 herramientas. Para cualquiera que no esté en la lista, usa una **huella digital universal**: 4 preguntas que le permiten escribir un prompt de calidad para cualquier sistema de IA que nunca haya visto antes.

<details>
<summary><h3>Haz clic para ver todos los perfiles de herramientas</h3></summary>

| Herramienta | Categoría | Qué corrige Maestro de Prompts |
|------|----------|--------------------------|
| **Claude 5 / Claude actual** | LLM de razonamiento y agente | Esfuerzo consciente del modelo, alcance, estructura XML y control de delegación |
| **ChatGPT / GPT-5.6** | LLM de razonamiento y agente | Enrutamiento Sol/Terra/Luna, contratos lean, control de autonomía y esfuerzo |
| **Codex** | Agente de código | Alcance de archivos, límites de aprobación, verificación y subagentes acotados |
| **Grok 4.6** | LLM de razonamiento y agente | Grounding con búsqueda, esfuerzo de razonamiento, herramientas, caché y condiciones de parada |
| **Gemini 2.x** | LLM de razonamiento | Anclajes de grounding, reglas de citación y bloqueos de formato |
| **o3 / o4-mini** | LLM de razonamiento | Instrucciones cortas y limpias solamente — nunca agrega CoT (estos modelos piensan internamente) |
| **Ollama** | LLM local | Pregunta qué modelo está cargado e incluye el system prompt para el Modelfile |
| **Qwen 2.5 / Qwen3** | LLM de peso abierto | Formato de plantilla de chat, detección de modo thinking vs non-thinking |
| **Modelos locales (Llama, Mistral)** | LLM de peso abierto | Prompts más cortos, estructura más simple, sin anidamiento complejo |
| **DeepSeek-R1** | LLM de razonamiento | Instrucciones cortas y limpias, elimina CoT y suprime la salida de pensamiento si es necesario |
| **MiniMax (M3 / M2.7)** | LLM de razonamiento | Límite de temperatura, control de la etiqueta thinking y salida estructurada optimizada |
| **Claude Code** | IA agente | Condiciones de parada, alcance de archivos y salida de checkpoints |
| **Cursor / Windsurf** | IA de IDE | Ruta de archivo, nombre de función, lista de no-tocar y guía de prompts secuenciales |
| **Cline (antes Claude Dev)** | IDE agente | Alcance de archivos, puertas de aprobación, condiciones de parada y desglose de tareas |
| **GitHub Copilot** | Autocompletado de IA | Contrato de función exacto en forma de docstring |
| **Antigravity** | IDE agente | Prompting basado en tareas, revisión de artefactos y nivel de autonomía |
| **Bolt / v0 / Lovable** | Generador full-stack | Especificación de stack, versión y qué NO generar |
| **Figma Make** | Generador full-stack | Referencias a nombres de componentes, alcance de frame-a-código |
| **Google Stitch** | Generador full-stack | Meta de interfaz sobre implementación, especificación de Material Design 3 |
| **Devin / SWE-agent** | Agente autónomo | Estado inicial, estado objetivo y condiciones de parada |
| **Manus** | Agente autónomo | Enfoque en el resultado, alcance de permisos y anclajes de memoria |
| **OpenAI Computer Use** | Agente de uso de computadora | Estado de pantalla, apps permitidas y detención antes de acciones irreversibles |
| **Perplexity Computer** | Agente de uso de computadora | Prompting orientado a artefactos, permisos acotados y pasos de verificación |
| **OpenClaw** | Agente de uso de computadora | Precisión conversacional, memoria persistente y restricciones de seguridad |
| **Perplexity / SearchGPT** | IA de búsqueda | Especificación de modo: búsqueda vs análisis vs comparación |
| **Midjourney** | IA de imágenes | Descriptores separados por comas, parámetros y prompts negativos |
| **DALL-E 3** | IA de imágenes | Descripción en prosa y exclusión de texto — detecta edición vs generación |
| **Stable Diffusion** | IA de imágenes | Sintaxis de peso `(palabra:1.3)`, guía de CFG y prompt negativo obligatorio |
| **SeeDream** | IA de imágenes | Estilo de arte primero, descriptores de ambiente y prompt negativo |
| **ComfyUI** | IA de imágenes | Separación positivo/negativo por nodos, sintaxis específica del checkpoint |
| **Meshy / Tripo / Rodin** | IA 3D | Estilo + formato de exportación + presupuesto de polígonos + requisitos de rig |
| **BlenderGPT** | IA 3D | Salida de script Python, versión de Blender y contexto de escena |
| **Unity AI** | IA 3D / juegos | Género de juego, plataforma objetivo y descripción de mecánicas sobre código |
| **Sora / Runway** | IA de video | Movimiento de cámara, duración y estilo de corte |
| **LTX / Dream Machine / Kling** | IA de video | Lenguaje cinematográfico, intensidad de movimiento y referencia de estilo |
| **ElevenLabs** | IA de voz | Emoción, ritmo, énfasis y velocidad del habla |
| **Zapier / Make / n8n** | Automatización de flujos | App y evento disparador + app de acción + mapeo de campos |

</details>

---

## 📐 13 plantillas de prompts (seleccionadas automáticamente)

Maestro de Prompts elige la arquitectura correcta para cada tarea de forma automática y silenciosa — nunca ves el nombre del framework, solo el prompt.

<details>
<summary><h3>Haz clic para ver las 13 plantillas</h3></summary>

| Plantilla | Ideal para |
|----------|----------|
| **RTF** (Rol, Tarea, Formato) | Tareas rápidas de una sola pasada |
| **CO-STAR** (Contexto, Objetivo, Estilo, Tono, Audiencia, Respuesta) | Documentos profesionales, informes y escritura de negocios |
| **RISEN** (Rol, Instrucciones, Pasos, Meta final, Acotamiento) | Proyectos complejos de varios pasos |
| **CRISPE** (Capacidad, Rol, Insight, Declaración, Personalidad, Experimento) | Trabajo creativo, voz de marca y contenido iterativo |
| **Razonamiento Auditable** | Matemáticas verificables, lógica, depuración y análisis sin solicitudes de razonamiento oculto |
| **Few-Shot** | Salidas estructuradas consistentes y replicación de patrones |
| **Alcance de Archivo** | Cursor, Windsurf, Copilot — cualquier IA de edición de código |
| **ReAct + Condiciones de Parada** | Claude Code, Devin, AutoGPT — cualquier agente autónomo |
| **Descriptor Visual** | Midjourney, DALL-E, Stable Diffusion, Sora — generación |
| **Edición de Imagen de Referencia** | Editar una imagen existente — detecta edición vs generación automáticamente |
| **ComfyUI** | Flujos de imágenes basados en nodos — separación positivo/negativo por checkpoint |
| **Decompilador de Prompts** | Descomponer, adaptar, simplificar o dividir prompts existentes |
| **Brief de Tarea para Claude actual** | Tareas complejas, de varios pasos o de agente en los modelos Claude actuales |

</details>

---

## 🛡️ 9 técnicas seguras, aplicadas solo cuando se necesitan

Maestro de Prompts solo usa técnicas con efectos confiables y acotados. Los métodos conocidos por producir alucinaciones o resultados impredecibles (Tree of Thought, Graph of Thought, Universal Self-Consistency, encadenamiento de prompts) están explícitamente excluidos.

| Técnica | Qué hace |
|-----------|-------------|
| **Asignación de Rol** | Asigna una identidad experta específica para calibrar profundidad y vocabulario |
| **Ejemplos Few-Shot** | Agrega 2 a 5 ejemplos cuando la consistencia de formato importa más que las instrucciones |
| **Etiquetas Estructurales XML** | Envuelve secciones en XML para herramientas basadas en Claude, que las interpretan de forma confiable |
| **Anclajes de Grounding** | Agrega reglas anti-alucinación para tareas factuales y de citación |
| **Razonamiento Auditable** | Solicita conclusiones, supuestos, evidencia y verificación sin razonamiento oculto |
| **Poda Estratégica** | Prohíbe jerga, clichés y exceso de longitud con restricciones concretas y verificables |
| **Socrático** | Activa el diagnóstico de contexto con preguntas previas antes de ejecutar la tarea final |
| **Abogado del Diablo** | Somete las premisas a un crítico escéptico concreto y reescribe la versión que sobrevive |
| **Traductor de Audiencias** | Adapta un mismo concepto a N públicos con foco, metáfora y tono calibrados en una sola llamada |

---

## 🪜 Escalera de Prompting — diagnóstico por niveles (0 a 6)

Cuando le pegas un prompt propio, Maestro de Prompts ubica su nivel y lo escala solo hasta donde tu objetivo lo requiere — cada nivel agrega tokens, así que no escala por deporte.

| Nivel | Nombre | Qué corrige |
|-------|--------|-------------|
| 0 🟢 | Prompt Ingenuo | Órdenes tipo buscador que producen respuestas enciclopédicas → sube a estructura |
| 1 🟡 | Estructurado | [ROL] [CONTEXTO] [MISIÓN] [FORMATO] — la base profesional |
| 2 🟠 | Pasos de Razonamiento | Lógica paso a paso auditable (nunca en modelos de razonamiento nativo) |
| 3 🔴 | Poda Estratégica | Saca la jerga, los clichés y el exceso de longitud del texto |
| 4 🟣 | Socrático | Respuestas genéricas por falta de diagnóstico de contexto previo |
| 5 ⚫ | Abogado del Diablo | Premisas débiles que no sobrevivirían a un comité o cliente escéptico |
| 6 🌈 | Traductor de Audiencias | Un mismo contenido calibrado para varios públicos a la vez |

La progresión completa, con ejemplos trabajados en prospectiva e investigación en salud, está en [references/escalera.md](references/escalera.md).

---

## 🚫 37 patrones que matan créditos (con ejemplos de antes y después)

<details>
<summary><h3>Patrones de tarea (7)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 1 | **Verbo de tarea vago** | "ayúdame con mi código" | "Refactoriza `getUserData()` para usar async/await y manejar retornos null" |
| 2 | **Dos tareas en un prompt** | "explica Y reescribe esta función" | Divide: explica primero, reescribe después |
| 3 | **Sin criterios de éxito** | "hazlo mejor" | "Terminado cuando la función pase las pruebas unitarias existentes y maneje entradas null" |
| 4 | **Agente sobre-permisivo** | "haz lo que sea necesario" | Lista explícita de acciones permitidas + lista explícita de acciones prohibidas |
| 5 | **Descripción emocional de la tarea** | "está totalmente roto, arréglalo todo" | "Lanza un TypeError no capturado en la línea 43 cuando `user` es null" |
| 6 | **Construir todo de golpe** | "construye toda mi app" | Divide en Prompt 1 (esqueleto), Prompt 2 (funcionalidad), Prompt 3 (pulido) |
| 7 | **Referencia implícita** | "ahora agrega la otra cosa que discutimos" | Reformula siempre la tarea completa; nunca referencies "la cosa que discutimos" |

</details>

<details>
<summary><h3>Patrones de contexto (6)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 8 | **Conocimiento previo asumido** | "continúa donde lo dejamos" | Incluye un Bloque de Memoria con todas las decisiones previas |
| 9 | **Sin contexto de proyecto** | "escribe una carta de presentación" | "Rol de PM en fintech B2B, 2 años de experiencia como SWE, lideré 3 funcionalidades como tech lead" |
| 10 | **Stack olvidado** | El nuevo prompt contradice una elección técnica previa | Incluye siempre el Bloque de Memoria |
| 11 | **Invitación a alucinar** | "¿qué dicen los expertos sobre X?" | "Cita solo fuentes de las que estés seguro. Si no lo estás, dilo." |
| 12 | **Audiencia indefinida** | "escribe algo para usuarios" | "Compradores B2B no técnicos, sin conocimiento de código, con nivel de decisión" |
| 13 | **Sin mención de intentos fallidos** | (vacío) | "Ya intenté X y falló por Y. No sugieras X." |

</details>

<details>
<summary><h3>Patrones de formato (6)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 14 | **Formato de salida faltante** | "explica este concepto" | "3 viñetas de menos de 20 palabras cada una, con un resumen de una oración al inicio" |
| 15 | **Longitud implícita** | "escribe un resumen" | "Escribe un resumen de exactamente 3 oraciones" |
| 16 | **Sin asignación de rol** | (vacío) | "Eres un ingeniero backend senior especializado en Node.js y PostgreSQL" |
| 17 | **Adjetivos estéticos vagos** | "haz que se vea profesional" | "Paleta monocromática, fuente base de 16px, interlineado de 24px, sin elementos decorativos" |
| 18 | **Sin prompt negativo (IA de imágenes)** | "un retrato de una mujer" | Agrega: "sin marca de agua, sin desenfoque, sin dedos extra, sin distorsión, sin texto" |
| 19 | **Prompt en prosa para Midjourney** | Oración descriptiva completa | "sujeto, estilo, ambiente, iluminación, composición, --ar 16:9 --v 6" |

</details>

<details>
<summary><h3>Patrones de alcance (6)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 20 | **Sin límite de alcance** | "arregla mi app" | "Arregla solo la validación del formulario de login en `src/auth.js`. No toques nada más." |
| 21 | **Sin restricciones de stack** | "construye un componente React" | "React 18, TypeScript estricto, sin librerías externas, solo Tailwind" |
| 22 | **Sin condición de parada para agentes** | "construye toda la funcionalidad" | Condiciones de parada explícitas + checkpoint de salida después de cada paso |
| 23 | **Sin ruta de archivo para IA de IDE** | "actualiza la función de login" | "Actualiza `handleLogin()` en `src/pages/Login.tsx` únicamente" |
| 24 | **Plantilla incorrecta para la herramienta** | Prompt en prosa estilo GPT usado en Cursor | Adaptado a la plantilla de Alcance de Archivo |
| 25 | **Pegar todo el código base** | El repositorio completo como contexto en cada prompt | Acota solo a la función y el archivo relevantes |

</details>

<details>
<summary><h3>Patrones de razonamiento (5)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 26 | **Sin contrato de auditoría para tareas lógicas** | "¿qué enfoque es mejor?" | Solicita la recomendación, supuestos, criterios, evidencia y verificaciones |
| 27 | **Solicitar razonamiento oculto** | "muestra tu cadena de pensamiento" | Elimínala — pide en su lugar un razonamiento conciso, evidencia y verificaciones |
| 28 | **Esperar memoria entre sesiones** | "ya conoces mi proyecto" | Vuelve a proporcionar el Bloque de Memoria en cada sesión nueva |
| 29 | **Contradecir trabajo previo** | El nuevo prompt ignora la arquitectura anterior | Incluye el Bloque de Memoria con todas las decisiones establecidas |
| 30 | **Sin regla de anclaje para tareas factuales** | "resume lo que los expertos dicen sobre X" | "Usa solo información de la que estés seguro. Di [incertidumbre] si no lo estás." |

</details>

<details>
<summary><h3>Patrones de agente (7)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 31 | **Sin estado inicial** | "constrúyeme una API REST" | "Proyecto Node.js vacío, Express instalado, `src/app.js` existe" |
| 32 | **Sin estado objetivo** | "agrega autenticación" | "`/src/middleware/auth.js` con verificación JWT. `POST /login` y `POST /register` en `/src/routes/auth.js`" |
| 33 | **Agente silencioso** | Sin salida de progreso | "Después de cada paso, escribe: ✅ [lo que se completó]" |
| 34 | **Sistema de archivos sin restricciones** | Sin límites de archivos | "Solo edita archivos dentro de `src/`. No toques `package.json`, `.env` ni ningún archivo de configuración." |
| 35 | **Sin disparador de revisión humana** | El agente decide todo de forma autónoma | "Detente y pregunta antes de: eliminar cualquier archivo, agregar cualquier dependencia o cambiar el esquema de la base de datos" |
| 36 | **Primer turno vago para un modelo agente** | "arregla el bug de auth" sin alcance, archivos ni criterios | Carga al frente el resultado, el contexto, el alcance, los límites y los criterios de aceptación |
| 37 | **Putrefacción de contexto en sesiones largas** | Repites correcciones mientras suposiciones obsoletas siguen en el contexto | Inicia una sesión nueva para trabajo no relacionado; de lo contrario, compacta en torno a decisiones, restricciones y estado actual |

</details>

---

## 🧠 Sistema de Bloque de Memoria

Cuando tu conversación tiene historial, Maestro de Prompts extrae las decisiones previas y antepone un Bloque de Memoria, para que la IA nunca contradiga trabajo anterior:

```
## Memoria (arrastrar desde el contexto previo)
- Stack: React 18 + TypeScript + Supabase
- La autenticación usa JWT en cookies httpOnly, no localStorage
- Convención de nombres de componentes: PascalCase, sin default exports
- Sistema de diseño: solo Tailwind, sin archivos CSS personalizados
- Arquitectura: sin Redux, solo Context API
```

Esta es la corrección individual más importante para sesiones largas. La mayoría de los re-prompts desperdiciados vienen de que la IA olvida lo que ya decidiste.

---

## ℹ️ Historial de versiones

- **1.11.0** — El bloque de aprendizaje pasa de tres líneas a cuatro partes: qué le faltaba, cómo quedó armado (una línea por cada parte del prompt entregado), por qué esa forma y no la obvia, y dos o tres consejos para la próxima. Techo de 250 palabras. La regla de preguntas deja de ser solo un techo y pasa a tener piso: pregunta por cada dimensión crítica que falte, hasta tres, y si no pregunta nada declara sus supuestos. Nueva regla de idioma: responde en el idioma de quien escribe, y el prompt va en ese idioma salvo que la herramienta rinda mejor en otro. Probado el portable en Gemini.
- **1.10.0** — Modo tutor. Cada entrega suma un bloque fijo de tres líneas —qué le faltaba al pedido, qué palanca se aplicó y qué probar la próxima vez— en lenguaje llano, sin nombres de framework ni de nivel: la skill deja de ser solo una máquina de prompts y transfiere el método. El portable sale del `.zip` y viaja junto a él: la carpeta que se instala en `~/.claude/skills/` queda solo con `SKILL.md` y `references/`. Los 29 perfiles de herramientas salen del procedimiento a `references/herramientas.md`: `SKILL.md` baja de 42 KB a 21 KB y deja de pagar el catálogo entero en cada activación; de paso, la parte que caduca queda aislada en un archivo que se revisa solo.
- **1.9.1** — Pasada de castellano sobre la skill y las referencias: se eliminan los anglicismos que debilitaban las reglas duras ("output" como verbo, "prependa", "scaffoldar"). Etiquetas Estructurales XML pasa a estar declarada como técnica segura también en el procedimiento, no solo en esta tabla. Descripción reescrita para que abra por condiciones de activación. Corregido el generador del portable: ya no altera los encabezados que viven dentro de los bloques de código de las plantillas.
- **1.9.0** — Agregada la Escalera de Prompting (Niveles 0–6) como sistema de diagnóstico y escalada de prompts, integrada desde talleres prácticos de prompting estratégico (prospectiva e investigación en salud). Cuatro técnicas seguras nuevas: Poda Estratégica, Socrático, Abogado del Diablo y Traductor de Audiencias. Nuevo archivo de referencia `references/escalera.md` con la progresión completa y ejemplos trabajados. Eliminadas las bases en inglés de la versión anterior (`references/patterns.md`, `references/templates.md`); el contenido canónico vive en las versiones en español.
- **1.8.0** — Actualización de modelos actuales. Agregados Claude Fable 5, Opus 5, Sonnet 5, GPT-5.6 Sol/Terra/Luna, Codex y enrutamiento de Grok 4.6. Reemplazadas las solicitudes de cadena de pensamiento oculta con razonamiento auditable y generalizado el brief de tarea de Claude para los modelos actuales de pensamiento adaptativo.
- **1.7.0** — Compatibilidad con Opus 4.8. Enrutamiento Claude 4.x consciente de versión: consejo durable generalizado a través de 4.6/4.7/4.8, perfil de Opus 4.8 agregado, Opus 4.7 mantenido como etiquetado. Nota de nivel de esfuerzo des-hardcodeada (ahora gestionada por el harness). La Plantilla M y el patrón 36 cubren 4.7 y 4.8.
- **1.6.0** — Actualización Opus 4.7. Agregada la Plantilla M (Brief de Tarea Opus 4.7). Actualizado el enrutamiento de Claude y Claude Code para literalismo, pensamiento adaptativo, esfuerzo xhigh e higiene de sesión. Agregados los patrones 36–37.
- **1.5.0** — Más enrutamiento de herramientas. Agregados los enrutamientos de IA agente y de IA de modelos 3D. Descripción fijada en 189 caracteres. Eliminada la estimación de tokens de la salida. Agregada la capa de instrucciones y los placeholders de copywriting.
- **1.4.0** — Agregadas la detección de edición de imagen de referencia, el soporte de ComfyUI y el modo Decompilador de Prompts. Corregida la descripción del disparador para invocar correctamente en Claude Code. 3 plantillas nuevas en la carpeta de referencias.
- **1.3.0** — Reconstruido en torno a la estructura posicional PAC2026 (30/55/15). El enrutamiento silencioso reemplaza la selección de framework visible para el usuario. Introducida la carpeta de referencias.
- **1.2.0** — Reestructurado para la arquitectura de atención. Eliminadas las técnicas propensas a fabricación (ToT, GoT, USC, encadenamiento de prompts). Plantillas y patrones movidos a la carpeta de referencias.
- **1.1.0** — Cobertura de herramientas expandida, sistema de Bloque de Memoria agregado, 35 patrones que matan créditos.
- **1.0.0** — Lanzamiento inicial.

---

## 📄 Licencia

MIT — ver [LICENSE](LICENSE) para los detalles.
