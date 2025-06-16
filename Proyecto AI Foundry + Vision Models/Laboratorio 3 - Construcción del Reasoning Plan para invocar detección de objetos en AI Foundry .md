# Laboratorio 3 - Construcción del Reasoning Plan para invocar detección de objetos en AI Foundry

## Objetivo

En este laboratorio vamos a:

- Construir un Reasoning Plan que controle cuándo invocar el modelo de visión.
- Integrar el Tool de detección de objetos dentro del flujo de reasoning.
- Permitir que el agente procese imágenes cargadas por el usuario.

## Prerrequisitos

- Haber completado los Laboratorios 1 y 2 de este track.
- Tool object-detection-tool funcional y probado.
- Agent creado dentro del Project en AI Foundry.

## Concepto aplicado

- El Reasoning Plan decidirá en qué casos se debe invocar el modelo de visión.
- AI Foundry permitirá al usuario subir imágenes desde la interfaz de Test Agent.
- Todo el flujo sigue siendo no-code.

## Paso 1 - Acceder a Reasoning Plans

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project.
- En el menú lateral selecciona Reasoning Plans.

## Paso 2 - Crear el Reasoning Plan

- Haz clic en Create Reasoning Plan.
- Completa los campos:

Reasoning Plan Name: reasoning-plan-object-detection

Description: Flujo de razonamiento para detección de objetos desde imágenes.

## Paso 3 - Diseñar el flujo lógico

Dentro del editor visual:

### Nodo 1 - Verificar si el input incluye imagen

- AI Foundry permite detectar automáticamente si el usuario ha cargado una imagen.

- Configura:

Si el input incluye Image, entonces invocar el Tool.

Si no hay imagen, utilizar el Foundation Model para responder normalmente.

### Nodo 2 - Invocar el Tool de detección

- Tool: object-detection-tool

- Mapea el input image directamente desde el prompt multimodal:

Input Mapping:

- image (user uploaded file) → Tool input (binary image)

### Nodo 3 - Postprocesamiento del resultado

- Toma el output JSON devuelto por el Tool.

- Extrae los campos:

tagName, probability, boundingBox

- Puedes mapear solo los tags para simplificar la respuesta inicial.

### Nodo 4 - Generar respuesta final

- Configura el agente para responder algo como:

"He analizado la imagen. Los siguientes objetos fueron detectados:

- Objeto: [tagName] (Confianza: [probability]%)
- Objeto: [tagName] (Confianza: [probability]%)"

- AI Foundry puede formatear esta respuesta directamente desde los outputs del Tool.

## Paso 4 - Asociar el Reasoning Plan al Agent

- Accede al Agent creado.
- Edita la configuración.
- En la sección Reasoning Plan, selecciona: reasoning-plan-object-detection.
- Guarda los cambios.

## Paso 5 - Prueba completa

- Ingresa a Test Agent.
- Carga una imagen de prueba que contenga alguno de los objetos que el modelo ha sido entrenado para detectar.
- Formula el prompt:

Por favor analiza esta imagen.

- Observa:

  - El Reasoning Plan detecta la imagen.
  - Invoca el Tool de visión.
  - Extrae los resultados.
  - Genera una respuesta estructurada.

## Paso 6 - Validación de logs

- Accede a Monitor → Agent Execution.
- Revisa:

  - Input Types (Text + Image).
  - Invocación al Tool.
  - Output generado.
  - Logs completos del Reasoning Plan.

## Resultado esperado

- Reasoning Plan multimodal operativo.
- Agent capaz de consumir imágenes y razonar sobre ellas.
- Flujo de orquestación agentica funcionando de forma declarativa.
- Logs auditables de ejecución.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/monitor-agents
