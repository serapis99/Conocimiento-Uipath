---
titulo: Condicionales IF en UiPath
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
  - Condicionales IF en UiPath
---
# Condicionales IF en UiPath

Las estructuras condicionales permiten que una automatización tome decisiones durante su ejecución. Dependiendo de si una condición se cumple o no, el flujo puede seguir diferentes caminos.

En UiPath debemos distinguir entre las actividades disponibles en los distintos tipos de workflows, especialmente `Sequence` y `Flowchart`.

## 1. IF en Sequences (Secuencias)

En un workflow de tipo `Sequence` podemos utilizar las actividades `If` y `Switch` para controlar las decisiones. La actividad `If` permite evaluar una condición y ejecutar un bloque de actividades dependiendo del resultado.

### Actividad If

La actividad `If` tiene dos ramas:

- Then: se ejecuta cuando la condición es verdadera (`True`).
- Else: se ejecuta cuando la condición es falsa (`False`).
    
Ejemplo:

Imagina que tenemos una variable `Edad` y queremos comprobar si una persona es mayor de edad.

```vb
Edad >= 18
```

|Condición|Rama ejecutada|
|---|---|
|`True`|Then: Mostrar "Mayor de edad".|
|`False`|Else: Mostrar "Menor de edad".|

![Pasted image 20261019214811](Adjuntos/Pasted%20image%2020261019214811.png)

### Else If

Cuando necesitamos evaluar varias condiciones, podemos utilizar una estructura `If` con condiciones adicionales mediante `Else If`.

Por ejemplo, queremos clasificar una calificación:

```
If Nota >= 90
    "Excelente"
Else If Nota >= 70
    "Aprobado"
Else
    "Reprobado"
```

El comportamiento sería:

|Condición|Resultado|
|---|---|
|`Nota >= 90`|Excelente|
|`Nota >= 70`|Aprobado|
|Ninguna de las anteriores|Reprobado|

>[!important] Importante: 
>Las condiciones se evalúan en orden. Cuando una condición resulta verdadera, se ejecuta su rama y no se evalúan las siguientes.

En UiPath, puedes construir esta lógica mediante actividades `If` anidadas o utilizando una actividad `If` con ramas adicionales, según las opciones disponibles en tu versión de Studio.

## 2. Condition en Flowcharts (Diagramas de flujo)

En un workflow de tipo `Flowchart`, la actividad utilizada para tomar decisiones es `Flow Decision`, que permite evaluar una condición y dividir el flujo en dos caminos.

Esta actividad tiene dos conexiones de salida:

- True: se sigue cuando la condición es verdadera.
- False: se sigue cuando la condición es falsa.
    
Ejemplo:

Queremos comprobar si una factura supera los 1.000.000:

```vb
InvoiceAmount > 1000000
```

|Resultado|Camino|
|---|---|
|True|Enviar factura a aprobación especial.|
|False|Continuar con el proceso normal.|

![Pasted image 20261019215039](Adjuntos/Pasted%20image%2020261019215039.png)

Importante sobre las conexiones: En UiPath Flowchart, al conectar las salidas de `Flow Decision`, debes identificar cuál corresponde a `True` y cuál a `False`. 

## 3. Diferencias entre If y Flow Decision

|Característica|If (Sequence)|Flow Decision (Flowchart)|
|---|---|---|
|Tipo de workflow|Sequence|Flowchart|
|Propósito|Evaluar una condición|Evaluar una condición|
|Resultado|True o False|True o False|
|Ramas|Then y Else|True y False|
|Organización|Bloques de actividades|Conexiones visuales|
|Uso habitual|Decisiones dentro de una secuencia|Decisiones que determinan rutas del diagrama|

## 4. Concepto clave para recordar

Ambas actividades realizan esencialmente la misma operación lógica: evaluar una condición y decidir qué camino seguir.

La diferencia está en cómo se representa y organiza el flujo:

- Sequence: utiliza `If`, con ramas `Then` y `Else`.
- Flowchart: utiliza `Flow Decision`, con conexiones `True` y `False`.