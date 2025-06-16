# Laboratorio 9: Ajuste de Prompt Engineering Avanzado dentro de AI Foundry

## Objetivo

En este laboratorio vamos a:

- Ajustar el prompting interno del agente.
- Modificar el system prompt (instructions) para definir el comportamiento deseado.
- Aplicar técnicas de prompt engineering para mejorar la calidad, consistencia y seguridad de las respuestas.
- Probar patrones de few-shot prompting.

El prompt engineering en AI Foundry es una de las capas clave de control del comportamiento de los agentes.

## Prerrequisitos

- Haber completado el Laboratorio 8.
- Agent funcional bajo Reasoning Plan.
- Acceso al Project dentro del Workspace de AI Foundry.

## Concepto de System Prompt en AI Foundry

- El System Prompt es la instrucción base que gobierna el comportamiento general del agente.
- Se define durante la creación o edición del Agent.
- Controla tono, rol, estilo de respuesta, profundidad de detalle, idioma y políticas de respuesta.

## Paso 1 - Acceder al Agent para ajuste de Prompt

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Accede al Workspace y Project creados.
- Ingresa al Agent: primer-agent-gpt4o.
- Haz clic en Edit Agent.

## Paso 2 - Ajustar el System Prompt

Reemplazaremos el prompt inicial por uno más detallado. Inserta el siguiente texto en la sección System Prompt (Instructions):

Eres un asesor financiero experto en políticas bancarias y regulatorias. Respondes de forma:

- Precisa.
- Basada únicamente en datos verificables.
- Objetiva, sin especulaciones.
- Con respuestas claras y fáciles de entender.
- Si no cuentas con suficiente información, indicas: "No dispongo de información suficiente para responder con certeza."

Siempre mantén un tono profesional, empático y neutral.

## Paso 3 - Aplicar técnicas de Formato de Respuesta

Agrega instrucciones adicionales para definir el formato de salida:

Cuando proporciones información, usa el siguiente formato:

- Respuesta principal.
- Si corresponde, lista de consideraciones adicionales.
- Siempre incluye advertencias si la información puede estar incompleta.

## Paso 4 - Aplicar Few-Shot Prompting (opcional)

Puedes agregar ejemplos dentro del mismo system prompt para reforzar el comportamiento:

Ejemplo 1:

Pregunta: ¿Cuál es el ROI típico en proyectos de tecnología?
Respuesta: El ROI típico en proyectos de tecnología puede variar ampliamente, pero frecuentemente oscila entre 15% y 30% anual, dependiendo de los costos iniciales, adopción del mercado y riesgos operativos.

Ejemplo 2:

Pregunta: ¿Cuál es la tasa de riesgo soberano de Marte?
Respuesta: No dispongo de información suficiente para responder con certeza.

Estos ejemplos ayudan al modelo a entender el patrón deseado de respuestas.

## Paso 5 - Guardar cambios y probar el agente

- Guarda la configuración actualizada del Agent.
- Ingresa a Test Agent.
- Realiza las siguientes pruebas:

Prueba 1: ¿Cuál es el ROI de un proyecto de infraestructura energética?

Prueba 2: ¿Cuál es la inflación proyectada en Neptuno?

Prueba 3: ¿Qué regulaciones aplican para la evaluación de riesgos crediticios?

## Paso 6 - Validar el impacto del Prompt Engineering

- Observa:

  - El tono profesional y neutral.
  - La claridad de las respuestas.
  - La capacidad de rechazar respuestas especulativas.
  - El formato de salida consistente.

## Resultado esperado

- Agent ajustado con prompting controlado.
- Comportamiento más estable, predecible y alineado a los objetivos de negocio.
- Implementación básica de few-shot prompting aplicada.
- Base sólida para agentes productivos en entornos regulados.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-studio/foundry/agents-overview
- https://learn.microsoft.com/en-us/azure/ai-studio/prompt-engineering-overview
- https://learn.microsoft.com/en-us/azure/ai-services/responsible-ai/
