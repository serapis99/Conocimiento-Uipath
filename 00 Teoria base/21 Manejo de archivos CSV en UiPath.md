---
titulo: Manejo de archivos CSV en UiPath
tipo: concepto
nivel: 🌱
estado: activo
fecha_creacion: 2026-11-18
ultimo_repaso: 2026-11-18
frecuencia_repaso: 1
nivel_dominio: bajo
tags:
  - software
  - automatizacion
aliases:
  - Manejo de archivos CSV en UiPath
---
# Manejo de archivos CSV en UiPath

Para trabajar con archivos CSV en UiPath podemos utilizar el paquete `UiPath.Excel.Activities`, que incluye actividades específicas para leer y escribir este tipo de archivos.

Un archivo CSV (Comma-Separated Values) es un archivo de texto que almacena datos organizados en filas y columnas. Los valores de cada fila se separan mediante un delimitador, que normalmente es una coma (`,`) o un punto y coma (`;`).

## 1. Instalar el paquete

Antes de utilizar las actividades CSV, debemos instalar el paquete `UiPath.Excel.Activities` desde Manage Packages.

Este paquete proporciona, entre otras, las siguientes actividades:

- Read CSV: lee el contenido de un archivo CSV y lo almacena en una variable de tipo `DataTable`.
- Write CSV: escribe los datos de una variable `DataTable` en un archivo CSV.

## 2. Actividad Read CSV

Permite leer los datos de un archivo `.csv` y almacenarlos en una variable de tipo `DataTable`.

Propiedades y configuraciones importantes:

| Propiedad                        | Descripción                                                                     |
| -------------------------------- | ------------------------------------------------------------------------------- |
| FilePath                         | Ruta del archivo CSV que se desea leer.                                         |
| DataTable                        | Variable donde se almacenarán los datos leídos.                                 |
| IncludeColumnNames / Has headers | Indica si la primera fila contiene los nombres de las columnas.                 |
| Delimiter                        | Carácter que separa los valores: coma, punto y coma, tabulador, entre otros.    |
| Encoding                         | Codificación de caracteres utilizada para interpretar correctamente el archivo. |

Por ejemplo, si tenemos este archivo:

```
Nombre,Edad,Ciudad
Juan,25,Bogota
Maria,30,Medellin
Pedro,28,Cali
```

Al leerlo, obtenemos una `DataTable` con tres columnas (`Nombre`, `Edad`, `Ciudad`) y tres filas de datos.

## 3. Actividad Write CSV

Permite escribir los datos de una variable `DataTable` en un archivo `.csv`.

Propiedades y configuraciones importantes:

| Propiedad                    | Descripción                                                           |
| ---------------------------- | --------------------------------------------------------------------- |
| FilePath                     | Ruta donde se guardará el archivo CSV.                                |
| DataTable                    | Variable que contiene los datos que se escribirán.                    |
| AddHeaders / Include headers | Indica si se deben incluir los nombres de las columnas en el archivo. |
| Delimiter                    | Carácter que separará los valores.                                    |
| Encoding                     | Codificación que se utilizará al guardar el archivo.                  |
## 4. Conceptos importantes al trabajar con CSV

### Delimitador

Es el carácter utilizado para separar los valores de cada columna.

\| Delimitador | Ejemplo |\
\|---|---|\
\| Coma (`,`) | `Juan,25,Bogota` |\
\| Punto y coma (`;`) | `Juan;25;Bogota` |\
\| Tabulador | `Juan    25    Bogota` |\
\| Barra vertical (`|`) | `Juan|25|Bogota` |

No debemos asumir que todos los CSV utilizan comas. En algunos países o configuraciones regionales es habitual encontrar archivos separados por punto y coma.

### Encabezados

Los encabezados son los nombres de las columnas y normalmente se encuentran en la primera fila del archivo.

Por ejemplo:

```
Nombre,Edad,Ciudad
Juan,25,Bogota
Maria,30,Medellin
```

Si indicamos que el archivo tiene encabezados, UiPath utilizará `Nombre`, `Edad` y `Ciudad` como nombres de las columnas de la `DataTable`.

### Codificación (Encoding)

Determina cómo se representan los caracteres dentro del archivo. Es importante para evitar problemas con tildes, eñes y otros caracteres especiales.

Por ejemplo, si encontramos `BogotÃ¡` en lugar de `Bogotá`, puede existir un problema de interpretación de la codificación.

## 5. Diferencia entre las actividades

| Actividad       | Función                                                                        |
| --------------- | ------------------------------------------------------------------------------ |
| `Read CSV`      | Lee un archivo CSV y obtiene sus datos en una `DataTable`.                     |
| `Write CSV`     | Escribe una `DataTable` en un archivo CSV, reemplazando el contenido anterior. |
| `Append To CSV` | Agrega datos al final de un archivo CSV existente.                             |

>[!note] Nota: 
>Aunque estas actividades están disponibles en el paquete `UiPath.Excel.Activities`, no significa que necesitemos tener Microsoft Excel instalado para trabajar con archivos CSV. CSV es un formato de texto plano, no un libro de Excel.&#x20;

## 6. Referencia visual

![Pasted image 20261101133931](Pasted%20image%2020261101133931.png)
