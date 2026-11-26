# Primera automatización pagina web

En este proyecto lo que se hace es automatizar el reto de descargar la base a procesar, y se procesa la base ingresando los datos en los inputs de la pagina a pesar que se mueven. 

## Paquetes 

- `Uipath.System.Activities`: paquete principal de uipath.
- `Uipath.UIAutomation.Activities`: paquete que nos permite interactuar con interfaz grafica de la aplicación. 
- `Uipath.Excel.Activities`: para el manejo de archivos de Excel.
- Instalar plugin para el navegador en este caso Firefox.

## Actividades

- `Use Application/Browser`: nos permite seleccionar la aplicación con la que queremos interactuar. 
- `click`: nos permite dar un click en el elemento seleccionado.
- `type into`: nos permite escribir en el elemento seleccionado.
- `wait for download`: esta actividad permite esperar a un archivo que se descargue.
- `take Screenshot`: nos permite tomar una captura de pantalla. 
- `Delete file`: nos permite eliminar un archivo se sugiere usar un try catch por si no existe un archivo a eliminar.


## Comandos usados

### tipo variable (Directory)

- `Directory.GetCurrentDirectory()`: nos trae el directorio donde corre el proyecto.
- `Path.Combine(projectPath, "input", "challenge.xlsx")`: forma correcta de unir directorios o rutas.
- `System.IO.Path.Combine(projectPath, "input")`: objeto completo para unir directorios o rutas.