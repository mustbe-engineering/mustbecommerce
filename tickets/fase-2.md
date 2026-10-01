# Tickets — Fase 2 Ciclo de compra

## SEAM-010 Seed de joyería

Productos con variantes de talla y metal, precios MXN, stock e imagen.
**Depende de:** SEAM-002
**Hecho cuando:** hay al menos tres piezas publicadas en dos colecciones.

## SEAM-011 PLP

Listado por colección y categoría. Tarjeta con imagen, nombre y precio.
**Depende de:** SEAM-004, SEAM-010
**Hecho cuando:** una colección vacía muestra estado vacío y una con stock lista sus piezas.

## SEAM-012 PDP galería

Lazy-load, zoom y video HTML5 si existe `metadata.video_url`.
**Depende de:** SEAM-011
**Hecho cuando:** una ficha con tres imágenes y una con video cargan sin bloquear el resto de la página.

## SEAM-013 Variantes

Selectores de talla, metal y acabado. Precio y stock de la variante activa.
**Depende de:** SEAM-012
**Hecho cuando:** cambiar talla cambia el precio y bloquea compra si stock es 0.

## SEAM-014 Grabado

Input máx. 24 caracteres. Se envía como `metadata.engraving`.
**Depende de:** SEAM-013
**Hecho cuando:** la orden en Medusa muestra el texto y una línea sin grabado no trae la clave.

## SEAM-015 Drawer

Agregar, quitar y cantidad. Totales desde Medusa. Drawer con Pinia.
**Depende de:** SEAM-004
**Hecho cuando:** el `cart_id` sigue tras refresh y un 404 de carrito crea uno nuevo.

## SEAM-016 Envío e impuesto

Zonas de envío, impuesto y recolección en tienda en un solo checkout.
**Depende de:** SEAM-015
**Hecho cuando:** el total cambia al elegir zona y recolección deja el envío en 0.

## SEAM-017 Stripe test

Stripe Elements, tarjeta y débito. MSI si la cuenta MX lo permite. Sin PAN en nuestros logs.
**Depende de:** SEAM-016
**Hecho cuando:** un pago test `4242` completa la orden y un rechazo deja el carrito vivo.

## SEAM-018 Motion

Transición de página y hover de ficha con GSAP, solo en cliente.
**Depende de:** SEAM-012
**Hecho cuando:** el HTML inicial de la PDP no espera a GSAP para mostrar imagen y precio.
