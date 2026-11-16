# MiniModa API · API de práctica (TestingAI · Clase 6)

API de práctica de la tienda MiniModa. Corre en tu compu, con datos ficticios y todo en memoria. Sirve para probar el contrato, automatizar una colección y medir la carga con k6.

## Qué necesitás

- Node.js 20 o más nuevo (`node -v`).

## Cómo se levanta

```bash
node server.js
```

Vas a ver:

```
MiniModa API 1.0.0 · modo con-defectos
API:     http://localhost:4000
Swagger: http://localhost:4000/docs
```

- Contrato (OpenAPI 3.0.3): `http://localhost:4000/openapi.json`
- Documentación con Swagger UI: `http://localhost:4000/docs` (funciona sin internet)
- Estado: `http://localhost:4000/health`
- Volver los datos al inicio: `POST http://localhost:4000/reset`

Para cerrar la API: `Ctrl + C` en la terminal.

## Instancia publicada

También está disponible en:

- API: https://minimoda-api.onrender.com
- Swagger: https://minimoda-api.onrender.com/docs
- Contrato: https://minimoda-api.onrender.com/openapi.json

Si nadie la usó en un rato, el primer pedido puede tardar unos segundos en despertarla. Los datos viven en memoria y se reinician cuando la instancia se apaga.

## Opciones

| Variable | Para qué sirve | Ejemplo (macOS / Linux) | Ejemplo (PowerShell) |
|---|---|---|---|
| `PORT` | Cambiar el puerto si el 4000 está ocupado | `PORT=4001 node server.js` | `$env:PORT=4001; node server.js` |
| `MODO` | `con-defectos` (por defecto, para la práctica) o `estable` | `MODO=estable node server.js` | `$env:MODO="estable"; node server.js` |

## Reglas

- La API se prueba como caja negra: el resultado esperado sale del contrato (`/openapi.json`), no del código.
- La carga se aplica solo contra esta API en tu compu. Nunca contra sitios ajenos.
- Las tarjetas son de prueba: `4111111111111111` aprueba y `4000000000000002` se rechaza. Nunca uses datos reales.

Swagger UI se incluye en `docs/vendor/` bajo licencia Apache 2.0 (ver `docs/vendor/LICENSE`).
