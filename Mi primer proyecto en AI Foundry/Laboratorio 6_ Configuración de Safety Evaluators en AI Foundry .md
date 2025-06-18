# Laboratorio 6: Configuración de Safety Evaluators en AI Foundry

## Objetivo

En este laboratorio configuraremos los mecanismos de Responsible AI nativos de AI Foundry:

- Activaremos evaluadores de seguridad (Safety Evaluators).
- Validaremos la detección de inconsistencias y contenido inapropiado.
- Veremos cómo AI Foundry aplica controles automáticos sobre el output de los agentes.

Los Safety Evaluators son fundamentales para entornos empresariales regulados.

## Prerrequisitos

- Haber completado el Laboratorio 5.
- Agent funcional con Memories, Tools y Skills configurados.
- Acceso al Project dentro del Workspace de AI Foundry.

## Concepto de Safety Evaluators

- Los Safety Evaluators permiten inspeccionar y validar los resultados generados por el agente.
- Operan en tiempo real durante el reasoning.
- Evalúan groundedness, toxicidad, factual consistency, hallucination risk y contenido sensible.

## Paso 1 - Crear el Storage Account (si no lo tienes)

1. Ve a [https://portal.azure.com](https://portal.azure.com)
2. Busca **Storage accounts** > haz clic en **+ Create**
3. Llena los campos:
   - Nombre: `evalfoundrystorage` (agrega tu identificador)
   - Primary Service: `ADLS Gen2`
   - Redundancia: `LRS`
   - Ubicación: la misma región donde tienes Foundry
4. Una vez creado, entra al recurso y crea un **contenedor Blob** llamado `evals`
5. Sube ahí el archivo `eval_set.jsonl`

![image](https://github.com/user-attachments/assets/6749fa6d-0541-4d39-b3ad-8fc3040c745f)

![image](https://github.com/user-attachments/assets/6c55f069-ebd4-4bc8-9d2a-4e555628544e)

![image](https://github.com/user-attachments/assets/4616744a-c105-4088-9a33-4db7e0a06cc7)

## Paso 2 - Crear el archivo de evaluación (`.jsonl`)

Ejemplo básico del archivo:

```json
{"input": "¿Cuánto vale 1 dólar en euros?", "expected_output": "≈"}
{"input": "Convierte 100 pesos mexicanos a dólares.", "expected_output": "≈"}
{"input": "¿Cuál es el tipo de cambio actual del euro al yen?", "expected_output": "≈"}
```

> Nota: `expected_output` puede contener el valor exacto o el símbolo `≈` si usarás comparación semántica, no exacta.

Guarda este archivo como `eval_set.jsonl` y súbelo al contenedor del Storage.

## Paso 3 - Obtener URL SAS o Connection String

1. En el contenedor donde subiste el archivo, haz clic en **Generate SAS**
2. Habilita lectura (`Read`) y establece una fecha de expiración
3. Copia la URL completa con `?sig=...` incluido

![image](https://github.com/user-attachments/assets/c45b63dc-d34f-48ce-aad6-832dc95c7893)

## Paso 4 - Crear la evaluación en Foundry

1. Ve a tu proyecto > sección **Evaluations**
2. Haz clic en **+ New evaluation**
3. Llena los campos:
   - Nombre de la evaluación: `evaluacion-divisas`
   - Agent a evaluar: tu agente principal (que llama al skill de divisas)
   - Eval set source: **Azure Blob Storage**
   - Pega la URL SAS o selecciona la conexión al Storage Account
   - Método de evaluación: LLM-based (recomendado) o exact match

4. Opcional: ajusta el número de muestras si tu archivo tiene muchas entradas

## Paso 5 - Acceder a Safety Evaluators

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project creados.
- En el menú lateral selecciona Evaluation.

![image](https://github.com/user-attachments/assets/d96c634d-db83-4015-a5d7-2f5f5cf8a961)

## Paso 6 - Activar Groundedness Evaluator

- Haz clic en Create Evaluator.
- Completa los campos:

![image](https://github.com/user-attachments/assets/8e0aca9d-2a05-48f7-8e95-2cd3c0ee989f)

![image](https://github.com/user-attachments/assets/b85bd2fb-2004-42b6-9cb6-135c56c5d215)

![image](https://github.com/user-attachments/assets/b168f3fd-a59c-4c82-911d-6f773e0e6dc9)

## Paso 7 - Evaluar modelo directamente (Evaluate model)

En este caso, evaluaremos qué tan bien responde el modelo ante ciertos prompts, sin necesidad de un valor esperado. Esta opción es útil para probar el comportamiento del agente cuando aún no se tiene una "respuesta correcta" establecida.

### Instrucciones:

1. En el paso 1 del asistente de evaluación, selecciona:
   **Evaluate model**
   Después selecciona **Simulate Questions**

![image](https://github.com/user-attachments/assets/038f9064-2c5a-4d7f-b2a1-fb23231036ab)

![image](https://github.com/user-attachments/assets/fcd86892-f6f8-4c49-b743-84bba8c3bd6a)

**Topics to generate questions about**
```
Tasas de cambio entre monedas, conversiones de divisas internacionales, equivalencias entre USD, MXN, EUR, JPY, GBP, ARS, BRL, CAD, CHF, y otras monedas. Consultas frecuentes de usuarios sobre valor actualizado de una moneda frente a otra.
```

**System Prompt**
```
Genera preguntas realistas que un usuario común podría hacerle a un agente de IA especializado en tasas de cambio y conversión de divisas. Las preguntas deben enfocarse en equivalencias entre monedas internacionales como USD, MXN, EUR, JPY, GBP, ARS, BRL, CAD, CHF, etc.

Incluye preguntas del tipo:
- ¿Cuánto vale un dólar en euros?
- Convierte 250 pesos mexicanos a dólares
- ¿Cuál es el tipo de cambio del euro al yen?

Evita preguntas sobre economía general, inflación, inversión, o temas fuera del dominio de divisas.
```
Click generate

![image](https://github.com/user-attachments/assets/4013bebc-768a-4ccc-83f3-8ea2062fe75a)

**Preview**

![image](https://github.com/user-attachments/assets/7ea7dc4d-2256-49b8-a748-16b96f840c3f)

**Select Evaluator:**

Model scorer or Likert-scale evaluator

![image](https://github.com/user-attachments/assets/395208dd-8177-474b-9427-3275540701ab)

**Model scorer**

![image](https://github.com/user-attachments/assets/e3441a84-d0c4-4f11-9b10-c2230983fba6)

![image](https://github.com/user-attachments/assets/c055850c-2dbe-47b2-b6e2-23587328b21d)

```
**User input**
{{item.question}}

**Response to evaluate**
{{item.answer}}
```

![image](https://github.com/user-attachments/assets/f1704ee8-14e4-4e29-986a-9b6b0f6b78e2)

Click Add

![image](https://github.com/user-attachments/assets/70895936-3bc1-430e-9c1f-054c0ab0e22d)

Same steps and add Likert-scale evaluator

![image](https://github.com/user-attachments/assets/3d2da38d-bc77-4017-9a79-43ac231c204b)

![image](https://github.com/user-attachments/assets/27f39a74-bd85-4549-ac6e-83f8d9dbe5f3)

![image](https://github.com/user-attachments/assets/a0e9264a-3198-485c-be3e-5843345139b9)

Click Add

![image](https://github.com/user-attachments/assets/c093e4be-e9e0-45ea-affe-3ec80d297d0d)

Click Next

![image](https://github.com/user-attachments/assets/f941b8f9-4f2d-40b0-8d5e-3595218a2b69)

Click Submit

![image](https://github.com/user-attachments/assets/0d051caa-98f9-4948-b90c-3c0e04ee2b5f)






## Resultado esperado

- Evaluadores de Safety creados y activos.
- Groundedness evaluando consistencia factual.
- Content Safety filtrando contenido sensible.
- Logs de evaluadores visibles en cada ejecución del reasoning plan.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/safety-evaluators
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/monitor-agents
- https://learn.microsoft.com/en-us/azure/ai-services/responsible-ai/
