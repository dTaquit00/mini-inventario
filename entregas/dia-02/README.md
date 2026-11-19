# Día 02 — Planeación de Mini Inventario

## Prompts clave

- Planear cinco historias de usuario, con criterios verificables, para una web de inventario con inicio de sesión, productos y alertas de existencias bajas.
- Diseñar la solución con Express, HTML y JavaScript sin framework, y Supabase para autenticación y datos.
- Crear un issue por historia y guardar los documentos en la rama dia-02-planeacion.

## Decisiones y correcciones

1. El usuario eligió cuentas de prueba ya creadas y limitó la web al inicio y cierre de sesión. Esto reduce el alcance de autenticación mientras se valida el inventario.
2. El usuario confirmó que se pueda editar solo la cantidad. Así se pueden reflejar entradas y salidas y comprobar que el aviso se recalcula, con un formulario limitado al cambio necesario.

## Error detectado y recuperación

El primer intento de revisar Git desde el entorno restringido recibió «Permission denied». La carpeta del repositorio se encuentra en el Escritorio, fuera del espacio inicial. Se repitió la consulta de solo lectura con acceso autorizado y se comprobó que main estaba limpia y sincronizada.

## Comando aprobado y comprobación

Se autorizó la consulta con gh issue list para comprobar si ya había issues en el repositorio y evitar duplicados. La consulta inicial no devolvió issues. Se verificaron cinco historias y catorce criterios de aceptación. Con la autorización de publicación, gh issue create abrió una tarea por historia usando sus criterios como casillas.

## Issues publicados

- [HU-01 — Iniciar y cerrar sesión](https://github.com/dTaquit00/mini-inventario/issues/2)
- [HU-02 — Registrar un producto](https://github.com/dTaquit00/mini-inventario/issues/3)
- [HU-03 — Consultar mi inventario](https://github.com/dTaquit00/mini-inventario/issues/4)
- [HU-04 — Detectar existencias bajas](https://github.com/dTaquit00/mini-inventario/issues/5)
- [HU-05 — Actualizar la cantidad](https://github.com/dTaquit00/mini-inventario/issues/6)
