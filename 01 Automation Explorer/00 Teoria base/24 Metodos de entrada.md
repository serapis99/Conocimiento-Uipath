---
titulo: Métodos de entrada
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
  - Métodos de entrada
---
## Métodos de entrada (Input Methods)

Los métodos de entrada determinan cómo UiPath envía acciones a una aplicación, por ejemplo, hacer clic, escribir texto o ejecutar atajos de teclado.

| Método             | ¿Cómo funciona?                                                                                              | Compatibilidad                                             | Ejecución en segundo plano | Velocidad |
| ------------------ | ------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------- | -------------------------- | --------- |
| Hardware Events    | Simula las acciones físicas del usuario mediante el mouse y teclado, comunicándose con el sistema operativo. | 100% – Todas las aplicaciones.                             | No                         | 50%       |
| SendWindowMessages | Envía mensajes directamente a la ventana de la aplicación, simulando las interacciones del usuario.          | 80%                                                        | Sí                         | 50%       |
| Simulate           | Interactúa directamente con los elementos de la interfaz gráfica, sin depender del hardware.                 | 99% – Aplicaciones web / 60% – Aplicaciones de escritorio. | Sí                         | 100%      |
| ChromiumAPI        | Se comunica directamente con el navegador mediante el protocolo DevTools de Chromium.                        | 100% – Chrome y Edge.                                      | Sí                         | 50%       |

## Características adicionales

| Característica                                  | Hardware Events | SendWindowMessages | Simulate | ChromiumAPI |
| ----------------------------------------------- | --------------- | ------------------ | -------- | ----------- |
| Soporte de atajos de teclado (Hotkeys)          | Sí              | Sí                 | No       | Sí          |
| Vaciar campo automáticamente (Auto empty field) | No              | No                 | Sí       | Sí          |
| Requiere interacción con mouse/teclado físico   | Sí              | No                 | No       | No          |
| Interfiere con el usuario                       | Sí              | No                 | No       | No          |

## Casos de uso y recomendaciones

|Método|¿Cuándo utilizarlo?|Ejemplo|
|---|---|---|
|Hardware Events|Cuando necesitas máxima compatibilidad con aplicaciones, incluso aquellas que no admiten otros métodos.|Automatizar aplicaciones mediante clics y escritura como lo haría una persona.|
|SendWindowMessages|Cuando necesitas enviar mensajes a una ventana y ejecutar la automatización en segundo plano.|Interactuar con aplicaciones de escritorio que responden a mensajes de ventana.|
|Simulate|Cuando buscas rapidez y precisión al interactuar con elementos de interfaces gráficas.|Hacer clic en botones o escribir en campos de texto.|
|ChromiumAPI|Cuando automatizas aplicaciones web que funcionan en navegadores basados en Chromium.|Extraer información de páginas web o automatizar formularios en Chrome y Edge.|

## Conceptos importantes para recordar

- Hardware Events: simula las acciones físicas del usuario. Necesita controlar el mouse y teclado.
- SendWindowMessages: envía mensajes a las ventanas de las aplicaciones.
- Simulate: interactúa directamente con los elementos de la interfaz. Generalmente es el método más rápido.
- ChromiumAPI: se comunica directamente con el navegador mediante DevTools.
    
>[!abstract] Importante: 
>Los métodos de entrada se pueden seleccionar a nivel de actividad (Activity Level). Por tanto, puedes utilizar diferentes métodos dentro de un mismo flujo de trabajo según las necesidades de cada interacción.