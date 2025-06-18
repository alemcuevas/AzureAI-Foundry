# Laboratorio 5: Creación de Connected Skills en Azure AI Foundry

## Objetivo

En este laboratorio aprenderemos a crear y conectar agentes secundarios (Connected Skills) a un agente principal en Azure AI Foundry. Esto permite componer soluciones más modulares, delegando tareas especializadas a subagentes.

## Prerrequisitos

- Tener un agente principal ya creado (por ejemplo: `agente-principal-gpt4o`)
- Haber creado al menos un agente adicional que actuará como skill (por ejemplo: `agente-clima`, `agente-finanzas`, etc.)
- Acceso al portal de Azure AI Foundry: https://ai.azure.com/

## Pasos del laboratorio

### Paso 1 - Crear los agentes secundarios (skills)

- Desde la sección **Agents**, haz clic en **+ New agent**.
- Asigna un nombre y propósito específico a cada agente. Ejemplos:
  - `agente-clima` → responde preguntas sobre clima.
  - `agente-divisas` → responde consultas sobre tipo de cambio.
- Asegúrate de asignar instrucciones claras y específicas para su dominio.

### Paso 2 - Acceder al agente principal

- En la sección **Agents**, selecciona tu agente principal.
- Accede a su configuración.

### Paso 3 - Agregar Connected Skills

- En el panel lateral derecho, desplázate a la sección **Connected agents (0)**.
- Haz clic en **+ Add**.
- Selecciona uno o más agentes que actuarán como skills.
- Opcional: define un nombre personalizado para cada skill si quieres que el agente los invoque por nombre.
- Guarda los cambios.

### Paso 4 - Validar en el Playground

- Haz clic en **Try in playground** desde el agente principal.
- Prueba preguntas que correspondan al dominio de los skills conectados. Ejemplos:
  - “¿Cómo está el clima en Madrid hoy?” (esperado: lo responde el `agente-clima`)
  - “¿Cuánto vale un dólar en euros?” (esperado: lo responde el `agente-divisas`)
- El agente principal debería delegar automáticamente la tarea al skill adecuado y devolver la respuesta final.

## Consideraciones adicionales

- Los Connected Skills funcionan mejor cuando cada skill tiene un dominio claro y no se superponen demasiado.
- Puedes conectar múltiples skills a un solo agente, y el runtime decidirá cuál invocar según el contexto de la conversación.
- En ambientes empresariales, puedes versionar y administrar estos agentes por equipo o función.

## Recursos oficiales

- Azure AI Foundry - Connected agents: https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-connected-agents
- Azure AI Foundry - Agent composition patterns: https://learn.microsoft.com/en-us/azure/ai-foundry/overview-agent-composition
