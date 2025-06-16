# Laboratorio 1 - Track Document Intelligence: Preparación de Azure AI Studio y Document Intelligence

## Objetivo

En este primer laboratorio vamos a:

- Preparar el entorno en Azure AI Studio.
- Crear el servicio de Document Intelligence.
- Configurar el modelo de extracción documental.
- Dejar listo el endpoint para integrarlo después con AI Foundry.

## Prerrequisitos

- Suscripción activa de Azure.
- Permisos de Contributor sobre la suscripción.
- Azure AI Studio habilitado en la región de trabajo.

## Concepto de Document Intelligence

- Azure Document Intelligence permite extraer información estructurada desde documentos empresariales.
- Soporta facturas, contratos, formularios, reportes financieros y documentos personalizados.
- El modelo puede ser preconstruido o entrenado personalizado (Custom Model).

## Paso 1 - Acceso a Azure AI Studio

- Inicia sesión en Azure AI Studio: https://ai.azure.com
- Selecciona el Workspace donde trabajaremos el laboratorio.
- Valida acceso a la sección de Document Intelligence.

## Paso 2 - Crear un proyecto de Document Intelligence

- Dentro de AI Studio selecciona "Document Intelligence".
- Haz clic en "New Project".
- Completa los campos:

Project Name: doc-intelligence-lab

Description: Proyecto para extracción de información financiera.

Data Storage: selecciona Azure Storage asociado al Workspace.

- Haz clic en Create.

## Paso 3 - Seleccionar tipo de modelo

Para este laboratorio usaremos un modelo preconstruido (sin entrenamiento):

- Selecciona Prebuilt Model.
- Elige el modelo "Prebuilt Invoice" o "Prebuilt Business Card" (ambos soportados sin entrenamiento).
- Estos modelos permiten hacer pruebas sin necesidad de entrenamiento personalizado.

## Paso 4 - Prueba de extracción

- Carga un archivo de ejemplo de factura (Invoice en PDF o imagen).
- Ejecuta la extracción de prueba.
- Observa los resultados de los campos extraídos:

  - Vendor Name
  - Invoice Date
  - Total Amount
  - Due Date
  - Tax Amount

- Valida que el modelo extrae correctamente los campos.

## Paso 5 - Generar el endpoint de inferencia

- Una vez validada la extracción:

  - Publica el modelo.
  - Obtén la URL del endpoint.
  - Obtén la clave API (Key) para autenticación.

Estos valores los utilizaremos para crear el Tool dentro de AI Foundry en los siguientes labs.

## Resultado esperado

- Proyecto de Document Intelligence creado.
- Modelo preconstruido habilitado y probado.
- Endpoint de inferencia publicado.
- Endpoint URL y Key disponibles para integración.

## Links de referencia

- https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/
- https://learn.microsoft.com/en-us/azure/ai-studio/document-intelligence-overview
