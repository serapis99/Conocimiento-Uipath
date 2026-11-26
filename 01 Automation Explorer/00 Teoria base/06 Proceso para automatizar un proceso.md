---
titulo: Proceso para automatizar un proceso
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
  - Proceso para automatizar un proceso
---
# Proceso para automatizar un proceso

Para automatizar un proceso empresarial mediante RPA, se recomienda seguir una serie de etapas que permiten comprender el proceso actual, identificar oportunidades de mejora, diseñar la solución y finalmente desarrollar la automatización.

El objetivo es evitar comenzar a desarrollar una automatización sin conocer previamente cómo funciona el proceso, qué problemas presenta y cuál debería ser el resultado esperado.

## 1. Etapas del proceso de automatización

### 1.1. Crear el diagrama AS-IS (situación actual)

El AS-IS representa cómo se ejecuta actualmente un proceso dentro de una organización.

Su propósito es documentar el funcionamiento real del proceso antes de implementar cualquier automatización.

Permite identificar:

- Actividades realizadas por los empleados.
- Aplicaciones y sistemas utilizados.
- Decisiones que se toman durante el proceso.
- Entradas y salidas de información.
- Problemas, errores y cuellos de botella.
- Actividades repetitivas que podrían automatizarse.

>[!Example] Ejemplo: 
>Documentar cómo un empleado recibe una factura, verifica sus datos, registra la información en un ERP y solicita su aprobación.

### 1.2. Crear el diagrama TO-BE (situación futura)

El TO-BE representa cómo debería funcionar el proceso después de implementar las mejoras propuestas.

Su propósito es diseñar el proceso futuro, considerando las oportunidades de optimización y automatización identificadas durante el análisis del AS-IS.

Permite definir:

- Qué actividades se automatizarán.
- Qué actividades seguirán siendo realizadas por personas.
- Cómo interactuarán los robots con los sistemas.
- Qué decisiones tomará el robot.
- Cómo se manejarán los errores y las excepciones.
- Qué resultados se esperan obtener.

>[!Example] Ejemplo:
>El robot recibe las facturas, extrae automáticamente la información, valida los datos y registra las facturas en el ERP. Si encuentra una inconsistencia, solicita la intervención de un empleado.

### Diferencia entre AS-IS y TO-BE

| Característica | AS-IS                                            | TO-BE                                                |
| -------------- | ------------------------------------------------ | ---------------------------------------------------- |
| Significado    | Situación actual.                                | Situación futura.                                    |
| Objetivo       | Documentar cómo funciona el proceso actualmente. | Diseñar cómo debería funcionar el proceso.           |
| Enfoque        | Comprender el proceso existente.                 | Mejorar y optimizar el proceso.                      |
| Automatización | No presupone automatización.                     | Incorpora las mejoras y automatizaciones propuestas. |
| Resultado      | Diagrama del proceso actual.                     | Diagrama del proceso propuesto.                      |

### 1.3. Aprobación de los diagramas

Una vez elaborados los diagramas AS-IS y TO-BE, deben revisarse y aprobarse por las personas responsables del proceso.

El propósito es garantizar que:

- El AS-IS representa correctamente la situación actual.
- El TO-BE refleja las mejoras esperadas.
- Las actividades y responsabilidades están correctamente identificadas.
- Los participantes están de acuerdo con el funcionamiento futuro.

Esta aprobación permite establecer una base común antes de continuar con la documentación y el desarrollo.

### 1.4. Crear el PDD (Process Definition Document)

El PDD (Process Definition Document) es el documento que describe detalladamente el proceso empresarial que se desea automatizar.

Su propósito es proporcionar una definición clara del proceso, sus actividades, reglas de negocio, excepciones y requisitos.

Generalmente incluye:

- Descripción y objetivo del proceso.
- Alcance de la automatización.
- Aplicaciones y sistemas utilizados.
- Entradas y salidas.
- Reglas de negocio.
- Descripción de las actividades.
- Excepciones y posibles errores.
- Volumen y frecuencia de ejecución.
- Responsables del proceso.

>[!Example] Ejemplo:
>documentar las reglas que debe seguir el robot para validar una factura, incluyendo qué hacer cuando falta el número de factura o cuando el importe no coincide.

### 1.5. Crear el SDD (Solution Design Document), si es necesario

El SDD (Solution Design Document) es el documento que describe cómo se implementará técnicamente la solución de automatización.

Mientras el PDD explica qué hace el proceso y cuáles son sus reglas de negocio, el SDD explica cómo se construirá la solución tecnológica.

Generalmente incluye:

