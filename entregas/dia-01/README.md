# Día 01 — Mini Inventario

## Prompts clave

- Consigna del curso: crear el repositorio público `mini-inventario`, declarar las versiones requeridas y excluir archivos locales y secretos con `.gitignore`.
- Consigna del curso: escribir `AGENTS.md` con las reglas de ramas, pull requests, secretos y aprobación.
- Aclaración del usuario: crear el repositorio en una carpeta nueva fuera de `Proyecto`.

## Error detectado y corrección

Codex propuso inicialmente crear el repositorio dentro de `Proyecto`. El usuario señaló que debía estar en una carpeta independiente. Se corrigió el destino antes de crear los archivos.

## Comando aprobado

Se autorizó `git clone --no-local` para generar una copia independiente del repositorio inicial en una carpeta temporal y comprobar qué archivos quedan disponibles después de clonar.

## Verificación

- En un clon local nuevo, `git ls-files` mostró `.gitignore`, `AGENTS.md` y `README.md`. Se leyó el README desde esa copia y se confirmaron los requisitos de Node.js 22 y Python 3.12.
- `git check-ignore -- .env .venv/prueba node_modules/prueba` devolvió las tres rutas. `git status --short` no mostró cambios en el clon.
- Versiones detectadas en la sesión inicial: Node.js 24.18.0 y Python 3.13.7. La actividad se verificó con Node.js 22.23.5 y npm 10.9.9 de una distribución portátil oficial, y con Python 3.12.14 incluido en Codex. Se conservó el PATH del usuario.
- Se verificó que el repositorio tiene visibilidad pública. En un clon independiente descargado con `gh repo clone dTaquit00/mini-inventario` se confirmaron los tres archivos iniciales, el contenido del README y el estado limpio.

[Salida del clon de GitHub](prueba-clon-github.png), renderizada a partir de la salida real de PowerShell.
