---
titulo: Tipos de flujos en UiPath
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
  - Tipos de flujos en UiPath
---
# Tipos de flujos en UiPath

Uipath Studio ofrece tres tipos principales de flujos de trabajo (Workflows): Sequence, Flowchart y State Machine. Cada uno permite organizar las actividades de una automatización, pero se diferencian en la forma de controlar el orden de ejecución y gestionar las decisiones.

## 1. `Sequence` (Secuencia)

Una `Sequence` es un flujo de trabajo en el que las actividades se ejecutan de manera secuencial, es decir, una después de otra, siguiendo el orden establecido.

Es adecuada para automatizaciones sencillas o procesos que tienen una estructura lineal y pocas decisiones.

Características:

- Las actividades se ejecutan siguiendo un orden definido.
- Permite organizar actividades dentro de otras secuencias.
- Puede contener condiciones, ciclos y otras estructuras de control; no está limitada exclusivamente a procesos lineales.
- Es fácil de crear, leer y mantener cuando el proceso es sencillo.
    
Ejemplo: Abrir Excel, leer un archivo, procesar los datos, guardar los resultados y cerrar Excel.

## 2. Flowchart (Diagrama de flujo)

Un Flowchart permite representar visualmente el proceso mediante actividades conectadas entre sí. Su principal ventaja es que facilita la comprensión de procesos con múltiples decisiones, ramificaciones y caminos de ejecución.

Características:

- Permite visualizar el flujo de ejecución mediante conexiones.
- Facilita la implementación de decisiones y ramificaciones.
- Permite que el proceso avance por diferentes caminos según las condiciones.
- Puede contener secuencias y otras actividades dentro de sus bloques.
- Es útil cuando existen múltiples caminos posibles para completar un proceso.
    
Ejemplo: Leer una factura y comprobar su importe:

- Si el importe es correcto, aprobar la factura.
- Si el importe es incorrecto, enviarla a revisión.
- Si faltan datos, solicitar información adicional.

## 3. State Machine (Máquina de estados)

Una State Machine organiza la automatización en diferentes estados. Cada estado representa una situación o etapa en la que puede encontrarse el proceso.

La automatización cambia de un estado a otro mediante transiciones, que pueden depender de condiciones o eventos.

Características:

- El proceso se divide en estados claramente definidos.
- Las transiciones determinan cuándo y cómo se pasa de un estado a otro.
- Permite regresar a estados anteriores si el proceso lo requiere.
- Facilita la gestión de procesos complejos con diferentes etapas y condiciones.
- Es especialmente útil cuando el proceso depende de eventos o puede permanecer en un estado hasta que ocurra algo.
    
Ejemplo: Procesamiento de una solicitud:

1. Recibida: el robot recibe la solicitud.
2. Validación: comprueba que la información esté completa.
3. Aprobada: la solicitud cumple los requisitos.
4. Rechazada: la solicitud no cumple los requisitos.
5. Pendiente de información: faltan datos y debe esperar una respuesta.
    
Una solicitud pendiente podría regresar al estado de validación cuando reciba la información faltante.

## 4. Tabla comparativa

|Característica|Sequence|Flowchart|State Machine|
|---|---|---|---|
|Organización|Actividades consecutivas|Actividades conectadas visualmente|Estados y transiciones|
|Complejidad habitual|Baja|Media|Media o alta|
|Decisiones|Sí|Sí, con ramificaciones visuales|Sí, mediante transiciones|
|Regresar a etapas anteriores|Posible mediante estructuras de control|Sí, mediante conexiones|Sí, mediante transiciones|
|Mejor aplicación|Procesos lineales|Procesos con varios caminos|Procesos basados en estados|

## 5. ¿Cómo elegir el tipo de flujo?

|Situación|Tipo recomendado|
|---|---|
|Ejecutar una serie de pasos en orden|Sequence|
|Tomar decisiones y seguir diferentes caminos|Flowchart|
|Gestionar un proceso con diferentes estados y transiciones|State Machine|

Importante: No son excluyentes. Puedes combinar estos tipos de flujos. Por ejemplo, una State Machine puede contener Flowcharts y Sequences dentro de sus estados.

## 6. Diferencia conceptual importante

No confundas estos tres conceptos:

- Sequence: representa el orden de ejecución de las actividades.
- Flowchart: representa las rutas que puede seguir la ejecución.
- State Machine: representa las situaciones en las que puede encontrarse el proceso y las transiciones entre ellas.

Una forma sencilla de recordarlo:

- Sequence = ¿Qué hago primero y qué hago después?
- Flowchart = ¿Qué camino debo seguir según la decisión?
- State Machine = ¿En qué estado estoy y a cuál puedo pasar?