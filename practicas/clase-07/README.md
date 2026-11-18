# Práctica · Clase 7 · Accesibilidad y testing visual

**TestingAI · AcademiaQA** · miércoles 18/11/2026

Auditás y automatizás una ficha de producto de MiniModa que tiene errores de accesibilidad y visuales **puestos a propósito**: escaneo con axe-core, revisión con teclado y lector de pantalla, capturas en tres tamaños, regresión visual contra una versión 2, issues y un PR en tu repo.

## Materiales

- [PDF de la práctica](practica-clase7.pdf)
- [Guía en Markdown](practica-clase7.md)
- [Archivo para tu IA](practica-clase7-para-tu-agente.md) (pasáselo completo al chat o agente que uses; ninguno es obligatorio)
- [Kit: la página de práctica](kit/) (versión 1, versión 2 y notas de la versión 2)

## Levantar la página

```bash
cd kit
python3 -m http.server 5507
```

Versión 1: `http://localhost:5507/` · Versión 2: `http://localhost:5507/index-v2.html`. También sirve `npx http-server -p 5507`.

## Los 8 pasos (resumen)

1. Preparar: rama `clase-07-a11y`, kit en `clase-07/kit/`, página en `localhost:5507`.
2. Escaneo automático con axe-core desde Playwright (y Lighthouse o pa11y como segunda opinión).
3. Ordenar los resultados con tu IA y confirmar dos hallazgos en la página.
4. Teclado: cinco preguntas, cada una con su criterio.
5. Lector de pantalla: botones, imágenes y mensajes.
6. Tamaños y zoom: 375, 768 y 1280 px, zoom al 200 % y 320 px.
7. Regresión visual contra la versión 2.
8. Tres issues en tu repo y un PR sin mergear.

Sin Node: seguí el camino corto del PDF.
