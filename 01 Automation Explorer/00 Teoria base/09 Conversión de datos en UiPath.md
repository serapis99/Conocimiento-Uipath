---
titulo: Conversión de datos en UiPath
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
  - Conversión de datos en UiPath
---
# Conversión de datos en UiPath

La conversión de datos consiste en transformar un valor de un tipo de dato a otro para poder utilizarlo en diferentes operaciones dentro de una automatización.

En UiPath, las variables tienen tipos definidos (`String`, `Int32`, `Double`, `Boolean`, `DateTime`, etc.). Sin embargo, en ocasiones necesitamos convertir un valor para poder utilizarlo en una actividad o realizar una operación determinada.

Por ejemplo, si tenemos el número `25` almacenado como `String`, necesitamos convertirlo a `Int32` para realizar operaciones matemáticas.

## 1. Conversión a String (cadena de texto)

Permite convertir diferentes tipos de datos en cadenas de texto.

|Tipo de origen|Método|Descripción|
|---|---|---|
|Cualquiera|`Convert.ToString(IntVar)`|Convierte un valor a String.|
|Cualquiera|`Variable.ToString()`|Obtiene la representación textual del objeto.|
|DateTime|`DateTimeVar.ToString("dd-MM-yyyy")`|Convierte una fecha a texto utilizando un formato específico.|
|Double|`DoubleVar.ToString()`|Convierte un número decimal a texto.|
|Boolean|`BooleanVar.ToString()`|Convierte un valor lógico a texto (`True` o `False`).|

Ejemplos:

```vb
Dim Edad As Int32 = 36
Dim EdadTexto As String = Convert.ToString(Edad)
```

Resultado:

```vb
"36"
```

Conversión de fecha:

```vb
Dim FechaActual As DateTime = DateTime.Now
Dim FechaTexto As String = FechaActual.ToString("dd-MM-yyyy")
```

Resultado ilustrativo:

```
17-11-2026
```

Diferencia entre `Convert.ToString()` y `ToString()`:

- `Convert.ToString()` puede manejar valores `Nothing` y devolver una cadena vacía.
- `ToString()` invocado directamente sobre una referencia `Nothing` genera una excepción `NullReferenceException`.

## 2. Conversión a entero (Int32 e Int64)

Permite convertir valores numéricos o cadenas que representan números en tipos enteros.

|Tipo de origen|Método|Descripción|
|---|---|---|
|Cualquiera compatible|`Convert.ToInt32(Valor)`|Convierte un valor a un entero de 32 bits.|
|Cualquiera compatible|`Convert.ToInt64(Valor)`|Convierte un valor a un entero de 64 bits.|
|String numérico|`CInt(StrVar)`|Convierte una expresión a un entero de 32 bits.|
|String numérico|`Integer.Parse(StrVar)`|Convierte una cadena numérica a Int32.|
|String numérico|`Long.Parse(StrVar)`|Convierte una cadena numérica a Int64.|

Ejemplo:

```vb
Dim EdadTexto As String = "36"
Dim Edad As Int32 = Convert.ToInt32(EdadTexto)
```

Resultado:

```
36
```

