---
titulo: Herramientas principales de la plataforma UiPath
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
  - Herramientas principales de la plataforma UiPath
---
# Herramientas principales de la plataforma Uipath

La plataforma Uipath cuenta con diferentes herramientas que permiten desarrollar, ejecutar, administrar y supervisar automatizaciones.

Entre sus componentes principales se encuentran:

1. `Uipath Studio`: entorno de desarrollo donde se crean las automatizaciones.
2. `Robots`: agentes de ejecución que ejecutan las automatizaciones desarrolladas.
3. `UiPath Orchestrator`: plataforma de administración centralizada que permite gestionar los robots, distribuir automatizaciones y supervisar su ejecución.

Estos tres componentes trabajan conjuntamente para permitir el desarrollo y la ejecución de soluciones RPA.

## 1. UiPath Studio

UiPath Studio es un IDE (Integrated Development Environment o entorno de desarrollo integrado) que permite crear, desarrollar, probar y depurar proyectos de automatización.

Es la herramienta que utilizan los desarrolladores para diseñar los flujos de trabajo que posteriormente ejecutarán los robots.

### Características principales

- **Desarrollo de automatizaciones**: permite construir flujos de trabajo mediante actividades visuales y código.
- **Depuración**: permite identificar y corregir errores durante el desarrollo.
- **Integración con Orchestrator**: permite publicar proyectos de automatización para que puedan almacenarse y distribuirse mediante Orchestrator.
- **Gestión de dependencias**: utiliza paquetes NuGet para incorporar actividades, bibliotecas y componentes necesarios para los proyectos.
### Paquetes NuGet

Un paquete NuGet es un paquete de distribución que contiene código compilado, dependencias y otros recursos necesarios para utilizar una biblioteca o componente de software.

En UiPath, cuando publicamos un proyecto desde Studio, se genera un paquete de automatización con extensión `.nupkg`.

Este paquete puede publicarse en Orchestrator o almacenarse en un repositorio local, dependiendo de la configuración.

Flujo de publicación:

1. El desarrollador crea una automatización en Uipath Studio.
2. Publica el proyecto.
3. Studio genera un paquete `.nupkg`.
4. El paquete se almacena en Orchestrator o en otro destino configurado.
5. Los robots pueden obtener el paquete para ejecutarlo.

### Tipos de Studio

UiPath ofrece diferentes experiencias de desarrollo:

| Herramienta    | Descripción                                                                                                                     |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Studio Web     | Entorno de desarrollo basado en navegador que permite crear automatizaciones sin instalar el Studio de escritorio.              |
| Studio Desktop | Entorno de desarrollo instalado localmente que proporciona capacidades más amplias para desarrollar automatizaciones complejas. |

Studio permite desarrollar automatizaciones que pueden ejecutarse en diferentes modalidades:

- **`Attended`**: automatizaciones que requieren la interacción o participación del usuario.
- **`Unattended`**: automatizaciones que se ejecutan sin intervención directa del usuario.

Importante: Attended y Unattended son modalidades de ejecución, no tipos de proyectos de Studio.

## 2. Robots

Un UiPath Robot es un agente de ejecución que permite ejecutar las automatizaciones desarrolladas y publicadas desde UiPath Studio.

En términos sencillos, Studio permite construir la automatización y el Robot se encarga de ejecutarla.

Los robots ejecutan los paquetes de automatización (`.nupkg`) y utilizan las actividades, bibliotecas y dependencias que estos requieren.

### Tipos de robots

| Tipo de robot    | Descripción                                                                                  | Ejemplo                                                                                          |
| ---------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Attended Robot   | Ejecuta automatizaciones con la participación del usuario.                                   | Un empleado inicia un robot para procesar información mientras trabaja.                          |
| Unattended Robot | Ejecuta automatizaciones sin intervención directa del usuario.                               | Un robot procesa facturas durante la noche.                                                      |
| Test Robot       | Ejecuta pruebas automatizadas para verificar el funcionamiento de aplicaciones y soluciones. | Ejecutar pruebas de regresión para comprobar que una aplicación sigue funcionando correctamente. |

### Automation Cloud Robots

UiPath también ofrece Automation Cloud Robots, un servicio que permite ejecutar automatizaciones utilizando infraestructura proporcionada por UiPath, sin que la organización tenga que administrar directamente las máquinas de ejecución.

Existen dos modalidades principales:

| Tipo                               | Infraestructura                               | Descripción                                                                                    |
| ---------------------------------- | --------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| VM Automation Cloud Robots         | Máquinas virtuales Windows.                   | Proporcionan un entorno de ejecución basado en una máquina virtual Windows.                    |
| Serverless Automation Cloud Robots | Infraestructura administrada basada en Linux. | Permiten ejecutar automatizaciones sin tener que administrar directamente una máquina virtual. |

