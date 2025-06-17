# Laboratorio 4: Creación de Tools Nativos en AI Foundry

## Objetivo

En este laboratorio aprenderemos a crear y configurar un Tool nativo (Action) para un agente en Azure AI Foundry utilizando el portal web. En este ejemplo, crearemos una acción basada en una API REST para consultar tasas de cambio en tiempo real.

## Prerrequisitos

- Haber creado previamente un agente en Azure AI Foundry.
- Tener acceso al portal: https://ai.azure.com/

## Pasos del laboratorio

### Paso 1 - Ingresar al agente

- Desde el menú lateral izquierdo, ir a **Agents**.
- Seleccionar el agente que utilizaremos.
- Acceder a su configuración.

### Paso 2 - Crear una Action (Tool)

- Desplázate a la sección **Actions (0)**.
- Haz clic en el botón **+ Add**.
- En el panel lateral que se abre, selecciona el tipo de acción: **REST API**.

### Paso 3 - Configurar el Tool REST

Completa los siguientes campos:

- **Name:** `obtener_tasa_cambio`
- **Description:** `Consulta la tasa de cambio del dólar respecto a otras monedas.`
- **Method:** `GET`
- **URL:** `https://api.exchangerate.host/latest?base=USD`
- **Authentication:** `None` (para este ejemplo)
- **Response format:** JSON

No es necesario definir parámetros de entrada si no vas a cambiar la moneda base o destino dinámicamente. En caso de hacerlo, puedes usar parámetros como `base` y `symbols`.

Haz clic en **Save** para guardar la Action.

### Paso 4 - Verificar que la Action se haya agregado

- Regresa a la sección **Actions** del agente.
- Verifica que aparezca la Action `obtener_tasa_cambio` en la lista.

### Paso 5 - Validar el uso del Tool en el Playground

- Haz clic en **Try in playground**.
- Escribe una pregunta como:  
  `¿Cuál es la tasa de cambio actual del dólar al euro?`
- El agente debería ejecutar la Action y responder con la información obtenida de la API.

## Consideraciones adicionales

- Puedes crear múltiples Tools para que el agente interactúe con diferentes APIs o fuentes externas.
- Los Tools se activan automáticamente cuando el agente detecta que la intención del usuario coincide con la funcionalidad del Tool.
- Es posible editar o eliminar Tools desde la misma sección **Actions**.

## Recursos oficiales

- Azure AI Foundry - Actions (Tools): https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-tools
- API utilizada en el ejemplo: https://exchangerate.host/#/#docs

