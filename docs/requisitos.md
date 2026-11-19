# Requisitos de Mini Inventario

El MVP permite que cada persona consulte y gestione sus propias existencias. Se usarán cuentas de prueba creadas previamente en Supabase; la web ofrece inicio y cierre de sesión.

## HU-01 — Iniciar y cerrar sesión

Como persona con una cuenta de prueba, quiero iniciar y cerrar sesión para controlar el acceso a mi inventario.

- [ ] Con correo y contraseña válidos, se abre el inventario.
- [ ] Con credenciales inválidas, aparece un mensaje y el inventario sigue sin mostrarse.
- [ ] Al cerrar sesión se ocultan los productos y, al recargar, se vuelve a mostrar el formulario de acceso.

## HU-02 — Registrar un producto

Como responsable del inventario, quiero registrar nombre, SKU, cantidad y cantidad mínima para controlar las existencias de un producto.

- [ ] Al guardar un nombre y SKU no vacíos y dos cantidades enteras no negativas, el producto aparece en el listado y persiste al recargar.
- [ ] Se rechazan campos vacíos y cantidades negativas, decimales o fuera del rango permitido.
- [ ] Se rechaza un SKU repetido en la misma cuenta, incluso si solo cambia el uso de mayúsculas o los espacios de los extremos. Otra cuenta puede usar el mismo SKU.

## HU-03 — Consultar mi inventario

Como responsable del inventario, quiero ver mis productos para revisar sus existencias y niveles mínimos.

- [ ] Cada fila muestra nombre, SKU, cantidad y mínimo.
- [ ] Una cuenta sin productos muestra un mensaje de inventario vacío.
- [ ] Si dos cuentas tienen productos distintos, cada una ve solo los suyos. Sin sesión no se pueden leer productos.

## HU-04 — Detectar existencias bajas

Como responsable del inventario, quiero ver cuáles productos están por debajo del mínimo para decidir qué reponer.

- [ ] Con mínimo de 5, una cantidad de 4 aparece en existencias bajas. Las cantidades de 5 y 6 quedan fuera.
- [ ] Si ningún producto está por debajo del mínimo, la vista muestra que no hay existencias bajas.

## HU-05 — Actualizar la cantidad

Como responsable del inventario, quiero actualizar la cantidad de un producto para reflejar entradas y salidas.

- [ ] Al cambiar la cantidad de 4 a 5 en un producto con mínimo de 5, desaparece de existencias bajas y el nuevo valor persiste al recargar.
- [ ] Una cantidad negativa, decimal o fuera del rango permitido se rechaza y se conserva el valor guardado.
- [ ] Una cuenta no puede actualizar la cantidad de un producto de otra cuenta.