La principal diferencia es que los robots VM utilizan máquinas virtuales dedicadas para su ejecución, mientras que los Serverless abstraen la administración de la infraestructura subyacente.

### Comunicación entre los robots y Orchestrator

Los robots pueden comunicarse con Orchestrator para recibir instrucciones, obtener paquetes de automatización, informar sobre su estado y enviar información de ejecución.

En esta comunicación intervienen varios conceptos:

A. UiPath Assistant

Es una aplicación de escritorio que permite al usuario interactuar con sus automatizaciones. Desde Assistant puede iniciar, consultar y administrar las automatizaciones disponibles para su usuario.

B. UiPath Robot Service

Es un servicio que forma parte de la infraestructura de ejecución de UiPath y permite gestionar la ejecución de los robots en el equipo.

C. Heartbeat (latido)

Es un mecanismo de comunicación periódica mediante el cual un robot informa a Orchestrator sobre su disponibilidad y estado de conexión.

En tus apuntes se menciona un intervalo de 30 segundos. Es importante entender que el heartbeat es una comunicación periódica de estado, no el mecanismo que ejecuta las automatizaciones.

### ¿Cómo obtiene un robot un paquete de automatización?

Cuando un robot necesita ejecutar una automatización, debe disponer del paquete correspondiente y de sus dependencias.

El flujo general es:

1. El desarrollador publica un proyecto desde Studio.
2. Orchestrator almacena el paquete en su repositorio de procesos, si se utiliza como destino de publicación.
3. Se crea o inicia un trabajo de automatización (Job).
4. El robot obtiene el paquete y la versión correspondiente si todavía no está disponible localmente.
5. El robot prepara el entorno de ejecución.
6. Ejecuta la automatización.
7. Envía información sobre el resultado y los registros de ejecución.

Conceptos importantes:

| Concepto | Definición                                                                  |
| -------- | --------------------------------------------------------------------------- |
| Package  | Paquete que contiene la automatización publicada.                           |
| Process  | Automatización publicada y configurada para su ejecución.                   |
| Job      | Instancia de ejecución de un proceso.                                       |
| Robot    | Agente que ejecuta la automatización.                                       |
| Trigger  | Disparador que permite iniciar una ejecución bajo determinadas condiciones. |

## 3. UiPath Orchestrator

UiPath Orchestrator es una aplicación web que permite administrar, controlar y supervisar centralizadamente los robots y las automatizaciones de una organización.

Es uno de los componentes principales de la plataforma porque permite coordinar la ejecución de las automatizaciones y gestionar los recursos necesarios para su funcionamiento.

Con Orchestrator podemos:

- Implementar y distribuir automatizaciones.
- Administrar robots y recursos de ejecución.
- Gestionar licencias, usuarios y permisos.
- Programar y ejecutar automatizaciones.
- Supervisar los trabajos de los robots.
- Consultar registros de ejecución (Logs).
- Administrar credenciales y otros recursos.
- Controlar la ejecución de procesos empresariales.

Además, funciona como repositorio de paquetes de automatización, bibliotecas y otros recursos utilizados por los robots.

### Principales capacidades de Orchestrator

| Capacidad                  | Descripción                                                                                                        |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Provisioning               | Permite configurar y administrar los recursos de ejecución y las conexiones de los robots.                         |
| License Management         | Permite administrar y asignar licencias según los permisos y necesidades de la organización.                       |
| User and Access Management | Gestiona usuarios, roles, permisos y acceso a los recursos mediante carpetas.                                      |
| Package Management         | Almacena y distribuye paquetes de automatización y bibliotecas.                                                    |
| Asset Management           | Permite almacenar y administrar recursos utilizados por las automatizaciones, como configuraciones y credenciales. |
| Job Management             | Permite iniciar, detener y administrar las ejecuciones de los procesos.                                            |
| Queues                     | Permite gestionar elementos de trabajo que los robots procesan de manera organizada.                               |
| Triggers                   | Permite iniciar automatizaciones automáticamente según horarios o condiciones configuradas.                        |
| Monitoring                 | Permite supervisar robots, trabajos y registros de ejecución.                                                      |

### Conceptos importantes de Orchestrator

A. Provisioning

Es el proceso de preparar y configurar los recursos necesarios para ejecutar automatizaciones.

Por ejemplo, configurar una máquina para que pueda conectarse a Orchestrator y ejecutar procesos.

B. Assets

Son recursos compartidos que pueden utilizar las automatizaciones.

Ejemplos:

- URL de una aplicación.
- Nombre de una carpeta.
- Parámetros de configuración.
- Credenciales de acceso.

Esto permite centralizar información sin tener que escribirla directamente en cada automatización.

C. Queues (Colas)

Son estructuras que permiten almacenar y administrar elementos de trabajo que deben ser procesados por los robots.

