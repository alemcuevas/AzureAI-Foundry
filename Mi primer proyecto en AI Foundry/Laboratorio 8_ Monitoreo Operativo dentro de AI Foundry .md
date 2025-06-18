# Laboratorio 8: Monitoreo Operativo dentro de AI Foundry

## Objetivo

En este laboratorio vamos a:

- Revisar las capacidades de monitoreo nativas de AI Foundry.
- Consultar los logs de reasoning plan.
- Validar el consumo de modelos y recursos.
- Observar la ejecución de Tools, Skills y Evaluators.

El monitoreo es fundamental para la operación segura, auditada y gobernada de los agentes.

## Prerrequisitos

- Haber completado el Laboratorio 7.
- Agent operativo bajo Reasoning Plan.
- Acceso al Project dentro del Workspace de AI Foundry.

## Concepto de Monitoreo en AI Foundry

- AI Foundry ofrece observabilidad nativa de las ejecuciones de agents.
- Permite visualizar:
  - Reasoning Plan Execution.
  - Invocaciones de Tools y Skills.
  - Evaluaciones de Safety.
  - Consumo de tokens.
  - Latencias y errores.

## Paso 1 - Acceder a la sección de Monitorización

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project creados.
- En el menú lateral selecciona Monitor.

![image](https://github.com/user-attachments/assets/dae6f3e1-4a8f-4835-9816-f2d3a3dfe91c)

![image](https://github.com/user-attachments/assets/671cbf26-40c7-4259-957b-f652376c43dc)

![image](https://github.com/user-attachments/assets/c49e67b3-8a79-4947-a321-2c39703a7d88)

![image](https://github.com/user-attachments/assets/aa9fe94d-ee4e-42e7-9bb8-89deffa50aba)

![image](https://github.com/user-attachments/assets/cd7c2861-26ab-4bbe-bcd3-c52aa735a0c0)

![image](https://github.com/user-attachments/assets/dcb99bc5-ff48-40ac-b1a8-c797dc0e517f)

## Paso 2 - Visualización de ejecución de Agents

- Dentro de Monitor, selecciona la pestaña Agent Execution.
- Filtra por el Agent: primer-agent-gpt4o.
- Observa el histórico de ejecuciones.

Para cada ejecución podrás ver:

- Timestamp.
- Status (Success, Failure, etc).
- Reasoning Plan utilizado.
- Safety Evaluations activadas.

## Paso 3 - Análisis de Reasoning Plan Execution

- Selecciona una ejecución específica.
- Visualiza el detalle del flujo ejecutado:

  - Inputs recibidos.
  - Flujo de Reasoning Plan (nodos activados).
  - Tools y Skills invocados.
  - Salidas de cada nodo.
  - Evaluaciones de groundedness y safety.

Este detalle permite auditar cada paso de la toma de decisión del agente.

## Paso 4 - Revisión de invocaciones de Tools y Skills

- Dentro del mismo log de ejecución, navega a:

  - Tool Invocation Logs.
  - Skill Execution Logs.

- Verifica los parámetros utilizados y las respuestas obtenidas.
- Confirma que las llamadas a los recursos externos y funciones personalizadas funcionaron correctamente.

## Paso 5 - Visualización de Evaluators

- Revisa los Safety Evaluations aplicados:

  - Groundedness Score.
  - Content Safety detections.
  - Hallucination Risk.

- Confirma que las evaluaciones están siendo aplicadas en cada respuesta.

## Paso 6 - Análisis de consumo de tokens

- En la pestaña Token Usage, revisa:

  - Tokens de prompt.
  - Tokens de completions.
  - Tokens consumidos por Tools y Skills.

- Este análisis permite comenzar el control FinOps sobre los agentes.

## Paso 7 - Configuración de exportación de logs (opcional)

- AI Foundry permite exportar los logs hacia Azure Monitor para centralización de observabilidad:

  - Configuración vía Diagnostic Settings.
  - Integración con Azure Log Analytics.
  - Integración con Microsoft Sentinel para auditoría de seguridad.

> Nota: Esta exportación requiere permisos adicionales en la suscripción de Azure.

## Resultado esperado

- Monitoreo operacional activo y validado.
- Ejecuciones auditables en detalle.
- Visualización de reasoning plan ejecutado.
- Revisión de Tools, Skills, Evaluators y consumo de tokens.
- Fundamento sólido para iniciar prácticas de gobernanza operacional.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/monitor-agents
- https://learn.microsoft.com/en-us/azure/azure-monitor/overview
- https://learn.microsoft.com/en-us/azure/ai-services/responsible-ai/
