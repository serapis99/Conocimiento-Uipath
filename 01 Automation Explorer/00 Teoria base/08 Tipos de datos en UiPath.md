---
titulo: Tipos de datos en UiPath
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
  - Tipos de datos en UiPath
---
# Tipos de datos en UiPath

UiPath utiliza los tipos de datos de .NET (Framework o moderno .NET, según la compatibilidad del proyecto) para almacenar y manipular información durante la ejecución de las automatizaciones.

Un tipo de dato determina qué clase de información puede almacenar una variable, qué valores puede representar y qué operaciones se pueden realizar con ella.

En UiPath podemos trabajar con tipos de datos simples, como `Int32`, `Double`, `String` y `Boolean`, así como con estructuras de datos más complejas, como `Array`, `List`, `Dictionary` y `DataTable`.

## 1. Tabla general de tipos de datos

|Categoría|Tipo en UiPath|Clase .NET|Descripción|Tamaño|
|---|---|---|---|---|
|Entero|`Int32`|`System.Int32`|Números enteros de 32 bits.|4 bytes|
|Entero|`Int64`|`System.Int64`|Números enteros de 64 bits.|8 bytes|
|Decimal|`Double`|`System.Double`|Números decimales de doble precisión.|8 bytes|
|Texto|`String`|`System.String`|Cadenas de caracteres.|Variable|
|Lógico|`Boolean`|`System.Boolean`|Valores `True` o `False`.|1 byte|
|Colección|`Array`|`System.Array`|Colección de elementos de tamaño fijo.|Variable|
|Colección|`List`|`System.Collections.Generic.List<T>`|Colección dinámica de elementos.|Variable|
|Colección|`Dictionary`|`System.Collections.Generic.Dictionary<TKey, TValue>`|Colección de pares clave-valor.|Variable|
|Estructura de datos|`DataTable`|`System.Data.DataTable`|Tabla de datos formada por filas y columnas.|Variable|
|Fecha y hora|`DateTime`|`System.DateTime`|Representa una fecha y una hora.|8 bytes|
|Intervalo de tiempo|`TimeSpan`|`System.TimeSpan`|Representa una duración o intervalo de tiempo.|8 bytes|

## 2. Tipos de datos numéricos

Permiten almacenar números y realizar operaciones matemáticas.

### 2.1. Int32

Representa números enteros de 32 bits (4 bytes).

|Característica|Valor|
|---|---|
|Tipo|`Int32`|
|Clase .NET|`System.Int32`|
|Tamaño|4 bytes|
|Valor mínimo|-2,147,483,648|
|Valor máximo|2,147,483,647|

Ejemplo:

```vb
Dim Edad As Int32 = 36
Dim Cantidad As Int32 = 150
Dim Temperatura As Int32 = -10
```

### 2.2. Int64

Representa números enteros de 64 bits (8 bytes).

|Característica|Valor|
|---|---|
|Tipo|`Int64`|
|Clase .NET|`System.Int64`|
|Tamaño|8 bytes|
|Valor mínimo|-9,223,372,036,854,775,808|
|Valor máximo|9,223,372,036,854,775,807|

Se utiliza cuando necesitamos almacenar números enteros que superan el rango de `Int32`.

### 2.3. Double

Representa números de punto flotante de doble precisión (64 bits).

|Característica|Valor|
|---|---|
|Tipo|`Double`|
|Clase .NET|`System.Double`|
|Tamaño|8 bytes|
|Precisión|Aproximadamente 15-17 dígitos significativos|
|Uso|Números decimales y cálculos científicos.|

Ejemplos:

```vb
Dim Precio As Double = 150.75
Dim Porcentaje As Double = 15.5
Dim Resultado As Double = 125.0 / 3.0
```

Importante: `Double` utiliza representación binaria de punto flotante, por lo que algunos valores decimales no se representan exactamente. Para cálculos financieros donde importa la precisión decimal, normalmente es preferible `Decimal` (`System.Decimal`).

## 3. Tipos de datos de texto y lógicos

### 3.1. String

Permite almacenar cadenas de caracteres, como palabras, frases, nombres y rutas de archivos.

|Característica|Valor|
|---|---|
|Tipo|`String`|
|Clase .NET|`System.String`|
|Tamaño|Variable|
|Contenido|Texto Unicode|

Ejemplos:

```vb
Dim Nombre As String = "Carlos"
Dim Ciudad As String = "Bogotá"
Dim RutaArchivo As String = "C:\Documentos\factura.xlsx"
```

