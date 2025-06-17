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
- Selecciona la opción **OpenAPI 3.0 specified tool**.

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
  
### Paso 4 - Configurar el Tool

- Una vez subido el archivo, asigna un nombre descriptivo al Tool, por ejemplo: `obtener_tasa_cambio`.
- Asegúrate de que el endpoint `/latest` esté habilitado para que el agente lo utilice.
- Guarda la configuración.

![image](https://github.com/user-attachments/assets/20528a8a-997f-4031-b01f-5bf6f4f15140)

### Paso 5 - Validar el uso del Tool en el Playground

- Haz clic en **Try in playground**.
- Escribe una pregunta como:  
  `¿Cuál es la tasa de cambio actual del dólar al euro?`
- El agente debería ejecutar la Action y responder con la información obtenida de la API.

> Antes

![image](https://github.com/user-attachments/assets/433dd8dd-5b28-4934-8feb-9136984315bf)

>Después



## Consideraciones adicionales

- El archivo OpenAPI puede alojar múltiples endpoints y ser versionado fácilmente.
- Este enfoque permite documentar claramente el comportamiento de los Tools usados por el agente.
- Si necesitas más control o lógica personalizada, considera usar **Custom Function** vía código.

## Recursos oficiales

- Azure AI Foundry - Tools: https://learn.microsoft.com/en-us/azure/ai-foundry/how-to-tools
- OpenAPI Specification: https://swagger.io/specification/
- API pública usada en el ejemplo: https://exchangerate.host/#/#docs

