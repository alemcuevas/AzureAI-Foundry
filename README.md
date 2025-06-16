# AI Foundry Workshop

## Descripción General

Este workshop está diseñado para habilitar arquitectos, data scientists, ingenieros de AI y equipos de producto en el uso completo de **Azure AI Foundry** dentro de Azure AI Studio, combinando:

- Orquestación agentic avanzada (Reasoning Plans).
- Procesamiento documental empresarial.
- Modelos custom de visión e integración multimodal.
- Integración con Responsible AI y Safety Evaluators.
- Todo construido sin necesidad de código, 100% declarativo dentro de AI Foundry.

---

## Requisitos Generales

- Suscripción activa de Azure.
- Azure AI Studio habilitado.
- Permisos Contributor sobre la suscripción.
- Acceso habilitado a Azure OpenAI Service con modelos GPT-4o.
- Acceso habilitado a Azure AI Vision Studio.
- Acceso habilitado a Azure Document Intelligence.

---

## Estructura de Tracks

Este workshop está dividido en 3 tracks independientes pero complementarios:

---

### **Track 1 - Agentic Reasoning Core (GPT-4o)**

Flujo clásico de AI Foundry para orquestación de agentes LLM:

**Laboratorios:**

1. Creación de Workspace y Proyecto en AI Foundry
2. Creación de un Agent básico con GPT-4o
3. Configuración de Memories (Conversational + Knowledge Memory)
4. Creación de Tools nativos (API externas no-code)
5. Implementación de Skills personalizados (lógica de negocio)
6. Configuración de Safety Evaluators (Responsible AI)
7. Construcción de Reasoning Plans (Orchestration)
8. Monitoreo Operativo en AI Foundry
9. Ajuste de Prompt Engineering Avanzado
10. Proyecto Final Enterprise Agent (agentic reasoning completo)

---

### **Track 2 - Document Intelligence + AI Foundry**

Integración completa de procesamiento documental empresarial dentro de AI Foundry.

**Laboratorios:**

1. Preparación de Azure AI Studio y Document Intelligence
2. Creación de Tool en AI Foundry para consumir el modelo de Document Intelligence
3. Integración del Tool dentro de un Reasoning Plan agentic
4. Configuración de Safety Evaluators sobre documentos
5. Proyecto Final Enterprise Document Intelligence + AI Foundry

---

### **Track 3 - Vision Custom Models + AI Foundry**

Integración de modelos personalizados de visión (Object Detection) con Reasoning Plans.

**Laboratorios:**

1. Entrenamiento y publicación de modelo de detección de objetos en Azure AI Vision Studio
2. Creación del Tool en AI Foundry para consumir el modelo de visión
3. Construcción del Reasoning Plan multimodal
4. Aplicación de Safety Evaluators sobre reasoning multimodal
5. Proyecto Final Enterprise Vision + Reasoning + Responsible AI

---

## Arquitectura Conceptual

- **Azure AI Studio Foundry** como motor de orquestación agentic.
- **Azure OpenAI (GPT-4o)** como modelo foundational multimodal.
- **Azure Document Intelligence** para extracción documental estructurada.
- **Azure AI Vision Studio** para entrenamiento de modelos custom de object detection.
- **Azure Monitor / Diagnostic Logs** para auditoría y observabilidad.

---

## Dependencias adicionales por track

| Track | Dependencias adicionales |
|-------|---------------------------|
| Agentic Reasoning | Ninguna |
| Document Intelligence | Azure AI Document Intelligence habilitado |
| Vision Custom | Azure AI Vision Studio habilitado |

---

## Flujo sugerido para ejecución

- Ejecutar Track 1 completo para habilitar el razonamiento básico.
- Luego seleccionar Track 2 o Track 3 como extensiones según el caso de negocio.

---

## Notas Enterprise

- Todos los labs están diseñados para funcionar bajo entornos auditables, gobernados y productivos.
- Todas las configuraciones de Reasoning Plan, Tools, Skills, Memories y Evaluators son declarativas vía Azure AI Studio Foundry.
- Las únicas configuraciones externas ocurren durante el entrenamiento de los modelos de Document Intelligence y Vision Studio.

---

## Documentación Oficial de Referencia

- [Azure AI Foundry Overview](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/overview)
- [Azure AI Foundry Reasoning Plans](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/reasoning-plans)
- [Azure AI Foundry Tools & Skills](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/tools-and-skills-overview)
- [Azure Document Intelligence](https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/)
- [Azure AI Vision Studio](https://learn.microsoft.com/en-us/azure/ai-studio/vision/)
- [Responsible AI & Safety Evaluators](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/safety-evaluators)
- [Azure Monitor Integration](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/monitor-agents)

---

## Créditos

Este workshop fue generado como práctica enterprise de AI Foundry sobre Azure AI Studio, diseñado para implementaciones reales de agente empresarial orquestado, visión multimodal e inteligencia documental en la nube.

