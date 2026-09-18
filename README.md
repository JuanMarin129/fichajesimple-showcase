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

### 1. Ecosistema de Paneles y Gestión de Empleados
Se implementó un rediseño completo de la experiencia de usuario para los administradores:
*   **Dashboard Principal:** Desarrollo de un panel de control totalmente nuevo e intuitivo para visualizar métricas generales y el estado del servicio en tiempo real.

![Dashboard Principal de FichajeSimple](dashboard-hero.jpg)

*   **Panel de Empleados Automatizado e Informes:** Creación de una interfaz dedicada para registrar nuevos trabajadores, gestionar estados y generar los documentos legales listos para descargar.

![Panel de Informes y Descargas PDF](informes_02.jpg)

### 2. Kiosco de Fichaje (Kiosk Mode)
*   Desarrollo de una vista de "Kiosco" diseñada específicamente para que los empleados puedan registrar su entrada y salida de manera rápida y segura. El sistema calcula automáticamente los tiempos y categoriza los motivos de pausa.

![Historial de Fichajes y Kiosco](fichajes_03.jpg)

## ⚙️ Retos Técnicos y Arquitectura Backend

### 1. Diseño y Gestión Integral de la Base de Datos (Supabase)
*   Fui responsable de diseñar el esquema relacional en PostgreSQL desde sus cimientos, asegurando la escalabilidad y consistencia de los datos.
*   **Seguridad Multi-inquilino (RLS):** Implementé políticas de Row Level Security (RLS) para garantizar que los asesores y administradores solo pudieran gestionar sus propias empresas vinculadas, impidiendo fugas de datos.

![Panel de Asesorías - Ecosistema Multi-tenant](asesorias_fichaje_simple_01.jpg)
*(Vista del panel de asesorías gestionando múltiples empresas de forma aislada gracias a RLS)*

### 2. Gestión de Suscripciones con Stripe Webhooks
*   Se integró Stripe Checkout para la pasarela de pago inicial. Para automatizar los cobros y mantener la base de datos sincronizada, configuré un endpoint en Node.js para escuchar los eventos de Webhooks de Stripe. 
*   *Testing local:* Durante el desarrollo, gestioné las pruebas de los eventos de pago utilizando la CLI de Stripe (`stripe listen --forward-to localhost:3000/api/webhooks/stripe`) para asegurar que el sistema actualizaba las suscripciones correctamente antes del paso a producción.

### 3. Orquestación Frontend-Backend
*   Para mantener un código limpio y seguro, la interfaz (Next.js) se comunica con la lógica del servidor a través de Node.js, validando las acciones del usuario antes de interactuar con la base de datos.
