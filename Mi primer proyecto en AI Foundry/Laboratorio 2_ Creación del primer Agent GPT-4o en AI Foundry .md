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

## ¿Qué es Temperature y Top P?

### **Temperature**

El parámetro **temperature** controla el nivel de aleatoriedad y creatividad en las respuestas generadas por el modelo.

- Valores bajos (por ejemplo: 0.1 - 0.3):  
  - Salidas más predecibles, conservadoras y repetitivas.
  - Útil en escenarios donde se requiere precisión y consistencia.
  - Ejemplos: agentes financieros, legales, cumplimiento.

- Valores altos (por ejemplo: 0.7 - 1.0):  
  - Salidas más variadas, creativas y diversas.
  - Útil para generación de ideas, brainstorming, escritura creativa.
  - Ejemplos: generación de contenidos, asistentes de redacción.

### **Top P (nucleus sampling)**

El parámetro **top_p** controla el rango de probabilidad acumulada de tokens que el modelo considerará al generar la siguiente palabra.

- **Top P = 1.0**:  
  - El modelo considera todo el espacio de probabilidad (sin filtrado).
  - Equivalente a no aplicar truncamiento probabilístico.

- **Top P < 1.0** (por ejemplo: 0.8):  
  - El modelo solo considera las opciones más probables que sumen hasta el porcentaje indicado.
  - Permite limitar respuestas demasiado improbables.
  - Combinado con temperature, controla la diversidad manteniendo coherencia.

> **Nota:**  
> En la mayoría de los escenarios enterprise, se recomienda partir con:
> 
> - **Temperature:** 0.3 a 0.7  
> - **Top P:** 0.8 a 1.0

Así se mantiene un balance adecuado entre control, precisión y algo de flexibilidad en el lenguaje.

![image](https://github.com/user-attachments/assets/ce9e1d95-ea57-4460-a6ce-11148fd45557)

## Paso 4 - Configuración básica de Inputs & Outputs

En este primer Agent, dejamos los parámetros básicos:

No configuraremos Memories, Tools ni Safety Evaluators aún (se abordarán en siguientes labs).

Haz clic en **Create Agent** para finalizar.

![image](https://github.com/user-attachments/assets/63ae34f9-b4c4-41ed-82b2-b0845e28b2b2)

![image](https://github.com/user-attachments/assets/82f6c38a-eeac-45f9-b4fb-e01dd15c2f5d)

![image](https://github.com/user-attachments/assets/eee1e29e-ca19-4bfc-adbc-f05b698bbec4)

![image](https://github.com/user-attachments/assets/c7cc3643-c611-4206-a282-6d6106f50f2a)

![image](https://github.com/user-attachments/assets/3ebee4bc-8af4-4eb0-9b57-0ef19727b3ed)

![image](https://github.com/user-attachments/assets/ef7a4f88-2fb4-42b0-997c-f4b401c7a241)

## Paso 5 - Pruebas iniciales de ejecución

Una vez creado el Agent, selecciona **Test Agent**.

Realiza pruebas de interacción básica. Ejemplos de prompts:

- ¿Cuál es el propósito de un análisis de riesgo financiero?
- ¿Qué es el capital de trabajo en una empresa?
- Explica qué es el ROI en un proyecto de inversión.

Observa las respuestas generadas.

Valida los logs de reasoning generados por el agente.

![image](https://github.com/user-attachments/assets/078039c4-00f9-4e52-bbfc-f67d9bc116fd)

![image](https://github.com/user-attachments/assets/e839fbed-bd47-4121-a559-44942619f555)

![image](https://github.com/user-attachments/assets/4721cc70-4d1a-4ea4-b4cf-dec75b0fd123)

![image](https://github.com/user-attachments/assets/78681b6d-024f-40f3-860e-44ac7db8be2b)

![image](https://github.com/user-attachments/assets/1ec68f71-22a5-406c-8646-565526b6a9bf)

![image](https://github.com/user-attachments/assets/e9a69f1d-0f78-4984-b954-37a6c9b83c4b)

![image](https://github.com/user-attachments/assets/6496eae7-8aa3-4b3d-bf6b-4d0ad229646a)


## Paso 6 - Análisis del comportamiento del reasoning

- Observa si el agente sigue las instrucciones definidas en el **Objective (System Prompt)**.
- Verifica si responde de forma profesional, objetiva y precisa.
- Toma nota de posibles ajustes de prompting o parámetros para mejorar en labs posteriores.

![image](https://github.com/user-attachments/assets/0b13f70a-a046-40db-bd84-6d23c25fa6f9)

![image](https://github.com/user-attachments/assets/20ab40aa-ebc5-4238-b5e4-eb76deed07e9)


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
