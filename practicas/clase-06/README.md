# Práctica · Clase 6 · De la API a la carga, automatizada

**TestingAI · AcademiaQA** · lunes 16/11/2026

En esta práctica automatizás primero las pruebas funcionales de la MiniModa API a partir del contrato y después la prueba de carga con k6. **Todo se hace contra la API que levantes en tu compu** (`http://localhost:4000`). La instancia en línea no se usa acá: es compartida, los datos se mezclan y se reinician, y una medición de carga ahí no dice nada.

## Materiales

- [PDF de la práctica](practica-clase6.pdf)
- [Guía en Markdown](practica-clase6.md)
- [Archivo para tu IA](practica-clase6-para-tu-agente.md) (pasáselo completo al chat o agente que uses; ninguno es obligatorio)

## La API, en tu compu

Hace falta Node.js 20 o más nuevo. Desde la raíz de este repo:

```bash
cd api
MODO=con-defectos node server.js
```

En Windows PowerShell: `cd api` y después `$env:MODO="con-defectos"; node server.js`.

Swagger: `http://localhost:4000/docs`. Contrato: `http://localhost:4000/openapi.json`. Si el puerto 4000 está ocupado, usá `PORT=4001`. Más detalle en [api/README.md](../../api/README.md) y en el paso 1 de la práctica (también hay un prompt para tu IA).

Importá el contrato en Bruno o Postman (OpenAPI) con `baseUrl = http://localhost:4000`. La colección, la CLI y la prueba de carga con k6 se corren solo contra esa URL. Nunca corras k6 contra un servidor compartido o ajeno.

## Los 9 pasos (resumen)

1. Levantar la API en tu compu (rama, `MODO=con-defectos node server.js`, comprobar `/health` y `/docs`).
2. Armar 6 casos desde el contrato (incluye uno de idempotencia).
3. Armar la colección con aserciones que citan el contrato (`baseUrl = http://localhost:4000`).
4. Correr la colección por línea de comandos.
5. Abrir 2 issues en tu repo.
6. Escribir el perfil de carga.
7. Revisar el script de k6 (`BASE_URL` en localhost).
8. Correr 1, 5 y 20 usuarios virtuales (solo en local) y guardar el reporte.
9. Escribir la conclusión con números y abrir el PR, sin mergear.

El detalle, los prompts y la plantilla del informe están en el PDF y en los Markdown. El contrato es el oráculo: el resultado esperado sale de ahí, no del código.
