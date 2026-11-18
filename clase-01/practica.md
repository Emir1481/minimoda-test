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
| 3 | ¿Qué pasa si no acepto los términos? | no permite completar el registro y muestra el mensaje de error:"Debés aceptar los términos." | acierto |

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

### Caso 1: Registro: alta exitosa con datos válidos
- Precondiciones: El usuario se encuentra en el formulario de registro de MiniModa, con todos los campos vacíos y un email no registrado anteriormente.
- Pasos: Ingresar nombre "Laura Martínez", email "laura.martinez.qa001@example.com", contraseña "PassTest2026", confirmar la misma contraseña, edad 28, seleccionar Argentina, aceptar los términos y hacer clic en "Crear cuenta".
- Resultado esperado:El sistema procesa el formulario, crea la cuenta y muestra un mensaje de registro exitoso: "¡Registro exitoso! Bienvenido/a a MiniModa, Laura Martínez. Te enviamos un email de bienvenida (ver Bandeja)."
- Evidencia: `evidencias/qase-MM-1-registro-alta-exitosa.png`

### Caso 2: Registro: rechazo de contraseña de 7 caracteres
- Precondiciones: El usuario se encuentra en el formulario de registro de MiniModa, con todos los campos vacíos.
- Pasos: Ingresar nombre "Carlos Gómez", email "carlos.qa002@example.com", contraseña "Abc1234", confirmar la misma contraseña, edad 30, seleccionar Chile, aceptar los términos y hacer clic en "Crear cuenta".
- Resultado esperado: El sistema rechaza el registro porque la contraseña tiene 7 caracteres y el mínimo permitido es 8. Se muestra un mensaje de validación. Texto exacto: "La contraseña debe tener al menos 8 caracteres."
- Evidencia: `evidencias/qase-MM-2-registro-password-7.png`

### Caso 3: Registro: contraseñas que no coinciden
- Precondiciones:El usuario se encuentra en el formulario de registro de MiniModa, con todos los campos vacíos.
- Pasos:Ingresar nombre "Mariana López", email "mariana.qa005@example.com", contraseña "Sistema2026", confirmar contraseña con "Sistema2025", edad 30, seleccionar Colombia, aceptar los términos y hacer clic en "Crear cuenta".
- Resultado esperado: El sistema rechaza el registro porque las contraseñas no coinciden. Se muestra un mensaje de validación asociado al campo Confirmar contraseña. Texto exacto:"Las contraseñas no coinciden."
- Evidencia: `evidencias/qase-MM-3-registro-password-no-coinciden.png`

## 7. Mapa del harness
| Pieza | En lo que usé |
|-------|---------------|
| Modelo |Gemini Pro 3.1 en chat y Gemini 3.8 Flash en antigravity (medium) |
| App | Gemini Chat y Google Antigravity|
| Harness |El entorno propio de chat y de antigravity (IDE / CLI runtime)|
| MCP | No use |
| Skill | No use |

## 8. Entrega
- Link de tu repo (pegalo también en el Telegram): ___tu respuesta aquí___
