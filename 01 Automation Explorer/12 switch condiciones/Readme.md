# Switch Condicional

Es una condición que permite tener muchas ramificaciones en una sola estructura es una opción simplificada de vez de usar `IF` concatenados.

Igual que varias actividades tenemos la actividad para `sequences` y para `flowchart`

- `sequences`: `Switch`
- `flowchart`: `flow switch`

## Paquetes 

- `uipath.System.Activities`: básico de uipath

## Comandos usados

### tipo variable (Directory)

- `Directory.GetFiles(ruta de una carpeta)`: se obtiene un array de las ruta completa de los archivos que están en esa carpeta.

### tipo variable (FileInfo)

- `new FileInfo(ruta archivo)`: se crea un objeto tipo FileInfo usando la ruta del archivo. 
- `file.name`: nos trae el nombre del archivo con extensión
- `file.name.Substring(0,file.Name.LastIndexOf("."))`: es una forma de traer el nombre del archivo sin extensión. 
 