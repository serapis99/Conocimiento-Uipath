# Manejo de Excel con Actividades modernas

Las actividades modernas nos obligan a instalar offices y tambien instalar el plugin de `excel-in`. 

En este proyecto lo que arremos es validar las ventas de cada agente y darle la  comicion correspondiente, se crea tabla dinamica y se inserta grafica. 

## Paquetes a instalar

- `Excel Add-in`: Open Studio > Click 'Home' > 'Tools' > 'UiPath Extensions' > on the Excel Add-in, click 'Install'.
- `UiPath.Excel.Activities`: necesario para el uso de archivos de Excel.

## Actividades a usar

- `Excel process scope`: se usa para darle un comportamiento a todos los archivos Excel que se abren lo normal es hacer visible o no cuando se abre el Excel.
- `Use Excel File`: Permite seleccionar el archivo a usar.
- `Remove Duplicate`: elimina filas duplicadas en el archivo Excel ya sea usando una columna o varias.
- `Copy or paste range`: permite copiar o pegar un rango.
- `Insert column`: nos permite insertar una columna antes o despues de otra.
- `VLookup`: permite buscar un valor es como buscar v 
- `Write cell`: nos permite escribir en una celda
- `create pivot table`: inserta tabla dinamica
- `pivot filed`: nos permite establecer los campos de la tabla dinamica 
- `Insert chart`: inserta un grafico en el archivo
- `Delete sheet`: Elimina una hoja del excel
- `Protect sheet`: proteje la hoja de Excel.