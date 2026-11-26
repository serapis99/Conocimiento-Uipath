---
titulo: Condicional Switch en UiPath
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
  - Condicional Switch en UiPath
---
# Condicional Switch en UiPath

La estructura condicional Switch permite evaluar una expresión y ejecutar diferentes bloques de actividades dependiendo de su valor.

Es especialmente útil cuando necesitamos comparar una misma variable o expresión con múltiples valores posibles.

En UiPath debemos distinguir cómo se implementa dependiendo del tipo de workflow que estemos utilizando: `Sequence` o `Flowchart`.

## 1. Switch en Sequences (Secuencias)

En un workflow de tipo `Sequence` utilizamos la actividad `Switch`.

Esta actividad funciona de la siguiente manera:

1. Recibe una expresión o variable.
2. Evalúa su valor.
3. Compara el resultado con los diferentes casos (Cases).
4. Ejecuta las actividades correspondientes al caso que coincide.
5. Si ningún caso coincide, ejecuta las actividades de `Default`, si está configurado.

Ejemplo:

Imagina que tenemos una variable llamada `DiaSemana` de tipo `Int32`.

```
DiaSemana = 2
```

Configuramos el `Switch` utilizando `DiaSemana` como expresión.

| Case      | Actividades              |
| --------- | ------------------------ |
| `1`       | Mostrar "Lunes".         |
| `2`       | Mostrar "Martes".        |
| `3`       | Mostrar "Miércoles".     |
| `4`       | Mostrar "Jueves".        |
| `5`       | Mostrar "Viernes".       |
| `Default` | Mostrar "Día no válido". |

Como el valor de `DiaSemana` es `2`, se ejecutará el caso correspondiente a `"Martes"`.

![Pasted image 20261118090314](Adjuntos/Pasted%20image%2020261118090314.png)
### Propiedades principales

| Propiedad    | Descripción                                              |
| ------------ | -------------------------------------------------------- |
| Expression   | Variable o expresión cuyo valor queremos evaluar.        |
| TypeArgument | Tipo de dato de la expresión.                            |
| Cases        | Valores posibles que se compararán con la expresión.     |
| Default      | Actividades que se ejecutan cuando ningún caso coincide. |

## 2. Switch en Flowcharts (Diagramas de flujo)

En un workflow de tipo `Flowchart` utilizamos la actividad Flow Switch.

Su funcionamiento es parecido al `Switch` de una `Sequence`: evalúa una expresión y permite dirigir la ejecución hacia diferentes caminos dependiendo del valor obtenido.

La diferencia principal está en cómo se representa el flujo:

- Cada caso (Case) tiene una conexión de salida.
- La conexión correspondiente al valor coincidente determina el camino que seguirá la automatización.
- La salida `Default` se utiliza cuando ninguno de los casos coincide.

Ejemplo:

Tenemos una variable `TipoDocumento` de tipo `String`:

```
TipoDocumento = "CC"
```

Configuramos `Flow Switch` con la expresión `TipoDocumento`.

| Case          | Camino de ejecución              |
| ------------- | -------------------------------- |
| `"CC"`        | Procesar cédula de ciudadanía.   |
| `"CE"`        | Procesar cédula de extranjería.  |
| `"NIT"`       | Procesar NIT.                    |
| `"Pasaporte"` | Procesar pasaporte.              |
| `Default`     | Tipo de documento no reconocido. |

Como el valor es `"CC"`, el flujo seguirá la conexión correspondiente a ese caso.

![Pasted image 20261118090719](Adjuntos/Pasted%20image%2020261118090719.png)

### Propiedades principales

| Propiedad    | Descripción                                               |
| ------------ | --------------------------------------------------------- |
| Expression   | Variable o expresión que se evalúa.                       |
| TypeArgument | Tipo de dato de la expresión.                             |
| Cases        | Valores que determinan las diferentes rutas de ejecución. |
| Default      | Ruta que se sigue cuando no coincide ningún caso.         |

## 3. Diferencias entre Switch y Flow Switch

| Característica      | Switch                                     | Flow Switch                         |
| ------------------- | ------------------------------------------ | ----------------------------------- |
| Tipo de workflow    | Sequence                                   | Flowchart                           |
| Propósito           | Seleccionar una alternativa según un valor | Seleccionar una ruta según un valor |
| Evaluación          | Expresión                                  | Expresión                           |
| Casos               | Cases                                      | Cases                               |
| Caso predeterminado | Default                                    | Default                             |
| Organización        | Bloques de actividades                     | Conexiones entre actividades        |

## 4. Diferencias entre If y Switch

Aunque ambas estructuras permiten tomar decisiones, tienen propósitos diferentes.

| Característica  | If                                                         | Switch                                       |
| --------------- | ---------------------------------------------------------- | -------------------------------------------- |
| Evaluación      | Condición booleana                                         | Valor de una expresión                       |
| Alternativas    | True y False                                               | Múltiples casos                              |
| Comparaciones   | Permite condiciones complejas (`>`, `<`, `=`, `And`, `Or`) | Compara la expresión con valores específicos |
| Uso recomendado | Evaluar condiciones y reglas                               | Seleccionar entre diferentes alternativas    |

Ejemplo utilizando If:

Queremos clasificar una edad según rangos:

```vb
If Edad < 18
    "Menor de edad"
Else If Edad < 65
    "Adulto"
Else
    "Adulto mayor"
```

Utilizamos `If` porque necesitamos evaluar rangos numéricos.

Ejemplo utilizando Switch:

Queremos identificar el tipo de documento:

```vb
TipoDocumento = "CC"
```

- `"CC"` → Cédula de ciudadanía.
- `"CE"` → Cédula de extranjería.
- `"NIT"` → Identificación tributaria.
- `"Pasaporte"` → Pasaporte.
- `Default` → Documento desconocido.

Utilizamos `Switch` porque comparamos una misma variable con diferentes valores específicos.

## 5. Concepto clave para recordar

UiPath dispone de dos actividades Switch según el tipo de workflow:

- Switch: se utiliza en `Sequences` y organiza las alternativas mediante bloques de actividades.
- Flow Switch: se utiliza en `Flowcharts` y organiza las alternativas mediante conexiones visuales.

Ambas permiten seleccionar una alternativa entre varios valores posibles.

Una forma sencilla de recordarlo:

- `If` = ¿Se cumple esta condición?
- `Switch` = ¿Cuál de estos valores tiene esta variable?