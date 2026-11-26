---
titulo: Bucle While en UiPath
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
  - Bucle While en UiPath
---
# Bucle While en UiPath

Un bucle (`Loop`) es una estructura de control que permite repetir un conjunto de actividades mientras se cumpla una condición.

En UiPath, la forma de implementar un bucle `While` depende del tipo de workflow que estemos utilizando: `Sequence` o `Flowchart`.

## 1. While en Sequences (Secuencias)

En un workflow de tipo `Sequence` utilizamos la actividad While.

Esta actividad evalúa una condición antes de ejecutar las actividades que contiene.

- Si la condición es `True`, ejecuta las actividades internas.
- Cuando termina, vuelve a evaluar la condición.
- Si la condición es `False`, sale del bucle y continúa con las siguientes actividades del workflow.

Ejemplo:

Imagina que queremos contar del 1 al 5.

Creamos una variable:

```vb
Contador = 1
```

Configuramos la actividad `While` con la condición:

```vb
Contador <= 5
```

Dentro del cuerpo del bucle colocamos:

1. `Write Line`: mostrar el valor de `Contador`.
2. `Assign`: incrementar el contador.

```vb
Contador = Contador + 1
```

El resultado sería:

```vb
1
2
3
4
5
```

![Pasted image 20261020222512](Adjuntos/Pasted%20image%2020261020222512.png)

>[!important] Importante: 
>La condición se evalúa antes de ejecutar el cuerpo. Por eso, si inicialmente es falsa, las actividades internas no se ejecutan ni una sola vez.

## 2. While en Flowcharts (Diagramas de flujo)

En un workflow de tipo `Flowchart` podemos construir un bucle conectando las actividades mediante las conexiones del diagrama.

La idea consiste en crear un camino que regrese a una actividad anterior, formando un ciclo.

Normalmente utilizamos una actividad `Flow Decision` para evaluar la condición:

- True: continúa hacia las actividades que forman parte del bucle.
- False: sale del bucle y continúa por otra ruta.
- Al terminar las actividades del camino verdadero, conectamos nuevamente el flujo con la decisión para evaluar la condición otra vez.

Ejemplo:

Utilizamos el mismo contador del ejemplo anterior:

```
Contador = 1
```

La estructura sería:

```
       ┌───────────────────┐
       │ Contador <= 5 ?   │
       └─────────┬─────────┘
                 │
          ┌──────┴──────┐
         True          False
          │              │
          v              v
    Mostrar contador    Salir
          │
          v
    Contador = Contador + 1
          │
          └───────────────┐
                          │
                          └── Volver a evaluar
```

![Pasted image 20261020222628](Adjuntos/Pasted%20image%2020261020222628.png)
## 3. Diferencias entre While en Sequence y Flowchart

| Característica | Sequence                                   | Flowchart                            |
| -------------- | ------------------------------------------ | ------------------------------------ |
| Implementación | Actividad `While`                          | Conexiones que forman un ciclo       |
| Evaluación     | Antes de cada iteración                    | Mediante `Flow Decision`             |
| Repetición     | Automática mientras se cumpla la condición | Se consigue regresando a la decisión |
| Salida         | Cuando la condición es falsa               | Mediante la conexión `False`         |
| Organización   | Actividades dentro del cuerpo del While    | Actividades conectadas visualmente   |
## 4. Conceptos importantes

### ¿Qué es una iteración?

Una iteración es cada repetición del cuerpo de un bucle.

Por ejemplo, si un `While` ejecuta cinco veces sus actividades internas, decimos que realizó cinco iteraciones.

### ¿Qué es un bucle infinito?

Es un bucle que nunca termina porque su condición siempre se mantiene verdadera.

Por ejemplo:

```vb
While Contador <= 5
    Write Line(Contador)
End While
```

Si nunca modificamos `Contador`, la condición seguirá siendo verdadera y el bucle no terminará.
Por eso es importante actualizar las variables que participan en la condición.

## 5. Concepto clave para recordar

- Sequence: utilizamos la actividad `While`, que administra automáticamente la repetición.
- Flowchart: construimos el bucle mediante conexiones que regresan a una decisión o actividad anterior.