Una característica importante es que `String` es un tipo de referencia en .NET y es inmutable: cuando modificamos una cadena, realmente se genera una nueva cadena.

### 3.2. Boolean

Permite almacenar valores lógicos que representan dos estados posibles.

|Característica|Valor|
|---|---|
|Tipo|`Boolean`|
|Clase .NET|`System.Boolean`|
|Tamaño|1 byte|
|Valores|`True` o `False`|

Ejemplos:

```vb
Dim EsActivo As Boolean = True
Dim TieneErrores As Boolean = False
```

Se utiliza principalmente en condiciones y decisiones.

Por ejemplo:

```vb
If EsActivo Then
    Console.WriteLine("El usuario está activo")
End If
```

## 4. Tipos de datos compuestos y colecciones

Estos tipos permiten almacenar y organizar varios elementos en una misma estructura.

### 4.1. Array (Arreglo)

Un `Array` es una estructura que permite almacenar varios elementos del mismo tipo en una colección de tamaño fijo.

|Característica|Valor|
|---|---|
|Tipo|`Array`|
|Clase .NET|`System.Array`|
|Tamaño|Fijo después de su creación|
|Elementos|Pueden ser de diferentes tipos si se utiliza `Object()`|

Ejemplo:

```vb
Dim Numeros As Int32() = {10, 20, 30, 40}
```

Para acceder a un elemento utilizamos su índice:

```vb
Dim PrimerNumero As Int32 = Numeros(0)
```

Importante: los índices de los arreglos comienzan en cero.

### 4.2. List (Lista)

Una `List` es una colección dinámica que permite almacenar elementos y modificar su cantidad durante la ejecución.

| Característica | Valor                                |
| -------------- | ------------------------------------ |
| Tipo           | `List(Of T)`                         |
| Clase .NET     | `System.Collections.Generic.List<T>` |
| Tamaño         | Dinámico                             |
| Elementos      | Generalmente del mismo tipo          |

Ejemplo:

```vb
Dim Nombres As New List(Of String)

Nombres.Add("Carlos")
Nombres.Add("Ana")
Nombres.Add("Pedro")
```

A diferencia de un Array, una List permite agregar y eliminar elementos fácilmente.

### 4.3. Dictionary (Diccionario)

Un `Dictionary` es una colección que almacena información mediante pares de clave y valor (Key-Value).

Cada clave identifica un valor dentro de la colección.

|Característica|Valor|
|---|---|
|Tipo|`Dictionary(Of TKey, TValue)`|
|Clase .NET|`System.Collections.Generic.Dictionary<TKey, TValue>`|
|Estructura|Clave - Valor|
|Claves|Únicas|

Ejemplo:

```vb
Dim Usuario As New Dictionary(Of String, String)

Usuario.Add("Nombre", "Carlos")
Usuario.Add("Ciudad", "Bogotá")
Usuario.Add("Pais", "Colombia")
```

Para consultar un valor:

```
Dim Nombre As String = Usuario("Nombre")
```

### Diferencia entre Array, List y Dictionary

|Característica|Array|List|Dictionary|
|---|---|---|---|
|Organización|Índices|Índices|Claves|
|Acceso|Por posición|Por posición|Por clave|
|Tamaño|Fijo|Dinámico|Dinámico|
|Elementos|Tipo definido|Tipo definido|Clave y valor|
|Ejemplo|`Numeros(0)`|`Nombres(0)`|`Usuario("Nombre")`|

## 5. Tipos de datos para tablas

### 5.1. DataTable

Un `DataTable` es una estructura de datos que permite almacenar información organizada en filas y columnas, de manera similar a una tabla de Excel o una tabla de una base de datos.

|Característica|Valor|
|---|---|
|Tipo|`DataTable`|
|Clase .NET|`System.Data.DataTable`|
|Estructura|Filas y columnas|
|Uso|Almacenar y manipular datos tabulares.|

Ejemplo:

Imagina que tenemos la siguiente información de clientes:

|Id|Nombre|Edad|
|---|---|---|
|1|Carlos|36|
|2|Ana|28|
|3|Pedro|42|

Podemos almacenar toda esta información en una variable de tipo `DataTable`.

En UiPath es especialmente útil para trabajar con actividades como:

- `Build Data Table`
- `Read Range`
- `Write Range`
- `Filter Data Table`
- `For Each Row in Data Table`
    
