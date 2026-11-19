# Diseño técnico de Mini Inventario

## Componentes

- Node.js 22.20 o posterior de la serie 22 ejecuta Express. Express sirve HTML, CSS y JavaScript desde el directorio público.
- HTML y JavaScript sin framework manejan la sesión, los formularios, el listado y el filtro de existencias bajas.
- Supabase Auth inicia y cierra sesión con correo y contraseña de cuentas de prueba creadas previamente. Se deshabilita el registro público.
- El navegador consulta Supabase con la clave publicable y la sesión del usuario. PostgreSQL aplica restricciones y seguridad por fila (RLS).

## Tabla productos

| Columna | Tipo | Restricción o valor inicial |
|---|---|---|
| id | uuid | Clave primaria con UUID generado en la base |
| user_id | uuid | Obligatorio, referencia a la clave primaria de auth.users, usa por defecto la identidad autenticada |
| nombre | text | Obligatorio y no vacío al quitar espacios de los extremos |
| sku | text | Obligatorio, sin espacios de los extremos y guardado en mayúsculas |
| cantidad | integer | Obligatorio, entre 0 y 2 147 483 647 |
| minimo | integer | Obligatorio, entre 0 y 2 147 483 647 |
| created_at | timestamptz | Obligatorio, registra la hora de creación en la base |

La combinación de user_id y sku es única. El registro envía los cuatro campos del formulario. La base asigna id, user_id y created_at.

## Validaciones por capa

| Capa | Responsabilidad |
|---|---|
| Navegador | Detecta campos vacíos, normaliza nombre y SKU y comprueba que cantidad y mínimo sean enteros dentro del rango. Muestra errores de guardado y calcula existencias bajas con cantidad menor que minimo. |
| Express | Sirve únicamente recursos públicos y entrega la configuración pública necesaria. Los archivos de entorno y las claves privadas quedan fuera del directorio servido. |
| Supabase Auth | Verifica credenciales y administra la sesión. |
| PostgreSQL | Rechaza valores inválidos y duplicados incluso si se omite el formulario. RLS limita SELECT, INSERT y UPDATE a filas de la persona autenticada. Los permisos de columna permiten actualizar solo cantidad. El rol anónimo no puede consultar ni modificar productos. |

Al entrar, el navegador recupera la sesión y lista los productos. Tras guardar una operación válida, actualiza el listado y el filtro. Al cerrar sesión, limpia los productos de la vista.

## Referencias

- [Archivos estáticos en Express](https://expressjs.com/starter/static-files/)
- [Seguridad por fila en Supabase](https://supabase.com/docs/guides/database/postgres/row-level-security)
