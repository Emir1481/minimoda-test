# Kit de la práctica · Clase 7 · Accesibilidad y testing visual

Página estática de práctica de MiniModa: una ficha de producto con errores de accesibilidad y visuales **puestos a propósito**. Es normal y deseado que tenga errores: es para practicar.

| Archivo | Qué es |
|---|---|
| `index.html` | Versión 1 de la ficha de producto |
| `index-v2.html` | Versión 2, con el cambio pedido en `notas-v2.md` |
| `notas-v2.md` | Qué cambio se pidió en la versión 2 |
| `estilos.css`, `img/`, `fonts/` | Estilos, imágenes y fuentes locales (Kanit, licencia OFL) |

## Cómo levantar la página

Desde la carpeta donde está este archivo, con cualquiera de estas dos opciones:

```bash
python3 -m http.server 5507
```

```bash
npx http-server -p 5507
```

Abrí `http://localhost:5507/` (versión 1) y `http://localhost:5507/index-v2.html` (versión 2).

No necesita backend, cuentas ni conexión a internet.
