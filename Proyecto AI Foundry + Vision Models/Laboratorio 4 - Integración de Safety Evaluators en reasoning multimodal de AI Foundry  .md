# Laboratorio 4 - Integración de Safety Evaluators en reasoning multimodal de AI Foundry

## Objetivo

En este laboratorio vamos a:

- Integrar evaluadores de seguridad (Safety Evaluators) sobre los reasoning plans multimodales.
- Validar la seguridad de las respuestas generadas después de la detección de objetos.
- Completar la capa enterprise de gobernanza sobre procesamiento de imágenes.

## Prerrequisitos

- Haber completado el Laboratorio 3 de este track.
- Agent operativo con Reasoning Plan multimodal.
- Workspace y Project de AI Foundry.

## Concepto aplicado

- Aunque el modelo de visión devuelve objetos, el razonamiento final del agent siempre es textual.
- Aplicaremos Content Safety Evaluator sobre el output textual final.
- Este esquema permite:

  - Auditar resultados.
  - Bloquear respuestas sensibles.
  - Proteger contra alucinaciones o respuestas inesperadas.

## Paso 1 - Acceder a Evaluators

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project.
- En el menú lateral selecciona Evaluators.

## Paso 2 - Crear el Content Safety Evaluator

- Haz clic en Create Evaluator.
- Selecciona Content Safety Evaluator.
- Completa los campos:

Evaluator Name: content-safety-object-detection

Description: Evaluador de contenido sensible aplicado al reasoning multimodal.

- Habilita detección para:

  - Hate
  - Violence
  - Sexual content
  - Self-harm
  - Offensive language

- Ajusta los umbrales de severidad (puedes dejar default para laboratorio).
- Guarda la configuración.

## Paso 3 - Asociar el Evaluator al Agent

- Accede al Agent.
- Edita la configuración.
- En la sección Evaluators, agrega: content-safety-object-detection.
- Guarda los cambios.

## Paso 4 - Prueba de escenarios de seguridad

### Escenario 1 - Imagen limpia

- Carga una imagen normal previamente usada.
- Prompt:

Por favor analiza esta imagen.

- Validación:

  - El agente procesa la imagen.
  - Detecta los objetos.
  - Responde de forma limpia.
  - El evaluator reporta riesgo bajo o cero.

### Escenario 2 - Imagen con resultados problemáticos (simulación)

- Carga una imagen de prueba donde el modelo de visión devuelva etiquetas sensibles o poco apropiadas (puede ser forzado con etiquetas ficticias o simuladas).
- Prompt:

Por favor analiza esta imagen.

- Validación:

  - El Content Safety Evaluator detecta el término sensible en el output textual.
  - El agent bloquea la respuesta o advierte según configuración.

## Paso 5 - Revisión de logs de ejecución

- Accede a Monitor → Agent Execution.
- Revisa:

  - Evaluator Results.
  - Detalles de detección por categoría.
  - Safety scores.
  - Acción tomada (allow / block / review).

## Resultado esperado

- Evaluador de seguridad activo sobre el reasoning multimodal.
- Detección automática de respuestas inapropiadas.
- Pipeline auditado de extremo a extremo.
- Control de seguridad enterprise aplicado al flujo de visión.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/safety-evaluators
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/monitor-agents
- https://learn.microsoft.com/en-us/azure/ai-services/responsible-ai/
