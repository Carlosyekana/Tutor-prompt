![](https://i.postimg.cc/kG03s7tk/prompt-banner.png)

<br/>

Un skill de Claude que escribe los prompts precisos para cualquier herramienta de IA. Cero tokens o créditos desperdiciados. Retención completa de contexto y memoria. Sin re-promptear hasta una respuesta que deberías haber obtenido en el primer intento.

**Funciona con:** Claude, ChatGPT, Codex, Grok, Gemini, o1/o3, MiniMax, Cursor, Claude Code, GitHub Copilot, Windsurf, Bolt, v0, Lovable, Devin, Perplexity, Midjourney, DALL-E, Stable Diffusion, ComfyUI, Sora, Runway, ElevenLabs, Zapier, Make, y cualquier herramienta de IA que le lances.

---

## 🚀 Instalación

### RECOMENDADO - Claude.ai (navegador)

1. Descarga este repo como ZIP
2. Ve a **claude.ai → Barra lateral → Personalizar → Skills → Subir un Skill**


### O clona directamente en el directorio de skills de Claude Code (No recomendado)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Carlosyekana/Tutor-prompt.git ~/.claude/skills/maestro-de-prompts
```

## 🔥 El Problema que Esto Resuelve

Cada usuario de IA desperdicia créditos de la misma manera:

> Escribe un prompt vago → obtén output incorrecto → re-promptea → acércate más → re-promptea de nuevo → finalmente obtén lo que querías en el intento 4

Eso son 3 llamadas a API desperdiciadas. Multiplica por 50 prompts al día. Eso es dinero real y tiempo real perdido.

### La idea clave

> "El mejor prompt no es el más largo. Es aquel donde cada palabra carga peso."

La mayoría de "generadores de prompts" hacen los prompts más largos. Este skill los hace más afilados.

---

## 🎯 Uso

En Claude, puedes invocar el skill naturalmente:

```
Escríbeme un prompt para Cursor para refactorizar mi módulo de autenticación
```

```
Necesito un prompt para Claude Code para construir una API REST — pregúntame lo que necesitas saber
```

```
Aquí hay un mal prompt que escribí para GPT-4o, arréglalo: [pega prompt]
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

## Cómo Funciona

Maestro de Prompts ejecuta un pipeline estructurado en cada solicitud:

1. **Detecta la herramienta objetivo** — descubre para qué sistema de IA es el prompt y enruta silenciosamente al enfoque correcto
2. **Extrae 9 dimensiones de intención** — tarea, input, output, restricciones, contexto, audiencia, memoria, criterios de éxito, ejemplos
3. **Hace preguntas clarificadoras enfocadas** — máximo 3 preguntas si falta información crítica, nunca más
4. **Enruta a la plantilla correcta** — elige y aplica la arquitectura de prompt correcta automáticamente, nunca mostrada al usuario
5. **Aplica solo técnicas seguras** — asignación de rol, ejemplos few-shot, estructura XML, anclajes de grounding, bloque de memoria según sea necesario
6. **Verifica recencia de modelo** — verifica modelos exactos y controles contra documentación oficial del proveedor cuando la solicitud depende de "el más reciente"
7. **Ejecuta una auditoría de eficiencia de tokens** — elimina cada palabra que no cambia el output
8. **Entrega el prompt** — un bloque limpio copiable con una nota de estrategia de una línea

---
## Ejemplo Completo #1: Generando Prompts para Imágenes

### Input del Usuario
```
Escríbeme un prompt de midjourney para un samurái realista parado bajo la lluvia de noche
```

### Prompt Generado
```
lone samurai standing in heavy rain at night, traditional armor, 
neon reflections on wet cobblestone street, cinematic lighting, 
dramatic shadows, fog, ultra detailed, photorealistic, 
shallow depth of field --ar 16:9 --v 6 --style raw

negative: blurry, low quality, watermark, cartoon, anime, extra limbs
```
**🎯 Objetivo:** Midjourney · **⚡ Framework:** Descriptor Visual · **💰 Tokens:** Ligero (~60) · **💡 Estrategia:** Descriptores separados por comas sobre prosa, iluminación y ambiente anclados temprano, relación de aspecto y versión bloqueadas, prompt negativo previene deriva de estilo.

---
## Ejemplo Completo #2: Generando Prompts para Código

### Input del Usuario
```
Construye un prompt de claude code para una landing page para un 
business dashboard que se vea y sienta exactamente como notion - animaciones suaves, 
UI limpia
```


### Prompt Generado
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
**🎯 Objetivo:** Claude Code · **💰 Tokens:** Medio (~380) · **💡 Estrategia:** Cada pista estética vaga de Notion traducida a valores hex exactos y especificaciones de píxel — Claude Code no puede adivinar mal. Animaciones definidas con timing, método y trigger exactos para que no haya interpretación necesaria.

---

## 🤝 Funciona con Cualquier Herramienta de IA

Maestro de Prompts incluye perfiles específicos para 20+ herramientas. Para cualquier cosa no en la lista, usa una **Huella Digital Universal**: 4 preguntas que le permiten escribir un prompt de calidad para cualquier sistema de IA que nunca haya visto antes.

<details>
<summary><h3> Haz clic para ver todos los 30+ perfiles de herramientas </h3></summary>

| Herramienta | Categoría | Qué Arregla Maestro de Prompts |
|------|----------|--------------------------|
| **Claude 5 / Claude actual** | LLM de razonamiento y agente | Esfuerzo consciente de modelo, alcance, estructura XML y control de delegación |
| **ChatGPT / GPT-5.6** | LLM de razonamiento y agente | Enrutamiento Sol/Terra/Luna, contratos lean, control de autonomía y esfuerzo |
| **Codex** | Agente de código | Alcance de archivos, límites de aprobación, verificación, subagentes acotados |
| **Grok 4.6** | LLM de razonamiento y agente | Grounding de búsqueda, esfuerzo de razonamiento, herramientas, caching y condiciones de parada |
| **Gemini 2.x** | LLM de razonamiento | Anclajes de grounding, reglas de citación, bloqueos de formato |
| **o3 / o4-mini** | LLM de razonamiento | Instrucciones cortas y limpias solamente — nunca agrega CoT (piensan internamente) |
| **Ollama** | LLM local | Pregunta qué modelo está cargado, incluye system prompt para Modelfile |
| **Qwen 2.5 / Qwen3** | LLM de peso abierto | Formato de chat template, detección de modo thinking vs non-thinking |
| **Modelos locales (Llama, Mistral)** | LLM de peso abierto | Prompts más cortos, estructura más simple, sin anidamiento complejo |
| **DeepSeek-R1** | LLM de razonamiento | Instrucciones cortas y limpias, elimina CoT, suprime output de pensamiento si es necesario |
| **MiniMax (M3 / M2.7)** | LLM de razonamiento | Clamping de temperatura, control de etiqueta thinking, optimización de output estructurado |
| **Claude Code** | IA agente | Condiciones de parada, alcance de archivos, output de checkpoint |
| **Cursor / Windsurf** | IA de IDE | Ruta de archivo, nombre de función, lista de no-tocar, guía secuencial de prompt |
| **Cline (anteriormente Claude Dev)** | IDE agente | Alcance de archivos, puertas de aprobación, condiciones de parada, desglose de tareas |
| **GitHub Copilot** | IA de autocompletado | Contrato de función exacto como docstring |
| **Antigravity** | IDE agente | Prompting basado en tareas, verificación de Artifact, nivel de autonomía |
| **Bolt / v0 / Lovable** | Generador full-stack | Especificación de stack, versión, qué NO scaffoldar |
| **Figma Make** | Generador full-stack | Referencias de nombres de componente, alcance frame-to-code |
| **Google Stitch** | Generador full-stack | Meta de interfaz sobre implementación, especificación de Material Design 3 |
| **Devin / SWE-agent** | Agente autónomo | Estado inicial, estado objetivo, condiciones de parada |
| **Manus** | Agente autónomo | Enfoque en resultado de tarea, alcance de permisos, anclajes de memoria |
| **OpenAI Computer Use** | Agente de uso de computadora | Estado de pantalla, apps permitidas, detente antes de acciones irreversibles |
| **Perplexity Computer** | Agente de uso de computadora | Prompting artifact-first, permisos acotados, pasos de verificación |
| **OpenClaw** | Agente de uso de computadora | Precisión conversacional, memoria persistente, restricciones de seguridad |
| **Perplexity / SearchGPT** | IA de búsqueda | Especificación de modo: búsqueda vs análisis vs comparación |
| **Midjourney** | IA de imágenes | Descriptores separados por comas, parámetros, prompts negativos |
| **DALL-E 3** | IA de imágenes | Descripción en prosa, exclusión de texto — detección de edición vs generación |
| **Stable Diffusion** | IA de imágenes | Sintaxis de peso `(palabra:1.3)`, guía CFG, prompt negativo obligatorio |
| **SeeDream** | IA de imágenes | Estilo de arte primero, descriptores de ambiente y atmósfera, prompt negativo |
| **ComfyUI** | IA de imágenes | Split de nodos positivo/negativo, sintaxis específica de checkpoint |
| **Meshy / Tripo / Rodin** | IA 3D | Estilo + formato de export + presupuesto de polígonos + requisitos de rig |
| **BlenderGPT** | IA 3D | Output de script Python, versión de Blender, contexto de escena |
| **Unity AI** | IA 3D / Juego | Género de juego, plataforma objetivo, descripción de mecánica sobre código |
| **Sora / Runway** | IA de video | Movimiento de cámara, duración, estilo de corte |
| **LTX / Dream Machine / Kling** | IA de video | Lenguaje cinematográfico, intensidad de movimiento, referencia de estilo |
| **ElevenLabs** | IA de voz | Emoción, ritmo, énfasis, velocidad del habla |
| **Zapier / Make / n8n** | Automatización de flujos | App de trigger + evento, app de acción + mapeo de campos |

</details>

---

## 📐 13 Plantillas de Prompts (Auto-Seleccionadas)

Maestro de Prompts elige la arquitectura correcta para cada tarea automáticamente y enruta silenciosamente — nunca ves el nombre del framework, solo el prompt.

<details>
<summary><h3> Haz clic para ver todas las 13 plantillas</h3></summary>

| Plantilla | Mejor Para |
|----------|----------|
| **RTF** (Rol, Tarea, Formato) | Tareas rápidas de una sola pasada |
| **CO-STAR** (Contexto, Objetivo, Estilo, Tono, Audiencia, Respuesta) | Documentos profesionales, reportes, escritura de negocios |
| **RISEN** (Rol, Instrucciones, Pasos, Meta Final, Acotamiento) | Proyectos complejos multi-paso |
| **CRISPE** (Capacidad, Rol, Insight, Declaración, Personalidad, Experimento) | Trabajo creativo, voz de marca, contenido iterativo |
| **Razonamiento Auditable** | Matemáticas verificables, lógica, depuración y análisis sin solicitudes de razonamiento oculto |
| **Few-Shot** | Output estructurado consistente, replicación de patrones |
| **Plantilla de Alcance de Archivo** | Cursor, Windsurf, Copilot — cualquier IA de edición de código |
| **ReAct + Condiciones de Parada** | Claude Code, Devin, AutoGPT — cualquier agente autónomo |
| **Descriptor Visual** | Midjourney, DALL-E, Stable Diffusion, Sora — generación |
| **Edición de Imagen de Referencia** | Editar una imagen existente — detecta edición vs generación automáticamente |
| **ComfyUI** | Flujos de trabajo de imágenes basados en nodos — split positivo/negativo por checkpoint |
| **Decompilador de Prompts** | Descomponer, adaptar, simplificar o dividir prompts existentes |
| **Brief de Tarea para Claude Actual** | Tareas complejas, multi-paso o agente en modelos Claude actuales |

</details>

---

## 🛡️ 5 Técnicas Seguras, Aplicadas Cuando se Necesitan

Maestro de Prompts solo usa técnicas con efectos confiables y acotados. Métodos conocidos por producir alucinaciones o output impredecible (Tree of Thought, Graph of Thought, Universal Self-Consistency, encadenamiento de prompts) están explícitamente excluidos.

| Técnica | Qué Hace |
|-----------|-------------|
| **Asignación de Rol** | Asigna una identidad experta específica para calibrar profundidad y vocabulario |
| **Ejemplos Few-Shot** | Agrega 2-5 ejemplos cuando la consistencia de formato importa más que las instrucciones |
| **Etiquetas Estructurales XML** | Envuelve secciones en XML para herramientas basadas en Claude que las parsean confiablemente |
| **Anclajes de Grounding** | Agrega reglas anti-alucinación para tareas factuales y de citación |
| **Razonamiento Auditable** | Solicita conclusiones, supuestos, evidencia y verificación sin razonamiento oculto |

---

## 🚫 37 Patrones que Matan Créditos Detectados (con Ejemplos Antes/Después)

<details>
<summary><h3> Patrones de Tarea (7)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 1 | **Verbo de tarea vago** | "ayúdame con mi código" | "Refactoriza `getUserData()` para usar async/await y manejar retornos null" |
| 2 | **Dos tareas en un prompt** | "explica Y reescribe esta función" | Divide: explica primero, reescribe después |
| 3 | **Sin criterios de éxito** | "hazlo mejor" | "Terminado cuando la función pase pruebas unitarias existentes y maneje input null" |
| 4 | **Agente sobre-permisivo** | "haz lo que sea necesario" | Lista explícita de acciones permitidas + lista explícita de acciones prohibidas |
| 5 | **Descripción emocional de tarea** | "está totalmente roto, arregla todo" | "Lanza TypeError no capturado en línea 43 cuando `user` es null" |
| 6 | **Construir-todo-de-golpe** | "construye toda mi app" | Divide en Prompt 1 (esqueleto), Prompt 2 (funcionalidad), Prompt 3 (pulido) |
| 7 | **Referencia implícita** | "ahora agrega la otra cosa que discutimos" | Siempre reafirma la tarea completa, nunca referencies "la cosa que discutimos" |

</details>

<details>
<summary><h3> Patrones de Contexto (6)</h3></summary>

### Patrones de Contexto

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 8 | **Conocimiento previo asumido** | "continúa donde lo dejamos" | Incluye Bloque de Memoria con todas las decisiones previas |
| 9 | **Sin contexto de proyecto** | "escribe una carta de presentación" | "Rol de PM en fintech B2B, 2 años de experiencia SWE, lideré 3 funcionalidades como tech lead" |
| 10 | **Stack olvidado** | Nuevo prompt contradice elección técnica previa | Siempre incluye Bloque de Memoria |
| 11 | **Invitación a alucinar** | "¿qué dicen los expertos sobre X?" | "Cita solo fuentes de las que estés seguro. Si no estás seguro, dilo." |
| 12 | **Audiencia indefinida** | "escribe algo para usuarios" | "Compradores B2B no técnicos, sin conocimiento de código, nivel de tomador de decisiones" |
| 13 | **Sin mención de fallos previos** | (vacío) | "Ya intenté X y falló porque Y. No sugieras X." |

</details>


<details>
<summary><h3> Patrones de Formato (6)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 14 | **Formato de salida faltante** | "explica este concepto" | "3 viñetas, cada una bajo 20 palabras, resumen de una oración al inicio" |
| 15 | **Longitud implícita** | "escribe un resumen" | "Escribe un resumen en exactamente 3 oraciones" |
| 16 | **Sin asignación de rol** | (vacío) | "Eres un ingeniero backend senior especializado en Node.js y PostgreSQL" |
| 17 | **Adjetivos estéticos vagos** | "haz que se vea profesional" | "Paleta monocromática, fuente base 16px, interlineado 24px, sin elementos decorativos" |
| 18 | **Sin prompts negativos (IA de imágenes)** | "un retrato de una mujer" | Agrega: "sin marca de agua, sin desenfoque, sin dedos extra, sin distorsión, sin texto" |
| 19 | **Prompt en prosa para Midjourney** | Oración descriptiva completa | "sujeto, estilo, ambiente, iluminación, composición, --ar 16:9 --v 6" |

</details>


<details>
<summary><h3> Patrones de Alcance (6)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 20 | **Sin límite de alcance** | "arregla mi app" | "Arregla solo la validación del formulario de login en `src/auth.js`. No toques nada más." |
| 21 | **Sin restricciones de stack** | "construye un componente React" | "React 18, TypeScript estricto, sin librerías externas, solo Tailwind" |
| 22 | **Sin condición de parada para agentes** | "construye toda la funcionalidad" | Condiciones de parada explícitas + checkpoint de output después de cada paso |
| 23 | **Sin ruta de archivo para IA de IDE** | "actualiza la función de login" | "Actualiza `handleLogin()` en `src/pages/Login.tsx` únicamente" |
| 24 | **Plantilla incorrecta para herramienta** | Prompt en prosa estilo GPT usado en Cursor | Adaptado a Plantilla de Alcance de Archivo (Plantilla G) |
| 25 | **Pegar todo el código base** | Contexto completo del repo en cada prompt | Acota solo a la función y archivo relevantes |

</details>

<details>
<summary><h3> Patrones de Razonamiento (5)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 26 | **Sin contrato de auditoría para tarea lógica** | "¿qué enfoque es mejor?" | Solicita la recomendación, supuestos, criterios, evidencia y verificaciones |
| 27 | **Solicitar razonamiento oculto** | "muestra tu cadena de pensamiento" | Elimínalo — pide un razonamiento conciso, evidencia y verificaciones en su lugar |
| 28 | **Esperar memoria entre sesiones** | "ya conoces mi proyecto" | Siempre re-proporciona el Bloque de Memoria en cada nueva sesión |
| 29 | **Contradecir trabajo previo** | Nuevo prompt ignora arquitectura anterior | Incluye Bloque de Memoria con todas las decisiones establecidas |
| 30 | **Sin regla de anclaje para tareas factuales** | "resume lo que los expertos dicen sobre X" | "Usa solo información de la que estés seguro. Di [incertidumbre] si no lo estás." |

</details>

<details>
<summary><h3> Patrones de Agente (7)</h3></summary>

| # | Patrón | Antes | Después |
|---|---------|--------|-------|
| 31 | **Sin estado inicial** | "constrúyeme una API REST" | "Proyecto Node.js vacío, Express instalado, `src/app.js` existe" |
| 32 | **Sin estado objetivo** | "agrega autenticación" | "`/src/middleware/auth.js` con verificación JWT. `POST /login` y `POST /register` en `/src/routes/auth.js`" |
| 33 | **Agente silencioso** | Sin output de progreso | "Después de cada paso output: ✅ [lo que se completó]" |
| 34 | **Sistema de archivos desbloqueado** | Sin restricciones de archivos | "Solo edita archivos dentro de `src/`. No toques `package.json`, `.env`, ni ningún archivo de config." |
| 35 | **Sin disparador de revisión humana** | El agente decide todo autónomamente | "Detente y pregunta antes de: eliminar cualquier archivo, agregar cualquier dependencia, o cambiar el esquema de la base de datos" |
| 36 | **Primer turno vago para modelo agente** | "arregla el bug de auth" sin alcance, archivos o criterios | Usa Plantilla M. Carga al frente el resultado, contexto, alcance, límites y criterios de aceptación. |
| 37 | **Putrefacción de contexto en sesiones largas** | Repite correcciones mientras suposiciones obsoletas permanecen en contexto | Inicia una nueva sesión para trabajo no relacionado; de lo contrario compacta alrededor de decisiones, restricciones y estado actuales. |

</details>

---

## 🧠 Sistema de Bloque de Memoria

Cuando tu conversación tiene historial, Maestro de Prompts extrae decisiones previas y prepende un Bloque de Memoria para que la IA nunca contradiga trabajo anterior:

```
## Memoria (Arrastrar desde Contexto Previo)
- Stack: React 18 + TypeScript + Supabase
- Auth usa JWT almacenado en cookies httpOnly, no localStorage
- Convención de nombres de componentes: PascalCase, sin default exports
- Sistema de diseño: solo Tailwind, sin archivos CSS personalizados
- Arquitectura: sin Redux, solo context API
```

Esta es la sola corrección más grande para sesiones largas. La mayoría de re-prompts desperdiciados vienen de la IA olvidando lo que ya decidiste.

---

## ℹ️ Historial de Versiones

- **1.8.0** — Actualización de modelos actuales. Agregado Claude Fable 5, Opus 5, Sonnet 5, GPT-5.6 Sol/Terra/Luna, Codex y enrutamiento Grok 4.6. Reemplazadas solicitudes de cadena de pensamiento oculta con razonamiento auditable y generalizado el brief de tarea de Claude para modelos actuales de pensamiento adaptativo.
- **1.7.0** — Compatibilidad con Opus 4.8. Enrutamiento Claude 4.x consciente de versión: consejo durable generalizado a través de 4.6/4.7/4.8, agregado perfil Opus 4.8 (default actual), mantenido Opus 4.7 etiquetado. Des-hardcodeada la nota de nivel de esfuerzo (ahora gestionada por harness). Plantilla M y patrón 36 cubren 4.7 y 4.8. Arreglado un fragmento suelto en patterns.md.
- **1.6.0** — Actualización Opus 4.7. Agregada Plantilla M (Brief de Tarea Opus 4.7). Actualizado enrutamiento Claude y Claude Code para literalismo, pensamiento adaptativo, esfuerzo xhigh e higiene de sesión. Agregados patrones 36–37.
- **1.5.0** — Agregado más enrutamiento de herramientas. Agregado enrutamiento de IA Agente y IA de Modelos 3D. Descripción fijada a 189 caracteres. Eliminada estimación de tokens del output. Agregada capa de instrucción y placeholders de copywriting.
- **1.4.0** — Agregada detección de edición de imagen de referencia, soporte ComfyUI, modo Decompilador de Prompts. Arreglada descripción de trigger para invocar correctamente en Claude Code. 3 plantillas nuevas agregadas a carpeta de referencias.
- **1.3.0** — Reconstruido alrededor de estructura posicional PAC2026 (30/55/15). Enrutamiento silencioso reemplaza selección de framework visible al usuario. Introducida carpeta de referencias.
- **1.2.0** — Reestructurado para arquitectura de atención. Eliminadas técnicas propensas a fabricación (ToT, GoT, USC, encadenamiento de prompts). Plantillas y patrones movidos a carpeta de referencias.
- **1.1.0** — Cobertura de herramientas expandida, agregado sistema de bloque de memoria, 35 patrones que matan créditos.
- **1.0.0** — Lanzamiento inicial

---

## 📄 Licencia

MIT: Ver [LICENSE](LICENSE) para detalles.

---

## ⭐ Historial de Estrellas

[![Gráfico de Historial de Estrellas](https://star-history.dera.page/svg?repos=nidhinjs/prompt-master&type=Date)](https://star-history.dera.page/#nidhinjs/prompt-master&Date)

---
