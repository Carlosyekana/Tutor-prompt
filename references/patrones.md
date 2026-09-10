# Referencia de Patrones que Desperdician Créditos

37 patrones que desperdician tokens y causan re-prompts. Lee este archivo cuando el usuario pegue un mal prompt y te pida que lo arregles, o cuando diagnosticas por qué un prompt está rindiendo mal.

---

## Patrones de Tarea

| # | Patrón | Mal Ejemplo | Arreglado |
|---|--------|-------------|-----------|
| 1 | **Verbo de tarea vago** | "ayúdame con mi código" | "Refactoriza `getUserData()` para usar async/await y manejar retornos null" |
| 2 | **Dos tareas en un solo prompt** | "explica Y reescribe esta función" | Divide en dos prompts: explica primero, reescribe después |
| 3 | **Sin criterios de éxito** | "hazlo mejor" | "Terminado cuando la función pase las pruebas unitarias existentes y maneje input null sin lanzar excepciones" |
| 4 | **Agente sobre-permisivo** | "haz lo que sea necesario" | Lista explícita de acciones permitidas + lista explícita de acciones prohibidas |
| 5 | **Descripción emocional de tarea** | "está totalmente roto, arregla todo" | "Lanza TypeError no capturado en la línea 43 cuando `user` es null" |
| 6 | **Construir-todo-de-golpe** | "construye toda mi app" | Divide en Prompt 1 (esqueleto), Prompt 2 (funcionalidad core), Prompt 3 (pulido) |
| 7 | **Referencia implícita** | "ahora agrega la otra cosa que discutimos" | Siempre reafirma la tarea completa — nunca hagas referencia a "la cosa que discutimos" |

---

## Patrones de Contexto

| # | Patrón | Mal Ejemplo | Arreglado |
|---|--------|-------------|-----------|
| 8 | **Conocimiento previo asumido** | "continúa donde lo dejamos" | Incluye el Bloque de Memoria con todas las decisiones previas |
| 9 | **Sin contexto de proyecto** | "escribe una carta de presentación" | "Rol de PM en fintech B2B, 2 años de experiencia como SWE transicionando a producto, lideré técnicamente 3 funcionalidades" |
| 10 | **Stack olvidado** | Nuevo prompt contradice elección técnica previa | Siempre incluye el Bloque de Memoria con el stack establecido |
| 11 | **Invitación a alucinar** | "¿qué dicen los expertos sobre X?" | "Cita solo fuentes de las que estés seguro. Si no estás seguro, dílo explícitamente en lugar de adivinar." |
| 12 | **Audiencia indefinida** | "escribe algo para usuarios" | "Compradores B2B no técnicos, sin conocimiento de código, nivel de tomador de decisiones" |
| 13 | **Sin mención de fallos previos** | (vacío) | "Ya intenté X y no funcionó porque Y. No sugieras X." |

---

## Patrones de Formato

| # | Patrón | Mal Ejemplo | Arreglado |
|---|--------|-------------|-----------|
| 14 | **Formato de salida faltante** | "explica este concepto" | "3 viñetas, cada una de menos de 20 palabras, con un resumen de una oración al inicio" |
| 15 | **Longitud implícita** | "escribe un resumen" | "Escribe un resumen en exactamente 3 oraciones" |
| 16 | **Sin asignación de rol** | (vacío) | "Eres un ingeniero backend senior especializado en Node.js y PostgreSQL" |
| 17 | **Adjetivos estéticos vagos** | "haz que se vea profesional" | "Paleta monocromática, fuente base 16px, interlineado 24px, sin elementos decorativos" |
| 18 | **Sin prompts negativos para IA de imágenes** | "un retrato de una mujer" | Agrega: "sin marca de agua, sin desenfoque, sin dedos extra, sin distorsión, sin texto superpuesto" |
| 19 | **Prompt en prosa para Midjourney** | Oración descriptiva completa | "sujeto, estilo, ambiente, iluminación, composición, --ar 16:9 --v 6" |

