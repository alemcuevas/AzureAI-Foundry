# Laboratorio 4: Creación de Tools Nativos en AI Foundry

## Objetivo

En este laboratorio vamos a:

- Diseñar un Tool nativo dentro de AI Foundry.
- Integrar el Tool con un API externo público (sin autenticación para simplificar el laboratorio).
- Validar cómo el agente invoca el Tool automáticamente durante el reasoning plan.

---

## Prerrequisitos

- Haber completado el **Laboratorio 3**.
- Agent ya creado con Memories asociadas.
- Acceso al Project dentro del Workspace de AI Foundry.

---

## Concepto de Tool en AI Foundry

- Un **Tool** es una interfaz que permite a un Agent invocar servicios externos.
- Los Tools pueden consumir APIs REST, bases de datos, o sistemas empresariales.
- Los Agents deciden cuándo invocar un Tool durante el reasoning.

---

## API utilizada para el laboratorio

Para este laboratorio usaremos una API pública simple de tipo REST:

**API de tipo Exchange Rates (sin autenticación):**

- Endpoint:  
  `https://api.exchangerate-api.com/v4/latest/USD`

- Descripción:  
  Devuelve tasas de cambio actuales de USD contra múltiples monedas.

---

## Paso 1 - Acceder a Tools dentro del proyecto

1. Inicia sesión en Azure AI Studio:  
   https://ai.azure.com

2. Accede al Workspace y Project creados.

3. En el menú lateral selecciona **Tools**.

---

## Paso 2 - Creación de un nuevo Tool

1. Haz clic en **Create Tool**.

2. Completa los campos iniciales:

- **Tool Name:**  
  `exchange-rate-tool`

- **Description:**  
  `Consulta tasas de cambio de USD en tiempo real.`

---

## Paso 3 - Definir la especificación del Tool

1. Selecciona el método de definición:  
   `Create manually (no OpenAPI import)`

2. Configura la operación principal:

- **Operation Name:**  
  `getExchangeRate`

- **Description:**  
  `Consulta tasas de cambio actuales.`

3. Configuración de la llamada:

- **HTTP Method:**  
  `GET`

- **URL:**  
  `https://api.exchangerate-api.com/v4/latest/USD`

- **Authentication:**  
  `None` (para simplificación en este laboratorio)

---

## Paso 4 - Configurar Inputs y Outputs

Dado que este endpoint no requiere parámetros de entrada, dejamos el esquema de input vacío.

Definimos el esquema de salida básico para facilitar el parsing:

- **Response Type:**  
  `application/json`

- **Output Schema (simplificado):**

```json
{
  "base": "string",
  "date": "string",
  "rates": {
    "type": "object"
  }
}
```

> **Nota:** AI Foundry permite definir esquemas más precisos, pero para el lab inicial mantendremos solo la estructura principal.

## Paso 5 - Guardar y probar el Tool

- Guarda la definición del Tool.
- Selecciona **Test Tool**.
- Ejecuta la prueba de invocación.
- Valida que recibes una respuesta como:

```json
{
  "base": "USD",
  "date": "2025-06-16",
  "rates": {
    "EUR": 0.92,
    "MXN": 18.02,
    "JPY": 155.30
  }
}
```

## Paso 6 - Asociar el Tool al Agent

- Accede al Agent `primer-agent-gpt4o`.
- Edita la configuración del Agent.
- En la sección **Tools**, agrega el nuevo Tool creado: `exchange-rate-tool`.
- Guarda los cambios.

## Paso 7 - Prueba completa de razonamiento + Tool

- Ingresa a **Test Agent**.
- Realiza una consulta que implique tasas de cambio. Ejemplos:
  - ¿Cuál es el tipo de cambio actual de USD a MXN?
  - Dame el tipo de cambio de USD a EUR.
- Observa en los logs de reasoning cómo el Agent:
  - Reconoce que necesita llamar al Tool.
  - Invoca automáticamente el API.
  - Utiliza la respuesta para generar su output final.

## Resultado esperado

- Tool creado y funcional dentro de AI Foundry.
- Agente invocando el Tool en tiempo real durante reasoning.
- Respuestas basadas en datos actualizados desde el API externo.
- Primer flujo de integración con fuentes externas validado.

## Links de referencia

- [Definición de Tools en AI Foundry](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview)
- [Test de Tools en AI Foundry](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/test-tools)
- [Uso de Tools en Reasoning Plan](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans)
