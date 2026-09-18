# Caso de Estudio: FichajeSimple (SaaS de Control Horario)

*Nota: El código fuente de este proyecto es privado al ser un desarrollo comercial para MLabsGroup. Este repositorio sirve como documentación técnica de la arquitectura y las soluciones implementadas.*

## 📌 Resumen del Proyecto
FichajeSimple es una plataforma web SaaS desarrollada para automatizar el registro de la jornada laboral de las empresas, garantizando el cumplimiento legal mediante la generación automática de documentos. 
*   **Equipo:** Desarrollado dentro de un equipo de 3 personas.
*   **Mi rol:** Desarrollo Full-Stack con fuerte enfoque en Frontend. Fui el encargado de diseñar y gestionar íntegramente la base de datos en Supabase, además de liderar la creación de la interfaz de usuario, los flujos de la aplicación y la pasarela de pagos.

## 🏗️ Arquitectura y Stack Tecnológico
*   **Frontend:** Next.js, React, TypeScript, Tailwind CSS.
*   **Backend & Conexión:** Node.js.
*   **Base de Datos & Auth:** Supabase (PostgreSQL).
*   **Pagos:** Stripe (Checkout Sessions & Webhooks).

## 🚀 Funcionalidades Clave y Desarrollo de Interfaz (UI/UX)

### 1. Landing Page y Flujo de Onboarding
Para mejorar la captación y retención de empresas, desarrollé desde cero:
*   **Landing Page:** Creación íntegra de la página de aterrizaje comercial, optimizada para la conversión y presentación del producto.
*   **Onboarding:** Diseño e implementación de un flujo de registro paso a paso, facilitando a las nuevas organizaciones la configuración inicial de su cuenta sin fricciones.

### 2. Ecosistema de Paneles y Gestión de Empleados
Se implementó un rediseño completo de la experiencia de usuario para los administradores:
*   **Dashboard Principal:** Desarrollo de un panel de control totalmente nuevo e intuitivo para visualizar métricas generales y el estado del servicio en tiempo real.
*   **Panel de Empleados Automatizado:** Creación de una interfaz dedicada para registrar nuevos trabajadores y mostrar toda su información laboral y estado de fichajes de forma centralizada.

### 3. Kiosco de Fichaje (Kiosk Mode)
*   Desarrollo de una vista de "Kiosco" diseñada específicamente para que los empleados puedan registrar su entrada y salida de manera rápida, segura y accesible desde un dispositivo físico compartido en la empresa.

## ⚙️ Retos Técnicos y Arquitectura Backend

### 1. Diseño y Gestión Integral de la Base de Datos (Supabase)
*   Fui responsable de diseñar el esquema relacional en PostgreSQL (gestionado a través de Supabase) desde sus cimientos, asegurando la escalabilidad y consistencia de los datos del proyecto.
*   **Seguridad Multi-inquilino (RLS):** Implementé políticas de Row Level Security (RLS) para garantizar a nivel de base de datos que cada usuario autenticado solo pudiera leer y escribir registros asociados a su propia organización, impidiendo fugas de datos entre empresas.

### 2. Gestión de Suscripciones con Stripe Webhooks
*   Se integró Stripe Checkout para la pasarela de pago inicial. Para automatizar los cobros y mantener la base de datos sincronizada, configuré un endpoint en Node.js para escuchar los eventos de Webhooks de Stripe. 
*   *Testing local:* Durante el desarrollo, gestioné las pruebas de los eventos de pago utilizando la CLI de Stripe para asegurar que el sistema actualizaba las suscripciones correctamente antes del paso a producción.

### 3. Orquestación Frontend-Backend
*   Para mantener un código limpio y seguro, la interfaz (Next.js) se comunica con la lógica del servidor a través de Node.js, validando las acciones del usuario antes de interactuar con la base de datos.
