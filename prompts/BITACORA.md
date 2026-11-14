# Bitacora de tecnicas avanzadas
#### Laboratorio 07: Tecnicas Avanzadas de Prompting.
#### Herramienta de IA usada: GhatGPT

## Ejercicio 2: Zero-shot, one-shot y few-shot

| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
| :--- | :---: | :--- | :---: |
| Zero-shot | 5 | Lista numerada con explicaciones libres | No |
| One-shot | 5 | Texto con flecha y etiqueta, pero con variaciones | No |
| Few-shot | 5 | "comentario" -> Etiqueta (estricto línea por línea) | Si |

## Ejercicio 3: Chain of Thought

| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
| :--- | :--- | :---: | :---: |
| Directo | 318.60 | No | Si |
| Paso a paso | 318.60 | Si | Si |

Ver el razonamiento es importante porque permite auditar cada cálculo intermedio y verificar que se aplicó el orden correcto (descuento antes del IGV). Si hubiera un error, se detecta exactamente en qué paso ocurrió en lugar de confiar a ciegamente en un número final.

## Ejercicio 4: Role prompting

| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
| :--- | :--- | :--- | :--- |
| A. Sin rol | Sencillo | Ejemplo básico y algo de código | Público general |
| B. Rol docente | Intermedio | Analogías cotidianas | Principiantes sin experiencia |
| C. Rol senior | Técnico (tipos de dato, memoria, alcance) | Código Java concreto | Programadores con base técnica |

## Ejercicio 5: Descomposicion

- **Paso 1:** Entregó los 5 requisitos funcionales principales (registro, actualización de stock, búsqueda, alertas y reportes).
- **Paso 2:** Diseñó las clases necesarias (Producto, Inventario, etc.) con sus atributos y tipos de dato en Java.
- **Paso 3:** Generó el código funcional de la clase Producto coherente con el diseño anterior.
- **Paso 4:** Propuso 3 mejoras concretas (validación de precios negativos, método toString y control de stock).
- **Comparación:** El pedido de una sola vez dio una respuesta genérica y difícil de controlar, mientras que la descomposición produjo un diseño ordenado, revisable y listo para compilar.

## Ejercicio 6: Prompt estructurado y autocritica

| Qué revisar | Cumple (Si/No) |
| :--- | :---: |
| ¿Tiene las 4 columnas pedidas? | Si |
| ¿Incluye el bloqueo después de 3 intentos? | Si |
| ¿Incluye casos con campos vacíos? | Si |
| ¿Indica qué casos agregó en la autocrítica? | Si |
| ¿Hay algún caso repetido o que no tenga sentido? | No |

```text
<rol>Actua como analista de pruebas de software.</rol>
<contexto>Login web con correo y contrasena. La cuenta se bloquea despues de 3 intentos fallidos.</contexto>
<tarea>Piensa paso a paso que puede fallar y escribe 6 casos de prueba.</tarea>
<formato>Tabla con las columnas: ID, escenario, datos de entrada, resultado esperado.</formato>

--- Autocritica ---
Revisa tu tabla: faltan casos limite como campos vacios, correo sin @ o contrasena con espacios? Agrega los que falten e indica cuales agregaste.