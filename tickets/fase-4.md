# Tickets — Fase 4 Integraciones y producción

## SEAM-040 Correos de orden

Resend o Postmark. Plantillas en `order.placed` y `order.shipment_created`: compra, envío con guía y entrega.
**Depende de:** SEAM-036
**Hecho cuando:** los tres correos llegan en test y el de envío incluye la guía.

## SEAM-041 Carrito abandonado

Edge Function. Carritos con correo, sin completar, mayores a `ABANDONED_CART_HOURS` (24).
**Depende de:** SEAM-040, SEAM-015
**Hecho cuando:** un carrito elegible recibe un solo correo y uno ya pagado no recibe nada.

## SEAM-042 GA4

`dataLayer`: `view_item`, `add_to_cart`, `begin_checkout`, `purchase` con `transaction_id`.
**Depende de:** SEAM-017
**Hecho cuando:** una compra test empuja los cuatro eventos en orden.

## SEAM-043 Meta CAPI

Pixel más Edge Function. `AddToCart`, `InitiateCheckout`, `Purchase`, mismo `event_id`.
**Depende de:** SEAM-017
**Hecho cuando:** CAPI registra `Purchase` aunque el navegador bloquee el pixel.

## SEAM-044 Feed

`GET /api/feed.xml` con id, title, description, link, image, price MXN y availability.
**Depende de:** SEAM-010
**Hecho cuando:** el XML lista solo publicados y marca sin stock las variantes en cero.

## SEAM-045 Pasarela MX

Flag `PAYMENT_SECONDARY` para Mercado Pago o Conekta (SPEI, OXXO). Default apagado.
**Depende de:** SEAM-017
**Hecho cuando:** con el flag apagado el checkout solo muestra Stripe.

## SEAM-046 Netlify

Pipeline de la rama de release. Variables públicas y secretos de Edge.
**Depende de:** SEAM-004
**Hecho cuando:** un push a release publica el storefront sin keys privadas en el bundle.

## SEAM-047 VPS y SSL

Medusa, Postgres y Admin en Docker. HTTPS en tienda, admin y API.
**Depende de:** SEAM-002, SEAM-046
**Hecho cuando:** compra test en el dominio y el admin solo entra con auth.

## SEAM-048 Legales y SEO

Privacidad, términos y devoluciones. Title, description y Open Graph por ruta.
**Depende de:** SEAM-033
**Hecho cuando:** compartir una PDP muestra imagen, título y precio en la previsualización.

## SEAM-049 Dominio

Tres opciones de dominio en presupuesto. DNS a Netlify y al API.
**Depende de:** SEAM-047
**Hecho cuando:** el dominio elegido resuelve la tienda por HTTPS.
