# Laboratorio 4 - Integración de Safety Evaluators en AI Foundry para Document Intelligence

## Objetivo

En este laboratorio vamos a:

- Agregar evaluadores de seguridad (Safety Evaluators) al agente documental.
- Validar contenido sensible extraído desde documentos.
- Controlar groundedness y factual consistency.
- Completar el pipeline enterprise de seguridad para procesamiento documental.

## Prerrequisitos

- Haber completado el Laboratorio 3 de este track.
- Reasoning Plan operativo.
- Agent funcional que invoca el Tool de Document Intelligence.

## Concepto de Safety Evaluators aplicado a procesamiento documental

- Los evaluadores permiten validar que la información extraída:

  - Sea consistente con el grounding de negocio.
  - No contenga contenido sensible, ofensivo o inapropiado.
  - Sea auditada de forma automática antes de entregarla al usuario.

- Aplican tanto sobre el output de los Tools como sobre la respuesta generada final.

## Paso 1 - Acceder a Evaluators en AI Foundry

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project.
- En el menú lateral selecciona Evaluators.

## Paso 2 - Crear Groundedness Evaluator (opcional en este track)

En el caso de Document Intelligence, si deseas validar grounding contra Knowledge Memories:

- Haz clic en Create Evaluator.
- Selecciona Groundedness Evaluator.
- Asocia la Knowledge Memory relevante (por ejemplo, políticas de procesamiento de facturas).
- Guarda la configuración.

> Este paso es opcional si no tenemos un Knowledge Memory configurado para documentos.

## Paso 3 - Crear Content Safety Evaluator

- Haz clic en Create Evaluator.
- Selecciona Content Safety Evaluator.
- Completa los campos:

Evaluator Name: content-safety-docs

Description: Evaluador de contenido sensible en respuestas documentales.

- Habilita detección para:

  - Hate
  - Violence
  - Sexual content
  - Self-harm
  - Offensive language

- Ajusta los umbrales de severidad (puedes dejar default para el laboratorio).
- Guarda la configuración.

## Paso 4 - Asociar los Evaluators al Agent

- Accede al Agent utilizado en este track.
- Edita su configuración.
- En la sección Evaluators, agrega:

  - content-safety-docs
  - (opcional) groundedness evaluator.

- Guarda los cambios.

## Paso 5 - Pruebas de detección de contenido sensible

### Escenario de prueba 1

- Prepara un documento de prueba con contenido sensible simulado:

Ejemplo de contenido:

Proveedor: Empresa XYZ  
Observación: Esta factura contiene actividades ilícitas y violentas.  
Monto total: 8500 USD

- Carga el documento en Azure Blob Storage (con SAS URL).

- Ingresa a Test Agent.

- Formula el prompt:

Por favor analiza el siguiente documento: https://[URL SAS del documento sensible]

### Validación:

- El Content Safety Evaluator debe detectar los términos sensibles.
- La respuesta del Agent debe ser bloqueada o advertida según la política configurada.
- Revisa el log de reasoning execution para observar el resultado del evaluador.

## Paso 6 - Revisión de logs

- Accede a Monitor → Agent Execution.
- Revisa:

  - Evaluator Results.
  - Safety scores.
  - Acciones tomadas por AI Foundry ante el contenido detectado.

## Resultado esperado

- Evaluadores de seguridad activos sobre el flujo documental.
- Detección automática de contenido inapropiado en documentos empresariales.
- Logs auditables para cada ejecución.
- Validación de compliance aplicado al agente documental.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/safety-evaluators
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/monitor-agents
- https://learn.microsoft.com/en-us/azure/ai-services/responsible-ai/
