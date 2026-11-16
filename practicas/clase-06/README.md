# Práctica · Clase 6 · De la API a la carga, automatizada

**TestingAI · AcademiaQA** · lunes 16/11/2026

En esta práctica automatizás primero las pruebas funcionales de la MiniModa API a partir del contrato y después la prueba de carga con k6.

## Materiales

- [PDF de la práctica](practica-clase6.pdf)
- [Guía en Markdown](practica-clase6.md)
- [Archivo para tu IA](practica-clase6-para-tu-agente.md) (pasáselo completo al chat o agente que uses; ninguno es obligatorio)

## La API

**En línea** (para abrir Swagger y para las pruebas funcionales):

- Swagger: https://minimoda-api-test.onrender.com/docs
- Contrato: https://minimoda-api-test.onrender.com/openapi.json
- API: https://minimoda-api-test.onrender.com

Si nadie la usó en un rato, el primer pedido puede tardar unos segundos en despertarla. Los datos se reinician cuando la instancia se apaga.

**En tu compu** (recomendado para toda la práctica y obligatorio para la carga):

Node.js 20 o más nuevo. Desde la raíz de este repo:

```bash
cd api
node server.js
```

Swagger: `http://localhost:4000/docs`. Contrato: `http://localhost:4000/openapi.json`. Más detalle en [api/README.md](../../api/README.md).

Importá el contrato en Bruno o Postman (OpenAPI). La prueba de carga con k6 (sobre todo la de 20 usuarios virtuales) se corre solo contra la API en tu compu. Si varios la corren contra la instancia en línea, se mezclan los resultados.

## Los 9 pasos (resumen)

1. Preparar la rama y levantar la API.
2. Armar 6 casos desde el contrato (incluye uno de idempotencia).
3. Armar la colección con aserciones que citan el contrato.
4. Correr la colección por línea de comandos.
5. Abrir 2 issues en tu repo.
6. Escribir el perfil de carga.
7. Revisar el script de k6.
8. Correr 1, 5 y 20 usuarios virtuales (solo en local) y guardar el reporte.
9. Escribir la conclusión con números y abrir el PR, sin mergear.

El detalle, los prompts y la plantilla del informe están en el PDF y en los Markdown. El contrato es el oráculo: el resultado esperado sale de ahí, no del código.
