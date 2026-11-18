# Práctica Clase 7 · Guía para tu IA (chat o agente)

Pasale este archivo completo a la IA que uses. Ninguna es obligatoria. La IA te ayuda a escribir tests, ordenar resultados, describir capturas y redactar issues; **vos confirmás cada hallazgo en la página**.

## Contexto para la IA

- Soy QA y estoy practicando testing de accesibilidad (WCAG 2.2 AA) y testing visual y responsive.
- Trabajo sobre una página estática de práctica de MiniModa (ficha «Campera polar infantil») con errores **puestos a propósito**. Está en `clase-07/kit/` de mi repo y la sirvo en `http://localhost:5507/` (versión 1) y `http://localhost:5507/index-v2.html` (versión 2). `clase-07/kit/notas-v2.md` dice qué cambio se pidió en la versión 2.
- Uso Playwright (ya lo tengo de la Clase 4) y `@axe-core/playwright`. Rama: `clase-07-a11y`.
- Reglas para la IA: no inventes hallazgos ni datos; marcá A CONFIRMAR lo que no se pueda afirmar; no modifiques los archivos del kit; no hagas merge ni push a `main`; no actualices capturas de referencia sin que yo lo apruebe.

## ¿Qué tiene que validar la persona a mano?

La IA y la herramienta automática no reemplazan esta revisión; recordásela a la persona y no la des por hecha:

- Con VoiceOver o NVDA: ¿cada botón dice qué hace?, ¿el texto alternativo describe la imagen?, ¿el orden de lectura tiene sentido? y ¿cada campo se anuncia con su nombre?
- Con el teclado: ¿se ve el foco?, ¿el orden es lógico? y ¿se puede salir de todo sin trabarse?
- Links: ¿se entiende adónde va cada uno?
- Zoom y celular: ¿con zoom al 200 % y a 375 px se usa todo?

## Paso 1 · Preparar

- **Objetivo:** tener la rama, el kit y la página funcionando.
- **¿Qué hacés?** `git checkout -b clase-07-a11y`; copiás el kit en `clase-07/kit/`; dentro de esa carpeta corrés `python3 -m http.server 5507` (o `python -m http.server 5507`, o `npx http-server -p 5507`); en la raíz del repo, `npm i -D @axe-core/playwright`.
- **Resultado esperado:** la ficha se ve en `http://localhost:5507/` y la versión 2 en `/index-v2.html`.
- **¿Cómo lo verificás?** Abrís las dos URL en el navegador; `git branch` muestra `clase-07-a11y`.
- **Errores comunes:** levantar el servidor fuera de la carpeta del kit (aparece la lista de archivos); el puerto 5507 ocupado (usá otro y cambiá la URL en los tests).

## Paso 2 · Escaneo automático

- **Objetivo:** tener `clase-07/tests/a11y.spec.ts` y `clase-07/resultados/axe.json`.
- **¿Qué hacés?** Pedile a la IA el prompt 2. Revisá la URL, las cinco etiquetas (`wcag2a`, `wcag2aa`, `wcag21a`, `wcag21aa`, `wcag22aa`) y que el test falle si hay violaciones. Corré `npx playwright test clase-07/tests/a11y.spec.ts`. Segunda opinión: Lighthouse en DevTools o `npx pa11y --runner axe --runner htmlcs http://localhost:5507/` (pide Node 22.13 o más; opcional).
- **Resultado esperado:** el test falla y `axe.json` tiene violaciones con regla, impacto, etiquetas y elementos.
- **¿Cómo lo verificás?** Abrí `axe.json` y buscá `"violations"`; cada una tiene `id`, `tags` y `nodes`.
- **Errores comunes:** «No tests found» (creá `clase-07/playwright.config.ts` con `testDir: './tests'` y usá `--config clase-07/playwright.config.ts`); olvidar `wcag22aa` (se pierden reglas de WCAG 2.2); que el test pase siempre porque no tiene la aserción; creer que lo que no aparece en el JSON está bien.

## Paso 3 · Ordenar con IA

- **Objetivo:** hallazgos agrupados por criterio y dos confirmados en la página.
- **¿Qué hacés?** Pegale el JSON a la IA con el prompt 1. Después abrís la página y confirmás dos hallazgos; uno de contraste, medido con el selector de color de las DevTools o con el verificador de WebAIM.
- **Resultado esperado:** una lista por criterio WCAG con regla, selector, impacto y cómo verificar; los ítems incompletos aparte.
- **¿Cómo lo verificás?** Cada criterio tiene número y nivel; el contraste medido coincide con el del JSON.
- **Errores comunes:** copiar a la IA solo una parte del JSON; aceptar un criterio mal asignado sin abrir la página.

## Paso 4 · Teclado