Importante: `CInt()` utiliza redondeo al entero más cercano cuando recibe un valor decimal. En los casos de empate utiliza redondeo al número par (banker's rounding).

Por ejemplo:

```
CInt(10.5) ' Resultado: 10
CInt(11.5) ' Resultado: 12
```

Si necesitas eliminar la parte decimal sin redondear, puedes utilizar `Math.Truncate()`.

## 3. Conversión a Double (número decimal)

Permite convertir valores numéricos o cadenas que representan números decimales a un tipo `Double`.

|Tipo de origen|Método|Descripción|
|---|---|---|
|String numérico|`Double.Parse(StrVar)`|Convierte una cadena numérica a Double.|
|Cualquiera compatible|`Convert.ToDouble(Valor)`|Convierte un valor compatible a Double.|
|String numérico|`CDbl(StrVar)`|Convierte una expresión a Double.|

Ejemplo:

```vb
Dim PrecioTexto As String = "150.75"
Dim Precio As Double = Double.Parse(PrecioTexto)
```

Resultado:

```
150.75
```

Importante: la conversión de cadenas decimales depende de la configuración regional (CultureInfo).

Por ejemplo:

- En algunas configuraciones se utiliza `150.75`.
- En otras se utiliza `150,75`.
    
Si procesas archivos de diferentes países, conviene especificar la cultura al convertir:

```
Double.Parse(PrecioTexto, System.Globalization.CultureInfo.InvariantCulture)
```

## 4. Conversión a Boolean (valor lógico)

Permite convertir diferentes tipos de datos a valores lógicos (`True` o `False`).

|Tipo de origen|Método|Descripción|
|---|---|---|
|Numérico|`Convert.ToBoolean(IntVar)`|Devuelve `False` si el número es cero y `True` si es diferente de cero.|
|String|`Boolean.Parse(StrVar)`|Convierte las cadenas `"True"` o `"False"` a Boolean.|
|String|`Convert.ToBoolean(StrVar)`|Convierte una cadena que representa un valor lógico.|

Ejemplo con números:

```vb
Dim Numero As Int32 = 0
Dim Resultado As Boolean = Convert.ToBoolean(Numero)
```

Resultado:

```
False
```

Otro ejemplo:

```vb
Dim Numero As Int32 = 10
Dim Resultado As Boolean = Convert.ToBoolean(Numero)
```

Resultado:

```
True
```

Ejemplo con cadenas:

```vb
Dim EstadoTexto As String = "True"
Dim Estado As Boolean = Boolean.Parse(EstadoTexto)
```

Resultado:

```
True
```

Importante: `Boolean.Parse()` no interpreta `"1"` como `True` ni `"0"` como `False`. Para esos casos puedes utilizar una conversión numérica.

## 5. Métodos adicionales de conversión

Existen otros métodos que pueden resultar útiles al desarrollar automatizaciones.

|Conversión|Método|Descripción|
|---|---|---|
|A DateTime|`DateTime.Parse(StrVar)`|Convierte una cadena en fecha y hora.|
|A DateTime|`DateTime.ParseExact(StrVar, "dd-MM-yyyy", CultureInfo.InvariantCulture)`|Convierte una cadena utilizando un formato específico.|
|A Decimal|`Decimal.Parse(StrVar)`|Convierte una cadena a Decimal.|
|A Char|`Convert.ToChar(Valor)`|Convierte un valor compatible a Char.|
|A Byte|`Convert.ToByte(Valor)`|Convierte un valor compatible a Byte.|

## 6. Diferencia entre Parse, Convert y CType

En UiPath, cuando trabajamos con VB.NET, encontramos diferentes mecanismos para realizar conversiones.

|Método|Característica|Ejemplo|
|---|---|---|
|`Parse()`|Convierte una cadena a un tipo determinado.|`Integer.Parse("25")`|
|`Convert.To...()`|Convierte valores de diferentes tipos compatibles.|`Convert.ToInt32("25")`|
|`CInt()`, `CDbl()`, `CStr()`|Funciones de conversión propias de VB.NET.|`CInt("25")`|
|`CType()`|Realiza conversiones y conversiones de tipo compatibles.|`CType(Valor, String)`|
|`DirectCast()`|Realiza conversiones entre tipos relacionados mediante herencia o implementación de interfaces.|`DirectCast(Objeto, MiClase)`|

### ¿Qué sucede cuando la conversión falla?

No todos los valores pueden convertirse a cualquier tipo de dato.

Por ejemplo:

```vb
Dim EdadTexto As String = "Treinta"
Dim Edad As Int32 = Convert.ToInt32(EdadTexto)
```

Esto genera una excepción `FormatException` porque `"Treinta"` no representa un número entero válido.

Para evitar que la automatización se detenga inesperadamente, podemos utilizar:

- `TryParse()`: intenta convertir un valor y devuelve un Boolean indicando si tuvo éxito.
- `Try Catch`: permite capturar y gestionar excepciones durante la conversión.
    
Ejemplo:

```vb
Dim EdadTexto As String = "36"
Dim Edad As Int32

Dim ConversionExitosa As Boolean = Integer.TryParse(EdadTexto, Edad)
```

Si la conversión es exitosa, `ConversionExitosa` será `True` y `Edad` contendrá `36`.

## 7. Resumen general

|Conversión|Método recomendado|
|---|---|
|A String|`Convert.ToString(Valor)`|
|A Int32|`Convert.ToInt32(Valor)`|
|A Int64|`Convert.ToInt64(Valor)`|
|A Double|`Double.Parse(Valor)`|
|A Decimal|`Decimal.Parse(Valor)`|
|A Boolean|`Convert.ToBoolean(Valor)`|
|A DateTime|`DateTime.Parse(Valor)`|

Idea fundamental: convertir datos permite utilizar la información en el formato que necesita cada actividad u operación. En UiPath es especialmente importante porque frecuentemente recibimos datos desde Excel, archivos, formularios, aplicaciones y APIs, y no siempre vienen en el tipo de dato que necesitamos.