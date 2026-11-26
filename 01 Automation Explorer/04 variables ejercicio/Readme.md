# Ejercicio de variables

En este ejercicio lo que hacemos es pedirle al usuario el nombre y su año de nacimiento se calcula edad y se transforma la primera letra en mayúscula.

## Paquetes

- `Uipath.System.Activities`: actividades básicas de uipath

## Actividades a usar

- `input dialogo`: pide al usuario datos.
- `assign`: permite asignar un valor a una variable.
- `message box`: crea una ventana de mensaje.

## Comandos usados

### tipo variable (String)

- `String.Substring(0,1)`: extrae una parte de la cadena en este caso el primer caracter.
- `String.ToUpper`: pasa el string a mayusculas
- `String.ToLower`: pasa el string a minusculas

### tipo variable (String)

- `DateTime.Now.Year`: nos trae el año actual.