# Automatización Inteligente de Gestión de Correos con Microsoft Copilot Studio

Este repositorio documenta un flujo de trabajo avanzado para la clasificación y gestión autónoma de correos electrónicos. Diseñado para optimizar los procesos administrativos y mejorar la productividad operativa, el sistema utiliza agentes de inteligencia artificial para evaluar, enrutar y accionar mensajes entrantes en tiempo real. 

Esta implementación refleja la aplicación práctica de herramientas de IA para fortalecer el rendimiento organizacional, reduciendo el tiempo dedicado a tareas repetitivas y priorizando la atención en acciones críticas.

## 📐 Arquitectura del Flujo de Trabajo

El sistema se construye sobre una arquitectura de nodos interconectados en Microsoft Copilot Studio:

![Arquitectura del Flujo de Trabajo](assets/image_34d707.png) *(Asegúrate de subir la imagen a una carpeta llamada 'assets')*

*   **Desencadenador Principal:** Conector de Office 365 ("When a new email arrives") que captura los metadatos, la importancia y el contenido de los mensajes entrantes de forma autónoma.
*   **Motor de Clasificación (Classify):** Utiliza el modelo Claude Sonnet 4.6 para evaluar dinámicamente el remitente, el asunto, el cuerpo y los archivos adjuntos, categorizando el correo en vías de acción específicas.

## ⚙️ Enrutamiento y Ejecución de Agentes

| Categoría de Correo | Secuencia de Nodos | Acción Ejecutada e Integraciones (MCP) |
| :--- | :--- | :--- |
| **Meeting** (Reunión) | `Meeting Logic` | El agente extrae el contexto y utiliza la herramienta de Calendario para generar y enviar automáticamente una invitación de Teams. |
| **Reply Requested** (Respuesta) | `Copilot` ➔ `Email Drafter` | M365 Copilot analiza el historial; el agente redactor utiliza la herramienta de Correo para estructurar y guardar una respuesta en borradores. |
| **Priority** (Prioridad) | `Agent` ➔ `Human review` ➔ `If/Else` | Un agente resume el contenido urgente y envía una solicitud de aprobación vía Teams. Dependiendo de la validación humana, agenda una reunión urgente o envía un correo de seguimiento diferido. |
| **Information** (Informativo) | `Info Sorter` | Identifica correos de lectura, gestiona el mensaje en la bandeja y envía una notificación resumida por Microsoft Teams. |
| **Other** (Otros) | N/A | Mecanismo de seguridad para capturar correspondencia que no cumpla con los parámetros principales. |

## 🛠️ Tecnologías y Competencias Clave

*   **Microsoft Copilot Studio & Model Context Protocol (MCP):** Orquestación de flujos y asignación de herramientas nativas (Mail, Calendar, Teams) a agentes autónomos.
*   **Ingeniería de Prompts y LLMs:** Diseño de instrucciones precisas e inyección de variables dinámicas para el procesamiento de lógica condicional.
*   **Optimización de Procesos (Human-in-the-loop):** Integración estratégica de puntos de validación humana en procesos críticos (correos prioritarios), asegurando el control de calidad.

---
**Desarrollado por:** Camilo Salinas[cite: 1, 2]  
**Perfil:** Especialista en Inteligencia de Negocios y Analítica con más de 10 años de experiencia profesional en administración, control interno y optimización de procesos[cite: 1, 2].
