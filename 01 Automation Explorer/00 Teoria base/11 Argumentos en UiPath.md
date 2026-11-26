---
titulo: Argumentos en UiPath
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
  - Argumentos en UiPath
---
# Argumentos en UiPath

Los argumentos permiten intercambiar información entre diferentes workflows (flujos de trabajo). Podemos entenderlos como los parámetros de una función o método en programación: permiten enviar información a un workflow y recibir resultados de su ejecución.

Por ejemplo, podemos tener un workflow principal que obtiene información de una factura y otro workflow encargado de procesarla. El workflow principal puede enviarle los datos mediante argumentos y recibir el resultado del procesamiento.

## 1. Direcciones de los argumentos

Los argumentos tienen tres direcciones (Directions), que determinan cómo se intercambia la información.

| Dirección | Prefijo recomendado | Descripción                                         |
| --------- | ------------------- | --------------------------------------------------- |
| In        | `in_`               | Recibe información desde el workflow que lo invoca. |
| Out       | `out_`              | Devuelve información al workflow que lo invoca.     |
| In/Out    | `io_`               | Recibe información y permite devolverla modificada. |

### In (Entrada)

Permite enviar información desde el workflow que invoca hacia el workflow que será ejecutado.

- El workflow recibe un valor.
- Se utiliza cuando el workflow necesita información externa para realizar su trabajo.

Ejemplo:

Un workflow llamado `CalculateTax` recibe el precio de un producto:

```vb
in_Price As Decimal
```

El workflow utiliza ese valor para calcular el impuesto.

### Out (Salida)

Permite devolver información desde el workflow ejecutado hacia el workflow que lo invocó.

- El workflow produce un resultado.
- Se utiliza cuando necesitamos recuperar información después de ejecutar otro workflow.

Ejemplo:

El workflow `CalculateTax` devuelve el valor del impuesto:

```vb
out_Tax As Decimal
```

### In/Out (Entrada y salida)

Permite recibir un valor, modificarlo dentro del workflow y devolver el resultado actualizado.

- El workflow recibe un valor inicial.
- Puede modificarlo durante su ejecución.
- Devuelve el valor modificado al workflow que lo invocó.

Ejemplo:

Un workflow llamado `ApplyDiscount` recibe el precio de un producto y devuelve el precio después de aplicar un descuento:

```vb
io_Price As Decimal
```

Importante: Los prefijos `in_`, `out_` e `io_` son convenciones de nomenclatura recomendadas. No son palabras reservadas ni determinan por sí mismas la dirección del argumento. La dirección se configura en las propiedades del argumento.

## 2. Diferencia entre argumentos y variables

Aunque ambos permiten almacenar información, tienen propósitos diferentes.

| Característica | Variables                                                  | Argumentos                                |
| -------------- | ---------------------------------------------------------- | ----------------------------------------- |
| Propósito      | Almacenar información durante la ejecución de un workflow. | Intercambiar información entre workflows. |
| Alcance        | Se utilizan dentro de su ámbito (Scope).                   | Permiten comunicar workflows.             |
| Dirección      | No tienen dirección.                                       | In, Out o In/Out.                         |
| Ejemplo        | `TotalFactura`                                             | `in_TotalFactura`                         |

Una forma sencilla de entenderlo:

- Variable: almacena información para utilizarla dentro de un workflow.
- Argumento: permite recibir o devolver información entre workflows.

## 3. Creación de argumentos

En UiPath Studio puedes crear argumentos mediante los siguientes atajos de teclado:

| Atajo              | Acción                           |
| ------------------ | -------------------------------- |
| `Ctrl + M`         | Crear argumento de entrada (In). |
| `Ctrl + Shift + M` | Crear argumento de salida (Out). |

También puedes administrarlos desde el panel Data Manager, en la sección de argumentos.

Para cada argumento debes configurar:

- Name: nombre del argumento.
- Direction: dirección (In, Out o In/Out).
- Argument Type: tipo de dato (.NET).
- Default Value: valor predeterminado, cuando corresponda.

## 4. Convenciones para nombrar workflows y argumentos

Se recomienda utilizar nombres descriptivos que permitan identificar fácilmente la responsabilidad de cada workflow.

Workflows:

- Utilizar nombres que comiencen con un verbo descriptivo.
- Aplicar nomenclatura PascalCase.
- Procurar que el nombre describa claramente la acción realizada.

Ejemplos:

| Nombre               | Descripción                             |
| -------------------- | --------------------------------------- |
| `GetTransactionData` | Obtener información de una transacción. |
| `ProcessTransaction` | Procesar una transacción.               |
| `TakeScreenshot`     | Tomar una captura de pantalla.          |
| `ValidateInvoice`    | Validar una factura.                    |
| `SendEmail`          | Enviar un correo electrónico.           |

Argumentos:

Se recomienda utilizar los prefijos correspondientes a su dirección y PascalCase para el nombre descriptivo.

Ejemplos:

```
in_InvoiceNumber As String
in_InvoiceAmount As Decimal
out_IsValid As Boolean
out_ErrorMessage As String
io_TransactionData As DataTable
```

## 5. Ejemplo práctico: comunicación entre workflows

Imagina que tienes dos workflows:

- `Main.xaml`: workflow principal.
- `CalculateTax.xaml`: workflow encargado de calcular un impuesto.

El workflow principal envía el precio al segundo workflow y recibe el impuesto calculado.

Argumentos de `CalculateTax.xaml`:

| Nombre     | Dirección | Tipo    |
| ---------- | --------- | ------- |
| `in_Price` | In        | Decimal |
| `out_Tax`  | Out       | Decimal |

El proceso sería:

1. `Main.xaml` obtiene el precio del producto.
2. Invoca `CalculateTax.xaml` mediante la actividad Invoke Workflow File.
3. Envía el precio a través de `in_Price`.
4. `CalculateTax.xaml` calcula el impuesto.
5. Devuelve el resultado mediante `out_Tax`.
6. `Main.xaml` recibe el impuesto y continúa con el proceso.

```
Main.xaml
    |
    | Envía in_Price
    v
CalculateTax.xaml
    |
    | Calcula el impuesto
    |
    | Devuelve out_Tax
    v
Main.xaml
    |
    | Continúa utilizando el resultado
```

## 6. Concepto clave para recordar

La diferencia fundamental es que las variables y los argumentos tienen responsabilidades distintas:

- Las variables permiten almacenar y manipular información dentro de un workflow.
- Los argumentos permiten comunicar información entre workflows.
- Las direcciones `In`, `Out` e `In/Out` determinan cómo se intercambia esa información.