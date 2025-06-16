# Laboratorio 1: Creación del Workspace y Proyecto en AI Foundry

## Objetivo

En este primer laboratorio configuraremos el entorno inicial en Azure AI Studio para trabajar con AI Foundry, incluyendo:

- Creación del Workspace de Azure AI Studio.
- Creación del primer Project dentro del Workspace.
- Validación de disponibilidad de modelos foundation.
- Confirmación de acceso al modelo GPT-4o.

---

## Prerrequisitos

- Suscripción activa de Azure.
- Permisos de **Owner** o **Contributor** sobre la suscripción.
- Rol habilitado para el uso de Azure AI Studio (AI Foundry está en Public Preview pero requiere habilitación de región).
- Acceso a la región donde esté disponible AI Foundry (por ejemplo: `East US`).

---

## Paso 1 - Acceso a Azure AI Studio

1. Inicia sesión en el portal de Azure:  
   https://portal.azure.com

2. Abre el servicio **Azure AI Studio**:  
   https://ai.azure.com

3. Valida que puedes acceder al panel principal de Azure AI Studio.

> Si no aparece la opción de AI Foundry, valida que el servicio esté habilitado para la suscripción y región.

---

## Paso 2 - Creación del Workspace de AI Studio

![image](https://github.com/user-attachments/assets/f7c1e8ba-c595-4eca-87d0-14111e6f93c3)

![image](https://github.com/user-attachments/assets/8e0d1dd3-86ca-4420-a593-bbbf5217d25c)

![image](https://github.com/user-attachments/assets/1a71258c-c8d0-43a9-b881-f30464d68636)



1. En Azure AI Studio selecciona **Create workspace**.

2. Completa los siguientes campos:

- **Subscription:** Selecciona la suscripción correcta.
- **Resource Group:** Puedes crear uno nuevo o usar uno existente (ejemplo: `rg-usuario-ai-#`).
- **Workspace name:**  
  `ws-usuario-ai-#`
- **Region:**  
  Selecciona una región donde AI Foundry esté disponible (ejemplo: `East US`).

3. Revisa las configuraciones de red (puedes dejar red pública para el laboratorio inicial).

4. Haz clic en **Review + Create** y confirma la creación.

> La creación del workspace puede tomar algunos minutos.

![image](https://github.com/user-attachments/assets/1f6bd3d2-27d8-4645-9eb2-e4f346a072a1)

![image](https://github.com/user-attachments/assets/4867663b-6b06-4185-941e-0d07bad5174c)

![image](https://github.com/user-attachments/assets/3870065c-0833-4b18-8e71-c57f7cd04ae7)

![image](https://github.com/user-attachments/assets/ba227055-5835-4aeb-b8dd-ef0aed3d7640)

![image](https://github.com/user-attachments/assets/c109d725-1548-43c7-9d8e-7c1e8fd72ea6)

---

## Paso 3 - Acceso al Workspace

1. Una vez creado el workspace, selecciona **Go to resource**.

2. Dentro del workspace, accede al menú de **Explore Azure AI Foundry portal**.

3. Valida que puedes acceder al portal de AI Foundry dentro de AI Studio.

![image](https://github.com/user-attachments/assets/b48d447d-9f06-4a3d-a049-ca354e6a4b10)

![image](https://github.com/user-attachments/assets/35a4d100-7ad8-47b7-ba39-081a541a13d4)

---

## Paso 4 - Creación del Proyecto AI Foundry

1. Dentro del workspace, navega a **Foundry → Projects**.

2. Haz clic en **New Project**.

3. Completa los siguientes datos:

- **Project name:**  
  `ai-foundry-lab-project-#`
- **Description (opcional):**  
  `Proyecto inicial de laboratorio AI Foundry`
- **Tags:**  
  Puedes agregar etiquetas como `environment:lab` o `workshop:foundry`.

4. Confirma la creación del proyecto.

![image](https://github.com/user-attachments/assets/96311e00-7695-478d-ac54-a4b50ab33210)

![image](https://github.com/user-attachments/assets/4fbb8469-1ede-4468-a6ee-87f908acd74a)

![image](https://github.com/user-attachments/assets/35065226-ec7b-4af0-8847-51b7e0883a5b)


---

## Paso 5 - Validación de modelos disponibles

1. Dentro del Project, selecciona **Foundation Models**.

2. Valida la disponibilidad de los modelos habilitados para la suscripción:

- `gpt-4o`
- `gpt-4-turbo`
- `gpt-35-turbo`
- `phi-3`
- `vision models` (si aplica)

> **Nota:** Algunos modelos requieren aprobación previa dentro del tenant.

3. Asegúrate de que **GPT-4o** aparece habilitado como modelo disponible.

---

## Paso 6 - Validación de permisos RBAC

1. Dentro de Azure AI Studio, accede a la configuración del Workspace.

2. Verifica los roles asignados:

- AI Studio Owner
- AI Studio Contributor
- AI Studio Reader

3. Valida que tienes permisos para:

- Crear Projects.
- Crear Agents.
- Configurar evaluadores de seguridad.

---

## Resultado esperado

Al finalizar este laboratorio debes tener:

- Un workspace de AI Studio creado y funcional.
- Un primer proyecto de AI Foundry listo para la creación de agents.
- Acceso confirmado a los Foundation Models habilitados.
- Permisos correctos para continuar con los siguientes laboratorios.

---

## Links de referencia

- [Azure AI Studio Overview](https://learn.microsoft.com/en-us/azure/ai-studio/overview)
- [AI Foundry Projects](https://learn.microsoft.com/en-us/azure/ai-studio/foundry/projects)
- [Azure AI Studio - Roles y permisos](https://learn.microsoft.com/en-us/azure/ai-studio/roles-permissions)

