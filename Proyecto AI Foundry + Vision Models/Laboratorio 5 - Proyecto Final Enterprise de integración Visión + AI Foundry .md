# Laboratorio 5 - Proyecto Final Enterprise de integración Visión + AI Foundry

## Objetivo

En este laboratorio final vamos a:

- Integrar todos los componentes configurados en los labs anteriores.
- Construir un agente multimodal enterprise completo.
- Ejecutar pruebas realistas de extremo a extremo.
- Validar el flujo completo de reasoning + visión + seguridad.

## Prerrequisitos

- Haber completado los Laboratorios 1 al 4 de este track.
- Contar con:

  - Workspace y Project en AI Foundry.
  - Tool: object-detection-tool.
  - Reasoning Plan: reasoning-plan-object-detection.
  - Evaluator: content-safety-object-detection.
  - Agent configurado.

## Escenario empresarial

El agente será un **Inspector Visual Automatizado**, capaz de:

- Procesar imágenes cargadas por el usuario.
- Detectar objetos específicos dentro de las imágenes.
- Filtrar posibles resultados sensibles o inapropiados.
- Generar respuestas estructuradas y seguras.

## Paso 1 - Validación de configuración previa

Antes de comenzar:

- Valida que todos los componentes estén activos y correctamente vinculados al Agent.
- Ten preparadas varias imágenes de prueba para los diferentes escenarios.

## Paso 2 - Ajuste del System Prompt final

Configura el siguiente System Prompt en el Agent:

Eres un inspector visual automatizado. Tu responsabilidad es:

- Analizar imágenes cargadas por el usuario.
- Detectar los objetos presentes en la imagen.
- Reportar los objetos detectados junto con su nivel de confianza.
- Filtrar resultados inapropiados o sensibles según las políticas de seguridad.
- Si no detectas objetos, indicas: "No se han identificado objetos relevantes en la imagen."

Siempre entregas la respuesta en formato estructurado, profesional y fácil de interpretar.

## Paso 3 - Ejecución de pruebas funcionales

### Escenario 1 - Imagen limpia con detección de objetos

- Sube una imagen que contenga objetos conocidos por el modelo.
- Prompt:

Por favor analiza esta imagen.

- Validación:

  - El agente invoca el Tool de visión.
  - El modelo detecta objetos.
  - El agente genera la respuesta con los objetos identificados.

### Escenario 2 - Imagen sin objetos detectables

- Sube una imagen fuera del dominio de entrenamiento.
- Prompt:

Por favor analiza esta imagen.

- Validación:

  - El agent indica que no se han identificado objetos relevantes.

### Escenario 3 - Imagen con resultados sensibles

- Sube una imagen (real o simulada) que contenga etiquetas sensibles.
- Prompt:

Por favor analiza esta imagen.

- Validación:

  - El Content Safety Evaluator detecta contenido sensible en la respuesta.
  - El agent bloquea o advierte la respuesta.

## Paso 4 - Revisión de logs operativos

- Accede a Monitor → Agent Execution.
- Valida:

  - Reasoning Plan execution completo.
  - Tool invocation del modelo de visión.
  - Evaluator results aplicados.
  - Safety scores reportados.
  - Logs auditables de reasoning completo.

## Resultado esperado

- Agente multimodal enterprise operativo.
- Pipeline completo de reasoning controlado.
- Integración exitosa de visión + AI Foundry.
- Evaluación de seguridad integrada.
- Flujo productivo reproducible para escenarios enterprise reales.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/overview
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/safety-evaluators
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/monitor-agents
- https://learn.microsoft.com/en-us/azure/ai-studio/vision/