- Arquitectura de la solución.
- Diseño de los workflows.
- Componentes y actividades de UiPath que se utilizarán.
- Integraciones con aplicaciones y APIs.
- Gestión de datos y credenciales.
- Manejo de excepciones.
- Estrategia de registro de logs.
- Configuración de Orchestrator.
- Requisitos de infraestructura y seguridad.

Ejemplo: definir que el robot utilizará UiPath Studio, extraerá información de facturas mediante actividades de procesamiento de documentos y registrará los datos en el ERP mediante una API.

### Diferencia entre PDD y SDD

| Característica     | PDD                                                       | SDD                                                   |
| ------------------ | --------------------------------------------------------- | ----------------------------------------------------- |
| Nombre             | Process Definition Document.                              | Solution Design Document.                             |
| Enfoque            | Proceso de negocio.                                       | Solución técnica.                                     |
| Pregunta principal | ¿Qué debe hacer el proceso?                               | ¿Cómo se implementará la automatización?              |
| Contenido          | Actividades, reglas de negocio, excepciones y requisitos. | Arquitectura, workflows, componentes e integraciones. |
| Orientado a        | Comprender y definir el proceso.                          | Diseñar la solución tecnológica.                      |

### 1.6. Aprobación del PDD

Una vez elaborado el PDD, debe revisarse y aprobarse por los responsables del proceso y las partes interesadas.

Su propósito es confirmar que la documentación refleja correctamente los requisitos y las reglas de negocio.

La aprobación permite establecer una referencia formal para el desarrollo de la automatización.

Importante: el PDD debe estar aprobado antes de comenzar el desarrollo. Si se necesita un SDD, también debe revisarse y aprobarse según el procedimiento de gobierno del proyecto.

### 1.7. Comenzar el desarrollo de la automatización

Una vez completadas las etapas anteriores, comienza el desarrollo de la solución.

Los desarrolladores utilizan el PDD y, cuando existe, el SDD como referencia para construir los workflows en UiPath Studio.

Esta etapa puede incluir:

1. Configurar el proyecto de UiPath.
2. Desarrollar los workflows.
3. Implementar las reglas de negocio.
4. Configurar las interacciones con las aplicaciones.
5. Implementar el manejo de excepciones.
6. Realizar pruebas de funcionamiento.
7. Publicar el paquete de automatización.
8. Configurar la ejecución en Orchestrator, cuando corresponda.

## 2. Diagrama general del proceso

```
       INICIO
          |
          v
   Crear diagrama AS-IS
          |
          v
   Crear diagrama TO-BE
          |
          v
   Aprobar los diagramas
          |
          v
      Crear PDD
          |
          v
 ¿Se necesita un SDD?
       /       \
     Sí         No
     |           |
     v           |
  Crear SDD      |
     |           |
     v           |
 Revisar diseño  |
     |           |
     +-----+-----+
           |
           v
     Aprobar PDD
           |
           v
  Desarrollar automatización
           |
           v
          FIN
```

>[!note] Nota: 
>El SDD es un documento condicional. En proyectos que lo requieren, debe completarse y aprobarse antes de implementar la solución.

## 3. Resumen de las etapas

| Orden | Etapa                   | Resultado esperado                                 |
| ----- | ----------------------- | -------------------------------------------------- |
| 1     | AS-IS                   | Documentación del proceso actual.                  |
| 2     | TO-BE                   | Diseño del proceso futuro.                         |
| 3     | Aprobación de diagramas | Validación del proceso actual y propuesto.         |
| 4     | PDD                     | Definición detallada del proceso y sus requisitos. |
| 5     | SDD (si es necesario)   | Diseño técnico de la solución.                     |
| 6     | Aprobación del PDD      | Validación formal de los requisitos del proceso.   |
| 7     | Desarrollo              | Construcción de la automatización en UiPath.       |

## 4. Conceptos fundamentales que debes recordar

- AS-IS: cómo funciona actualmente el proceso.
- TO-BE: cómo debería funcionar el proceso después de las mejoras.
- PDD: define qué debe hacer el proceso que se quiere automatizar.
- SDD: define cómo se construirá técnicamente la solución.
- Aprobación: permite validar que los responsables están de acuerdo con el proceso y sus requisitos.
- Desarrollo: consiste en implementar la solución de automatización utilizando herramientas como UiPath Studio.

>[!tip] Idea clave: 
>Antes de automatizar, primero debemos comprender el proceso; después, diseñar cómo queremos que funcione y documentar sus requisitos. Solo entonces debemos comenzar a desarrollar la solución.

