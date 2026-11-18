# Práctica clase 01: casos del registro de MiniModa con IA

**Sitio:** https://minimoda-navy.vercel.app/registro

> Así tiene que quedar tu entrega. Reemplazá cada `___tu respuesta aquí___` con lo tuyo.

## 1. Preparación
- Navegador y fecha: Google chrome 18/11/2026

## 2. Superficie elegida
- Elegí (chat o cowork): Chat
- Por qué: Puede leer desde el navegador (gemini)

## 3. Preguntas a Gemini
| # | Pregunta | Respuesta (resumen) | ¿Acierto o error/invento? |
|---|----------|---------------------|---------------------------|
| 1 | ¿Qué campos pide el formulario de registro de https://minimoda-navy.vercel.app/registro? | Nombre email apellido y contraseña, confirmar contraseña, pais y casilla de terminos y condiciones |Error ; declara campo de texto en nombre y se pueden ingresar numeros |
| 2 | ¿Cuál es el largo mínimo de la contraseña y qué edad se permite? | entre 8 caracteres y entre 13 y 120 años  | acierto|
| 3 | ¿Qué pasa si no acepto los términos? | no permite completar el registro y muestra el mensaje de error:
"Debés aceptar los términos." | acierto |

- Un acierto:Gemini identifico correctamente la longitud minima de la contraseña y el rango de edad permitido
- Un error o invento:En la parte de nombre que declara (campo de texto)

## 4. Primer modo
- Superficie y modo: Gemini - chat, modo pro.
- Prompt de ejemplo:
  ```
  Sos QA. Vamos a probar el registro de https://minimoda-navy.vercel.app/registro
  Campos: nombre, email, contraseña, confirmar contraseña, edad, país y aceptar términos.
  1. Listá las reglas que se ven, los datos válidos e inválidos y los valores límite.
  2. Escribí 6 casos de prueba con: título, precondiciones, pasos con datos concretos,
     resultado esperado, prioridad (high/medium/low) y tipo (functional/negative/boundary).
  No inventes mensajes: si no sabés el texto exacto, marcalo "A VERIFICAR".
  ```
- Qué devolvió: Gemini identificó las reglas del formulario los datos válidos e inválidos y los valores límite de contraseña y edad. Generó 6 casos de prueba con título, precondiciones, pasos, resultado esperado, prioridad y tipo.
Los casos que genero son los siguientes :
TC-01: Registro exitoso con datos completamente válidos
TC-02: Validación de límite inferior inválido en Contraseña (7 caracteres)
TC-03: Validación de límite inferior válido en Edad (13 años)
TC-04: Validación de límite superior inválido en Edad (121 años)
TC-05: Rechazo de registro por contraseñas que no coinciden
TC-06: Intento de registro sin aceptar términos y condiciones
Algunos casos no tienen datos de ejemplo en todos los casos y los mensajes desconocidos salen marcados como " a verificar "
## 5. Otra superficie: comparación en 3 líneas
1. Chat (Gemini): Generó 6 casos de prueba con reglas, datos válidos e inválidos y valores límite, marcando los mensajes desconocidos como "A VERIFICAR"
2.Antigravity: Generó 6 casos de prueba más detallados, incluyendo validaciones, valores límite y mensajes de error específicos.
3.Conclusión: Antigravity es más detallado (ademas pidio mas permisos a la hora de realizar el analisis) pero Gemini fue más cuidadoso con la información no confirmada

## 6. Mis 3 mejores casos (cargados en Qase, proyecto MiniModa)
Formato del título: `Registro: <qué se prueba>`
Captura de la suite en Qase con tus casos: `evidencias/qase-suite-casos.png`

### Caso 1: ___tu respuesta aquí___
- Precondiciones: ___tu respuesta aquí___
- Pasos: ___tu respuesta aquí___
- Resultado esperado: ___tu respuesta aquí___
- Evidencia: `evidencias/qase-MM-4-registro-alta-exitosa.png`

### Caso 2: ___tu respuesta aquí___
- Precondiciones: ___tu respuesta aquí___
- Pasos: ___tu respuesta aquí___
- Resultado esperado: ___tu respuesta aquí___
- Evidencia: `evidencias/qase-MM-5-registro-password-7.png`

### Caso 3: ___tu respuesta aquí___
- Precondiciones: ___tu respuesta aquí___
- Pasos: ___tu respuesta aquí___
- Resultado esperado: ___tu respuesta aquí___
- Evidencia: `evidencias/qase-MM-6-registro-edad-12.png`

## 7. Mapa del harness
| Pieza | En lo que usé |
|-------|---------------|
| Modelo | ___tu respuesta aquí___ |
| App | ___tu respuesta aquí___ |
| Harness | ___tu respuesta aquí___ |
| MCP | ___tu respuesta aquí___ |
| Skill | ___tu respuesta aquí___ |

## 8. Entrega
- Link de tu repo (pegalo también en el Telegram): ___tu respuesta aquí___