---

## Patrones de Alcance

| # | Patrón | Mal Ejemplo | Arreglado |
|---|--------|-------------|-----------|
| 20 | **Sin límite de alcance** | "arregla mi app" | "Arregla solo la validación del formulario de login en `src/auth.js`. No toques nada más." |
| 21 | **Sin restricciones de stack** | "construye un componente React" | "React 18, TypeScript estricto, sin librerías externas, solo Tailwind" |
| 22 | **Sin condición de parada para agentes** | "construye toda la funcionalidad" | Condiciones de parada explícitas + ✅ output de checkpoint después de cada paso |
| 23 | **Sin ruta de archivo para IA de IDE** | "actualiza la función de login" | "Actualiza `handleLogin()` en `src/pages/Login.tsx` únicamente" |
| 24 | **Plantilla incorrecta para la herramienta** | Prompt en prosa estilo GPT usado en Cursor | Adapta a la Plantilla de Alcance de Archivo (Plantilla G) |
| 25 | **Pegar todo el código base** | Contexto completo del repo en cada prompt | Limita solo a la función y archivo relevantes |

---

## Patrones de Razonamiento

| # | Patrón | Mal Ejemplo | Arreglado |
|---|--------|-------------|-----------|
| 26 | **Sin contrato de auditoría para tarea lógica** | "¿qué enfoque es mejor?" | Solicita la recomendación, supuestos, criterios de decisión, evidencia y verificaciones |
| 27 | **Solicitar razonamiento oculto** | "muestra tu cadena de pensamiento" | Elimínalo — pide un razonamiento conciso, evidencia y verificaciones en su lugar |
| 28 | **Esperar memoria entre sesiones** | "ya conoces mi proyecto" | Siempre re-proporciona el Bloque de Memoria en cada nueva sesión |
| 29 | **Contradecir trabajo previo** | Nuevo prompt ignora arquitectura anterior | Incluye el Bloque de Memoria con todas las decisiones establecidas |
| 30 | **Sin regla de anclaje para tareas factuales** | "resume lo que los expertos dicen sobre X" | "Usa solo información de la que estés altamente seguro de que es precisa. Di [incertidumbre] si no lo estás." |

---

## Patrones de Agentes

| # | Patrón | Mal Ejemplo | Arreglado |
|---|--------|-------------|-----------|
| 31 | **Sin estado inicial** | "constrúyeme una API REST" | "Proyecto Node.js vacío, Express instalado, `src/app.js` existe" |
| 32 | **Sin estado objetivo** | "agrega autenticación" | "`/src/middleware/auth.js` con verificación JWT. `POST /login` y `POST /register` en `/src/routes/auth.js`" |
| 33 | **Agente silencioso** | Sin output de progreso | "Después de cada paso output: ✅ [lo que se completó]" |
| 34 | **Sistema de archivos desbloqueado** | Sin restricciones de archivos | "Solo edita archivos dentro de `src/`. No toques `package.json`, `.env`, ni ningún archivo de configuración." |
| 35 | **Sin disparador de revisión humana** | El agente decide todo autónomamente | "Detente y pregunta antes de: eliminar cualquier archivo, agregar cualquier dependencia, o cambiar el esquema de la base de datos" |
| 36 | **Primer turno vago para modelo agente** | "arregla el bug de auth" sin alcance, archivos o criterios | Usa la Plantilla M. Carga al frente el resultado, contexto relevante, alcance de archivos, restricciones, límites de acción y criterios de aceptación. |
| 37 | **Putrefacción de contexto en sesiones largas** | Repite correcciones mientras suposiciones obsoletas permanecen en el contexto | Inicia una nueva sesión para trabajo no relacionado; de lo contrario, compacta alrededor de decisiones actuales, restricciones, fallos y estado objetivo. Delega solo investigación independiente y sustancial. |
