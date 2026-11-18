---
titulo: Plataforma Uipath
tipo: concepto
nivel: 🌱
estado: activo
fecha_creacion: 2026-11-17
ultimo_repaso: 2026-11-17
frecuencia_repaso: 1
nivel_dominio: bajo
tags:
  - software
  - automatizacion
aliases:
  - Plataforma Uipath
---
# Plataforma Uipath

La plataforma de Uipath organiza sus capacidades y herramientas en tres grandes categorías: `Discover`, `Automate` y `Operate`.

Estas categorías representan las diferentes etapas del ciclo de vida de un programa de automatización empresarial:

1. `Discover (Descubrir)`: identificar qué procesos y actividades se pueden automatizar.
2. `Automate (Automatizar)`: diseñar, desarrollar e implementar las automatizaciones.
3. `Operate (Operar)`: ejecutar, administrar, supervisar y optimizar las automatizaciones.
    
## 1. `Discover `(Descubrir)

Esta categoría proporciona herramientas para identificar oportunidades de automatización y determinar qué procesos pueden mejorarse.

Su objetivo es descubrir cómo funciona una organización, identificar actividades repetitivas y encontrar oportunidades de mejora que generen valor empresarial.

|Herramienta|Descripción|¿Para qué sirve?|
|---|---|---|
|Process Mining|Analiza los procesos de negocio utilizando datos registrados en los sistemas empresariales.|Identificar cómo se ejecutan realmente los procesos, detectar cuellos de botella, desviaciones e ineficiencias.|
|Task Mining|Obtiene una visión objetiva y basada en datos de las actividades que realizan las personas en sus escritorios.|Identificar tareas repetitivas y oportunidades de automatización mediante el análisis de las interacciones con las aplicaciones.|
|Communications Mining|Analiza comunicaciones empresariales, como correos electrónicos y mensajes.|Identificar información relevante, clasificar solicitudes y descubrir oportunidades para automatizar la gestión de comunicaciones.|
|Idea Capture & Management|Centraliza las ideas de automatización y mejora de procesos.|Recopilar, evaluar y priorizar oportunidades según criterios como impacto, viabilidad y ROI.|

### Diferencia entre `Process Mining` y `Task Mining`

Aunque ambas herramientas permiten descubrir oportunidades de automatización, analizan aspectos diferentes:

|Característica|Process Mining|Task Mining|
|---|---|---|
|Enfoque|Procesos empresariales.|Actividades individuales.|
|Fuente de información|Registros de eventos (event logs) de los sistemas.|Datos de las interacciones de los usuarios con sus aplicaciones.|
|Analiza|El recorrido de un proceso entre diferentes sistemas y actividades.|Cómo las personas realizan determinadas tareas en sus equipos.|
|Objetivo|Encontrar ineficiencias en los procesos completos.|Encontrar tareas repetitivas que puedan automatizarse.|
|Ejemplo|Analizar el proceso de aprobación de facturas.|Analizar cómo un empleado abre facturas, copia datos y los registra en un ERP.|

Ejemplo para comprenderlo:

Imagina que una empresa tiene un proceso de gestión de facturas.

- `Process Mining`: permite analizar el proceso completo desde que se recibe una factura hasta que se realiza el pago.
- `Task Mining`: permite analizar cómo un empleado realiza determinadas actividades dentro de ese proceso, como descargar documentos, copiar información y registrarla en un sistema.
    
## 2. Automate (Automatizar)

Esta categoría proporciona herramientas para desarrollar automatizaciones y aplicaciones empresariales, permitiendo que personas y robots trabajen conjuntamente.

Su objetivo es transformar las oportunidades identificadas durante la etapa Discover en soluciones de automatización.

|Herramienta|Descripción|¿Para qué sirve?|
|---|---|---|
|Low-code Development|Permite desarrollar aplicaciones empresariales y automatizaciones mediante herramientas visuales y una cantidad reducida de código.|Facilitar el desarrollo de soluciones sin necesidad de programar todo desde cero.|
|UI & API Automation|Permite automatizar aplicaciones mediante interfaces gráficas (UI) o interfaces de programación (API).|Interactuar con aplicaciones, consultar información y ejecutar operaciones automáticamente.|
|Process Orchestration|Coordina la ejecución de procesos y la colaboración entre personas, robots y sistemas.|Organizar actividades, distribuir tareas y gestionar la interacción entre humanos y robots.|
|Intelligent Document Processing (IDP)|Utiliza inteligencia artificial para interpretar, clasificar y extraer información de documentos.|Automatizar el procesamiento de facturas, contratos, formularios y otros documentos.|
|NLP & AI/ML|Utiliza procesamiento del lenguaje natural (NLP), inteligencia artificial (AI) y aprendizaje automático (ML).|Permitir que las automatizaciones comprendan lenguaje, clasifiquen información y realicen tareas más sofisticadas.|

### Conceptos importantes

A. `UI Automation` (Automatización de interfaz de usuario)
Consiste en automatizar la interacción con las aplicaciones mediante sus elementos visuales.

Por ejemplo:

- Hacer clic en botones.
- Escribir información en campos de texto.
- Seleccionar opciones.
- Leer información de una pantalla.
    
B. `API Automation` (Automatización mediante API)

Consiste en interactuar directamente con las funcionalidades y los datos de una aplicación mediante una API (Application Programming Interface).