Por ejemplo, una empresa recibe 1.000 facturas y necesita procesarlas.

En lugar de crear una ejecución independiente para cada factura, puede registrar las facturas como elementos de una cola y distribuir su procesamiento entre varios robots.

D. Triggers (Disparadores)

Permiten iniciar automáticamente la ejecución de un proceso cuando se cumple una condición determinada.

Por ejemplo:

- Ejecutar un proceso todos los días a las 8:00 a. m.
- Ejecutar un proceso cada hora.
- Iniciar un proceso cuando se cumplan determinadas condiciones de ejecución.

E. Jobs (Trabajos)

Un Job representa una ejecución concreta de un proceso de automatización.

Por ejemplo, si un proceso de generación de informes se ejecuta tres veces, tendremos tres ejecuciones o Jobs independientes.

F. Logs (Registros)

Son registros que almacenan información sobre lo que sucede durante la ejecución de una automatización.

Permiten:

- Identificar errores.
- Consultar las actividades realizadas.
- Investigar problemas.
- Supervisar el comportamiento de los robots.

## 4. ¿Cómo trabajan juntos Studio, Robot y Orchestrator?

Esta es una de las relaciones más importantes que debes comprender.

| Componente   | Responsabilidad                                        | Pregunta que responde                       |
| ------------ | ------------------------------------------------------ | ------------------------------------------- |
| Studio       | Crear y publicar automatizaciones.                     | ¿Cómo construimos la automatización?        |
| Robot        | Ejecutar automatizaciones.                             | ¿Quién ejecuta la automatización?           |
| Orchestrator | Administrar, distribuir y supervisar automatizaciones. | ¿Quién coordina y controla las ejecuciones? |

### Ejemplo de funcionamiento

Imagina que desarrollas una automatización para procesar facturas:

```
       DESARROLLADOR
             |
             ▼
       UIPATH STUDIO
             |
       Crea el proyecto
             |
       Publica el proyecto
             |
             ▼
        PAQUETE NUPKG
             |
             ▼
      UIPATH ORCHESTRATOR
             |
      Almacena el paquete
             |
      Crea o inicia un Job
             |
             ▼
        UIPATH ROBOT
             |
      Descarga el paquete
      si es necesario
             |
      Ejecuta la automatización
             |
             ▼
        RESULTADO
             |
      Envía información
      y registros a Orchestrator
```

### Diferencia entre Robot Service y Robot Executor

Un detalle adicional: el Robot no es simplemente un único programa. Está compuesto por diferentes componentes.

| Componente                   | Función                                                                                    |
| ---------------------------- | ------------------------------------------------------------------------------------------ |
| Robot Service                | Administra la conexión con Orchestrator, las sesiones y la comunicación entre componentes. |
| Robot Executor               | Ejecuta las actividades y los flujos de trabajo de la automatización.                      |
| Command Line Interface (CLI) | Permite controlar y ejecutar automatizaciones mediante comandos.                           |

## 5. Resumen general para estudiar

| Herramienta             | Concepto clave                            | Función principal                                                                |
| ----------------------- | ----------------------------------------- | -------------------------------------------------------------------------------- |
| UiPath Studio           | IDE                                       | Desarrollar automatizaciones.                                                    |
| UiPath Robot            | Agente de ejecución                       | Ejecutar automatizaciones.                                                       |
| Robot Service           | Servicio de comunicación y administración | Mantener la conexión y gestionar la ejecución.                                   |
| Robot Executor          | Motor de ejecución                        | Ejecutar las actividades del workflow.                                           |
| UiPath Assistant        | Aplicación de escritorio                  | Permitir al usuario interactuar con los robots.                                  |
| UiPath Orchestrator     | Administración centralizada               | Gestionar robots, paquetes, procesos, Jobs y recursos.                           |
| Automation Cloud Robots | Infraestructura administrada              | Ejecutar automatizaciones sin administrar directamente los equipos de ejecución. |

## 6. Fuentes oficiales para profundizar

- [UiPath Studio - Publicación de proyectos](https://docs.uipath.com/es/studio/standalone/2026.10/user-guide/about-publishing-automation-projects?utm_source=chatgpt.com)
- [UiPath Robot - Robot Service](https://docs.uipath.com/robot/standalone/latest/admin-guide/service?utm_source=chatgpt.com)
- [UiPath Robot - Componentes](https://docs.uipath.com/robot/standalone/latest/admin-guide/robot-components?utm_source=chatgpt.com)
- [UiPath - Cloud Robots](https://docs.uipath.com/robot/automation-cloud/latest/user-guide/about-cloud-robots?utm_source=chatgpt.com)

Idea fundamental que debes recordar:

Studio desarrolla, Robot ejecuta y Orchestrator administra y coordina.

Esta relación es la base para comprender cómo funciona la arquitectura de automatización de UiPath.