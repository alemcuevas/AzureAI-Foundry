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
  `primer-agent-gpt4o`
- **Description (opcional):**  
  `Primer agente de laboratorio utilizando GPT-4o`
- **Objective (System Prompt):**  
  ```markdown
  Eres un agente de IA financiero. Respondes preguntas de forma precisa, objetiva, profesional y basada en datos. Si no sabes la respuesta, indicas que no tienes suficiente información.
