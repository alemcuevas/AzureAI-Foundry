# 🧠 Laboratorio-Reto: Construcción de un Agente Financiero Multicomponente en Azure AI Foundry

## 🎯 Objetivo del reto

Crear un **Agente Financiero Maestro** en Azure AI Foundry que integre múltiples agentes especializados (subagentes) conectados mediante la funcionalidad de **Connected Skills**, con el fin de resolver de manera precisa, útil y contextual preguntas dentro del dominio financiero.

El agente que responda de forma más completa, clara y relevante a una batería de preguntas reales será el ganador.

---

## 🧩 Estructura del ejercicio

Cada participante o equipo deberá construir:

1. **Agentes especializados** (mínimo 2), por ejemplo:
   - `agente_divisas`: experto en tasas de cambio
   - `agente_inversiones`: experto en tipos de inversión
   - `agente_ahorro`: enfocado en finanzas personales
   - `agente_credito`: resuelve dudas sobre préstamos, tasas y créditos

2. **Un agente maestro** llamado `agente_finanzas` que actúe como orquestador y delegue a los subagentes según el contexto.

---

## 🛠️ ¿Qué se puede usar?

✅ Herramientas permitidas en el **portal de Azure AI Foundry**:

- Prompts base del agente (Instructions)
- Connected Skills
- Tools configurados en Actions (opcional)
- Memories (Knowledge, opcional)

🚫 No se permite:

- Código personalizado (no VSCode ni SDK)
- JSON externos
- Modificación vía API

---

## 📝 Actividades del laboratorio

### Paso 1 – Crear subagentes especializados

Crea al menos dos agentes financieros enfocados en diferentes temas.  
Ejemplos:

- `agente_divisas` → responde: *¿Cuánto valen 100 euros en pesos?*
- `agente_inversiones` → responde: *¿Qué es un Cete? ¿Cuánto rinde?*
- `agente_credito` → responde: *¿Cuáles son los requisitos para solicitar una tarjeta?*
- `agente_ahorro` → responde: *¿Cuál es la mejor forma de ahorrar en México?*

> **Tip**: En las Instructions de cada uno, especifica bien su rol y limita su ámbito.  
> Ejemplo:  
> _"Eres un experto en divisas. Solo respondes preguntas sobre tipos de cambio. Si la pregunta no es relevante, indícalo claramente."_  

---

### Paso 2 – Crear el agente maestro

Crea un nuevo agente llamado `agente_finanzas`.

En sus Instructions escribe algo como:

```text
Eres un asesor financiero general. Cuando una pregunta es muy específica, delegas a un subagente experto. Conectas con otros agentes especializados para dar respuestas precisas y completas.
```

Conecta los subagentes creados previamente en la sección **Connected Skills**.

---

### Paso 3 – Validar en el Playground

Usa el Playground para probar tu agente maestro con las siguientes preguntas:

1. ¿Cuánto valen 500 dólares en pesos colombianos?
2. ¿Qué opciones tengo para invertir a corto plazo?
3. ¿Cuánto me costaría pedir un préstamo de 100,000 pesos?
4. ¿Cuál es la mejor forma de ahorrar si gano 10,000 pesos al mes?

---

## 🏆 Criterios de evaluación

Se evaluará a cada `agente_finanzas` en base a:

| Criterio                        | Peso |
|---------------------------------|------|
| Claridad y precisión de las respuestas | 40% |
| Uso correcto de subagentes especializados | 30% |
| Diseño lógico del prompt maestro | 20% |
| Creatividad / especialización de subagentes | 10% |

---

## 💡 Consejo

No intentes poner todo en un solo agente. Divide responsabilidades y comunica claramente el alcance de cada uno. Un buen prompt vale más que un pipeline.

---

## 🏁 Entregable

- Tu agente `agente_finanzas` configurado en Foundry
- Mínimo 2 subagentes funcionales y conectados
- Captura de pantalla del Playground con respuestas a las 4 preguntas
- Nombre del equipo o participante

---

## 🏅 Premio simbólico

El equipo con el agente más completo y preciso será reconocido como el **Arquitecto Foundry Financiero** del reto.

---

## 📚 Recursos útiles

- [Azure AI Foundry – Connected Skills](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/agents/overview)
- [Prompt design for multi-agent orchestration](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/prompts)
