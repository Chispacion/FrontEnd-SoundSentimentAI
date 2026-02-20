# Soundsentiment FRONTEND

Proyecto frontend ligero para la interfaz de Soundsentiment AI — busca artistas, analiza biografías y genera líneas de tiempo.

## Resumen

Interfaz web sencilla escrita en HTML, CSS y JavaScript puro. Permite enviar el nombre de un artista a un endpoint backend (`/api/artist/analyze`) y mostrar los resultados (imagen, biografía, clasificación y línea de tiempo).

## Estructura del proyecto

- `/index.html` — Página principal.
- `/src/app.js` — Lógica frontend (manejo del formulario, renderizado de resultados, utilidades).
- `/src/styles.css` — Estilos globales y componentes UI.

> Nota: las rutas están organizadas dentro de `src/` para separar recursos y facilitar mantenimiento.

## Cómo ejecutar localmente

Opcional 1 — con Python (simple, sin dependencias adicionales):

```powershell
cd "c:\Users\Sebastian Gamarra\Downloads\SoundSentimentFRONTEND"
# Python 3
python -m http.server 3000
# Abrir http://localhost:3000/
```

Opcional 2 — con Node.js y `http-server`:

```powershell
npm install -g http-server
cd "c:\Users\Sebastian Gamarra\Downloads\SoundSentimentFRONTEND"
http-server -p 3000
```

Recuerda que la UI espera un backend en `/api/artist/analyze`. Si no tienes el backend, puedes probar con respuestas mock usando herramientas como `json-server` o implementando un pequeño endpoint de prueba.

## Archivos clave

- `index.html`: carga `src/styles.css` y `src/app.js`.
- `src/app.js`: contiene:
  - manejo del formulario y llamadas `fetch` al backend,
  - funciones de render (biografía, línea de tiempo, riesgo de carrera),
  - utilidades para escapar HTML y generar una línea de tiempo cliente si el servidor no proporciona una.
- `src/styles.css`: temas, layout, componentes (badges, timeline, botones).

## Buenas prácticas y siguientes pasos sugeridos

- Agregar un `package.json` y tareas de desarrollo (`npm run start`) si se desea integrar herramientas de build.
- Añadir validaciones UI más robustas y estados de carga accesibles.
- Implementar pruebas simples (unitarias o E2E) para asegurar renderizado básico.
- Si el proyecto crece, separar componentes en una estructura `src/components/` y considerar un bundler (Vite, Webpack) o un framework.

## Licencia

Contenido del frontend sin licencia explícita — añade un archivo `LICENSE` si necesitas declarar una licencia.
