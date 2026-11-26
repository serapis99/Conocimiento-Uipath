La herramienta `App/Web recorder` nos permite grabar los pasos o el proceso que se hace en la interface grafica del usuario con esto podemos tener todas las posibles actividades que se usan en el proceso con esto podemos automatizar mas rápido. aunque debemos validar las actividades creadas automáticamente ya que pueden crear varias que no necesitemos para el proceso.

![Pasted image 20261117180616](Adjuntos/Pasted%20image%2020261117180616.png)

una vez que le damos click a `App/web Recorder` nos aparecerá la herramienta el cual tiene varias herramientas que nos permitirá modificar las actividades y la grabación que estamos haciendo.

![Pasted image 20261117180911](Adjuntos/Pasted%20image%2020261117180911.png)

- `botón de pausar o iniciar grabación`: inicia o pausa la grabación del proceso 
- `botón de guardar`: nos permite guardar los pasos grabados y volver a uipath Studio
- `botón Object Repository`: nos permite crear o reutilizar un objeto
- `botón de configuración`: nos permite validar el target, anchor.
- `Input method`:  nos permite seleccionar el metodo de entrada que se usaran en la grabacion.
	- Auto
	- Chromium API
	- Window Messages
	- Simulate
	- Hardware Events
- `change UI framework (f4)`

## Cuadro resumen: acciones y actividades:

depende de las actividades tendremos algunas actividades que podremos cambiar solo debemos acercarnos a la parte de abajo del elemento que requiere que se realice en la actividad. 

![Pasted image 20261117182011](Adjuntos/Pasted%20image%2020261117182011.png)

| Acción del usuario | Actividad generada | Registro |
|---|---|---|
| Clic en botón, enlace, icono o imagen | `Click` | Automático |
| Escribir en un campo de texto | `Type Into` | Automático |
| Marcar o desmarcar checkbox | `Check / Uncheck` | Automático |
| Enviar atajos de teclado | `Keyboard Shortcuts` | Automático |
| Seleccionar opción de lista desplegable | `Select Item` | Automático |
| Copiar texto | `Get Text` | Manual |
| Pasar el cursor sobre un elemento | `Hover` | Manual |
| Resaltar un elemento | `Highlight` | Manual |

