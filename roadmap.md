# Roadmap — SEAMAN

Entrega contractual: 02 oct 2026. Hoy la revisión de contenidos es el 21 sep 2026. Lo que no esté en un ticket de fase 1–4 no entra en esta entrega.

## Hitos de negocio

| Fecha | Hito | Salida |
| --- | --- | --- |
| 07 sep 2026 | Arranque | Requerimientos cerrados. Diseño y repos iniciados |
| 21 sep 2026 | Primera revisión | Contenido, referencias visuales y alcance validados |
| 02 oct 2026 | Entrega | Tienda en HTTPS, compra de prueba y admin operando |

## Fases

### 1. Andamiaje — 07 al 14 sep

Compose local, Medusa, Nuxt, Tailwind, Pinia y una llamada real a la Store API. Tokens visuales de SEAMAN.

**Sale de la fase cuando:** el storefront local lista un producto de Medusa.

### 2. Ciclo de compra — 15 al 24 sep

Seed, PLP, PDP, carrito, envío, impuesto y Stripe test de punta a punta. Incluye la revisión del 21 sep (textos, fotos, referencias).

**Sale de la fase cuando:** una compra test queda como orden en Medusa.

### 3. Encargo y operación — 22 al 28 sep

WhatsApp, guía, contacto, páginas de marca, grabado ya visible en la orden, admin comprobado: catálogo, stock, pedidos, promos y CSV.

**Sale de la fase cuando:** un pedido con grabado se ve en el admin y el brief de encargo abre WhatsApp.

### 4. Integraciones y producción — 29 sep al 02 oct

Correo, GA4, Meta CAPI, feed, Netlify, VPS, SSL, legales y SEO social.

**Sale de la fase cuando:** el dominio responde por HTTPS, el pago test y los tres correos transaccionales ocurren en producción.

## Después de la entrega

- Soporte 1 año: mantenimiento mensual y parches. Cambios de alcance van a soporte ampliado.
- Reporte analítico trimestral (heatmap, permanencia, rebote, conversiones, piezas más vistas).
- Pasarela secundaria (Mercado Pago o Conekta) solo si el cliente la activa.

## Dependencias

Fase 2 depende de fase 1. El checkout depende del seed y de las zonas de envío. CAPI, feed y correos dependen de una orden real. El deploy depende de dominio y llaves del cliente.
