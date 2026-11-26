# Manejo de Excel básico

En este desarrollo lo que se hace es tomar los archivos de las diferentes tiendas que están en la carpeta `Daily Reports` y crear un único reporte de las tiendas con grafico integrado, en la carpeta de salida `Sales Results`.

## Paquetes a instalar

- `Excel Add-in`: Open Studio > Click 'Home' > 'Tools' > 'UiPath Extensions' > on the Excel Add-in, click 'Install'.
- `UiPath.Excel.Activities`: necesario para el uso de archivos de Excel.
- `Uipath.System.Activities`: paquete principal de las actividades de Uipath

## Actividades a usar

- `file Exists`: validar si existe un archivo
- `delete file`: permite eliminar un archivo
- `Excel process scope`: permite agrupar comportamientos de archivos de Excel como si van a ser visibles o no.
- `use excel file`: nos permite seleccionar o crear el archivo Excel a usar.
- `write cell`: nos permite escribir en una celda del Excel.
- `format cells`: nos permite dar formato a las celdas del Excel, buscar en propiedades.
- `append range`: agregar datos de un archivo Excel a otro archivo o a otra hoja del mismo archivo.
- `autofit range`: nos permite auto ajustar el tamaño de las columnas
- `create pivot table`: nos permite crear la tabla dinámica en una hoja especifica.
- `pivot Field`: nos permite seleccionar el campo a usar en la tabla dinámica.
- `Insert chart`: nos permite insertar una grafica en el Excel. 

## Comandos usados

### tipo variable (UiPath.Excel.WorkbookQuickHandle)

- `ArchivoExcel.Sheet("NombreHoja")`: selecciona la hoja con el nombre que le pasamos
- `ArchivoExcel.SelectedSheet.Name`: nos trae la hoja Excel seleccionada útil si el archivo Excel solo tiene una hoja y no sabemos que nombre traiga esa hoja.
- `ArchivoExcel.Sheet("NombreHoja").Cell("A1")`: nos permite seleccionar la celda a usar en este caso A1
- `ArchivoExcel.Sheet("Hoja1").Range("A1:D1")`: nos permite seleccionar un rango de celdas en este caso de A1 a D1 

### tipo variable (System.IO.FileInfo)

- `FileInfo.FullName`: nos trae la ruta completa de un archivo
- `FileInfo.Name`: nos trae el nombre del archivo con extension
- `FileInfo.Extension`: nos trae la extension del archivo
- `FileInfo.Length`: tamaño del archivo en bytes

### Otras

- `Variable.GetType().ToString()`: nos devuelve el tipo de variable que se esta usando. 

 