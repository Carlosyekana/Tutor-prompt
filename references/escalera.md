# Escalera de Prompting — Referencia Completa (Niveles 0 a 6)

Progresión pedagógica de 7 niveles para llevar un prompt de respuesta enciclopédica a conocimiento estratégico aplicado. Cada nivel incluye el concepto, un prompt de ejemplo y la respuesta esperada. Los ejemplos vienen trabajados en dos dominios reales de taller: **prospectiva** (Universidad del Valle) e **investigación en salud** (Universidad Libre).

Regla de uso: escala solo hasta el nivel que el objetivo requiere. Cada nivel agrega tokens; el Nivel 1 bien hecho resuelve la mayoría de las tareas profesionales.

---

## 🟢 Nivel 0: El Prompt Ingenuo

**Concepto:** órdenes directas que tratan a la IA como un buscador. Generan resultados genéricos y superficiales.

**Ejemplo (prospectiva):** `¿Qué es la prospectiva y los estudios de futuro?`

**Respuesta típica (tipo Wikipedia):**
> "La prospectiva es una disciplina que estudia el futuro para comprenderlo y poder influir en él. Se diferencia de la predicción porque no busca adivinar un resultado único, sino explorar múltiples escenarios posibles."

**Ejemplo (salud):** `¿Qué impacto a futuro tiene la inteligencia artificial en la salud?`

**Diagnóstico:** si el usuario pega algo así, subir a Nivel 1 es obligatorio.

---

## 🟡 Nivel 1: El Prompt Estructurado

**Concepto:** arquitectura base **[ROL] [CONTEXTO] [MISIÓN] [FORMATO]**. Es el baseline profesional.

**Ejemplo (prospectiva):**
> **[ROL]** Actúa como Director del Instituto de Prospectiva de Univalle.
> **[CONTEXTO]** Estoy redactando la justificación de una tesis sobre innovación pública en el Valle del Cauca.
> **[MISIÓN]** Define la prospectiva estratégica y su valor para el desarrollo regional.
> **[FORMATO]** Un párrafo técnico seguido de 3 viñetas de impacto.

**Ejemplo (salud):**
> **[ROL]** Actúa como Investigador Principal en Salud Pública de la Universidad Libre seccional Cali.
> **[CONTEXTO]** Estoy redactando la justificación de un proyecto sobre adopción de herramientas predictivas para diagnóstico temprano de enfermedades crónicas en la red hospitalaria del Valle del Cauca.
> **[MISIÓN]** Define el impacto de estas tecnologías en la salud pública regional y su valor para el sistema de salud.
> **[FORMATO]** Un párrafo técnico seguido de 3 viñetas de impacto clínico.

**Clave:** el rol calibra vocabulario, el contexto ancla el dominio, la misión precisa la operación y el formato bloquea la salida.

---

## 🟠 Nivel 2: Pasos de Razonamiento (Cadena de Pasos)

**Concepto:** obligar a la IA a mostrar su lógica paso a paso para reducir alucinaciones y mejorar el razonamiento metodológico.

**Ejemplo (prospectiva):**
> "Explícame qué es la prospectiva siguiendo estos pasos:
> **Paso 1:** Identifica el origen del pensamiento prospectivo frente al determinismo.
> **Paso 2:** Deduce por qué es una herramienta crítica para la innovación.
> **Paso 3:** Redacta una conclusión sobre el perfil del prospectivista hoy."

**Ejemplo (salud):**
> "Explícame cómo integrar una nueva tecnología en los protocolos de salud siguiendo estos pasos:
> **Paso 1:** Identifica las barreras éticas y de privacidad de datos (Ley Estatutaria de Salud en Colombia).
> **Paso 2:** Deduce por qué es necesario capacitar al personal médico frente al riesgo de sesgo algorítmico.
> **Paso 3:** Redacta una conclusión sobre el perfil del médico-investigador moderno."

**⚠️ Compatibilidad con modelos actuales:** implementa este nivel como **razonamiento auditable por pasos** — cada paso pide conclusión, supuestos y evidencia, nunca una traza de pensamiento oculta. NO lo uses en modelos de razonamiento nativo (o3/o4-mini, DeepSeek-R1, Qwen3 en modo thinking, GPT-5.6 con esfuerzo alto): ahí degrada el output; basta con declarar la meta y el formato.

---

## 🔴 Nivel 3: Poda Estratégica (Prompt Negativo)

**Concepto:** prohibir vicios, jerga vacía y clichés para generar textos limpios, directos y listos para un artículo científico o comunicado institucional.

