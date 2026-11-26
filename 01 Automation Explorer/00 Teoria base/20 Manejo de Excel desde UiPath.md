---
titulo: Manejo de Excel desde UiPath
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
  - Manejo de Excel desde UiPath
---
# Manejo de Excel desde UiPath

UiPath permite interactuar con archivos de Excel mediante actividades especializadas que facilitan la lectura, escritura, modificación y administración de libros de cálculo.

Para utilizar estas actividades debemos instalar el paquete `UiPath.Excel.Activities`. A diferencia de las actividades `Workbook`, las actividades de automatización de Excel pueden utilizar la aplicación Microsoft Excel para trabajar con los archivos y aprovechar sus funcionalidades.

## 1. Requisitos para trabajar con Excel

Para utilizar las actividades de Excel que interactúan con la aplicación debemos tener en cuenta:

- **UiPath.Excel.Activities**: paquete que proporciona las actividades para trabajar con Excel.
- **Microsoft Excel**: aplicación de escritorio instalada cuando utilizamos las funcionalidades que dependen de ella.
- **Excel Add-in**: complemento que permite la integración entre UiPath y Microsoft Excel para determinadas funcionalidades, especialmente las relacionadas con la automatización desde Excel.
    
>[!important] Importante: 
>No todas las actividades de `UiPath.Excel.Activities` necesitan Microsoft Excel instalado. Las actividades Workbook, por ejemplo, permiten manipular archivos sin depender de la aplicación. Tampoco todas las automatizaciones modernas de Excel requieren instalar manualmente el complemento Excel Add-in; depende de las actividades y del método de integración utilizado.

## 2. Actividades principales

Las dos actividades fundamentales para comenzar a trabajar con Excel son `Excel Process Scope` y `Use Excel File`.

### Excel Process Scope

La actividad `Excel Process Scope` permite controlar cómo se administra el proceso de Microsoft Excel durante la ejecución de la automatización.

Su función principal es establecer las opciones de ejecución y comportamiento de los procesos de Excel.

Características:

- Permite configurar el comportamiento del proceso de Excel.
- Controla aspectos relacionados con la apertura y administración de instancias de Excel.
- Permite establecer opciones para el cierre y la reutilización de procesos.
- Puede contener actividades `Use Excel File`.

Ejemplo de uso:

Si vamos a trabajar con varios archivos de Excel, podemos utilizar `Excel Process Scope` para definir cómo se gestionarán los procesos de Excel durante la automatización.

### Use Excel File

La actividad `Use Excel File` permite seleccionar el archivo de Excel con el que queremos trabajar y proporciona un contexto para ejecutar otras actividades sobre ese libro.

Características:

- Permite indicar la ruta del archivo Excel.
- Permite abrir un archivo existente o crear uno nuevo, según la configuración.
- Proporciona acceso a las hojas, tablas, rangos y celdas del libro.
- Contiene las actividades que interactúan con el archivo seleccionado.
- Permite configurar opciones de guardado y apertura.
    
Ejemplo:

Queremos trabajar con el archivo:

```
C:\Facturas\Registro.xlsx
```

Configuramos `Use Excel File` para utilizar esa ruta y dentro colocamos actividades como:

- `Read Range`: leer un rango de celdas.
- `Write Range`: escribir información.
- `Read Cell`: leer una celda.
- `Write Cell`: modificar una celda.
- `Append Range`: agregar información.
    
## 3. Relación entre Excel Process Scope y Use Excel File

Estas actividades tienen responsabilidades diferentes y pueden utilizarse conjuntamente.

|Actividad|Responsabilidad|
|---|---|
|`Excel Process Scope`|Configura y administra el proceso de Excel.|
|`Use Excel File`|Selecciona el libro de Excel con el que se trabajará.|
|Actividades internas|Ejecutan operaciones sobre el contenido del libro.|

La estructura habitual sería:

```
Excel Process Scope
│
└── Use Excel File
    │
    ├── Read Range
    ├── Read Cell
    ├── Write Cell
    └── Write Range
```

## 4. Diferencia entre Workbook y Excel

Es importante relacionar este tema con lo que vimos anteriormente.

|Característica|Workbook|Excel moderno|
|---|---|---|
|Paquete|UiPath.Excel.Activities|UiPath.Excel.Activities|
|Microsoft Excel instalado|No|Generalmente sí|
|Actividad principal|Read Range Workbook|Use Excel File|
|Interacción con la aplicación|No|Sí, según la actividad y configuración|
|Administración del proceso Excel|No|Puede utilizar Excel Process Scope|
|Uso habitual|Manipulación directa de archivos|Automatización con funcionalidades de Excel|

## 5. Concepto clave para recordar

- `UiPath.Excel.Activities`: paquete que proporciona las actividades para trabajar con Excel.
- `Excel Process Scope`: administra el comportamiento del proceso de Excel.
- `Use Excel File`: establece el libro con el que vamos a trabajar.
- Actividades internas: permiten leer, escribir y manipular los datos del libro.