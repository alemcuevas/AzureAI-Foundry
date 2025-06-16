# Laboratorio 7: Construcción de Reasoning Plans (Orchestrations) en AI Foundry

## Objetivo

En este laboratorio vamos a:

- Diseñar un Reasoning Plan personalizado dentro de AI Foundry.
- Controlar cómo el agente decide invocar Tools, Skills y Memories.
- Aplicar condicionales simples en el flujo de razonamiento.

Los Reasoning Plans permiten definir flujos controlados, seguros y reproducibles, ideales para entornos empresariales.

## Prerrequisitos

- Haber completado el Laboratorio 6.
- Agent configurado con Memories, Tools, Skills y Evaluators.
- Acceso al Project dentro del Workspace de AI Foundry.

## Concepto de Reasoning Plan

- Los Reasoning Plans permiten definir de forma explícita el flujo de razonamiento de un Agent.
- Evitan que el LLM tome decisiones libremente sobre cuándo invocar Tools o Skills.
- Mejoran el control, la reproducibilidad y la auditabilidad del agente.

## Escenario del laboratorio

Vamos a construir un Reasoning Plan donde:

- Si el usuario pregunta por tasas de cambio, el agente invocará el Tool de Exchange Rates.
- Si el usuario pregunta por cálculos de APR, invocará el Skill de cálculo de APR.
- En otros casos, usará el modelo GPT-4o para generar respuestas generales.

## Paso 1 - Acceder a Reasoning Plans

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project creados.
- En el menú lateral selecciona Reasoning Plans.

## Paso 2 - Crear un nuevo Reasoning Plan

- Haz clic en Create Reasoning Plan.
- Completa los campos:

Reasoning Plan Name: reasoning-plan-lab

Description: Plan de razonamiento controlado para el laboratorio.

## Paso 3 - Definir el flujo lógico

- Utiliza el editor visual de Reasoning Plan.

- Agrega los siguientes nodos de flujo:

  1. **Input Classifier (Optional para el lab inicial):**
  
     - Puedes omitir en esta primera versión o usar simple keywords.

  2. **Conditional Branch:**

     - Condición 1: Si el prompt contiene "tipo de cambio" o "exchange rate"

       - Acción: Invocar el Tool exchange-rate-tool

     - Condición 2: Si el prompt contiene "APR" o "tasa efectiva"

       - Acción: Invocar el Skill calculo-apr-skill

     - Else:

       - Acción: Invocar el Foundation Model (GPT-4o) directamente.

## Paso 4 - Configurar cada nodo

- Para los nodos de Tool y Skill:

  - Selecciona los recursos previamente creados en los Labs anteriores.
  - Mapea los inputs desde el prompt cuando sea necesario.
  - Puedes simplificar el mapeo en este primer lab.

- Para el nodo de Foundation Model:

  - Selecciona GPT-4o como modelo de fallback.
  - Configura temperatura y max tokens (se puede usar default).

## Paso 5 - Validación del Reasoning Plan

- Guarda el Reasoning Plan.
- Ejecuta pruebas en modo Test Plan:

  - Pregunta 1: ¿Cuál es el tipo de cambio actual de USD a EUR?
  - Pregunta 2: Calcula la tasa efectiva si tengo 8% nominal con 12 periodos.
  - Pregunta 3: ¿Qué es el capital de trabajo?

- Observa cómo el Reasoning Plan enruta las solicitudes al Tool, al Skill o al modelo según corresponda.

## Paso 6 - Asociar el Reasoning Plan al Agent

- Accede al Agent primer-agent-gpt4o.
- Edita la configuración del Agent.
- En la sección Reasoning Plan, selecciona: reasoning-plan-lab.
- Guarda los cambios.

## Paso 7 - Prueba completa del Agent con Reasoning Plan

- Ingresa a Test Agent.
- Realiza nuevamente las preguntas del Paso 5.
- Observa el flujo completo de reasoning planificado y los logs de ejecución de cada nodo.

## Resultado esperado

- Reasoning Plan creado y funcional.
- Flujo de razonamiento controlado según tipo de pregunta.
- Integración automática de Tools, Skills y Foundation Model.
- Ejecución completamente auditada dentro de AI Foundry.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/agents-overview
