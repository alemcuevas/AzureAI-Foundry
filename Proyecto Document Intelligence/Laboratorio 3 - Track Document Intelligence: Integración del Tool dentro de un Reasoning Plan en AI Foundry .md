# Laboratorio 3 - Track Document Intelligence: Integración del Tool dentro de un Reasoning Plan en AI Foundry

## Objetivo

En este laboratorio vamos a:

- Construir un Reasoning Plan que controle cuándo invocar el Tool de Document Intelligence.
- Definir el flujo de razonamiento que valide el input, ejecute el análisis documental y devuelva resultados estructurados.
- Simular el comportamiento enterprise donde el agente procesa documentos a petición.

## Prerrequisitos

- Haber completado los Laboratorios 1 y 2 de este track.
- Tool document-intelligence-tool funcional y probado.
- Workspace, Project y Agent activos en AI Foundry.

## Concepto de Reasoning Plan (aplicado al procesamiento documental)

- Permite definir cuándo y cómo el agente decide utilizar el Tool de Document Intelligence.
- Permite controlar validaciones, flujo de ejecución, manejo de errores y generación de respuestas empresariales auditables.

## Paso 1 - Acceder a Reasoning Plans

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project creados.
- En el menú lateral selecciona Reasoning Plans.

## Paso 2 - Crear el Reasoning Plan

- Haz clic en Create Reasoning Plan.
- Completa los campos:

Reasoning Plan Name: reasoning-plan-doc-intelligence

Description: Flujo de razonamiento para procesamiento de documentos empresariales.

## Paso 3 - Definir la lógica del flujo

- Dentro del editor visual, crea el siguiente flujo lógico:

1. **Nodo de input inicial**: Recibe el prompt completo.

2. **Branch / Condición simple**:

- Condición: Si el usuario provee una URL (por ejemplo: si el texto contiene "https" o "documento en la URL").

- Acción:

  - Invocar el Tool document-intelligence-tool.
  - Proveerle el parámetro urlSource capturado del prompt.

- Si no se detecta una URL:

  - Invocar el Foundation Model GPT-4o normalmente para responder.

> Nota: Para este laboratorio, podemos usar un simple keyword matching para detectar presencia de URL.

## Paso 4 - Configurar el mapeo de parámetros al Tool

- En el nodo de invocación al Tool:

  - Mapea el campo urlSource al valor proporcionado en el prompt.

- Ejemplo de mapeo simple: extraer directamente el string que contenga la URL del texto.

> En escenarios reales, podrías utilizar un Skill previo o pre-procesamiento para parsear la URL.

## Paso 5 - Formato de respuesta final

- Configura el nodo posterior al Tool para estructurar la respuesta final al usuario. Ejemplo de output esperado:

"He analizado el documento. Los datos extraídos son:

- Proveedor: [VendorName]
- Fecha de factura: [InvoiceDate]
- Monto total: [TotalAmount]"

- Este formateo puede definirse dentro del mismo Reasoning Plan o mediante instrucciones al modelo.

## Paso 6 - Asociar el Reasoning Plan al Agent

- Accede al Agent que estamos utilizando.
- Edita su configuración.
- En la sección Reasoning Plan, selecciona: reasoning-plan-doc-intelligence.
- Guarda los cambios.

## Paso 7 - Prueba completa end-to-end

- Ingresa a Test Agent.
- Formula el prompt:

Por favor analiza el siguiente documento: https://[URL SAS del documento PDF de prueba]

- Observa:

  - Cómo el Reasoning Plan detecta la URL.
  - Cómo invoca el Tool de Document Intelligence.
  - Cómo construye la respuesta estructurada.
  - Cómo loguea cada paso de reasoning plan.

## Paso 8 - Revisión de logs de ejecución

- Accede a Monitor → Agent Execution.
- Revisa la ejecución:

  - Inputs recibidos.
  - Invocación al Tool.
  - Outputs generados.
  - Evaluaciones de seguridad (si están activos los evaluators).

## Resultado esperado

- Reasoning Plan operativo.
- Flujo controlado de análisis documental.
- Extracción de información real desde documentos empresariales.
- Respuesta final limpia, clara y auditada.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview
- https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/