- **Objetivo:** encontrar las barreras de teclado que la herramienta no ve.
- **¿Qué hacés?** Recorrés la página solo con Tab, Shift+Tab, Enter, Espacio, flechas y Esc, sin aceptar el banner de cookies todavía. Respondés: ¿llego a todo? (2.1.1), ¿veo dónde estoy? (2.4.7), ¿el orden tiene sentido? (2.4.3), ¿puedo salir de cada ventana? (2.1.2) y ¿el foco queda a la vista? (2.4.11)
- **Resultado esperado:** una tabla en el informe con cada barrera, su criterio y cómo la encontraste.
- **¿Cómo lo verificás?** Podés repetir cada barrera siguiendo tus pasos.
- **Errores comunes:** usar el mouse «un ratito»; no probar las ventanas que se abren; anotar una barrera sin criterio.

## Paso 5 · Lector de pantalla

- **Objetivo:** escuchar lo que la página declara.
- **¿Qué hacés?** Con NVDA, Narrador, VoiceOver o TalkBack escuchás el botón del carrito, la imagen principal, el aviso al agregar al carrito y el error del formulario de newsletter. Plan B: árbol de accesibilidad de las DevTools (Elements → Accessibility).
- **Resultado esperado:** para cada elemento, qué dijo el lector y qué debería decir.
- **¿Cómo lo verificás?** El entorno del informe tiene el lector y su versión.
- **Errores comunes:** probar sin auriculares en un lugar con ruido; confundir lo que se ve con lo que se anuncia.

## Paso 6 · Tamaños y zoom

- **Objetivo:** tener `clase-07/tests/visual.spec.ts` y revisar la página en 375, 768 y 1280 px, con zoom al 200 % y a 320 px.
- **¿Qué hacés?** Pedile a la IA el prompt 3. Corré `npx playwright test clase-07/tests/visual.spec.ts --update-snapshots` para generar las capturas de la versión 1 y revisalas. En el navegador probá el zoom al 200 % y el ancho de 320 px con el modo dispositivo. Si querés, usá el prompt 4 con las capturas.
- **Resultado esperado:** tres capturas de referencia en `clase-07/tests/visual.spec.ts-snapshots/` y una tabla de tamaños en el informe con lo que se rompe (1.4.4 y 1.4.10).
- **¿Cómo lo verificás?** Las capturas tienen el nombre del sistema (`-linux`, `-darwin` o `-win32`) y la zona con hora aparece tapada (máscara).
- **Errores comunes:** capturar sin desactivar animaciones; no enmascarar `[data-dinamico]` (la hora cambia y el test falla siempre); comparar capturas de sistemas distintos.

## Paso 7 · Regresión visual

- **Objetivo:** comparar la versión 2 contra la referencia de la versión 1 y clasificar cada diferencia.
- **¿Qué hacés?** `PAGINA=http://localhost:5507/index-v2.html npx playwright test clase-07/tests/visual.spec.ts` (en PowerShell: `$env:PAGINA="http://localhost:5507/index-v2.html"; npx playwright test clase-07/tests/visual.spec.ts`) y después `npx playwright show-report`. Clasificá cada diferencia en «cambio esperado» (está en `notas-v2.md`) o «defecto».
- **Resultado esperado:** los tests de la versión 2 fallan y el reporte muestra el diff de cada ancho; el informe tiene la clasificación.
- **¿Cómo lo verificás?** En el reporte, pestañas Diff, Actual y Expected de cada test.
- **Errores comunes:** correr `--update-snapshots` con la versión 2 (la referencia pasa a tener el defecto); un umbral alto que se traga los cambios chicos.

## Paso 8 · Issues y PR

- **Objetivo:** 3 issues en tu repo y un PR sin mergear.
- **¿Qué hacés?** Con el prompt 5, redactá 2 issues con la etiqueta `accesibilidad` y 1 con `visual` (formato CT-DAT §4.3.2: título, descripción, entorno, pasos, obtenido, esperado, criterio, impacto y evidencia). Completá «¿Lo detectó la herramienta?» en el informe. Abrí el PR de `clase-07-a11y` a `main`, sin mergear, con los issues enlazados.
- **Resultado esperado:** PR abierto con `informe-accesibilidad-visual.md`, los dos tests, las capturas, `resultados/` y 3 issues enlazados.
- **¿Cómo lo verificás?** El PR muestra los archivos y los issues; el estado es «Open».
- **Errores comunes:** abrir los issues en el repo de otra persona; mergear el PR; issues sin criterio WCAG ni evidencia.

## Camino corto (sin Node)

- **Objetivo:** hacer la misma práctica sin Node.
- **¿Qué hacés?** Servís el kit con `python3 -m http.server 5507`; escaneás con Lighthouse o con Accessibility Insights for Web (FastPass, sin cuenta); hacés los pasos 4 y 5; sacás capturas de las dos versiones en 375, 768 y 1280 px con el modo dispositivo y las comparás con el prompt 4; abrís los issues igual.
- **Resultado esperado:** informe e issues, sin los dos tests.
- **¿Cómo lo verificás?** Cada hallazgo tiene criterio, evidencia y la columna «¿Lo detectó la herramienta?».
- **Errores comunes:** tomar el puntaje de Lighthouse como «accesible».

## Prompts

Los cinco prompts están en `practica-clase7.md` (sección «Prompts»).
