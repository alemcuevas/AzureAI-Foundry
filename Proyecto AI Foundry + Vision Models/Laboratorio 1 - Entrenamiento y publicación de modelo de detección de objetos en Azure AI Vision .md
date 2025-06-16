# Laboratorio 1 - Entrenamiento y publicación de modelo de detección de objetos en Azure AI Vision

## Objetivo

En este primer laboratorio vamos a:

- Preparar un modelo de visión especializado en detección de objetos.
- Publicarlo como endpoint de inferencia en Azure AI Studio.
- Dejarlo listo para ser integrado como Tool dentro de AI Foundry.

Este modelo luego será orquestado por el agente agentic de AI Foundry.

## Prerrequisitos

- Suscripción activa de Azure.
- Permisos de Contributor sobre la suscripción.
- Azure AI Studio habilitado.
- Dataset de imágenes anotadas (puede ser un dataset de ejemplo provisto por Azure AI Vision).

## Concepto de flujo

- Los modelos de visión no se entrenan dentro de AI Foundry.
- Se entrenan en Azure AI Vision Studio o Azure ML.
- Luego los endpoints se consumen desde Foundry vía Tool declarativo.

## Paso 1 - Acceder a Azure AI Studio Vision

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Selecciona la sección Vision Projects (si es la primera vez, habilitar acceso si lo solicita).
- Valida acceso al servicio.

## Paso 2 - Crear nuevo proyecto de visión

- Haz clic en New Project.
- Completa los campos:

Project Type: Object Detection

Project Name: object-detection-lab

Description: Modelo de detección de objetos para integración con AI Foundry.

Domain: General (multiclass object detection)

- Selecciona el recurso de almacenamiento vinculado (Azure Storage).

## Paso 3 - Preparar el dataset de entrenamiento

- Puedes usar datasets de prueba como:

Dataset: Retail Shelf Products (para detección de productos en góndola)

- Carga las imágenes con anotaciones (bounding boxes).
- Si no tienes anotaciones, puedes utilizar el editor visual de AI Vision Studio para etiquetar los objetos manualmente.

> Nota: para el laboratorio puedes trabajar con ~20 a 50 imágenes de ejemplo.

## Paso 4 - Entrenar el modelo

- Una vez cargado el dataset, selecciona Train.
- Elige:

Training Type: Quick Training (suficiente para laboratorio)

- Inicia el entrenamiento.

> La duración depende del tamaño del dataset (normalmente 10-30 minutos en laboratorios).

## Paso 5 - Publicar el modelo

- Una vez finalizado el entrenamiento:

Selecciona Publish Model.

Model Name: object-detection-lab-v1

Resource: selecciona el recurso de Azure AI Studio Vision.

- El modelo quedará publicado y listo para inferencia.

## Paso 6 - Obtener el endpoint de inferencia

- Accede a la sección Model Details.
- Obtén:

Endpoint URL: URL de inferencia.

Prediction Key: clave API de inferencia.

- Guarda estos valores, los utilizaremos para configurar el Tool dentro de AI Foundry.

## Paso 7 - Probar el modelo manualmente (opcional)

- Puedes realizar inferencias de prueba cargando imágenes de validación.
- Observa los outputs con bounding boxes y etiquetas de objetos detectados.

## Resultado esperado

- Modelo de detección de objetos entrenado.
- Modelo publicado como endpoint REST.
- Endpoint URL y Key de inferencia disponibles.
- Listo para integración en AI Foundry.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/
- https://learn.microsoft.com/en-us/azure/ai-studio/vision/
- https://learn.microsoft.com/en-us/azure/ai-studio/vision/create-projects
- https://learn.microsoft.com/en-us/azure/ai-studio/vision/train-models
- https://learn.microsoft.com/en-us/azure/ai-studio/vision/publish-models
