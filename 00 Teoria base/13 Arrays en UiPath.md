---
titulo: Arrays en UiPath
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
  - Arrays en UiPath
---
# Arrays en UiPath

Un Array (arreglo) es una estructura de datos que permite almacenar varios elementos del mismo tipo dentro de una única variable.

Por ejemplo, en lugar de crear dos variables independientes para almacenar un nombre y un apellido, podemos utilizar un array de tipo `String` para guardar ambos valores.

## 1. Declaración de un Array

Para crear un array en UiPath Studio:

1. Abrir el panel `Data Manager`.
2. Crear una variable.
3. En `Variable Type`, seleccionar el tipo de dato que almacenará el array.
4. Seleccionar la opción `Array of [T]`, donde `T` representa el tipo de dato de los elementos.

![Pasted image 20261019171542](Pasted%20image%2020261019171542.png)

Por ejemplo, para crear un array de cadenas de texto, seleccionamos:

```
String[]
```

También podemos utilizar la sintaxis:

```
Array of String
```

## 2. Asignar valores a un Array

Una vez creado el array, podemos asignarle valores utilizando llaves `{}`.

Por ejemplo:

```
{"Joe", "Doe"}
```

Si tenemos una variable llamada `Names` de tipo `String[]`, podemos asignarle esos valores:

```
Names = {"Joe", "Doe"}
```

El resultado sería:

| Índice | Valor |
| ------ | ----- |
| 0      | Joe   |
| 1      | Doe   |

>[!important] Importante: 
>Los arrays utilizan índices que comienzan en `0`, no en `1`.

## 3. Acceder a los elementos de un Array

Para obtener un elemento específico, utilizamos el nombre de la variable seguido del índice entre paréntesis:

```
Names(0) ' Joe
Names(1) ' Doe
```

En UiPath, que utiliza expresiones VB.NET en muchos tipos de proyectos, esta es la sintaxis habitual.

## 4. Operaciones comunes con Arrays

| Operación                     | Expresión          | Resultado |
| ----------------------------- | ------------------ | --------- |
| Obtener primer elemento       | `Names(0)`         | `"Joe"`   |
| Obtener segundo elemento      | `Names(1)`         | `"Doe"`   |
| Obtener cantidad de elementos | `Names.Length`     | `2`       |
| Obtener último índice         | `Names.Length - 1` | `1`       |
| Comprobar si está vacío       | `Names.Length = 0` | `False`   |

Para recorrer todos los elementos podemos utilizar la actividad `For Each`.

Ejemplo:

Si tenemos:

```
Names = {"Joe", "Doe", "Smith"}
```

Podemos utilizar `For Each` para recorrer el array y procesar cada nombre.

## 5. Características importantes de los Arrays

- Tamaño fijo: una vez creado el array, su cantidad de posiciones no puede cambiar directamente.
- Mismo tipo de datos: todos sus elementos pertenecen al tipo declarado.
- Índice base cero: el primer elemento se encuentra en la posición `0`.
- Acceso por índice: podemos obtener o modificar un elemento indicando su posición.
- Puede contener elementos repetidos: no exige que los valores sean únicos.

Si necesitamos agregar o eliminar elementos dinámicamente, podemos utilizar una colección `List(Of T)` en lugar de un array.

## 6. Diferencia entre Array y List

| Característica     | Array           | List               |
| ------------------ | --------------- | ------------------ |
| Tamaño             | Fijo            | Dinámico           |
| Agregar elementos  | No directamente | Sí, con `Add()`    |
| Eliminar elementos | No directamente | Sí, con `Remove()` |
| Acceso por índice  | Sí              | Sí                 |
| Tipo de elementos  | Definido        | Definido           |

Concepto clave: Un Array permite almacenar varios elementos del mismo tipo en una estructura de tamaño fijo, accediendo a ellos mediante índices.