# Soundsentiment FRONTEND

Proyecto frontend ligero para la interfaz de Soundsentiment AI — busca artistas, analiza biografías y genera líneas de tiempo.

## Resumen

Interfaz web sencilla escrita en HTML, CSS y JavaScript puro. Permite enviar el nombre de un artista a un endpoint backend (`/api/artist/analyze`) y mostrar los resultados (imagen, biografía, clasificación y línea de tiempo).

## Estructura del proyecto

- `/index.html` — Página principal.
- `/src/app.js` — Lógica frontend (manejo del formulario, renderizado de resultados, utilidades).
- `/src/styles.css` — Estilos globales y componentes UI.

> Nota: las rutas están organizadas dentro de `src/` para separar recursos y facilitar mantenimiento.

## Cómo ejecutar localmente (con .NET / C#)

A continuación se muestran dos formas sencillas de servir esta carpeta estática usando herramientas del ecosistema .NET:

Opción A — usar la herramienta `dotnet-serve` (recomendada, simple):

```powershell
cd "c:\Users\Sebastian Gamarra\Downloads\SoundSentimentFRONTEND"
# Instalar la herramienta (una sola vez)
dotnet tool install --global dotnet-serve

# Servir la carpeta en el puerto 3000
dotnet-serve -p 3000
# Abrir http://localhost:3000/
```

Opción B — crear una pequeña aplicación ASP.NET Core que sirva archivos estáticos:

```powershell
cd "c:\Users\Sebastian Gamarra\Downloads\SoundSentimentFRONTEND"
# Crear proyecto minimal (si no existe)
dotnet new web -o StaticServer
cd StaticServer

# Reemplaza el contenido de Program.cs por el siguiente (o añade UseStaticFiles si ya existe):
#
# var builder = WebApplication.CreateBuilder(args);
# var app = builder.Build();
# app.UseDefaultFiles();
# app.UseStaticFiles();
# app.Run();

# Copia los archivos estáticos desde la carpeta raíz al directorio wwwroot
Copy-Item -Path "..\*" -Destination "wwwroot" -Recurse

dotnet run --urls http://localhost:3000
# Abrir http://localhost:3000/
```

Notas:

- La UI espera un backend en `/api/artist/analyze`. Si no tienes el backend en ejecución, puedes crear un endpoint de prueba en la aplicación ASP.NET Core o usar respuestas mock para probar la interfaz.
- Si prefieres no instalar herramientas globales, la Opción B crea un pequeño servidor usando el SDK de .NET.

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


