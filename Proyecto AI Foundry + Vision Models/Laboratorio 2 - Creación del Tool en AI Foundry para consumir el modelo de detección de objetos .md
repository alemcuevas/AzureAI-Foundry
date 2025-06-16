# Laboratorio 2 - Creación del Tool en AI Foundry para consumir el modelo de detección de objetos

## Objetivo

En este laboratorio vamos a:

- Crear un Tool declarativo en AI Foundry.
- Integrar el modelo de Computer Vision (Object Detection) previamente entrenado.
- Dejarlo listo para ser invocado desde los reasoning plans del agente.

Este será el componente que permite al agente razonador invocar visión dentro de sus flujos.

## Prerrequisitos

- Haber completado el Laboratorio 1 de este track.
- Tener el Endpoint URL y la Prediction Key del modelo de visión.
- Workspace y Project de AI Foundry ya creados (puedes crear uno nuevo o usar uno existente).

## Concepto de integración vía Tool

- Los Tools permiten conectar APIs REST externas sin escribir código.
- AI Foundry se encarga de orquestar las llamadas dentro de los reasoning plans.
- Toda la configuración es declarativa vía UI.

## Paso 1 - Acceder a AI Foundry

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace de trabajo.
- Selecciona el Project donde crearemos el Tool.

## Paso 2 - Crear el nuevo Tool

- En el menú lateral selecciona Tools.
- Haz clic en Create Tool.
- Completa los campos:

Tool Name: object-detection-tool

Description: Tool para detección de objetos mediante modelo de visión.

## Paso 3 - Definir el endpoint del modelo

- Selecciona Create manually.
- Configura la operación principal:

Operation Name: detectObjects

Description: Ejecuta detección de objetos sobre imagen enviada.

- Método HTTP: POST
- URL: utiliza el Endpoint URL obtenido en el Lab 1. Ejemplo:

https://{your-resource-name}.cognitiveservices.azure.com/customvision/v3.0/Prediction/{project-id}/detect/iterations/{iteration-name}/image

> Nota: la estructura exacta de la URL depende de cómo hayas publicado el modelo.

## Paso 4 - Configurar Autenticación

- Authentication: API Key
- Header Name: Prediction-Key
- Value: inserta aquí la Prediction Key obtenida en el Lab 1.

## Paso 5 - Definir el esquema de entrada

- Input Type: Binary (Image file upload)

Esto permite enviar imágenes directamente al modelo.

- AI Foundry automáticamente permite subir imágenes en la UI cuando se configura este tipo de input.

## Paso 6 - Definir el esquema de salida

- Output Body Type: JSON

- Output schema básico simplificado:

{
  "predictions": [
    {
      "tagName": "string",
      "probability": "number",
      "boundingBox": {
        "left": "number",
        "top": "number",
        "width": "number",
        "height": "number"
      }
    }
  ]
}

> Este esquema permite mapear los objetos detectados junto con sus probabilidades y bounding boxes.

## Paso 7 - Guardar y probar el Tool

- Guarda el Tool.
- Selecciona Test Tool.
- Sube una imagen de prueba (puede ser cualquiera de las usadas durante el entrenamiento).
- Ejecuta la inferencia.

### Resultado esperado:

{
  "predictions": [
    {
      "tagName": "Bottle",
      "probability": 0.95,
      "boundingBox": {
        "left": 0.23,
        "top": 0.10,
        "width": 0.40,
        "height": 0.55
      }
    }
  ]
}

## Paso 8 - Asociar el Tool al Agent (preparación para próximos labs)

- Accede al Agent en AI Foundry.
- Edita la configuración.
- En la sección Tools, agrega: object-detection-tool.
- Guarda los cambios.

## Resultado esperado

- Tool configurado sin código.
- AI Foundry conectado al modelo de visión.
- Pruebas de inferencia exitosas desde la UI de Foundry.
- Agent listo para consumir visión dentro del reasoning plan.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/test-tools
- https://learn.microsoft.com/en-us/azure/ai-services/custom-vision-service/prediction
