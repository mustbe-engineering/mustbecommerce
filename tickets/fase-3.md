# Tickets — Fase 3 Encargo y admin

## SEAM-030 WhatsApp

Formulario de encargo. Arma `https://wa.me/{tel}?text=` con el brief codificado.
**Depende de:** SEAM-003
**Hecho cuando:** con campos inválidos no abre WhatsApp; con válidos el texto incluye pieza, metal y descripción.

## SEAM-031 Guía

Página de tallas de anillo y cuidados de la pieza.
**Depende de:** SEAM-005
**Hecho cuando:** la ruta es pública y enlaza desde la PDP.

## SEAM-032 Contacto

Formulario con nombre, correo y mensaje. Correo al comercio.
**Depende de:** SEAM-005
**Hecho cuando:** un envío vacío marca el campo y uno válido queda aceptado. El correo sale con SEAM-040.

## SEAM-033 Páginas de marca

Inicio, Acerca de, Colecciones y Contacto. Proceso artesanal visible en la ficha.
**Depende de:** SEAM-005, SEAM-012
**Hecho cuando:** las cuatro rutas responden en SSR con title propio.

## SEAM-034 Catálogo admin

Alta, edición y archivado de producto, variantes, categoría y colección, sin tocar código.
**Depende de:** SEAM-002
**Hecho cuando:** una pieza creada en admin aparece en la PLP tras publicar.

## SEAM-035 Stock bajo

Alerta por variante cuando disponible ≤ `low_stock_threshold` (default 2).
**Depende de:** SEAM-034
**Hecho cuando:** bajar una variante a 2 marca alerta y a 0 la PDP bloquea la compra.

## SEAM-036 Fulfillment

Estatus procesando, enviado y entregado. Guía obligatoria al marcar enviado.
**Depende de:** SEAM-017
**Hecho cuando:** la orden test se ve en admin con cliente, grabado y guía.

## SEAM-037 Promos

Código porcentual o monto fijo, con inicio y expiración.
**Depende de:** SEAM-016
**Hecho cuando:** un código vigente descuenta y uno vencido no cambia el total.

## SEAM-038 CSV de ventas

Exportación por rango: folio, fecha, cliente, total, estatus.
**Depende de:** SEAM-036
**Hecho cuando:** el archivo incluye la orden test y excluye lo fuera de rango.
