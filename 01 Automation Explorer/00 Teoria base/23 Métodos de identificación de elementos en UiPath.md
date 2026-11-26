---
titulo: Métodos de identificación de elementos en UiPath
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
  - Métodos de identificación de elementos en UiPath
---
# Métodos de identificación de elementos en UiPath

Para interactuar con una aplicación mediante UI Automation, UiPath necesita identificar primero el elemento de la interfaz con el que queremos trabajar. A este elemento se le denomina `Target` (objetivo).

Por ejemplo, si queremos hacer clic en un botón llamado Iniciar sesión, UiPath debe localizar ese botón antes de ejecutar la acción.

## 1. Target y Anchor

Un `Target` es el elemento principal con el que queremos interactuar.

Un `Anchor` es un elemento de referencia que ayuda a UiPath a localizar o distinguir el `Target`. Es especialmente útil cuando el elemento objetivo no tiene suficientes atributos para identificarlo de forma única.

Ejemplo: imaginemos que queremos identificar un botón que no tiene un nombre reconocible. Podemos utilizar como referencia un texto cercano, como «Contraseña», para ayudar a ubicarlo.

### Recomendaciones sobre los Anchor

- Utilizar un `Anchor` cuando realmente ayude a identificar el `Target`.
- Preferir la menor cantidad de referencias necesarias.
- Evitar referencias que puedan cambiar frecuentemente, como textos dinámicos o elementos que aparecen y desaparecen.
- Más referencias no significan necesariamente una identificación más fiable.

El objetivo es encontrar un equilibrio entre precisión y estabilidad.

## 2. Métodos de identificación (Targeting methods)

UiPath dispone de diferentes métodos para identificar un `Target`. Estos métodos se organizan según su prioridad y capacidad de recuperación cuando uno de ellos no consigue localizar el elemento.

### 2.1. Método principal (Primary targeting methods)

Utiliza selectores para identificar los elementos de la interfaz.

| Método          | Descripción                                                                                                                                          |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Strict Selector | Identifica el elemento utilizando atributos específicos de la interfaz. Es preciso, pero puede fallar si cambian atributos importantes del elemento. |
| Fuzzy Selector  | Busca el elemento utilizando coincidencias aproximadas de sus atributos. Es más tolerante a ciertos cambios en la interfaz.                          |

### 2.2. Método secundario (Secondary targeting method)

| Método               | Descripción                                                                                                                                        |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Computer Vision (CV) | Analiza visualmente la interfaz para reconocer elementos y su posición. Puede ser útil cuando los selectores no consiguen identificar el elemento. |

### 2.3. Método terciario (Tertiary targeting method)

| Método | Descripción                                                                                                         |
| ------ | ------------------------------------------------------------------------------------------------------------------- |
| Image  | Identifica el elemento mediante una imagen de referencia y compara su apariencia con lo que se muestra en pantalla. |

## 3. Orden de búsqueda de los métodos

La búsqueda sigue una jerarquía:

1. Primary: Strict Selector y Fuzzy Selector.
2. Secondary: Computer Vision.
3. Tertiary: Image.

El comportamiento depende de una configuración del proyecto llamada `Wait for primary targeting method until timeout`.

Con esta opción habilitada (valor predeterminado en proyectos nuevos desde determinadas versiones):

- Strict Selector comienza la búsqueda primero.
- Fuzzy Selector comienza poco después.
- Strict tiene prioridad sobre Fuzzy.
- Si los métodos principales no encuentran el elemento dentro del tiempo asignado, se utilizan los métodos secundarios y terciarios.

Si la opción está deshabilitada, los métodos pueden competir dentro de un mismo tiempo de espera, respetando la prioridad establecida.

## 4. Consideraciones importantes

- UiPath permite agregar manualmente hasta tres Anchors por cada Target.
- UiPath puede detectar automáticamente un Anchor cuando identifica un Target.
- No siempre se necesitan Anchors. Si el Strict Selector identifica correctamente el elemento, estos no se utilizan en ese método.
- Si existen varios elementos similares, los Anchors ayudan a distinguir cuál es el correcto.
- Computer Vision e Image son métodos alternativos de identificación, no necesariamente mejores que los selectores.

## 5. Resumen general

| Jerarquía  | Método          | Tipo de identificación    |
| ---------- | --------------- | ------------------------- |
| Principal  | Strict Selector | Atributos específicos     |
| Principal  | Fuzzy Selector  | Coincidencias aproximadas |
| Secundario | Computer Vision | Análisis visual           |
| Terciario  | Image           | Comparación de imágenes   |

>[!hint] Una idea para recordar: 
>UiPath intenta identificar los elementos mediante selectores porque suelen proporcionar una identificación más estructurada. Si estos no funcionan, puede recurrir a métodos visuales como Computer Vision e Image.

Documentación oficial: [Advanced descriptor configuration - UiPath](https://docs.uipath.com/activities/other/latest/ui-automation/advanced-descriptor-configuration?utm_source=chatgpt.com).