# Buque determinado

En este proyecto lo que hacemos es renombrar archivos `pdf` agregando la fecha en que se procesan.
algo a tener en cuenta es que los bucles determinados se usan mas en `sequences` y se tienen varias actividades dependiendo que queremos recorrer

- `for each`: básico nos permite recorrer cualquier colección.
- `for each row in data table`: nos permite recorrer registros de un `datatable`.
- `for each for file`: nos permite recorrer archivos de una carpeta, podemos realizar un filtro de estos archivos

## Paquetes 

- `uipath.System.Activities`: básico de uipath

## Actividades

- `browser for folder`: muestra ventana para que uno seleccione una carpeta.
- `copy file`: nos permite copiar un archivo
- `move file` nos permite mover un archivo

## Comandos usados

### tipo variable (Directory)

- `Directory.getFIles("ruta carpeta a obtener")`: nos permite obtener los archivos de una carpeta. 

### tipo variable (String)

- `variable.Replace(".pdf",Now.ToString("_yyyy_MM_dd")+".pdf"))`: cambia la extensión `.pdf` por `fecha + pdf`
