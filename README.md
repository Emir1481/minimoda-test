# minimoda-test

Ejemplos de las prácticas de testing del curso TestingAI sobre MiniModa, una tienda online ficticia ([sitio](https://minimoda-navy.vercel.app/)). Este repo no incluye el código de esa tienda.

| Carpeta | Práctica | Qué muestra |
|---------|----------|-------------|
| [clase-01/](clase-01/README.md) | Clase 1: casos del registro con IA | Plantilla de entrega (`practica.md`) y capturas de ejemplo de los casos cargados en Qase |
| [auditoria-agente-minimoda/](auditoria-agente-minimoda/) | Clase 3: hackear una IA sin escribir código | Auditoría resuelta del Asistente MiniModa: 6 hallazgos, casos de prueba y evidencias |
| [practicas/clase-06/](practicas/clase-06/) | Clase 6: de la API a la carga, automatizada | PDF, guía y archivo para tu IA |
| [api/](api/) | MiniModa API de la Clase 6 | API de práctica para levantar en tu compu (o usar en línea) |

Para las carpetas de ejemplo de clases anteriores, este repo sirve de referencia: cada alumno arma el suyo desde cero. Para la Clase 6 sí podés clonarlo o descargar el zip, porque la API está acá.

## Clase 6 · Testing de APIs y performance

En esta clase trabajás con una API de práctica (MiniModa API). Podés probarla en línea o levantarla en tu compu.

**Práctica (PDF, guía y archivo para tu IA):** [practicas/clase-06/](practicas/clase-06/)

**API en línea**

- Swagger: https://minimoda-api-test.onrender.com/docs
- Contrato: https://minimoda-api-test.onrender.com/openapi.json
- API: https://minimoda-api-test.onrender.com

Si nadie la usó en un rato, el primer pedido puede tardar unos segundos en despertarla. Los datos viven en memoria y se reinician cuando la instancia se apaga.

**API en tu compu**

Node.js 20 o más nuevo. Cloná este repo o descargá el zip, y después:

```bash
cd api
node server.js
```

- Swagger: `http://localhost:4000/docs`
- Contrato: `http://localhost:4000/openapi.json`

Importá el contrato en Bruno o Postman (OpenAPI). La prueba de carga con k6 se corre solo contra la API en tu compu, no contra la instancia en línea: si varios la cargan al mismo tiempo, los resultados se mezclan.

Más detalle en [api/README.md](api/README.md).
