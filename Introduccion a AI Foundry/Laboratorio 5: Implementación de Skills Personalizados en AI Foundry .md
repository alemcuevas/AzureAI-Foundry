# Laboratorio 5: Implementación de Skills Personalizados en AI Foundry

## Objetivo

En este laboratorio vamos a:

- Crear un Skill personalizado dentro de AI Foundry.
- Agregar lógica de negocio interna al agente.
- Validar cómo el agente invoca el Skill durante el reasoning plan.

Los Skills permiten que el agente ejecute funciones específicas definidas por el usuario, integrando lógica empresarial sin necesidad de APIs externas.

## Prerrequisitos

- Haber completado el Laboratorio 4.
- Agent creado y funcional con Memories y Tools configurados.
- Acceso al Project dentro del Workspace de AI Foundry.

## Concepto de Skill en AI Foundry

- Un Skill es una función personalizada que encapsula lógica de negocio.
- Los Skills son invocados directamente por el agente dentro de su reasoning plan.
- A diferencia de los Tools (que acceden a APIs externas), los Skills ejecutan lógica interna predefinida.

## Caso de uso del laboratorio

Simularemos un Skill de negocio sencillo: calcular la tasa de interés efectiva anual (APR) a partir de un interés nominal y el número de periodos de capitalización.

Fórmula del cálculo:

APR = (1 + i / n)^n - 1

Donde:

- i = tasa de interés nominal (decimal).
- n = número de periodos de capitalización por año.

## Paso 1 - Acceder a Skills dentro del proyecto

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project creados.
- En el menú lateral selecciona Skills.

## Paso 2 - Crear un nuevo Skill

- Haz clic en Create Skill.
- Completa los campos iniciales:

Skill Name: calculo-apr-skill

Description: Skill para calcular tasa de interés efectiva anual (APR).

## Paso 3 - Definir los parámetros del Skill

Define los parámetros de entrada:

Parámetro | Tipo | Descripción
--- | --- | ---
nominal_rate | number | Tasa de interés nominal (por ejemplo, 0.08 para 8%).
periods | integer | Número de periodos de capitalización al año.

Define el esquema de salida:

Output: effective_rate (number)

Descripción: Tasa de interés efectiva calculada (APR).

## Paso 4 - Definir la lógica del Skill

En AI Foundry puedes definir la lógica del Skill utilizando el editor incorporado. Para este laboratorio, definimos:

def main(nominal_rate: float, periods: int) -> dict:
    apr = (1 + nominal_rate / periods) ** periods - 1
    return {"effective_rate": apr}

Nota: Toda la lógica es ejecutada por AI Foundry dentro del entorno seguro y gestionado.

## Paso 5 - Guardar y probar el Skill

- Guarda el Skill.
- Selecciona Test Skill.
- Ejecuta la prueba de invocación. Ejemplo:

nominal_rate: 0.08

periods: 12

Resultado esperado:

{
  "effective_rate": 0.082999
}

Aproximadamente 8.30% efectivo anual.

## Paso 6 - Asociar el Skill al Agent

- Accede al Agent primer-agent-gpt4o.
- Edita la configuración del Agent.
- En la sección Skills, agrega el nuevo Skill creado: calculo-apr-skill.
- Guarda los cambios.

## Paso 7 - Prueba completa del reasoning + Skill

- Ingresa a Test Agent.
- Realiza una consulta que requiera cálculo. Ejemplos:

¿Cuál es la tasa efectiva anual si la tasa nominal es de 8% anual y se capitaliza 12 veces por año?

Calcula el APR para una tasa nominal de 10% con 4 periodos de capitalización.

- Observa cómo el Agent:

Reconoce que necesita invocar el Skill.

Llama automáticamente al cálculo interno.

Integra el resultado en su respuesta final.

## Resultado esperado

- Skill creado y funcional dentro de AI Foundry.
- Agente ejecutando lógica interna personalizada.
- Respuestas generadas basadas en cálculo exacto, no en inferencias del modelo.
- Ejecución validada de reasoning plan + invocación de Skill.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview#skills
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/create-skills
- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans
