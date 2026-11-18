---
titulo: Interacción con la interfaz de usuario en UiPath
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
  - Interacción con la interfaz de usuario en UiPath
---
# Interacción con la interfaz de usuario en UiPath

Para interactuar con las interfaces gráficas de usuario (GUI) de aplicaciones y navegadores web, UiPath dispone del paquete `UiPath.UIAutomation.Activities`.

Este paquete proporciona actividades que permiten al robot simular acciones de un usuario, como hacer clic, escribir texto, seleccionar opciones o marcar casillas.

## Principales actividades

|Actividad|Descripción|
|---|---|
|`Use Application/Browser`|Indica la aplicación de escritorio o el navegador con el que se va a trabajar. Sirve como contenedor para organizar las actividades de automatización.|
|`Click`|Hace clic sobre un elemento de la interfaz, como un botón, enlace, icono o imagen.|
|`Type Into`|Escribe texto en un campo de entrada, como una caja de texto.|
|`Check/Uncheck`|Marca o desmarca una casilla de verificación (checkbox).|
|`Select Item`|Selecciona una opción de un elemento compatible, como una lista desplegable.|

## ¿Dónde encontrar estas actividades?

En UiPath Studio podemos buscar las actividades disponibles en el panel Activities, dentro de la categoría UI Automation.

El paquete contiene muchas más actividades, por lo que no es necesario memorizarlas todas. Lo importante es conocer su propósito y saber identificarlas cuando las necesitemos.

## Ejemplo de estructura

Una automatización sencilla para iniciar sesión en una aplicación podría tener esta estructura:

```
Use Application/Browser
│
├── Type Into (campo usuario)
├── Type Into (campo contraseña)
└── Click (botón iniciar sesión)
```

## Conceptos importantes

- `UI Automation`: automatización de interfaces gráficas mediante interacciones con elementos visuales.
    
- `Target (objetivo)`: elemento de la interfaz con el que queremos interactuar, por ejemplo, un botón o campo de texto.
    
- `Selector`: mecanismo que permite identificar un elemento de la interfaz mediante sus propiedades y atributos.
    
- `Contenedor`: actividad que proporciona el contexto de una aplicación o navegador para las actividades que contiene.
    

> [!important] Importante: 
> `Use Application/Browser` no es una acción como hacer clic o escribir texto. Su función es establecer el contexto de la aplicación o navegador sobre el que se ejecutarán las demás actividades.

![Pasted image 20261101134957](Pasted%20image%2020261101134957.png)