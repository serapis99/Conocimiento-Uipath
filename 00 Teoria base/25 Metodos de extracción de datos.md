---
titulo: Métodos de extracción de datos
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
  - Métodos de extracción de datos
---
## Métodos de extracción de datos (Output Methods)

Los métodos de salida determinan cómo Uipath obtiene información de los elementos de una interfaz gráfica (UI), generalmente texto.

Uipath dispone de tres métodos principales:

### 1. Tabla comparativa general

|Característica|FullText|Native|OCR|
|---|---|---|---|
|Descripción|Extrae texto directamente de la interfaz.|Extrae texto mediante la tecnología GDI de Windows.|Reconoce caracteres a partir de imágenes.|
|Compatibilidad|La mayoría de aplicaciones compatibles.|Aplicaciones que utilizan GDI.|Imágenes y entornos virtuales.|
|Velocidad|Muy rápida|Media|Muy lenta|
|Precisión|100%|100% en aplicaciones compatibles con GDI.|Variable según la calidad de la imagen y configuración.|
|Ejecución en segundo plano|Sí|No|No|
|Extraer texto oculto|Sí|No|No|
|Entornos virtuales|No|No|Sí|
|Captura posición del texto|No|Sí|Sí|
|Captura formato y color|No|Sí|No se especifica captura de formato; reconoce la posición del texto.|

### 2. Características particulares

|Método|Características adicionales|
|---|---|
|FullText|Es el método predeterminado. Puede extraer texto oculto, por ejemplo, opciones de una lista desplegable. Permite ignorar mensajes ocultos y extraer solamente el texto visible.|
|Native|Puede identificar caracteres separadores (comas, espacios, etc.). Permite especificar determinados separadores e ignorar los demás. Captura información sobre la posición y formato del texto, incluido su color.|
|OCR|Reconoce caracteres y sus posiciones a partir de imágenes. Puede utilizar diferentes motores OCR.|

### 3. Motores OCR disponibles

OCR (Optical Character Recognition) es una tecnología que permite reconocer texto dentro de imágenes.

|Motor OCR|Desarrollador|Disponibilidad|
|---|---|---|
|Google Tesseract|Google / comunidad de código abierto|Gratuito|
|Microsoft MODI|Microsoft|Tecnología antigua|
|OmniPage|Tungsten Automation (anteriormente Kofax)|Comercial|
|ABBYY Embedded|ABBYY|Según licencia|
|IntelligentOCR|ABBYY|Comercial|

## 4. ¿Cuándo utilizar cada método?

|Situación|Método recomendado|Motivo|
|---|---|---|
|Extraer texto rápidamente de una aplicación.|FullText|Es el método más rápido.|
|Extraer opciones ocultas de una lista desplegable.|FullText|Puede reconocer texto oculto.|
|Extraer texto junto con su posición y color.|Native|Captura información de formato y posición.|
|Extraer texto de una aplicación compatible con GDI.|Native|Está diseñado para este tipo de aplicaciones.|
|Leer texto dentro de una imagen.|OCR|Reconoce caracteres visualmente.|
|Extraer texto de un entorno virtual.|OCR|Es el único de los tres compatible con entornos virtuales.|
|Ejecutar la extracción en segundo plano.|FullText|Permite trabajar sin interferir con el usuario.|

## 5. Conceptos importantes para recordar

- FullText: extrae texto visible y oculto. Es el más rápido, tiene una precisión indicada del 100% y funciona en segundo plano.
    
- Native: extrae texto mediante GDI. Permite obtener posición y formato, pero no funciona en segundo plano ni extrae texto oculto.
    
- OCR: reconoce texto visualmente a partir de imágenes. Es el más lento, su precisión es variable y permite trabajar con entornos virtuales.
    

>[!abstract] Importante 
>Los métodos de extracción también se pueden seleccionar a nivel de actividad (Activity Level). La elección depende de la aplicación, la velocidad requerida, la visibilidad del texto y el entorno de ejecución.

