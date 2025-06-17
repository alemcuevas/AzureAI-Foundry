# Laboratorio 3: Configuración de Memories en AI Foundry

## Objetivo

En este laboratorio aprenderemos a configurar la memoria vectorial (Knowledge) de un agente en Azure AI Foundry, utilizando exclusivamente el portal web, sin necesidad de utilizar código o Visual Studio Code.

> Nota: En la versión actual de Azure AI Foundry (junio 2025), la configuración de Memories se gestiona desde la sección Knowledge dentro del agente.

## Prerrequisitos

- Acceso al portal de Azure AI Foundry: https://ai.azure.com/
- Haber creado previamente:
  - Un AI Hub
  - Un Project dentro del Hub
  - Un Agent dentro del Project

## Pasos del laboratorio

### Paso 1 - Ingresar al Agent

- Desde el menú lateral izquierdo, ingresar a la sección Agents.
- Seleccionar el agente previamente creado.
- Acceder al editor del agente.

### Paso 2 - Acceder a la sección Knowledge

- Dentro de la pantalla de configuración del agente, localizar la sección Knowledge.
- Hacer clic en + Add para agregar un nuevo vector store.

### Paso 3 - Crear o asociar el Vector Store

- Seleccionar uno de los Vector Stores previamente configurados en el proyecto (por ejemplo: Azure AI Search, Blob Storage + Embeddings, Cosmos DB vector, etc.)
- Si no existe aún, crear un nuevo Vector Store desde el menú de la izquierda:
  - Ir a Vector Stores.
  - Crear el nuevo recurso, indicando el tipo de almacenamiento y el embedding model a utilizar.
  - Confirmar la creación.
- Nota: Para efectos del laboratorio, se recomienda utilizar Azure AI Search como vector store primario.

### Paso 4 - Cargar datos al Vector Store

- Desde la sección de Vector Stores, seleccionar el vector store correspondiente.
- Subir archivos de datos (PDF, TXT, DOCX, JSON).
- El sistema realizará el chunking y la indexación automática utilizando el embedding model configurado.
- Validar que los documentos hayan sido cargados correctamente.

### Paso 5 - Asociar el Vector Store al agente

- Regresar al agente en la sección Knowledge.
- Seleccionar el Vector Store creado previamente.
- Confirmar la asociación.

### Paso 6 - Validación en el Playground

- Hacer clic en Try in playground.
- Realizar preguntas al agente relacionadas a los documentos cargados.
- Validar que el agente utiliza el conocimiento indexado para enriquecer sus respuestas.

## Consideraciones adicionales

- La short-term memory (memoria conversacional de corto plazo) actualmente es administrada por el runtime del agente y no es configurable desde el portal.
- Toda la configuración realizada en este laboratorio corresponde a la long-term memory basada en embeddings y retrieval.

## Recursos oficiales

- Azure AI Foundry - Knowledge Sources: https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-knowledge-sources
- Azure AI Foundry - Vector Stores: https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-vector-stores
