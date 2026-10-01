# Especificación — Admin y catálogo

Medusa Admin es el panel. El equipo de SEAMAN no edita código ni base de datos.

## Catálogo

- Alta, edición y baja (archivado) de productos.
- Variantes con opciones: talla, metal, acabado. Cada variante tiene SKU y precio en MXN.
- Categorías y colecciones asignables desde el admin.
- Campos de joyería en metadata del producto: `video_url`, texto de proceso artesanal, `low_stock_threshold` (default 2).

## Inventario

- Stock por variante, no por producto.
- Alerta cuando la cantidad disponible es menor o igual al umbral de esa variante.
- La PDP no ofrece agregar si el disponible es 0.

## Pedidos

- Estatus operativos: procesando, enviado, entregado.
- Al marcar enviado se guarda número de guía. Ese dato dispara `order.shipment_created`.
- Ficha de pedido: cliente, líneas, grabado, totales, envío o recolección.

## Promociones

- Código de porcentaje o de monto fijo, en MXN.
- Fecha de inicio y de expiración. Fuera de vigencia el checkout lo rechaza.
- Un código inválido no modifica el total.

## Reportes

- Exportación de ventas del rango elegido: folio, fecha, cliente, total, estatus.
- Formato CSV descargable desde el admin o un endpoint autenticado del motor.

## Seed local

Piezas de ejemplo con al menos dos metales y un rango de tallas, para probar PLP, PDP y checkout sin catálogo real.