Importante: un DataTable puede contener columnas de diferentes tipos de datos.

## 6. Tipos de datos relacionados con fechas y tiempo

### 6.1. DateTime

Representa una fecha y una hora determinadas.

|Característica|Valor|
|---|---|
|Tipo|`DateTime`|
|Clase .NET|`System.DateTime`|
|Tamaño|8 bytes|
|Contenido|Fecha y hora|

Ejemplo:

```vb
Dim FechaActual As DateTime = Now
Dim FechaNacimiento As DateTime = New DateTime(1990, 12, 5)
```

El formato de visualización depende de la configuración regional o del formato aplicado.

Por ejemplo:

```
FechaActual.ToString("dd/MM/yyyy HH:mm:ss")
```

Resultado ilustrativo:

```
17/11/2026 20:35:00
```

### 6.2. TimeSpan

Representa una duración o intervalo de tiempo, no una fecha específica.

|Característica|Valor|
|---|---|
|Tipo|`TimeSpan`|
|Clase .NET|`System.TimeSpan`|
|Tamaño|8 bytes|
|Contenido|Días, horas, minutos, segundos y fracciones de segundo|

Ejemplo:

```vb
Dim Duracion As TimeSpan = TimeSpan.FromHours(2)
```

También podemos calcular cuánto tiempo transcurrió entre dos fechas:

```vb
Dim FechaInicio As DateTime = DateTime.Now
Dim FechaFin As DateTime = FechaInicio.AddHours(3)
Dim Duracion As TimeSpan = FechaFin - FechaInicio
```

Diferencia entre DateTime y TimeSpan:

- `DateTime`: representa un momento específico.
- `TimeSpan`: representa una duración entre dos momentos.

## 7. Otros tipos de datos importantes en UiPath

Además de los tipos anteriores, existen otros que encontrarás frecuentemente al desarrollar automatizaciones.

| Tipo            | Clase .NET                             | Uso                                                         |
| --------------- | -------------------------------------- | ----------------------------------------------------------- |
| `Decimal`       | `System.Decimal`                       | Cálculos financieros y valores decimales de alta precisión. |
| `Char`          | `System.Char`                          | Almacenar un carácter Unicode.                              |
| `Byte`          | `System.Byte`                          | Almacenar números enteros de 0 a 255.                       |
| `Object`        | `System.Object`                        | Referenciar objetos de diferentes tipos.                    |
| `FileInfo`      | `System.IO.FileInfo`                   | Representar información de un archivo.                      |
| `DirectoryInfo` | `System.IO.DirectoryInfo`              | Representar información de un directorio.                   |
| `Regex`         | `System.Text.RegularExpressions.Regex` | Trabajar con expresiones regulares.                         |
| `XDocument`     | `System.Xml.Linq.XDocument`            | Trabajar con documentos XML.                                |

## 8. Consideraciones importantes

1. Los tipos de datos de UiPath provienen de .NET: por eso encontrarás nombres como `System.Int32` o `System.String`.
    
2. No todos los tipos son primitivos: `Int32`, `Double` y `Boolean` son tipos de valor, mientras que `String`, `Array`, `List` y `Dictionary` son tipos de referencia.
    
3. Las colecciones almacenan múltiples elementos: Array, List y Dictionary permiten organizar información de diferentes maneras.
    
4. DataTable permite trabajar con datos tabulares: es especialmente útil para automatizaciones que procesan información de Excel.
    
5. DateTime y TimeSpan son estructuras diferentes: una representa un momento y la otra una duración.
    

## 9. Resumen conceptual

|Grupo|Tipos principales|¿Qué almacenan?|
|---|---|---|
|Numéricos|`Int32`, `Int64`, `Double`, `Decimal`|Números.|
|Texto|`String`, `Char`|Caracteres y cadenas de texto.|
|Lógicos|`Boolean`|Valores verdaderos o falsos.|
|Colecciones|`Array`, `List`, `Dictionary`|Conjuntos de elementos.|
|Tabulares|`DataTable`|Información en filas y columnas.|
|Temporales|`DateTime`, `TimeSpan`|Fechas, horas y duraciones.|
|Objetos|`Object`, `FileInfo`, `DirectoryInfo`|Referencias a objetos y recursos.|

Idea fundamental: conocer los tipos de datos es esencial para desarrollar automatizaciones en UiPath, porque cada variable debe tener un tipo adecuado para la información que necesitamos almacenar y manipular.