# Laboratorio 3: Configuración de Memories en AI Foundry

## Objetivo

En este laboratorio configuraremos las dos principales capacidades de memoria de AI Foundry:

- **Conversational Memory**: Permite mantener el contexto durante interacciones multi-turn.
- **Knowledge Memory**: Permite grounding factual a partir de documentos empresariales.

Ambas capacidades fortalecen el razonamiento planificado y la precisión de los agentes.

---

## Prerrequisitos

- Haber completado el **Laboratorio 2**.
- Agent básico creado y funcional en el proyecto `ai-foundry-lab-project`.
- Permisos de Contributor sobre el Project.

---

## Sección 1: Creación de Conversational Memory

### Paso 1 - Acceder al proyecto

1. Inicia sesión en Azure AI Studio:  
   https://ai.azure.com

2. Accede al workspace y project creados.

3. Ingresa a **Memories** en el menú lateral.

### Paso 2 - Crear Conversational Memory

1. Haz clic en **Create Memory**.

2. Selecciona el tipo de memoria:  
   `Conversational Memory`

3. Completa los campos:

- **Memory Name:**  
  `memoria-conversacional-lab`

- **Description:**  
  `Memoria conversacional para mantener contexto multi-turn.`

4. Opciones adicionales:

- **Retention Period:**  
  30 días (valor por defecto es suficiente para laboratorio).
  
- **Data Store Type:**  
  `Azure Managed Store` (uso de almacenamiento interno gestionado).

5. Haz clic en **Create**.

### Paso 3 - Asociar Conversational Memory al Agent

1. Accede al Agent creado (`primer-agent-gpt4o`).

2. Selecciona **Edit Agent**.

3. En la sección de Memories, agrega:

- **Conversational Memory:**  
  `memoria-conversacional-lab`

4. Guarda los cambios.

### Paso 4 - Validación funcional

1. Entra a **Test Agent**.

2. Realiza una conversación multi-turn. Ejemplo:

- Prompt 1: `¿Cuál es el ROI típico en proyectos de tecnología?`
- Prompt 2: `¿Y cómo cambia ese ROI en proyectos de infraestructura?`

3. Observa cómo el Agent retiene el contexto de la primera pregunta.

---

## Sección 2: Creación de Knowledge Memory (Grounding)

### Paso 1 - Preparar documento de grounding

Prepara un documento simple en PDF o TXT con contenido empresarial. Ejemplo:

- Nombre: `politicas_riesgo_crediticio.pdf`
- Contenido: definiciones de riesgo crediticio, criterios de evaluación, políticas internas.

> **Nota:** El documento no requiere formato especial para el laboratorio.

### Paso 2 - Crear Knowledge Memory

1. Dentro de **Memories**, haz clic en **Create Memory**.

2. Selecciona el tipo de memoria:  
   `Knowledge Memory`

3. Completa los campos:

- **Memory Name:**  
  `memoria-conocimiento-lab`

- **Description:**  
  `Memoria de conocimiento financiero para grounding.`

4. Selecciona el Data Store Type:  
  `Azure Managed Store`

5. Haz clic en **Create**.

### Paso 3 - Ingesta de documentos

1. Dentro de la nueva Knowledge Memory, selecciona **Add Documents**.

2. Carga el archivo `politicas_riesgo_crediticio.pdf`.

3. Espera a que el proceso de indexación se complete (puede demorar algunos minutos dependiendo del documento).

### Paso 4 - Asociar Knowledge Memory al Agent

1. Ingresa nuevamente al Agent (`primer-agent-gpt4o`).

2. Edita la configuración y agrega:

- **Knowledge Memory:**  
  `memoria-conocimiento-lab`

3. Guarda los cambios.

### Paso 5 - Validación funcional

1. Entra a **Test Agent**.

2. Realiza preguntas relacionadas al documento cargado. Ejemplos:

- `¿Cuál es el criterio de evaluación de riesgo crediticio según las políticas internas?`
- `¿Cómo clasifica la empresa el riesgo alto en créditos personales?`

3. Observa cómo el Agent utiliza el grounding del documento.

---

## Resultado esperado

- Conversational Memory funcional con retención de contexto multi-turn.
- Knowledge Memory integrada con grounding factual desde documentos.
- Agent capaz de responder preguntas con base en el contenido cargado.
- Reasoning controlado y consistente con las políticas de negocio.

---

## Links de referencia

- [Memories en AI Foundry](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/memories-overview)
- [Conversational Memory](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/conversational-memory)
- [Knowledge Memory y grounding](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/knowledge-memory)
