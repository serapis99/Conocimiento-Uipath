---
titulo: Bucle For Each en UiPath
tipo: concepto
nivel: 🌱
estado: activo
fecha_creacion: 2026-11-18
ultimo_repaso: 2026-11-18
frecuencia_repaso: 1
nivel_dominio: bajo
tags:
  - software
  - automatizacion
aliases:
  - Bucle For Each en UiPath
---
# Bucle For Each en UiPath

El bucle For Each permite recorrer una colección de elementos y ejecutar un conjunto de actividades para cada uno de ellos.

Una colección puede ser un Array, una List, un Dictionary, una colección de archivos, filas de una tabla, entre otras estructuras de datos.

A diferencia de `While` y `Do While`, no necesitamos controlar manualmente un contador para recorrer los elementos. `For Each` se encarga de avanzar automáticamente por la colección.

## 1. For Each en Sequences (Secuencias)

En un workflow de tipo `Sequence`, utilizamos la actividad `For Each`.

Esta actividad funciona de la siguiente manera:

1. Recibe una colección de elementos.
2. Obtiene el primer elemento.
3. Ejecuta las actividades que contiene utilizando ese elemento.
4. Pasa al siguiente elemento.
5. Repite el proceso hasta recorrer toda la colección.

Ejemplo: recorrer un Array de nombres

Creamos una variable llamada `Names` de tipo `String[]`:

```
Names = {"Joe", "Doe", "Smith"}
```

Configuramos la actividad `For Each`:

| Propiedad    | Valor         |
| ------------ | ------------- |
| Values       | `Names`       |
| TypeArgument | `String`      |
| CurrentItem  | `CurrentName` |

Dentro del cuerpo de `For Each` colocamos una actividad `Write Line` con:

```
CurrentName
```

El resultado sería:

```
Joe
Doe
Smith
```

## 2. Propiedades principales

La actividad `For Each` tiene algunas propiedades importantes:

| Propiedad    | Descripción                                                        |
| ------------ | ------------------------------------------------------------------ |
| Values       | Colección que queremos recorrer.                                   |
| TypeArgument | Tipo de dato de los elementos de la colección.                     |
| CurrentItem  | Variable que representa el elemento actual durante cada iteración. |
| Body         | Contiene las actividades que se ejecutan para cada elemento.       |
|              |                                                                    |

>[!important] Importante: 
>El tipo de `TypeArgument` debe ser compatible con los elementos de la colección. Por ejemplo, si recorremos un array de `String`, debemos utilizar `String`.

## 3. For Each con diferentes colecciones

`For Each` no está limitado a los Arrays. También podemos utilizarlo con diferentes tipos de colecciones.

| Colección          | TypeArgument | Ejemplo                                                                                          |
| ------------------ | ------------ | ------------------------------------------------------------------------------------------------ |
| Array de texto     | `String`     | `{"Ana", "Luis"}`                                                                                |
| Array de enteros   | `Int32`      | `{10, 20, 30}`                                                                                   |
| Lista de decimales | `Decimal`    | `List(Of Decimal)`                                                                               |
| Lista de fechas    | `DateTime`   | `List(Of DateTime)`                                                                              |
| Archivos           | `FileInfo`   | `Directory.GetFiles()` devuelve rutas como String; `DirectoryInfo.GetFiles()` devuelve FileInfo. |

### Ejemplo: recorrer una lista de números

Supongamos que tenemos:

```
Numbers = {10, 20, 30, 40}
```

Configuramos:

- `Values`: `Numbers`
- `TypeArgument`: `Int32`
- `CurrentItem`: `CurrentNumber`

Dentro del bucle podemos utilizar:

```
CurrentNumber * 2
```

Resultado:

```
20
40
60
80
```

## 4. Diferencia entre For Each y los bucles While

| Característica           | For Each                           | While                                    | Do While                                 |
| ------------------------ | ---------------------------------- | ---------------------------------------- | ---------------------------------------- |
| Propósito                | Recorrer una colección             | Repetir mientras se cumpla una condición | Repetir mientras se cumpla una condición |
| Control de iteraciones   | Automático según la colección      | Mediante una condición                   | Mediante una condición                   |
| Necesita contador manual | No                                 | Generalmente sí                          | Generalmente sí                          |
| Evaluación de condición  | No requiere una condición propia   | Antes de ejecutar                        | Después de ejecutar                      |
| Ejecución mínima         | 0 veces si la colección está vacía | 0 veces                                  | 1 vez                                    |

## 5. ¿Cuándo utilizar For Each?

| Situación                           | Ejemplo                                                   |
| ----------------------------------- | --------------------------------------------------------- |
| Recorrer un Array                   | Procesar una lista de nombres.                            |
| Recorrer una List                   | Calcular el total de una lista de precios.                |
| Recorrer archivos                   | Obtener información de todos los archivos de una carpeta. |
| Recorrer filas                      | Procesar registros de una colección de datos.             |
| Recorrer elementos de una colección | Validar cada elemento individualmente.                    |

>[!note] Nota: 
>Si necesitas recorrer las filas de un `DataTable`, UiPath también dispone de la actividad específica `For Each Row in Data Table`, que facilita el acceso a cada fila y sus columnas.

## 6. Concepto clave para recordar

- `For Each`: recorre automáticamente todos los elementos de una colección.
- `While`: repite actividades mientras una condición sea verdadera.
- `Do While`: ejecuta primero las actividades y después comprueba si debe repetir.

Una forma sencilla de recordarlo:

> For Each = Para cada elemento de esta colección, ejecuta estas actividades.