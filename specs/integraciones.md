# Especificación — Integraciones

Secretos solo en entorno. El storefront público no incluye llaves privadas.

## Pagos

- Principal: Stripe. Stripe Elements tokeniza. El servidor confirma el PaymentIntent y completa el carrito.
- MSI (meses sin intereses) se ofrece si la cuenta Stripe de MX lo tiene habilitado.
- Secundario, por cliente y apagado por default: Mercado Pago o Conekta para SPEI y OXXO. Flag `PAYMENT_SECONDARY`.
- PCI DSS queda en el proveedor. El sitio no almacena tarjeta.

## GA4

`dataLayer` en Nuxt, eventos de e-commerce:

- `view_item` en PDP
- `add_to_cart` al agregar
- `begin_checkout` al abrir checkout
- `purchase` con `transaction_id` al completar

## Meta

- Pixel en el cliente y Conversions API en Edge Function.
- Eventos: `AddToCart`, `InitiateCheckout`, `Purchase`.
- Mismo `event_id` en pixel y CAPI para deduplicar.
- CAPI no depende de que el navegador acepte el pixel.

## Feed

- `GET /api/feed.xml` genera XML de productos publicados.
- Campos: id, title, description, link, image_link, price, availability.
- Precio con moneda MXN. Disponibilidad según stock de variantes.

## Correo

- Proveedor: Resend o Postmark, elegido por `EMAIL_PROVIDER`.
- Medusa escucha `order.placed` y `order.shipment_created`.
- Plantillas HTML: confirmación de compra, aviso de envío (con guía), aviso de entrega.
- Carrito abandonado: Edge Function revisa carritos con correo, no completados, más viejos que `ABANDONED_CART_HOURS` (default 24). Un solo correo por carrito.

## Producción

- Storefront en Netlify, con CI en la rama de release.
- Motor y PostgreSQL en VPS, Docker, HTTPS en tienda, admin y API.
- Dominio: tres opciones dentro del presupuesto. DNS apuntando a Netlify y al API.
- Páginas legales publicadas: aviso de privacidad, términos, devoluciones.
- SEO: title, description y Open Graph por ruta, válidos al compartir en Facebook, Instagram y WhatsApp.
