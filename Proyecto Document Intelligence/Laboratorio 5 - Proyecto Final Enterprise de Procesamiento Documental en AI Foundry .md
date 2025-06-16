# Laboratorio 5 - Proyecto Final Enterprise de Procesamiento Documental en AI Foundry

## Objetivo

En este laboratorio final vamos a:

- Integrar todos los componentes configurados en los labs anteriores.
- Construir un agente documental enterprise completo.
- Ejecutar pruebas realistas de extremo a extremo.
- Validar el flujo completo de procesamiento, extracción, razonamiento y seguridad.

## Prerrequisitos

- Haber completado los Laboratorios 1 al 4 de este track.
- Todos los siguientes componentes funcionales:

  - Workspace y Project de AI Foundry.
  - Tool: document-intelligence-tool.
  - Reasoning Plan: reasoning-plan-doc-intelligence.
  - Content Safety Evaluator: content-safety-docs.
  - Knowledge Memory (opcional si aplicaste grounding).
  - Agent creado y configurado.

## Escenario empresarial

El agente será un **Revisor Automático de Facturas Empresariales** que:

- Recibe un documento (SAS URL).
- Ejecuta la extracción de campos usando Document Intelligence.
- Evalúa los datos extraídos.
- Filtra contenido sensible.
- Devuelve respuestas estructuradas y auditables.

## Paso 1 - Validación de configuración previa

Antes de comenzar:

- Valida que el Tool, Reasoning Plan y Evaluators están correctamente asociados al Agent.
- Verifica que dispones de documentos de prueba cargados en Azure Blob Storage.

## Paso 2 - Ajuste del System Prompt Final

Configura el siguiente system prompt en el Agent:

Eres un agente de procesamiento documental empresarial. Tus funciones son:

- Analizar documentos de facturación proporcionados por los usuarios.
- Extraer campos clave: Proveedor, Fecha de Factura, Monto Total.
- Validar que el contenido extraído no contenga elementos sensibles o inapropiados.
- Si detectas problemas de seguridad, informa al usuario que el documento requiere revisión manual.
- Si no dispones de un documento válido, indicas: "No se ha proporcionado un documento válido para analizar."

Siempre entrega las respuestas en un formato profesional y estructurado.

## Paso 3 - Ejecución de pruebas funcionales

### Escenario 1: Documento limpio

- URL de documento de prueba SAS con una factura estándar.

Prompt:

Por favor analiza el siguiente documento: https://[URL del documento válido]

Validación:

- El agente debe:

  - Detectar el documento.
  - Invocar el Tool de Document Intelligence.
  - Extraer los campos.
  - Formatear la respuesta de forma estructurada.

### Escenario 2: Documento con contenido sensible

- URL de documento de prueba SAS con contenido problemático.

Prompt:

Por favor analiza el siguiente documento: https://[URL del documento sensible]

Validación:

- El agente debe:

  - Invocar el Tool.
  - Extraer los campos.
  - Activar el Content Safety Evaluator.
  - Advertir al usuario que el documento requiere revisión manual.

### Escenario 3: Prompt sin documento

Prompt:

Por favor analiza el documento.

Validación:

- El agente debe indicar que no se ha proporcionado un documento válido.

## Paso 4 - Revisión de monitoreo y auditoría

- Accede a Monitor → Agent Execution.
- Revisa:

  - Reasoning Plan Execution.
  - Invocación del Tool.
  - Evaluator Results.
  - Safety Scores.
  - Token Usage.
  - Logs completos de ejecución.

## Resultado esperado

- Pipeline documental enterprise completo.
- Extracción documental funcional.
- Reasoning planificado activo.
- Evaluación de seguridad aplicada.
- Logs auditables de extremo a extremo.
- Agente listo para validación en escenarios reales de adopción.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/overview
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/safety-evaluators
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/monitor-agents
