# Laboratorio 9: Integración de Voz en Azure AI Foundry

## 🎯 Objetivo

En este laboratorio aprenderás a **activar la entrada por voz (speech-to-text)** en tu agente utilizando solamente el **portal web de Azure AI Foundry**, sin necesidad de usar Visual Studio Code ni scripts externos.

---

## 🧩 Prerrequisitos

Antes de iniciar, asegúrate de tener lo siguiente:

- Acceso al portal: [https://ai.azure.com/](https://ai.azure.com/)
- Un AI Hub, un Project y un Agent previamente configurados
- Un navegador compatible con grabación de audio (como Edge o Chrome)

---

## 🔧 Pasos del laboratorio

### Paso 1 – Ingresar al agente

1. Desde el menú lateral, ve a **Agents**
2. Selecciona el agente en el que deseas activar entrada por voz
3. Da clic en **Try in Playground** para acceder a la vista de prueba

![image](https://github.com/user-attachments/assets/df1b482a-b06a-4f72-a550-309a19ff704e)

---

### Paso 2 – Activar el micrófono en el Playground

1. En la barra inferior del Playground, ubica el **ícono de micrófono** 🎤  
2. Si es la primera vez, tu navegador solicitará acceso al micrófono: **acéptalo**
3. Da clic en el micrófono para iniciar la grabación de tu pregunta
4. Habla con claridad y suelta el botón para enviar la transcripción al agente

> ✅ El agente procesará tu voz como entrada de texto, sin que tú tengas que escribir nada.

![image](https://github.com/user-attachments/assets/b9e0fcd7-9247-4591-91af-67d65bc6521d)

---

### Paso 3 – Crear un agente de voz tipo “cajero bancario”

Ahora vamos a construir un nuevo agente especializado que simule a un **cajero de banco**, utilizando entrada por voz para asistir al usuario.

#### 3.1 Crear el agente

1. Desde el menú lateral, selecciona **Agents**
2. Da clic en **+ Create agent**
3. Asigna el nombre: `agente_cajero_banco`
4. Selecciona un modelo como `gpt-4o` o `gpt-35-turbo` según disponibilidad
5. Da clic en **Create**

---

#### 3.2 Configurar el system prompt

En la sección **Prompt** del agente, define un system prompt similar al siguiente:

```plaintext
Eres un cajero virtual de una sucursal bancaria. Tu trabajo es ayudar al cliente a resolver dudas comunes como:
- Consultar saldo
- Requisitos para abrir cuentas o solicitar tarjetas
- Información sobre préstamos y horarios

Habla de forma educada, breve y con instrucciones claras. Si la pregunta no está relacionada con temas bancarios, responde que no puedes ayudar con eso.
```

#### 3.3 Activar entrada por voz

1. Da clic en **Try in Playground** dentro del agente `agente_cajero_banco`.
2. Ubica el ícono del **micrófono** 🎤 en la parte inferior del Playground.
3. Haz clic en el ícono para comenzar la grabación de voz.
4. Habla con claridad y suelta el botón cuando termines.
5. Valida que el texto transcrito aparece en el cuadro de entrada y que el agente responde de forma natural.

##### 🗣️ Ejemplos de preguntas por voz

- `¿Cuáles son los requisitos para abrir una cuenta de débito?`
- `¿Puedo retirar dinero sin mi tarjeta?`
- `¿Qué tipos de préstamos ofrecen?`
- `¿Cuál es el horario de atención de la sucursal?`
- `¿Cómo solicito una tarjeta de crédito?`

> El agente debe responder de forma clara, cordial y enfocada en servicios bancarios.

---

### Paso 4 – Medir el desempeño del agente cajero

1. Ve al menú lateral y selecciona **Evaluation > Evaluate model**
2. Escoge la opción **Simulate Questions**
3. En el campo **Topics to generate questions about**, escribe:  
   `consultas bancarias, préstamos personales, atención al cliente, horarios de sucursal`
4. En **System prompt**, pega el mismo que configuraste en el agente
5. Ajusta el número de preguntas a generar (por ejemplo, 10)
6. Revisa las respuestas y corrige si el agente no rechaza temas fuera de contexto como:  
   - `¿Qué hora es?`
   - `¿Cuánto cuesta un iPhone?`

> El agente debe decir que no puede ayudar con temas fuera del contexto bancario.

![image](https://github.com/user-attachments/assets/f731c010-9d77-49f7-8984-29eee831b32d)

![image](https://github.com/user-attachments/assets/889175fd-a56f-4f91-a30d-b5a553d91096)

---

### ✅ Resultado esperado

- Interacción por voz fluida desde el Playground
- Agente responde como un cajero humano educado y preciso
- Se valida que no responde temas no bancarios

---

## 🧠 Consideraciones adicionales

| Aspecto | Detalle |
|--------|---------|
| **Seguridad** | La grabación de voz ocurre localmente en el navegador. No se almacena en Azure a menos que se use una tool explícita. |
| **Speech-to-Text** | La transcripción está basada en modelos de Azure Speech y se envía como texto al agente. |
| **Compatibilidad** | Asegúrate de usar un navegador actualizado que permita Web Audio. |

---

## ✅ Resultado esperado

Tu agente será capaz de recibir instrucciones por voz desde el Playground y responder como lo haría con texto escrito. Esto mejora la accesibilidad y naturalidad de uso.

---

## 🏁 Siguientes pasos (opcional)

- Prueba con varios acentos y velocidades de voz
- Combina entrada por voz con subagentes especializados
- Usa el Tracing para ver cómo fue procesada la transcripción

---

## 📚 Recursos oficiales

- [Azure AI Foundry – Playground](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/playground)
- [Azure AI Speech Overview](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/overview)
