---
titulo: Constantes y variables globales en UiPath
tipo: concepto
nivel: 🌱
estado: activo
fecha_creacion: 2026-11-17
ultimo_repaso: 2026-11-17
frecuencia_repaso: 1
nivel_dominio: bajo
tags:
  - software
  - automatizacion
aliases:
  - Constantes y variables globales en UiPath
---
# Constantes y variables globales en UiPath

UiPath permite crear variables globales y constantes desde el panel `Data Manager`. Ambas facilitan la administración de información que puede utilizarse en diferentes partes de un proyecto, pero tienen propósitos distintos.

## 1. Variables globales (Global Variables)

Una variable global es una variable cuyo ámbito (Scope) abarca todo el proyecto, permitiendo acceder a ella desde diferentes workflows sin necesidad de pasarla explícitamente mediante argumentos.

Características:

- Puede utilizarse desde diferentes workflows del proyecto.
- Su valor puede modificarse durante la ejecución.
- Tiene un nombre y un tipo de dato definidos.
- No es necesario pasarla mediante argumentos para acceder a ella desde otros workflows que tengan acceso a esa variable.
- Su ámbito es global dentro del proyecto.
    
Ejemplo:

Imagina que tienes varios workflows encargados de procesar facturas. Todos necesitan conocer la ruta de la carpeta donde se almacenan los archivos.

Podrías crear una variable global:

|Propiedad|Valor|
|---|---|
|Nombre|`Global_InputFolder`|
|Tipo|`String`|
|Scope|`Global`|
|Valor inicial|`"C:\Facturas\Input"`|

Así, diferentes workflows pueden consultar esa ruta sin tener que recibirla mediante un argumento.

## 2. Constantes (Constants)

Una constante es un valor definido que no puede modificarse durante la ejecución del proyecto.
Se utiliza cuando necesitamos almacenar información que debe permanecer fija.

Características:

- Su valor no puede modificarse después de su definición.
- Tiene un nombre y un tipo de dato definidos.
- Puede utilizarse desde diferentes partes del proyecto, según su disponibilidad.
- Evita modificar accidentalmente valores que deben permanecer constantes.
    
Ejemplo:

Imagina que necesitas utilizar una tasa de impuesto fija en diferentes workflows:

|Propiedad|Valor|
|---|---|
|Nombre|`TaxRate`|
|Tipo|`Decimal`|
|Valor|`0.19`|

Los workflows pueden consultar `TaxRate`, pero no modificar su valor.

## 3. Diferencias entre variables locales, globales y constantes

|Característica|Variable local|Variable global|Constante|
|---|---|---|---|
|Propósito|Almacenar información dentro de un ámbito específico.|Compartir información en diferentes workflows.|Almacenar un valor que no debe cambiar.|
|Puede modificar su valor|Sí|Sí|No|
|Ámbito|Scope definido|Global|Según su disponibilidad en el proyecto|
|Se puede utilizar en otros workflows|No directamente|Sí|Sí, según su disponibilidad|
|Requiere argumentos para compartir información|Sí, si se necesita comunicar con otro workflow|No|No, si está disponible globalmente|

## 4. Creación de variables globales y constantes

Puedes crearlas desde el panel `Data Manager` siguiendo estos pasos:

1. Abrir `Data Manager`.
2. Hacer clic derecho sobre la sección de variables.
3. Seleccionar `New`.
4. Elegir una de las siguientes opciones:
    - `Global Variable`.
    - `Constant`.
        
![Pasted image 20261020161549](Pasted%20image%2020261020161549.png)

### Convertir una variable local en global

También puedes convertir una variable existente en global modificando su propiedad `Scope` y seleccionando `Global`, siempre que el tipo de variable y las condiciones del proyecto lo permitan.

## 5. Restricciones de modificación

Según las características que estás estudiando, las variables globales y las constantes tienen restricciones sobre sus propiedades estructurales:

|Propiedad|Variable local|Variable global|Constante|
|---|---|---|---|
|Cambiar nombre|Sí|No, después de crearla|No, después de crearla|
|Cambiar tipo|Sí|No, después de crearla|No, después de crearla|
|Cambiar Scope|Sí|No, después de crearla|No aplica como una variable local|
|Cambiar valor durante la ejecución|Sí|Sí|No|
## 6. ¿Cuándo utilizar cada una?

| Situación                                                   | Recomendación   |
| ----------------------------------------------------------- | --------------- |
| Guardar un dato que solo necesita un workflow               | Variable local  |
| Compartir una configuración entre varios workflows          | Variable global |
| Guardar un valor fijo que no debe modificarse               | Constante       |
| Enviar información de un workflow a otro de forma explícita | Argumentos      |

Concepto clave para recordar:

- Variable local: información limitada a un ámbito.
- Variable global: información compartida dentro del proyecto.
- Constante: información cuyo valor permanece fijo.
- Argumento: mecanismo para intercambiar información entre workflows.
    
>[!note] Nota: 
>La disponibilidad y las restricciones concretas de edición pueden variar según la versión de UiPath Studio y el tipo de proyecto. Conviene comprobarlas en la versión que estés utilizando.

