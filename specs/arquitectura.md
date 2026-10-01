# Especificación — Arquitectura

El storefront no accede a PostgreSQL ni a la Admin API. Solo consume la Store API de Medusa.

## Storefront

- Nuxt 3, SSR activo. PLP y PDP salen renderizadas para SEO y primera carga.
- Tailwind. Color, tipo y spacing de SEAMAN viven en el theme, no en estilos sueltos.
- GSAP corre en cliente, después del primer paint. No entra en el HTML inicial.
- Pinia `useCart`: persiste `cart_id` en `localStorage` y rehidrata en plugin de cliente.
- Netlify construye el storefront. Edge Functions cubren CAPI, feed y carrito abandonado.

## Motor

- Medusa.js. Store API con header `x-publishable-api-key`.
- PostgreSQL: catálogo, precios, inventario, carritos, órdenes, clientes, promociones.
- Redis: cola de eventos y caché de sesión.
- Medusa Admin (React) en el mismo VPS, con auth. El navegador de la tienda no lo llama.
- Docker Compose: `medusa`, `postgres`, `redis`. Un stack y un `.env` por cliente.

## Región

- Región `mx`, moneda `mxn`. Impuesto según zona de envío.
- Sales channel: Storefront.
- Envío por zona y recolección en tienda a precio 0.

## Contrato que usa Nuxt

| Acción | Llamada |
| --- | --- |
| Listado y ficha | `GET /store/products`, `GET /store/products/:id` |
| Carrito | `POST /store/carts` |
| Línea | `POST /store/carts/:id/line-items` |
| Grabado | `metadata.engraving` en la línea |
| Envío | `POST /store/carts/:id/shipping-methods` |
| Pago | sesión de Stripe y complete del carrito |
| Promo | `POST /store/carts/:id/promotions` |

El navegador no ve PAN ni secretos de Stripe. Stripe Elements tokeniza.

## Réplica

Cliente nuevo = mismo compose, otro `.env` (dominio, Stripe, WhatsApp, región). Imágenes en el storage de Medusa.