**Ejemplo (prospectiva):**
> "Describe la prospectiva estratégica.
> **Restricciones:** NO uses lenguaje denso, NO excedas 50 palabras, NO uses la frase 'en conclusión' ni 'es importante destacar'."

**Ejemplo (salud):**
> "Describe el uso de modelos epidemiológicos predictivos.
> **Restricciones:** NO uses lenguaje matemático denso, NO excedas 50 palabras, NO uses la frase 'en conclusión' ni 'es importante destacar'."

**Clave:** las prohibiciones deben ser específicas y verificables (frases exactas vetadas, techo de palabras), no adjetivos vagos.

---

## 🟣 Nivel 4: El Socrático

**Concepto:** hacer preguntas de contexto para activar redes de razonamiento en la IA **antes** de pedirle que ejecute la tarea final.

**Ejemplo (prospectiva):**
> "¿Cuáles son los retos de planeación en el suroccidente colombiano? ¿Cómo afecta la visión de corto plazo a la competitividad? **[ACCIÓN]** Ahora, define prospectiva como la solución a esos problemas."

**Ejemplo (salud):**
> "¿Cuáles son los mayores retos de atención primaria en las comunas más vulnerables de Cali? ¿Cómo afecta la escasez de especialistas a los tiempos de morbimortalidad? **[ACCIÓN]** Ahora, con eso en mente, define cómo una herramienta de triaje inteligente podría ser la solución a esos problemas."

**Clave:** la respuesta final nace del diagnóstico, no de la plantilla. Úsalo para justificaciones, definiciones y propuestas que deben sonar a territorio, no a Wikipedia.

---

## ⚫ Nivel 5: Abogado del Diablo

**Concepto:** someter ideas y premisas a crítica severa para identificar puntos ciegos y destruir la autocomplacencia, antes de defenderlas ante terceros.

**Ejemplo (prospectiva):**
> "Aquí está mi definición: 'La prospectiva ayuda a planear mejor'. Actúa como un político escéptico que cree que esto es una pérdida de tiempo. Critica mi definición y luego reescríbela para que sea irrefutable."

**Ejemplo (salud):**
> "Aquí está la premisa de mi investigación: *'La tecnología mejorará la atención al paciente'*. Actúa como el Director Médico del hospital, altamente escéptico, preocupado por el presupuesto y las posibles demandas por mala praxis. Critica mi premisa sin piedad y luego reescríbela para que sea sólida frente a un comité de ética."

**Estructura de salida esperada:** crítica sin piedad → versión reforzada que sobrevive a esa crítica.

**Clave:** el crítico debe ser concreto — cargo, incentivos y objeciones reales. "Critica esto" a secas produce crítica genérica.

---

## 🌈 Nivel 6: Traductor de Audiencias

**Concepto:** adaptar un mismo concepto técnico o hallazgo a múltiples realidades, niveles de literacidad y tonos simultáneamente.

**Ejemplo (prospectiva):**
> "Explica qué es la prospectiva para:
> 1. Un Ministro de Hacienda (foco en eficiencia),
> 2. Un estudiante de colegio (metáfora sencilla),
> 3. Un post de Instagram (inspirador)."

**Ejemplo (salud):**
> "Explica el impacto de la tecnología predictiva en salud para:
> 1. El Secretario de Salud Municipal (foco en indicadores y presupuesto),
> 2. Un paciente de la tercera edad (metáfora sencilla y tranquilizadora),
> 3. Un post de Instagram (inspirador para estudiantes de medicina)."

**Respuesta tipo (multimodal):**
> **Ministro:** herramienta de optimización fiscal que mitiga riesgos sistémicos mediante análisis de escenarios de largo plazo.
> **Estudiante:** es como usar luces altas en un carro: ves los obstáculos del camino mucho antes de llegar a ellos.
> **Instagram:** 🚀 ¡El futuro no se adivina, se diseña! #Futuros

**Clave:** una sola llamada, N registros calibrados. Cada versión lleva su foco explícito entre paréntesis para que el modelo no mezcle tonos.

---

## Cómo Componer los Niveles

Los niveles no son excluyentes. Composiciones útiles:

- **1 + 3:** estructura completa + poda → textos institucionales limpios de una pasada.
- **4 + 1:** diagnóstico socrático → definición estructurada → justificaciones con arraigo local.
- **1 + 5:** propuesta estructurada sometida a crítica adversarial → lista para comité.
- **1 + 6:** concepto estructurado traducido a N audiencias → paquete de divulgación completo.
- **4 + 5 + 3:** diagnóstico, crítica y poda → la pieza estratégica más resistente (y más cara en tokens).

Recuerda: cada nivel agregado consume tokens y atención del modelo. Escala solo cuando la falla diagnosticada lo pida.
