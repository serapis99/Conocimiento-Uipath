---
titulo: Orchestrator Manager access
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
  - Orchestrator Manager access
---
#  Orchestrator Manager access

Nos dirigimos al `Orquestator` de uipath, para esto damos click al menú y seleccionamos `Orchestrator`

![Pasted image 20261007140202](Pasted%20image%2020261007140202.png)

Nos dirigimos al `tenant` -> `Manage access` -> `Assign access` 

![Pasted image 20261007140506](Pasted%20image%2020261007140506.png)

--- 

## Usuario

Lo primero que hacemos es buscar al usuario al que estamos invitando.

![Pasted image 20261007140801](Pasted%20image%2020261007140801.png)

el siguiente paso es agregar los roles que va a tener este usuario en este caso `Robot-TenantScopedOnly`. 

![Pasted image 20261007140939](Pasted%20image%2020261007140939.png)

por ultimo, le asignamos un `UI Profile` y `Personal automation setup`.

>[!note] Nota:
>validar esto si al invitado no le carga el rol de desarrollo suele pasar que si no tiene perfil no se le da el rol.

![Pasted image 20261007141219](Pasted%20image%2020261007141219.png)


---

>[!important] importante
> - [roles](https://docs.uipath.com/es/orchestrator/automation-cloud/latest/user-guide/default-roles#robot-role): validar los permisos necesarios para los robots de uipath.
> - [documentacion](https://docs.uipath.com/es): para ver la documentación de uipath.
> - [foro](https://forum.uipath.com/): para comunicarnos con la comunidad de uipath resolver problemas.
> - [marketplace](https://marketplace.uipath.com/): nos permite encontrar desarrollos de uipath o partner 
