# Laboratorio 2: Creación del primer Agent GPT-4o en AI Foundry

## Objetivo

En este laboratorio vamos a crear el primer Agent básico utilizando GPT-4o como modelo de reasoning central.

El Agent podrá recibir prompts, ejecutar reasoning básico y entregar respuestas directamente dentro del entorno de AI Foundry.

---

## Prerrequisitos

- Haber completado el **Laboratorio 1**.
- Workspace y Project de AI Foundry ya configurados.
- Confirmación de disponibilidad del modelo `gpt-4o`.

---

## Paso 1 - Acceso al proyecto de AI Foundry

1. Inicia sesión en Azure AI Studio:  
   https://ai.azure.com

2. Navega al Workspace creado (`ai-foundry-lab-ws`).

3. Ingresa al **Project** creado en el Lab 1 (`ai-foundry-lab-project`).

---

## Paso 2 - Creación del Agent

1. Dentro del Project, selecciona **Agents** en el menú lateral.

2. Haz clic en **Create Agent**.

3. Completa los campos básicos:

- **Agent Name:**  
  `primer-agent-gpt4o-usuario-1`
- **Description (opcional):**  
  `Primer agente de laboratorio utilizando GPT-4o`
- **Objective (System Prompt):**  
  ```markdown
  Eres un agente de IA financiero. Respondes preguntas de forma precisa, objetiva, profesional y basada en datos. Si no sabes la respuesta, indicas que no tienes suficiente información.

![image](https://github.com/user-attachments/assets/6d74a497-f377-476c-b242-3a814bfdd460)

![image](https://github.com/user-attachments/assets/1ee50fea-5213-494b-898d-afb917796da2)

4. Haz clic en **Next** para continuar la configuración.

## Paso 3 - Selección del Foundation Model

En la sección de Foundation Model selecciona:

- **Model provider:** Azure OpenAI
- **Model version:** gpt-4o (última versión disponible)

Puedes dejar los parámetros por default para este primer ejercicio:

- **Temperature:** 0.7
- **Top P:** 1.0
- **Max Tokens:** 4096

> Nota: Estos parámetros podrán ajustarse en futuros laboratorios para modificar el comportamiento del reasoning.

## Paso 4 - Configuración básica de Inputs & Outputs

En este primer Agent, dejamos los parámetros básicos:

- **Input Type:** Text
- **Output Type:** Text

No configuraremos Memories, Tools ni Safety Evaluators aún (se abordarán en siguientes labs).

Haz clic en **Create Agent** para finalizar.

## Paso 5 - Pruebas iniciales de ejecución

Una vez creado el Agent, selecciona **Test Agent**.

Realiza pruebas de interacción básica. Ejemplos de prompts:

- ¿Cuál es el propósito de un análisis de riesgo financiero?
- ¿Qué es el capital de trabajo en una empresa?
- Explica qué es el ROI en un proyecto de inversión.

Observa las respuestas generadas.

Valida los logs de reasoning generados por el agente.

## Paso 6 - Análisis del comportamiento del reasoning

- Observa si el agente sigue las instrucciones definidas en el **Objective (System Prompt)**.
- Verifica si responde de forma profesional, objetiva y precisa.
- Toma nota de posibles ajustes de prompting o parámetros para mejorar en labs posteriores.

## Resultado esperado

- Agent creado exitosamente usando el modelo gpt-4o.
- Capacidad de recibir inputs de texto y generar respuestas coherentes.
- Primer flujo de reasoning ejecutado dentro de AI Foundry.
- Logs de ejecución disponibles para revisión.

## Consideraciones para siguientes laboratorios

- En siguientes labs incorporaremos Memories, Tools, Skills, Safety Evaluators y Reasoning Plans.
- Este primer Agent servirá como base para extender sus capacidades.

## Links de referencia

- [Creación de Agents en AI Foundry](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/agents-overview)
- [Configuración de Foundation Models](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/models-overview)
- [Azure OpenAI Models - GPT-4o](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/models#gpt-4o)
