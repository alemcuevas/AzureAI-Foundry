# Laboratorio 8: Generación de Video con Sora – Diseño e Integración Conceptual

## 🎯 Objetivo

Diseñar un flujo de interacción que permita generar un video utilizando el modelo Sora como backend externo, y simular su integración en Azure AI Foundry como una herramienta conectada (Connected Tool), para agentes que generen contenido visual desde texto.

> Este laboratorio no requiere código y puede completarse 100% desde el portal de Azure AI Foundry.

---

## 🧩 Prerrequisitos

- Acceso a Azure AI Foundry: [https://ai.azure.com](https://ai.azure.com)
- Un AI Hub y un Project creados
- Un agente activo donde puedas conectar herramientas (Tools o Connected Skills)
- Conocimiento básico de Prompt Engineering

---

## 🔧 Pasos del laboratorio

### Paso 1 – Crear un agente llamado `generador_video_sora`

1. En la sección **Agents**, crea un nuevo agente.
2. Nombre: `generador_video_sora`
3. Modelo: `gpt-4o` (recomendado por su capacidad multimodal)
4. Prompt inicial (System prompt):

```plaintext
Eres un generador de video inteligente. Tu tarea es interpretar descripciones escritas y producir instrucciones para crear un video con base en esa narrativa. Cuando un usuario escribe una historia breve o escena, generas una descripción estructurada para enviarla a un generador de video como Sora.
