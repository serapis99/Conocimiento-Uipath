---
titulo: Variables en UiPath
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
  - Variables en UiPath
---
# Variables en UiPath

Las variables son elementos que permiten almacenar información temporalmente durante la ejecución de una automatización.

En UiPath, las variables permiten guardar datos que posteriormente pueden utilizarse, modificarse y consultarse dentro de los workflows.

Por ejemplo, podemos almacenar el nombre de un cliente, una fecha, un número, una ruta de archivo o el resultado de una operación.

## 1. Características principales de una variable

Al crear una variable en UiPath debemos tener presentes cuatro conceptos fundamentales:

|Concepto|Descripción|Ejemplo|
|---|---|---|
|Nombre (Name)|Identificador que permite reconocer y utilizar la variable. Se recomienda utilizar nomenclatura PascalCase.|`NombreCliente`|
|Tipo (Variable Type)|Define qué tipo de información puede almacenar la variable.|`String`, `Int32`, `Boolean`, `DateTime`.|
|Ámbito (Scope)|Determina en qué parte del workflow puede utilizarse la variable.|`Sequence`, `Flowchart` o `Main`.|
|Valor por defecto (Default Value)|Valor inicial que tendrá la variable antes de ser modificada durante la ejecución.|`""`, `0`, `False`, `Nothing`.|

### 1.1. Nombre (Name)

Es el identificador mediante el cual hacemos referencia a una variable dentro de una automatización.

UiPath recomienda utilizar nombres descriptivos que permitan comprender qué información almacena cada variable.

Nomenclatura PascalCase: consiste en escribir cada palabra con su primera letra en mayúscula, sin utilizar espacios ni guiones bajos.

Ejemplos:

|Nombre|Descripción|
|---|---|
|`NombreCliente`|Almacena el nombre de un cliente.|
|`EdadUsuario`|Almacena la edad de un usuario.|
|`FechaNacimiento`|Almacena una fecha de nacimiento.|
|`TotalFactura`|Almacena el importe de una factura.|
|`RutaArchivo`|Almacena la ubicación de un archivo.|

### 1.2. Tipo (Variable Type)

Define qué tipo de dato puede almacenar una variable y qué operaciones podemos realizar con ese dato.

Por ejemplo:

|Tipo|Información que almacena|Ejemplo|
|---|---|---|
|`String`|Cadenas de texto.|`"Hola mundo"`|
|`Int32`|Números enteros de 32 bits.|`25`|
|`Double`|Números decimales de doble precisión.|`25.75`|
|`Boolean`|Valores lógicos.|`True` o `False`|
|`Char`|Un carácter Unicode.|`'A'`|
|`DateTime`|Fecha y hora.|`Now`|
|`TimeSpan`|Intervalos de tiempo.|`TimeSpan.FromHours(2)`|
|`Object`|Referencia a un objeto de cualquier tipo.|`New Object()`|

>[!tip] Importante: 
>UiPath utiliza los tipos de datos de .NET, por lo que muchos de los tipos que encontrarás también se utilizan en C# y VB.NET.

### 1.3. Ámbito (Scope)

El Scope o ámbito determina la región del workflow en la que una variable está disponible y puede utilizarse.

Por ejemplo, si creamos una variable dentro de una secuencia, su ámbito puede limitarse a esa secuencia y sus elementos internos.

Se recomienda utilizar el ámbito más pequeño posible, siempre que permita cumplir con las necesidades de la automatización.

¿Por qué?

- Facilita la comprensión del workflow.
- Evita que las variables estén disponibles donde no se necesitan.
- Reduce posibles conflictos entre variables.
- Facilita el mantenimiento y la depuración.
    
Ejemplo:

Imagina que tenemos un workflow principal llamado `Main` y dentro de él dos secuencias:

```
Main
│
├── Sequence 1
│   └── Variable: NombreCliente
│
└── Sequence 2
    └── Variable: TotalFactura
```

En este caso:

- `NombreCliente` pertenece al ámbito de `Sequence 1`.
- `TotalFactura` pertenece al ámbito de `Sequence 2`.
    
Cada variable estará disponible dentro de su ámbito correspondiente y los elementos internos que puedan acceder a él.

### 1.4. Valor por defecto (Default Value)

Es el valor inicial que recibe una variable cuando se crea y antes de que se le asigne otro valor durante la ejecución.

El valor predeterminado depende del tipo de dato.

|Tipo|Valor por defecto habitual en .NET|
|---|---|
|`String`|`Nothing` (referencia nula).|
|`Int32`|`0`|
|`Double`|`0`|
|`Boolean`|`False`|
|`Char`|`'\0'`|
|`DateTime`|`01/01/0001 00:00:00`|
|`Object`|`Nothing`|

En UiPath también puedes establecer manualmente un valor inicial.

Por ejemplo:

|Variable|Tipo|Valor por defecto|
|---|---|---|
|`NombreCliente`|String|`"Carlos"`|
|`EdadUsuario`|Int32|`25`|
|`EsActivo`|Boolean|`True`|
|`TotalFactura`|Double|`0.0`|

Nota: `Nothing` es el valor que representa la ausencia de una referencia a un objeto. No debe confundirse con una cadena vacía (`""`) ni con el número cero (`0`).

## 2. ¿Cómo crear variables en UiPath Studio?

Existen diferentes formas de crear variables.

### Método 1. Atajo de teclado Ctrl + K

Permite crear rápidamente una variable desde una propiedad de una actividad.

Procedimiento:

1. Seleccionar una actividad.
2. Ubicar una propiedad que permita utilizar una variable.
3. Presionar `Ctrl + K`.
4. Escribir el nombre de la variable.
5. UiPath crea la variable y la asigna a la propiedad seleccionada.
    
![Pasted image 20261016165814](Adjuntos/Pasted%20image%2020261016165814.png)

### Método 2. Menú contextual

Permite crear una variable mediante el menú contextual de una actividad o propiedad.

Procedimiento:

1. Hacer clic derecho sobre la propiedad correspondiente.
2. Seleccionar `Create Variable`.
3. Escribir el nombre de la variable.
4. Configurar su tipo y ámbito desde el panel de variables.

![Pasted image 20261016170031](Adjuntos/Pasted%20image%2020261016170031.png)

### Método 3. Data Manager

El Data Manager permite administrar los datos utilizados en un proyecto, incluyendo variables, argumentos y otros elementos.

Procedimiento:

1. Abrir el panel `Data Manager`.
2. Buscar la sección `Variables`.
3. Hacer clic en `Create Variable`.
4. Asignar un nombre.
5. Configurar el tipo, ámbito y valor por defecto.
    
![Pasted image 20261016170404](Adjuntos/Pasted%20image%2020261016170404.png)

## 3. Resumen general

|Concepto|Pregunta que responde|
|---|---|
|Name|¿Cómo identificamos la variable?|
|Variable Type|¿Qué tipo de información almacena?|
|Scope|¿Dónde podemos utilizarla?|
|Default Value|¿Qué valor tiene inicialmente?|

Formas de crear variables:

- `Ctrl + K`: creación rápida desde una propiedad.
- `Create Variable`: creación mediante el menú contextual.
- `Data Manager`: creación y administración desde el panel de datos.