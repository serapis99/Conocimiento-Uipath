# Primera automatización desktop

En este proyecto lo que se hace es automatizar una aplicación de escritorio y se usa actividades de `workbook` y como se trata de aprender a usar la extracción de texto se usa la actividad `get text`

## Paquetes 

- `Uipath.System.Activities`: paquete principal de uipath.
- `Uipath.UIAutomation.Activities`: paquete que nos permite interactuar con interfaz grafica de la aplicación. 
- `Uipath.Excel.Activities`: para el manejo de archivos de Excel.

## Actividades

- `Use Application/Browser`: nos permite seleccionar la aplicación con la que queremos interactuar. 
- `click`: nos permite dar un click en el elemento seleccionado.
- `type into`: nos permite escribir en el elemento seleccionado.
- `read range workbook`: nos permite leer un archivo de Excel.
- `get text`: nos permite la extraccion de un texto.
- `create new workbook`: nos permite crear un archivo de Excel.
- `write range workbook`: nos permite escribir en un archivo de Excel.

## Comandos usados

### tipo variable (Directory)

por alguna razon las nuevas actividades de `workbook` usan el objeto `IResource` para poder crearlo desde una ruta usamos

+ `LocalResource.FromPath("input\base.xlsx")`


