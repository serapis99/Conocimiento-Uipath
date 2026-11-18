---
titulo: Bucle Do While en UiPath
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
  - Bucle Do While en UiPath
---
# Bucle Do While en UiPath

El bucle `Do While` es una estructura de control que permite repetir un conjunto de actividades mientras se cumpla una condición.

Su principal diferencia con `While` es que primero ejecuta las actividades y después evalúa la condición. Por esta razón, el cuerpo del bucle se ejecuta al menos una vez, independientemente de si la condición es verdadera o falsa inicialmente.

## 1. Do While en Sequences (Secuencias)

En un workflow de tipo `Sequence`, simplemente utilizamos la actividad `Do While`.

Esta actividad funciona de la siguiente manera:

1. Ejecuta las actividades que contiene.
2. Evalúa la condición.
3. Si la condición es `True`, vuelve a ejecutar las actividades.
4. Si la condición es `False`, termina el bucle y continúa con las siguientes actividades.

Ejemplo:

Imagina que queremos contar del 1 al 5.

Creamos una variable:

```vb
Contador = 1
```

Configuramos la actividad `Do While` con la condición:

```vb
Contador <= 5
```

Dentro de la actividad colocamos:

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

![Pasted image 20261020230058](Pasted%20image%2020261020230058.png)
## 2. Diferencia entre While y Do While

La diferencia fundamental está en el momento en que se evalúa la condición.

| Característica                   | While                                           | Do While                                               |
| -------------------------------- | ----------------------------------------------- | ------------------------------------------------------ |
| Primera operación                | Evalúa la condición                             | Ejecuta las actividades                                |
| Evaluación                       | Antes de cada iteración                         | Después de cada iteración                              |
| Ejecución mínima                 | 0 veces                                         | 1 vez                                                  |
| Si la condición inicial es falsa | No ejecuta el cuerpo                            | Ejecuta el cuerpo una vez                              |
| Uso habitual                     | Cuando no sabemos si debemos ejecutar el cuerpo | Cuando necesitamos ejecutar el cuerpo al menos una vez |

## 3. Ejemplo comparativo

Supongamos que tenemos:

```
Contador = 1
```

Y utilizamos la siguiente condición:

```
Contador > 5
```

¿Qué sucedería?

Con While:

```
1. Evalúa: Contador > 5
2. Resultado: False
3. Termina sin ejecutar las actividades.
```

Resultado: 0 iteraciones.

Con Do While:

```
1. Ejecuta las actividades.
2. Evalúa: Contador > 5
3. Resultado: False
4. Termina el bucle.
```

Resultado: 1 iteración.

## 4. Concepto clave para recordar

- While: primero pregunta y después ejecuta.
- Do While: primero ejecuta y después pregunta.

Una forma sencilla de recordarlo:

> While = ¿Se cumple la condición? Entonces ejecuto.
> Do While = Ejecuto y después compruebo si debo repetir.