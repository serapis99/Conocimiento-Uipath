# Extracción de tablas en UiPath (Table Extraction)

Table Extraction permite extraer automáticamente información estructurada de aplicaciones, especialmente de páginas web y tablas visibles en interfaces de usuario, y almacenarla en un objeto `DataTable`.

La información extraída puede utilizarse posteriormente en diferentes actividades y procesos de automatización.

## 1. Aplicaciones de Table Extraction

|Aplicación|Ejemplo|
|---|---|
|Data Entry Automation|Extraer datos de facturas y recibos para registrarlos en Excel o en una base de datos.|
|Web Scraping|Extraer información estructurada de páginas web, catálogos y otros sitios.|
|Business Intelligence|Extraer información de informes financieros y ventas para elaborar informes y dashboards.|

## 2. Table Extraction Wizard

El Table Extraction Wizard es un asistente que permite seleccionar visualmente los datos que queremos extraer y configurar las columnas que formarán parte de la tabla.

Se puede abrir desde:

- Design Ribbon: cuando está disponible en la configuración de diseño de Studio.
- Extract Table Data: agregando esta actividad al workflow y configurando la extracción.
    
El asistente configura la actividad `Extract Table Data`, cuyo resultado principal es un objeto `DataTable`.

### Opciones principales del asistente

|Opción|Función|
|---|---|
|Add new column|Agrega una columna para extraer otro tipo de información.|
|Select similar elements|Busca y selecciona elementos similares al elemento elegido.|
|Extract text|Extrae el texto del elemento seleccionado.|
|Extract URL|Extrae la dirección URL asociada al elemento.|
|Extract URLs and image sources|Permite extraer las URL y las fuentes de imágenes asociadas a los elementos.|
|Delete|Elimina una columna de extracción.|
|Column settings|Permite configurar individualmente una columna.|

>[!important] importante: 
>cuando seleccionamos un elemento, UiPath intenta identificar otros elementos similares para extraer sus valores y organizarlos como registros de una misma columna.
>
>Por ejemplo, si seleccionamos el título de un producto, UiPath puede identificar los demás títulos de productos que siguen una estructura similar.

## 3. Column Settings: configuración de columnas

Cada columna dispone de un icono de configuración (rueda dentada) que permite personalizar cómo se extraerán y procesarán sus datos.

### Propiedades principales

|Propiedad|Función|Ejemplo|
|---|---|---|
|Column name|Cambia el nombre de la columna.|`Titulo`|
|Parse data as|Define cómo interpretar los datos extraídos.|Text, Numbers, Date & Time|
|Sort|Establece el orden de los registros extraídos.|Ascending / Descending|
|Sample after parsing|Muestra una vista previa de los datos después de aplicar la conversión.|Fecha convertida|

### Parse data as: tipos de datos

Esta opción permite indicar cómo debe interpretar UiPath la información extraída.

|Tipo|Utilización|Ejemplo|
|---|---|---|
|Text|Información textual.|`"Producto A"`|
|Numbers|Valores numéricos.|`1500`|
|Date & Time|Fechas y horas.|`18/11/2026`|

>[!important] Importante: 
>seleccionar un tipo de dato permite interpretar o convertir la información extraída. No significa que el contenido original de la página ya tenga ese tipo de dato.

### Sort: ordenamiento

Permite establecer el orden en el que se presentan los registros de una columna.

| Opción     | Significado              |     |
| ---------- | ------------------------ | --- |
| None       | No aplicar ordenamiento. |     |
| Ascending  | Orden ascendente.        |     |
| Descending | Orden descendente.       |     |

El criterio de ordenamiento depende del tipo de dato:

- Texto: orden alfabético.
- Números: orden numérico.
- Fecha: orden cronológico.
    
## 4. Extracción de datos de múltiples páginas

Cuando la información está distribuida en varias páginas, podemos configurar la extracción para que UiPath navegue automáticamente entre ellas.

Para ello, habilitamos:

`Extract data from multiple pages = Yes`

Después debemos indicar el elemento que permite navegar a la siguiente página, conocido como Next Page (botón o enlace de siguiente página).

### Configuración de límites

Podemos establecer límites para controlar la cantidad de información que queremos extraer.

|Configuración|Función|
|---|---|
|No Limit|No establece un límite explícito de páginas o filas para la extracción.|
|Max Pages|Limita la cantidad de páginas que se procesarán.|
|Max Rows|Limita la cantidad de filas que se extraerán.|

### Ejemplo práctico

Supongamos que una página web contiene información distribuida en tres páginas y queremos extraerlas todas.

Configuración:

```
Extract data from multiple pages = Yes
Next Page = Botón para avanzar a la siguiente página
Max Pages = 3
```

El proceso sería:

1. Extraer los datos de la página 1.
2. Identificar y pulsar el botón Next Page.
3. Extraer los datos de la página 2.
4. Avanzar a la página 3.
5. Extraer sus datos y finalizar.
    
### Preview: vista previa

La sección Preview permite comprobar los resultados de la extracción antes de ejecutar el workflow.

Desde esta sección podemos:

- Consultar cuántas filas están disponibles en la página actual.
- Visualizar los datos que UiPath ha identificado.
- Utilizar el icono del ojo para consultar los datos extraídos.
    
## 5. Resultado de la extracción: DataTable

Una vez configurada y ejecutada la actividad `Extract Table Data`, los datos se almacenan en una variable de tipo `DataTable`.

Por ejemplo, imaginemos que extraemos información de un catálogo de productos:

|Titulo|Precio|URL|
|---|---|---|
|Teclado|80000|`https://ejemplo.com/teclado`|
|Mouse|45000|`https://ejemplo.com/mouse`|
|Monitor|650000|`https://ejemplo.com/monitor`|

Posteriormente, podemos utilizar ese `DataTable` para:

- Escribir los datos en un archivo Excel.
- Guardarlos en un archivo CSV.
- Recorrer sus filas mediante `For Each Row in Data Table`.
- Filtrar y procesar los registros.
- Enviar la información a una base de datos.
    
## 6. Conceptos que debes recordar

|Concepto|Significado|
|---|---|
|Table Extraction|Técnica para extraer información estructurada de una interfaz.|
|Extract Table Data|Actividad que ejecuta la extracción configurada.|
|Table Extraction Wizard|Asistente visual para configurar las columnas y los datos que se extraerán.|
|Column|Campo o atributo que queremos extraer.|
|Row|Registro que contiene los valores de las columnas.|
|Next Page|Elemento que permite navegar a la siguiente página.|
|DataTable|Estructura que almacena los datos extraídos en filas y columnas.|

>[!important] importante: 
>Table Extraction no es simplemente extraer texto de un elemento. Su propósito es reconocer patrones de información repetidos y organizarlos en una estructura tabular.