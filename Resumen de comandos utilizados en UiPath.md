# Resumen de comandos utilizados en UiPath

### 1. Excel – `UiPath.Excel.WorkbookQuickHandle`

|Comando|Función|Ejemplo|
|---|---|---|
|`.Sheet("NombreHoja")`|Selecciona una hoja por su nombre.|`ArchivoExcel.Sheet("Hoja1")`|
|`.SelectedSheet.Name`|Obtiene el nombre de la hoja seleccionada.|`ArchivoExcel.SelectedSheet.Name`|
|`.Sheet("Hoja1").Cell("A1")`|Selecciona una celda específica.|`ArchivoExcel.Sheet("Hoja1").Cell("A1")`|
|`.Sheet("Hoja1").Range("A1:D1")`|Selecciona un rango de celdas.|`ArchivoExcel.Sheet("Hoja1").Range("A1:D1")`|

### 2. Archivos – `System.IO.FileInfo`

|Propiedad / método|Función|Ejemplo|
|---|---|---|
|`.FullName`|Obtiene la ruta completa del archivo.|`file.FullName`|
|`.Name`|Obtiene el nombre con extensión.|`file.Name`|
|`.Extension`|Obtiene la extensión del archivo.|`file.Extension`|
|`.Length`|Obtiene el tamaño en bytes.|`file.Length`|
|`New FileInfo(ruta)`|Crea un objeto FileInfo a partir de una ruta.|`New FileInfo("C:\Docs\archivo.pdf")`|

Obtener nombre sin extensión:

```
file.Name.Substring(0, file.Name.LastIndexOf("."))
```

### 3. Cadenas de texto – `String`

|Método / propiedad|Función|Ejemplo|
|---|---|---|
|`.Substring(inicio, cantidad)`|Extrae una parte del texto.|`texto.Substring(0,1)`|
|`.ToUpper()`|Convierte el texto a mayúsculas.|`texto.ToUpper()`|
|`.ToLower()`|Convierte el texto a minúsculas.|`texto.ToLower()`|
|`.Replace(buscar, reemplazar)`|Reemplaza una parte del texto.|`texto.Replace(".pdf", "_2026_11_18.pdf")`|
|`String.Join(separador, arreglo)`|Une elementos de un arreglo en una cadena.|`String.Join("-", arreglo)`|

Ejemplo: agregar fecha al nombre de un archivo:

```
variable.Replace(".pdf", Now.ToString("_yyyy_MM_dd") & ".pdf")
```

### 4. Directorios – `System.IO.Directory`

|Método|Función|Ejemplo|
|---|---|---|
|`Directory.GetFiles(ruta)`|Obtiene las rutas completas de los archivos de una carpeta.|`Directory.GetFiles("C:\Docs")`|
|`Directory.GetCurrentDirectory()`|Obtiene el directorio de trabajo actual.|`Directory.GetCurrentDirectory()`|

Ejemplo: obtener archivos de una carpeta:

```
archivos = Directory.GetFiles("C:\Docs")
```

El resultado es un arreglo de tipo `String()` con las rutas de los archivos.

### 5. Rutas – `System.IO.Path`

|Método|Función|Ejemplo|
|---|---|---|
|`Path.Combine(ruta1, ruta2)`|Combina segmentos de una ruta correctamente.|`Path.Combine(projectPath, "input")`|

Ejemplo: construir una ruta completa:

```
projectPath = Directory.GetCurrentDirectory()

archivo = Path.Combine(projectPath, "input", "challenge.xlsx")
```

También puedes utilizar el nombre completo:

```
System.IO.Path.Combine(projectPath, "input")
```

### 6. Fechas – `DateTime`

|Propiedad|Función|Ejemplo|
|---|---|---|
|`DateTime.Now`|Obtiene la fecha y hora actual.|`DateTime.Now`|
|`DateTime.Now.Year`|Obtiene el año actual.|`DateTime.Now.Year`|
|`DateTime.Now.Month`|Obtiene el mes actual.|`DateTime.Now.Month`|
|`DateTime.Now.Day`|Obtiene el día actual.|`DateTime.Now.Day`|

Para dar formato a una fecha:

```
Now.ToString("yyyy_MM_dd")
```

### 7. Otros comandos útiles

| Comando                         | Función                                                   | Ejemplo                                     |
| ------------------------------- | --------------------------------------------------------- | ------------------------------------------- |
| `Variable.GetType().ToString()` | Obtiene el tipo de dato de una variable.                  | `miVariable.GetType().ToString()`           |
| `Environment.NewLine`           | Inserta un salto de línea en un texto.                    | `"Hola" & Environment.NewLine & "Mundo"`    |
| `LocalResource.FromPath(ruta)`  | Crea un recurso local (`IResource`) a partir de una ruta. | `LocalResource.FromPath("input\base.xlsx")` |

## Algunas consideraciones importantes

1. `FileInfo` y `Directory` no son lo mismo: `FileInfo` representa un archivo individual, mientras que `Directory` permite trabajar con directorios y sus archivos.
    
2. `GetFiles()` devuelve un arreglo: si quieres trabajar con las propiedades de cada archivo, puedes recorrerlo y crear un `FileInfo` para cada ruta.
    

```
For Each ruta In Directory.GetFiles("C:\Docs")
    file = New FileInfo(ruta)
Next
```

3. `String.Join()` y `Environment.NewLine`: puedes combinarlos para unir elementos en varias líneas:

```
String.Join(Environment.NewLine, arreglo)
```

4. `LocalResource.FromPath()`: es especialmente útil en las actividades modernas de Workbook que trabajan con recursos `IResource`.
    
5. `Directory.GetCurrentDirectory()`: devuelve el directorio de trabajo actual, que no necesariamente coincide con la carpeta raíz del proyecto UiPath.
    