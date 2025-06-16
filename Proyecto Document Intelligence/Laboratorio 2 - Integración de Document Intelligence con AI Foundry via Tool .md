# Laboratorio 2 - Integración de Document Intelligence con AI Foundry via Tool

## Objetivo

En este laboratorio vamos a:

- Crear un Tool dentro de AI Foundry.
- Integrar el modelo de Document Intelligence a través del endpoint previamente configurado.
- Dejar al agente listo para consumir documentos y extraer información estructurada.

## Prerrequisitos

- Haber completado el Laboratorio 1 de este track.
- Tener el endpoint URL y la Key de Document Intelligence disponibles.
- Workspace y Project de AI Foundry ya creados (puedes reutilizar los que ya tenías).

## Concepto de integración vía Tool

- AI Foundry permite consumir APIs externas a través de Tools declarativos.
- No requiere escribir código para invocar APIs REST.
- Nos permite conectar fácilmente con Document Intelligence sin salir de Foundry.

## Paso 1 - Acceder a AI Foundry

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace de trabajo.
- Selecciona el Project donde realizaremos la integración.

## Paso 2 - Crear un nuevo Tool

- En el menú lateral selecciona Tools.
- Haz clic en Create Tool.
- Completa los campos iniciales:

Tool Name: document-intelligence-tool

Description: Tool para extracción automática de campos desde facturas usando Document Intelligence.

## Paso 3 - Definir el endpoint de Document Intelligence

- Selecciona Create manually.
- Configura la operación:

Operation Name: extractInvoiceData

Description: Extrae datos de facturas usando Document Intelligence.

- Método HTTP: POST
- URL: utiliza el endpoint generado en el Lab 1. Ejemplo:

https://{your-resource-name}.cognitiveservices.azure.com/formrecognizer/documentModels/prebuilt-invoice:analyze?api-version=2023-07-31

> Nota: Asegúrate de utilizar la versión correcta del API según la documentación.

## Paso 4 - Configuración de Autenticación

- Authentication: API Key
- Header name: Ocp-Apim-Subscription-Key
- Value: inserta aquí la Key obtenida en el Lab 1.

## Paso 5 - Definir el esquema de entrada

- Input Body Type: JSON
- Input schema:

{
  "urlSource": "string"
}

> Este campo es la URL del documento a analizar. Usaremos documentos previamente cargados en Azure Blob Storage (SAS URL).

## Paso 6 - Definir el esquema de salida

- Output Body Type: JSON
- Output schema básico (simplificado para el laboratorio inicial):

{
  "documents": [
    {
      "fields": {
        "VendorName": {
          "content": "string"
        },
        "InvoiceDate": {
          "content": "string"
        },
        "TotalAmount": {
          "content": "string"
        }
      }
    }
  ]
}

> Este esquema puede extenderse para soportar más campos según lo necesites.

## Paso 7 - Guardar y probar el Tool

- Guarda el Tool.
- Selecciona Test Tool.
- En el campo urlSource ingresa una URL SAS válida de un documento en Azure Blob Storage.
- Ejecuta la prueba de invocación.

Resultado esperado:

{
  "documents": [
    {
      "fields": {
        "VendorName": { "content": "Contoso Ltd." },
        "InvoiceDate": { "content": "2025-06-20" },
        "TotalAmount": { "content": "4825.50" }
      }
    }
  ]
}

## Paso 8 - Asociar el Tool al Agent

- Accede al Agent de AI Foundry.
- Edita su configuración.
- En la sección Tools, agrega: document-intelligence-tool.
- Guarda los cambios.

## Paso 9 - Prueba completa con el Agent

- Ingresa a Test Agent.
- Formula la consulta:

Por favor analiza la factura ubicada en la siguiente URL: [Pega aquí la URL SAS del documento]

- Observa cómo el Agent:

  - Detecta que debe invocar el Tool.
  - Extrae los campos desde el documento.
  - Integra el resultado en su respuesta final.

## Resultado esperado

- Tool de Document Intelligence funcional.
- Agente integrado capaz de analizar documentos empresariales.
- Extracción de campos estructurados validada.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans
