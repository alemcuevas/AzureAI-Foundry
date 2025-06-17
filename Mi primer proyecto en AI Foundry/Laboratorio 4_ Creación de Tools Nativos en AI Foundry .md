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

![image](https://github.com/user-attachments/assets/cc96bbdc-37d8-43e6-9051-0fb686603761)

![image](https://github.com/user-attachments/assets/52ffae6e-1912-42a3-9ce2-4241dac97c17)

### Paso 3 - Subir el archivo OpenAPI

- Sube tu archivo OpenAPI con la definición del endpoint REST que deseas invocar.
- Por ejemplo, puedes utilizar la siguiente definición para una API pública de tasas de cambio:

```yaml
openapi: 3.0.0
info:
  title: Exchange Rate API
  version: 1.0.0
paths:
  /latest:
    get:
      summary: Get latest exchange rates
      description: Returns the latest exchange rates based on the USD.
      parameters:
        - in: query
          name: base
          schema:
            type: string
          required: false
          description: Base currency (default is USD)
        - in: query
          name: symbols
          schema:
            type: string
          required: false
          description: Target currency symbols (comma-separated)
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: object
```
- Esta definición puede guardarse como exchange-rate-openapi.yaml.
  
### Paso 4 - Verificar que la Action se haya agregado

- Regresa a la sección **Actions** del agente.
- Verifica que aparezca la Action `obtener_tasa_cambio` en la lista.

### Paso 5 - Validar el uso del Tool en el Playground

- Haz clic en **Try in playground**.
- Escribe una pregunta como:  
  `¿Cuál es la tasa de cambio actual del dólar al euro?`
- El agente debería ejecutar la Action y responder con la información obtenida de la API.

> Antes

![image](https://github.com/user-attachments/assets/433dd8dd-5b28-4934-8feb-9136984315bf)

>Después



## Consideraciones adicionales

- Puedes crear múltiples Tools para que el agente interactúe con diferentes APIs o fuentes externas.
- Los Tools se activan automáticamente cuando el agente detecta que la intención del usuario coincide con la funcionalidad del Tool.
- Es posible editar o eliminar Tools desde la misma sección **Actions**.

## Recursos oficiales

- Azure AI Foundry - Actions (Tools): https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-tools
- API utilizada en el ejemplo: https://exchangerate.host/#/#docs

