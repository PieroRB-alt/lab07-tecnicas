# Tarea: Mi prompt avanzado

## Tarea elegida
Generar casos de prueba funcionales y de borde para un formulario web de registro de usuarios con validaciones de correo, contraseña segura y edad mínima.

## Version 1: prompt basico
```text
Dame casos de prueba para un registro de usuarios.
```
- **Técnica agregada:** Ninguna.
- **Por qué y qué mejoró:** Sirve como punto de partida. La IA devolvió una lista general en texto plano.

## Version 2
```text
Actua como ingeniero QA senior especializado en aplicaciones web.
Crea 5 casos de prueba para un formulario de registro de usuarios que exige correo valido, contrasena de al menos 8 caracteres con un numero, y edad minima de 18 anos.
Responde en una tabla con columnas: ID, Escenario, Datos de entrada, Resultado esperado.
```
- **Técnica agregada:** Role prompting y formato definido.
- **Por qué y qué mejoró:** Al definir el rol y las reglas del negocio, la IA dejó de dar respuestas genéricas y entregó una tabla técnica ordenada y alineada a los requisitos.

## Version 3: prompt final
```text
<rol>Actua como ingeniero QA senior especializado en pruebas funcionales web.</rol>
<contexto>Formulario de registro de usuarios: requiere correo con formato valido, contrasena de minimo 8 caracteres con al menos un numero, y edad minima de 18 anos.</contexto>
<ejemplos>
| CP-00 | Registro exitoso | correo: ana@mail.com, pass: Clave123, edad: 22 | Usuario registrado y redirigido al panel |
</ejemplos>
<tarea>Piensa paso a paso que validaciones y casos limite pueden fallar, y genera 6 casos de prueba (positivos y negativos).</tarea>
<formato>Tabla Markdown con las columnas: ID, Escenario, Datos de entrada, Resultado esperado.</formato>
```
- **Técnica agregada:** Prompt estructurado (etiquetas), Few-shot y Chain of Thought (pensar paso a paso).
- **Por qué y qué mejoró:** Las etiquetas evitaron que se mezclaran las instrucciones, el ejemplo fijó el estilo exacto de cada celda y el razonamiento paso a paso aseguró la inclusión de casos límite como edad 17 o contraseña sin números.

## Tecnicas usadas en el prompt final
| Técnica | Parte del prompt donde se aplica |
| :--- | :--- |
| Role prompting | `<rol>Actua como ingeniero QA senior...</rol>` |
| Prompt estructurado | Uso de etiquetas `<rol>`, `<contexto>`, `<ejemplos>`, `<tarea>`, `<formato>` |
| Few-shot (One-shot) | Bloque `<ejemplos>` con la fila modelo `CP-00` |
| Chain of Thought | Indicación "Piensa paso a paso que validaciones y casos limite pueden fallar" |

## Evaluacion del resultado
| Criterio | Cumple (Si/No) |
| :--- | :---: |
| ¿Respeta las 4 columnas exactas de la tabla? | Si |
| ¿Incluye casos positivos y negativos? | Si |
| ¿Evalúa la edad mínima de 18 años y la regla de contraseña? | Si |
| ¿Sigue el mismo estilo de redacción del ejemplo dado? | Si |

## Por que elegi estas tecnicas
Elegí Role prompting para obtener vocabulario técnico de QA, Prompt estructurado para separar claramente las reglas de negocio de las instrucciones, Few-shot para asegurar que el formato de los datos de entrada sea consistente, y Chain of Thought para que la IA analice los casos límite antes de escribir la tabla. No usé descomposición porque toda la tarea se resuelve de forma limpia en una sola interacción bien estructurada.