# Referencia de Perfiles de Herramientas

Los 29 perfiles de enrutamiento: qué tiene de particular cada herramienta y cómo se le escribe.
Lee **solo el perfil de la herramienta objetivo**, nunca el archivo entero.

Esta es la parte de la skill que caduca: nombres de modelos, controles y disponibilidad cambian
cada pocos meses. Cuando el modelo exacto importe, manda la puerta de recencia del procedimiento,
no lo que diga este archivo.

## Perfiles

- [Claude (claude.ai, API de Claude, Claude 5 / modelos Claude actuales)](#claude-claudeai-api-de-claude-claude-5-modelos-claude-actuales)
- [ChatGPT / GPT-5.6 / Modelos GPT de OpenAI](#chatgpt-gpt-56-modelos-gpt-de-openai)
- [o3 / o4-mini / Modelos de razonamiento de OpenAI](#o3-o4-mini-modelos-de-razonamiento-de-openai)
- [Grok / Grok 4.6 / xAI](#grok-grok-46-xai)
- [Gemini 2.x / Gemini 3 Pro](#gemini-2x-gemini-3-pro)
- [Qwen 2.5 (variantes instruct)](#qwen-25-variantes-instruct)
- [Qwen3 (modo thinking)](#qwen3-modo-thinking)
- [Ollama (despliegue de modelos locales)](#ollama-despliegue-de-modelos-locales)
- [Llama / Mistral / LLMs de peso abierto](#llama-mistral-llms-de-peso-abierto)
- [DeepSeek-R1](#deepseek-r1)
- [MiniMax (M3 / M2.7)](#minimax-m3-m27)
- [Claude Code](#claude-code)
- [Codex CLI / ChatGPT Work / Codex IDE](#codex-cli-chatgpt-work-codex-ide)
- [Antigravity (IDE agente-first de Google, potenciado por Gemini 3 Pro)](#antigravity-ide-agente-first-de-google-potenciado-por-gemini-3-pro)
- [Cursor / Windsurf](#cursor-windsurf)
- [Cline (anteriormente Claude Dev)](#cline-anteriormente-claude-dev)
- [GitHub Copilot](#github-copilot)
- [Bolt / v0 / Lovable / Figma Make / Google Stitch](#bolt-v0-lovable-figma-make-google-stitch)
- [Devin / SWE-agent](#devin-swe-agent)
- [IA de Investigación / Orquestación (Perplexity, Manus AI)](#ia-de-investigación-orquestación-perplexity-manus-ai)
- [Agentes de Uso de Computadora / Agentes de Navegador (Perplexity Comet/Computer, OpenAI Atlas, Claude en Chrome, OpenClaw Agents)](#agentes-de-uso-de-computadora-agentes-de-navegador-perplexity-cometcomputer-openai-atlas-claude-en-chrome-openclaw-agents)
- [IA de Imágenes — Generación (Midjourney, DALL-E 3, Stable Diffusion, SeeDream)](#ia-de-imágenes-generación-midjourney-dall-e-3-stable-diffusion-seedream)
- [IA de Imágenes — Edición de Referencia (cuando el usuario tiene una imagen existente para modificar)](#ia-de-imágenes-edición-de-referencia-cuando-el-usuario-tiene-una-imagen-existente-para-modificar)
- [ComfyUI](#comfyui)
- [IA 3D — Texto a 3D/Sistemas de Juego (Meshy, Tripo, Rodin)](#ia-3d-texto-a-3dsistemas-de-juego-meshy-tripo-rodin)
- [IA 3D — IA Dentro del Motor (Unity AI, herramientas de IA de Blender)](#ia-3d-ia-dentro-del-motor-unity-ai-herramientas-de-ia-de-blender)
- [IA de Video (Sora, Runway, Kling, LTX Video, Dream Machine)](#ia-de-video-sora-runway-kling-ltx-video-dream-machine)
- [IA de Voz (ElevenLabs)](#ia-de-voz-elevenlabs)
- [IA de Flujos de Trabajo (Zapier, Make, n8n)](#ia-de-flujos-de-trabajo-zapier-make-n8n)

---

## Claude (claude.ai, API de Claude, Claude 5 / modelos Claude actuales)

No asumas un default universal de Claude. Cuando no estés seguro, comienza con **Claude Opus 5** (`claude-opus-5`) para código agente complejo y trabajo empresarial. Usa **Claude Fable 5** (`claude-fable-5`) para los agentes de larga ejecución de mayor capacidad, **Claude Sonnet 5** (`claude-sonnet-5`) para velocidad más inteligencia frontera, y **Claude Haiku 4.5** para cargas de trabajo rápidas y económicas. Pregunta cuál modelo solo cuando la distinción cambie el prompt.

*Durable a través de modelos Claude actuales:*
- Sé claro y directo. Declara la salida deseada, restricciones y alcance explícitamente; explica por qué cuando la razón afecte el juicio.
- Usa etiquetas XML como `<context>`, `<task>`, `<constraints>`, y `<output_format>` para prompts complejos de contenido mixto; usa unos pocos ejemplos relevantes y diversos cuando el formato o tono deban bloquearse.
- Para contexto largo, pon documentos fuente antes de la consulta y envuelve documentos más metadatos en etiquetas XML descriptivas.
- Prefiere instrucciones positivas que describan el resultado deseado sobre largas listas de prohibiciones.
- No solicites razonamiento oculto ni reproduzcas pensamiento. Pide un razonamiento conciso, evidencia y resultados de verificación.
- Los modelos Claude 5 actuales usan pensamiento adaptativo y un control de esfuerzo. No hardcodees budgets de pensamiento manual; recomienda un nivel de esfuerzo solo cuando el usuario controle configuraciones de API o harness.
- Usa la Plantilla M para tareas complejas o agente.

*Fable 5:*
- Fable 5 está optimizado para el trabajo autónomo de largo horizonte más difícil. Dale una especificación completa enfocada en resultados, límites de acción explícitos e infraestructura adecuada para ejecuciones asíncronas largas.
- Ancla cada afirmación de progreso de larga ejecución en resultados reales de herramientas. Delega flujos de trabajo independientes a subagentes cuando sea útil y establece verificación basada en intervalos para construcciones largas; limita la concurrencia o el gasto cuando el costo importe.

*Opus 5:*
- Opus 5 es el punto de partida recomendado para código agente complejo y trabajo empresarial. Mantén el alcance ajustado: "Entrega lo que se pidió. No agregues funcionalidades, refactorizaciones ni abstracciones más allá de la tarea."
- Opus 5 ya se auto-verifica fuertemente. Evita instrucciones redundantes de "revisa todo" y subagentes verificadores para trabajo rutinario; delega solo flujos de trabajo genuinamente independientes y sustanciales.

*Sonnet 5:*
- Sonnet 5 sigue instrucciones literalmente, especialmente a menor esfuerzo. Declara cuando una regla aplica a cada ítem o sección.
- Eleva el esfuerzo para trabajo multi-paso difícil en lugar de compensar con prompts de razonamiento elaborados. Usa dirección de estilo y diseño explícita en lugar de parámetros de muestreo no default.

*Claude 4.8 y modelos seleccionables anteriores:*
- Los prompts explícitos y cargados al frente existentes permanecen compatibles. Si el modelo es 4.7 o posterior, usa pensamiento adaptativo y esfuerzo en lugar de `budget_tokens`.

---

## ChatGPT / GPT-5.6 / Modelos GPT de OpenAI
- Familia GPT-5.6 actual: **Sol** (`gpt-5.6-sol`, también el alias `gpt-5.6`) para capacidad flagship, **Terra** (`gpt-5.6-terra`) para trabajo diario balanceado, y **Luna** (`gpt-5.6-luna`) para trabajo rápido, repetible y de alto volumen. En ChatGPT estándar, la disponibilidad depende del plan del usuario; no prometas una opción específica de selector.
- Comienza lean. Para trabajo complejo usa cuatro secciones compactas: Meta, Contexto, Restricciones y Terminado. Declara cada instrucción una vez.
- GPT-5.6 infiere intención bien; especifica contexto de dominio, restricciones duras, límites de aprobación, criterios de éxito y qué ambigüedad debería disparar una pregunta, pero no prescribas cada paso de razonamiento.
- Define autonomía claramente: inspección local segura en alcance, ediciones y validación pueden proceder; escrituras externas, acciones destructivas, compras y expansión material de alcance requieren confirmación.
- Usa el nivel de razonamiento más bajo que cumpla con el nivel de calidad.
- Para la API, recomienda mayor esfuerzo, `reasoning.mode: "pro"`, o la beta multi-agente de Responses solo cuando la calidad medida justifique la latencia y el costo agregados. El modo Pro no es un slug de modelo de API separado.
- Para superficies de ChatGPT y Codex, recomienda controles de producto disponibles como Sol Pro, Max o Ultra solo para trabajo suficientemente difícil. No traduzcas esos controles de UI en parámetros de API.
- Declara expectativas de uso de herramientas y evidencia requerida explícitamente. Usa orquestación programática o multi-agente de herramientas solo para trabajo acotado que se divida limpiamente.
- Nunca solicites razonamiento oculto. Pide conclusiones, supuestos, evidencia y verificaciones.
- Controla la longitud visible con el contrato de salida (y `text.verbosity` en la API), no pidiendo menos pensamiento.

---

## o3 / o4-mini / Modelos de razonamiento de OpenAI
- Instrucciones CORTAS y limpias SOLAMENTE — estos modelos razonan a través de miles de tokens internos
- NUNCA agregues CoT, "piensa paso a paso" o andamiaje de razonamiento — degrada activamente la salida
- Prefiere zero-shot primero — agrega few-shot solo si es estrictamente necesario y alineado de cerca
- Declara lo que quieres y qué se ve como terminado. Nada más.
- Mantén los system prompts bajo 200 palabras — los prompts más largos dañan el rendimiento en modelos de razonamiento

---

## Grok / Grok 4.6 / xAI
- Usa `grok-4.6` para chat general actual, código, agente y trabajo de conocimiento. Soporta texto e imagen input, razonamiento configurable, function calling, búsqueda web, búsqueda en X y ejecución de código.
- Mantén la tarea enfocada en el resultado: Meta, Contexto/Input, Restricciones, Herramientas/Permisos y Terminado. Grok 4.6 es compatible con OpenAI-API, pero el prompt debe nombrar las herramientas y la evidencia que la tarea requiere.
- Elige el esfuerzo de razonamiento intencionalmente: `low` para trabajo acotado o sensible a latencia, `medium` para trabajo balanceado, `high` (el default de API) para tareas difíciles, y `xhigh` solo cuando una exploración más profunda valga el costo. El razonamiento de Grok 4.6 no puede deshabilitarse. No pidas cadena de pensamiento.
- Para hechos actuales, requiere explícitamente Web Search o X Search y citaciones. El modelo base de Grok no tiene conocimiento en tiempo real sin herramientas de búsqueda habilitadas.
- Para bucles agente largos y con muchas herramientas, define condiciones de parada, límites de aprobación, límites de reintentos y checkpoints de compactación de contexto. Mantén instrucciones estables al frente para preservar la reutilización de caché de prompt.
- Para notas de configuración de API, recomienda `prompt_cache_key` en la Responses API o `x-grok-conv-id` en Chat Completions para enrutamiento confiable de caché; no coloques valores secretos en el prompt.
- Grok de consumo y la API de xAI exponen controles diferentes. Si el usuario está en grok.com o X y no puede establecer parámetros de modelo, codifica solo requisitos de comportamiento en el prompt en lugar de configuraciones de API.

---

## Gemini 2.x / Gemini 3 Pro
- Fuerte en contexto largo y multimodal — aprovecha su gran ventana de contexto para prompts con muchos documentos
- Propenso a citaciones alucinadas — siempre agrega "Cita solo fuentes de las que estés seguro. Si no estás seguro, di [incertidumbre]."
- Puede desviarse de formatos de salida estrictos — usa bloqueos de formato explícitos con un ejemplo etiquetado
- Para tareas ancladas agrega "Basa tu respuesta solo en el contexto proporcionado. No extrapoles."

---

## Qwen 2.5 (variantes instruct)
- Excelente seguimiento de instrucciones, salida JSON, datos estructurados — aprovecha estas fortalezas
- Proporciona un system prompt claro definiendo el rol — Qwen2.5 responde bien al contexto de rol
- Funciona bien con especificaciones de formato de salida explícitas incluyendo esquemas JSON
- Los prompts más cortos y enfocados superan a los largos y complejos — acota fuertemente

---

## Qwen3 (modo thinking)
- Dos modos: modo thinking (/think o enable_thinking=True) y modo non-thinking
- Modo thinking: trata exactamente como o3 — instrucciones cortas y limpias, sin CoT, sin andamiaje
- Modo non-thinking: trata como Qwen2.5 instruct — estructura completa, formato explícito, asignación de rol

---

## Ollama (despliegue de modelos locales)
- SIEMPRE pregunta qué modelo está corriendo antes de escribir — Llama3, Mistral, Qwen2.5, CodeLlama se comportan diferente
- El system prompt es la palanca más impactante — inclúyelo en la salida para que el usuario pueda configurarlo en su Modelfile
- Los prompts más cortos y simples superan a los complejos — los modelos locales pierden coherencia con anidamiento profundo
- Temperature 0.1 para tareas de código/deterministas, 0.7-0.8 para tareas creativas
- Para código: CodeLlama o Qwen2.5-Coder, no Llama general

---

## Llama / Mistral / LLMs de peso abierto
- Funcionan mejor con prompts más cortos — estos modelos pierden coherencia con instrucciones profundamente anidadas
- Estructura simple y plana — evita anidamiento pesado o jerarquías multi-nivel
- Sé más explícito de lo que serías con Claude o GPT — el seguimiento de instrucciones es más débil
- Siempre incluye un rol en el system prompt

---

## DeepSeek-R1
- Nativo de razonamiento como o3 — NO agregues instrucciones CoT
- Solo instrucciones cortas y limpias — declara la meta y el formato de salida deseado
- Devuelve el razonamiento en etiquetas `thinking` por default — agrega "Entrega solo la respuesta final, sin razonamiento." si es necesario

---

## MiniMax (M3 / M2.7)
- API compatible con OpenAI — los prompts que funcionan con modelos GPT se transfieren directamente
- Fuerte en seguimiento de instrucciones, salida estructurada y síntesis de contexto largo — ventana de contexto de 1M en M2.7
- M2.7-highspeed está optimizado para velocidad — úsalo para tareas sensibles a latencia
- La temperatura debe estar entre 0 y 1 (inclusive) — los prompts que establecen temperatura sobre 1 fallarán
- Puede devolver razonamiento en etiquetas `thinking` — agrega "Entrega solo la respuesta final, sin etiquetas de razonamiento." si el usuario no quiere pensamiento visible
- Bueno en generación de código, salida JSON y análisis multi-paso — aprovecha estas fortalezas
- Responde bien a asignación de rol explícita y prompts estructurados con especificaciones claras de formato de salida
- Para function calling: soporta definiciones de herramientas estilo OpenAI — incluye esquemas de herramientas directamente

---

## Claude Code
- Agente — ejecuta herramientas, edita archivos, ejecuta comandos autónomamente
- Estado inicial + estado objetivo + acciones permitidas + acciones prohibidas + condiciones de parada + checkpoints
- Las condiciones de parada son OBLIGATORIAS — los bucles descontrolados son los mayores desperdiciadores de créditos
- No asumas el modelo de Claude Code. Aplica la ruta Claude actual coincidente arriba; cuando el comportamiento específico del modelo importe, pregunta cuál modelo está seleccionado.
- Carga al frente la intención, rutas relevantes, restricciones, criterios de aceptación y comandos de verificación. Solicita uso de herramientas explícitamente cuando la inspección sea requerida.
- Los modelos Fable/Opus actuales pueden excederse en el alcance y delegar fácilmente. Agrega "Solo haz cambios directamente solicitados" y reserva subagentes para pistas de investigación o implementación independientes y sustanciales.
- No fuerces un verificador separado en Opus 5 para trabajo rutinario; solicita pruebas concretas y evidencia respaldada por herramientas en su lugar. Para ejecuciones largas de Fable 5, requiere que las afirmaciones de progreso citen resultados reales de herramientas.
- Siempre acota a archivos y directorios específicos — nunca des una instrucción global sin un ancla de ruta
- Disparadores de revisión humana requeridos: "Detente y pregunta antes de eliminar cualquier archivo, agregar cualquier dependencia o afectar el esquema de la base de datos"
- Para tareas complejas, usa la Plantilla M. Maneja alcance, criterios, límites de acción y evidencia de progreso en un bloque estructurado.

---

## Codex CLI / ChatGPT Work / Codex IDE
- Usa la ruta GPT-5.6 arriba. Sol es el default de capacidad primero, Terra es el caballo de batalla diario, y Luna es mejor para tareas claras y repetibles.
- Estructura prompts de implementación como Meta, Contexto, Alcance, Restricciones, Límites de Aprobación y Terminado. Incluye comandos de verificación concretos cuando se conozcan.
- Comienza con razonamiento default. Súbelo para trabajo que necesite planificación o verificación más profundas; usa Max para las tareas de agente único más difíciles y Ultra solo cuando la tarea se divida en pistas independientes significativas.
- Mantén un agente primario responsable de la síntesis. Nombra el entregable acotado de cada subagente y limita la concurrencia en lugar de solicitar un enjambre abierto.
- Pide un razonamiento conciso, evidencia, resumen de archivos cambiados y resultados de verificación — no razonamiento oculto.

---

## Antigravity (IDE agente-first de Google, potenciado por Gemini 3 Pro)
- Prompting basado en tareas — describe resultados, no pasos
- Pide un Artifact (lista de tareas, plan de implementación) antes de la ejecución para que puedas revisarlo primero
- La automatización de navegador está integrada — incluye pasos de verificación: "Después de construir, verifica la UI en 375px y 1440px usando el agente de navegador"
- Especifica nivel de autonomía: "Pregunta antes de ejecutar comandos destructivos de terminal"
- NO mezcles tareas no relacionadas — acota a un entregable por sesión

---

## Cursor / Windsurf
- Ruta de archivo + nombre de función + comportamiento actual + cambio deseado + lista de no-tocar + lenguaje y versión
- Nunca des una instrucción global sin un ancla de archivo
- "Terminado cuando:" es requerido — define cuándo el agente deja de editar
- Para tareas complejas: divide en prompts secuenciales en lugar de un prompt grande

---

## Cline (anteriormente Claude Dev)
- Extensión agente de VS Code — edita archivos autónomamente, ejecuta comandos de terminal, usa herramientas de navegador
- Potenciado por Claude, GPT u otros LLMs — el estilo de prompting debe coincidir con el modelo subyacente
- Estado inicial + estado objetivo + alcance de archivos + condiciones de parada + puertas de aprobación
- Siempre especifica qué archivos editar y cuáles dejar intactos
- Agrega "Pregunta antes de ejecutar comandos de terminal" o "Pregunta antes de instalar dependencias" para prevenir acciones no deseadas
- Puede leer contenidos de archivos, buscar en bases de código y usar automatización de navegador — aprovecha estos para recolección de contexto
- Para tareas multi-paso: divide en prompts secuenciales con checkpoints claros
- Cline muestra una lista de tareas antes de ejecutar — revísala y ajusta el alcance si es necesario

---

## GitHub Copilot
- Escribe la firma de función exacta, docstring o comentario inmediatamente antes de invocar
- Describe tipos de input, tipo de retorno, casos extremos y qué NO debe hacer la función
- Copilot completa lo que predice, no lo que pretendes — no dejes ambigüedad en el comentario

---

## Bolt / v0 / Lovable / Figma Make / Google Stitch
- Los generadores full-stack default a boilerplate inflado — acótalos explícitamente
- Siempre especifica: stack, versión, qué NO debe generar de base, límites claros de componentes
- Lovable responde bien a descripciones design-forward — incluye intención visual/UX
- v0 es nativo de Vercel — especifica si necesitas salida no-Next.js
- Bolt maneja full-stack — sé explícito sobre qué partes son frontend vs backend vs base de datos
- Figma Make es nativo de design-to-code — referencia tus nombres de componentes de Figma directamente
- Google Stitch está enfocado en prompt-to-UI — describe la meta de la interfaz no la implementación. Agrega "sigue las guías de Material Design 3" para estilo nativo de Google
- Agrega "No agregues autenticación, modo oscuro ni funcionalidades no listadas explícitamente" para prevenir inflación de funcionalidades

---

## Devin / SWE-agent
- Completamente autónomo — puede navegar la web, ejecutar terminal, escribir y probar código
- Estado inicial muy explícito + estado objetivo requerido
- La lista de acciones prohibidas es crítica — Devin tomará decisiones que no pretendiste sin restricciones explícitas
- Acota el sistema de archivos: "Trabaja solo dentro de /src. No toques infraestructura, config ni archivos de CI."

---

## IA de Investigación / Orquestación (Perplexity, Manus AI)
- Modo de búsqueda de Perplexity: especifica búsqueda vs análisis vs comparación. Agrega requisitos de citación. Reformula preguntas propensas a alucinación como consultas ancladas.
- Manus y Perplexity Computer son orquestadores multi-agente — describe el entregable final, no los pasos. Descomponen internamente.
- Para Perplexity Computer: especifica el tipo de artefacto de salida (reporte / hoja de cálculo / código / resumen). Agrega "Señala cualquier dato sobre el que no estés confiado."
- Para tareas multi-paso largas: agrega checkpoints de verificación ya que cada paso encadenado compone riesgo de alucinación

---

## Agentes de Uso de Computadora / Agentes de Navegador (Perplexity Comet/Computer, OpenAI Atlas, Claude en Chrome, OpenClaw Agents)
- Estos agentes controlan un navegador real — hacen clic, hacen scroll, llenan formularios y completan transacciones autónomamente
- Describe el resultado, no los pasos de navegación: "Encuentra el vuelo más barato de X a Y en Emirates o KLM, no Boeing 737 Max, máximo una escala"
- Especifica restricciones explícitamente — el agente tomará sus propias decisiones sin ellas
- Agrega límites de permiso: "No hagas ninguna compra. Solo investigación."
- Agrega una condición de parada para acciones irreversibles: "Pregúntame antes de enviar cualquier formulario, completar cualquier transacción o enviar cualquier mensaje"
- Comet funciona mejor para investigación web, comparación y extracción de datos
- Atlas es más fuerte para tareas de comercio multi-paso y gestión de cuentas

---

## IA de Imágenes — Generación (Midjourney, DALL-E 3, Stable Diffusion, SeeDream)
Primero detecta: ¿generación desde cero o edición de una imagen existente?

- **Midjourney**: Descriptores separados por comas, no prosa. Sujeto primero, luego estilo, ambiente, iluminación, composición. Parámetros al final: `--ar 16:9 --v 6 --style raw`. Prompts negativos vía `--no [elementos no deseados]`
- **DALL-E 3**: Funciona la descripción en prosa. Agrega "no incluyas texto en la imagen a menos que se especifique." Describe primer plano, plano medio y fondo separadamente para composiciones complejas.
- **Stable Diffusion**: Sintaxis de peso `(palabra:peso)`. CFG 7-12. El prompt negativo es OBLIGATORIO. Pasos 20-30 para borradores, 40-50 para finales.
- **SeeDream**: Fuerte en generación artística y estilizada. Especifica el estilo de arte explícitamente (anime, cinematográfico, pictórico) antes del contenido de la escena. Los descriptores de ambiente y atmósfera funcionan bien. Prompt negativo recomendado.

---

## IA de Imágenes — Edición de Referencia (cuando el usuario tiene una imagen existente para modificar)
Detecta cuando: el usuario menciona "cambiar", "editar", "modificar", "ajustar" algo en una imagen existente, o sube una referencia.
Siempre instruye al usuario a adjuntar la imagen de referencia a la herramienta primero. Construye el prompt alrededor del delta SOLAMENTE — qué cambia, qué permanece igual.
Usa la Plantilla J, que trae la plantilla completa de edición de referencia.

---

## ComfyUI
Flujo de trabajo basado en nodos — no es un solo cuadro de prompt. Pregunta qué modelo de checkpoint está cargado antes de escribir.
Entrega siempre dos bloques separados: Prompt Positivo y Prompt Negativo. Nunca los mezcles.
Usa la Plantilla K, que trae la plantilla completa de ComfyUI.

---

## IA 3D — Texto a 3D/Sistemas de Juego (Meshy, Tripo, Rodin)
- Describe: palabra clave de estilo (low-poly / realista / caricatura estilizada) + sujeto + características clave + material primario + detalle de textura + especificación técnica
- Prompt negativo soportado — úsalo: "sin fondo, sin base, sin partes flotantes"
- Meshy: mejor para assets de juego y equipos. Los prompts de assets de juego funcionan mejor aquí.
- Tripo: más rápido para topología limpia. Prototipado rápido y assets de concepto.
- Rodin: mayor calidad para prompts fotorealistas. Más lento y más caro.
- Especifica el uso de exportación previsto: motor de juego (GLB/FBX), impresión 3D (STL), web (GLB)
- Para personajes: especifica pose en A o pose en T si el modelo será riggeado

---

## IA 3D — IA Dentro del Motor (Unity AI, herramientas de IA de Blender)
- Unity AI (Unity 6.2+, reemplaza Muse retirado): usa /ask para documentación y consultas de proyecto, /run para automatizar tareas repetitivas del Editor, /code para generar o revisar código C#. Sé preciso — declara exactamente qué necesita pasar en el Editor.
- Generadores de IA de Unity: texto-a-sprite, texto-a-textura, texto-a-animación. Describe el tipo de asset, estilo de arte y restricciones técnicas (resolución, paleta de colores, loop de animación o one-shot).
- BlenderGPT / add-ons de IA de Blender: estos generan scripts de Python que se ejecutan en Blender. Sé específico sobre geometría, nombres de materiales y contexto de escena. Incluye "aplicar al objeto seleccionado" o "aplicar a toda la escena" para evitar ambigüedad.

---

## IA de Video (Sora, Runway, Kling, LTX Video, Dream Machine)
- Sora: describe como si dirigieras una toma de película. El movimiento de cámara es crítico — estático vs dolly vs grúa cambia la salida dramáticamente.
- Runway Gen-3: responde a lenguaje cinematográfico — referencia estilos de película para estética consistente.
- Kling: fuerte en movimiento humano realista — describe el movimiento corporal explícitamente, especifica ángulo de cámara y tipo de toma.
- LTX Video: generación rápida, sensible al prompt — mantén descripciones concisas y visuales. Especifica resolución e intensidad de movimiento explícitamente.
- Dream Machine (Luma): calidad cinematográfica — referencia configuraciones de iluminación, tipos de lente y estilos de gradación de color.

---

## IA de Voz (ElevenLabs)
- Especifica emoción, ritmo, marcadores de énfasis y velocidad del habla directamente
- Usa marcadores tipo SSML para énfasis: indica qué palabras enfatizar, dónde pausar
- Las descripciones en prosa no se traducen — especifica parámetros directamente

---

## IA de Flujos de Trabajo (Zapier, Make, n8n)
- App de trigger + evento de trigger → app de acción + acción + mapeo de campos. Paso a paso.
- Requisitos de auth notados explícitamente — "asume que [app] ya está conectada"
- Para flujos multi-paso: numera cada paso y especifica qué datos pasan entre pasos