Por ejemplo:

- Consultar información de clientes.
- Crear registros.
- Actualizar datos.
- Enviar solicitudes a otros sistemas.
    
La diferencia principal es que `UI Automation` interactúa con la interfaz gráfica, mientras que `API Automation` se comunica directamente con los servicios que proporciona una aplicación.

C. `Intelligent Document Processing` (IDP)

Es el procesamiento inteligente de documentos mediante tecnologías de inteligencia artificial.

Por ejemplo, una automatización puede recibir una factura en PDF, identificar su número, fecha, proveedor y valor total, y extraer esos datos para registrarlos en un sistema empresarial.

## 3. `Operate `(Operar)

Esta categoría proporciona herramientas para ejecutar, administrar, supervisar y optimizar un programa de automatización a escala empresarial.

Su objetivo es garantizar que las automatizaciones funcionen correctamente, sean confiables y puedan administrarse de manera centralizada.

|Herramienta|Descripción|¿Para qué sirve?|
|---|---|---|
|Analytics|Proporciona información operativa y empresarial sobre el programa de automatización.|Medir resultados, analizar el rendimiento y evaluar el impacto de las automatizaciones.|
|Continuous Testing|Permite probar y supervisar continuamente las automatizaciones y las aplicaciones de las que dependen.|Detectar errores y garantizar la calidad y confiabilidad de las soluciones.|
|Unified Management & Governance|Permite administrar y gobernar centralmente la plataforma y el programa de automatización.|Gestionar usuarios, permisos, recursos, políticas y controles de seguridad.|
|Flexible Deployment|Ofrece diferentes alternativas para implementar y alojar la plataforma.|Adaptar el despliegue de UiPath a las necesidades y la infraestructura de cada organización.|

### Flexible Deployment

Existen dos modalidades principales:

|Modalidad|Descripción|Característica|
|---|---|---|
|SaaS (Software as a Service)|La plataforma se proporciona como un servicio alojado y administrado por el proveedor.|La organización utiliza los servicios sin tener que administrar toda la infraestructura subyacente.|
|Self-hosted|La organización aloja y administra la plataforma en su propia infraestructura.|Tiene mayor responsabilidad sobre la infraestructura, configuración y mantenimiento.|

## 4. Resumen general de la plataforma Uipath

Las tres categorías se complementan y representan diferentes etapas de un programa de automatización.

|Categoría|Pregunta que responde|Objetivo principal|
|---|---|---|
|Discover|¿Qué podemos automatizar?|Identificar oportunidades de automatización.|
|Automate|¿Cómo podemos automatizarlo?|Desarrollar e implementar soluciones.|
|Operate|¿Cómo administramos y mejoramos las automatizaciones?|Ejecutar, supervisar y optimizar las soluciones.|

### Flujo conceptual

```
DISCOVER
   │
   ├── Process Mining
   ├── Task Mining
   ├── Communications Mining
   └── Idea Capture & Management
          │
          ▼
AUTOMATE
   │
   ├── Low-code Development
   ├── UI & API Automation
   ├── Process Orchestration
   ├── Intelligent Document Processing
   └── NLP & AI/ML
          │
          ▼
OPERATE
   │
   ├── Analytics
   ├── Continuous Testing
   ├── Unified Management & Governance
   └── Flexible Deployment
```

## 5. Ejemplo práctico: automatización del procesamiento de facturas

Imaginemos una empresa que quiere automatizar la recepción y el registro de facturas.

|Etapa|Herramienta|Aplicación|
|---|---|---|
|Discover|Process Mining|Analizar el proceso actual de recepción y aprobación de facturas.|
|Discover|Task Mining|Identificar las tareas manuales que realizan los empleados.|
|Discover|Idea Capture & Management|Registrar y priorizar la oportunidad de automatización.|
|Automate|Intelligent Document Processing|Extraer los datos de las facturas.|
|Automate|UI & API Automation|Registrar la información en el sistema empresarial.|
|Automate|Process Orchestration|Coordinar las aprobaciones entre empleados y robots.|
|Operate|Analytics|Medir el tiempo ahorrado y el rendimiento.|
|Operate|Continuous Testing|Comprobar que la automatización siga funcionando correctamente.|
|Operate|Unified Management & Governance|Administrar permisos y supervisar los robots.|

## 6. Conceptos que debes recordar

- `Discover`: descubrir oportunidades de automatización.
- `Automate`: desarrollar soluciones de automatización.
- `Operate`: administrar y optimizar las soluciones implementadas.
- `Process Mining`: analiza procesos completos mediante registros de eventos.
- `Task Mining`: analiza las actividades individuales realizadas por los usuarios.
- `UI Automation`: automatiza las interacciones con interfaces gráficas.
- `API Automation`: automatiza la comunicación con aplicaciones mediante sus interfaces de programación.
- `IDP`: utiliza inteligencia artificial para comprender y procesar documentos.
- `Process Orchestration`: coordina personas, robots y sistemas para ejecutar procesos.
- `SaaS`: plataforma proporcionada como servicio.
- `Self-hosted`: plataforma alojada y administrada por la propia organización.

> [!tip] Idea clave:
> UiPath no es solamente una herramienta para crear robots RPA. Es una plataforma que permite descubrir oportunidades, desarrollar automatizaciones y administrar todo un programa de automatización empresarial.

