# Leer archivos Excel sin Instalar Offices

en este proyecto lo que se hace es usar las actividades que podemos usar para manejar archivos Excel sin tener que instalar office los cuales son actividades `workbook`

## Paquetes 

- `uipath.Excel.Activities`: esta actividad nos da las actividades para manejo de archivos Excel y CSV.

## Actividades

- `For Each File in Folder`: nos permite recorrer los archivos en una carpeta no lo devuelve en `fileinfo`.
- `Read range`: nos permite leer un rango del archivo Excel.
- `merge data table`: nos permite unir `datatables`.
- `Filter data table`: nos permite filtrar los datos de un `datatable`
- `For Each row in Datatable`: nos permite recorrer fila a fila un `datatable`
- `write range`: nos permite escribir datos en un archivo Excel se suele usar `datatable`.

