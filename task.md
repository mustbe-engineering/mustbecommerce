# SEAMAN — Joyería

Boilerplate headless de e-commerce, replicable, con el primer cliente en joyería. Prioridad: SEO, carga rápida y escalabilidad modular, sin SaaS monolítico.

## Alcance firmado

Sitio profesional, funcional y adaptado a celular y escritorio, sobre la identidad visual de SEAMAN (colores, logotipo, tipografía).

- Páginas: Inicio, Acerca de, Colecciones, Contacto y una página adicional si hace falta (3–5).
- Tienda: catálogo, ficha de pieza, carrito, checkout y pasarela.
- Formulario de contacto, SEO básico, Facebook, Instagram y WhatsApp.
- Panel de administración para productos, inventario y pedidos, usable sin conocimientos técnicos.
- Fichas de joyería: galería amplia, variantes de talla y material, y contenido del proceso artesanal.

## Cronograma y pagos

| Hito | Fecha | Pago | Entrega |
| --- | --- | --- | --- |
| Arranque | 07 sep 2026 | Anticipo 7,000 MXN | Validación de requerimientos; inicio de diseño y desarrollo |
| Primera revisión | 21 sep 2026 | 3,500 MXN + IVA | Validación de información y referencias |
| Entrega | 02 oct 2026 | 3,500 MXN + IVA | Sitio operativo y probado; funcionalidades implementadas |

Plazo estimado: 2–4 semanas según complejidad y volumen de contenido. Diseño: dos rondas de revisión. Equipo: full-stack, UI/UX y project manager.

## Arquitectura

Presentación y motor de comercio van separados.

**Storefront:** Vue 3 / Nuxt 3 (SSR), Tailwind CSS, GSAP, Pinia (carrito en `localStorage`), Netlify (CI/CD y Edge Functions).

**Motor:** Medusa.js, PostgreSQL, Redis, Medusa Admin (React). VPS (DigitalOcean o Hetzner) con Docker, para replicar en clientes futuros.

## Diseño

- [ ] UI única, sin template genérico; sistema de componentes reutilizables
- [ ] Paleta, tipografía, grid y layout alineados a SEAMAN
- [ ] Mobile-first (prioridad: ~60% del tráfico)
- [ ] Iconografía personalizada o licenciada
- [ ] Carruseles, CTAs, motion (GSAP), microinteracciones hover/focus
- [ ] Modo claro y oscuro
- [ ] Dos rondas de revisión con el cliente

## Fase 1 — Entorno local

- [ ] Medusa.js con PostgreSQL y Redis vía Docker Compose
- [ ] Nuxt 3 con Tailwind y Pinia
- [ ] Comunicación REST entre Nuxt y Medusa

## Fase 2 — Ciclo de compra

- [ ] Seed de piezas y variantes de joyería
- [ ] PLP y PDP: galería lazy-load, zoom, video HTML5 opcional
- [ ] Variantes: talla de anillo, tipo de metal, acabado
- [ ] Grabado personalizado como metadata de `line_item`
- [ ] Carrito persistente: agregar, quitar, cantidad; drawer con Pinia
- [ ] Checkout de un paso: zonas de envío, impuestos, recolección en tienda
- [ ] Stripe en modo test (tarjeta, débito, MSI) con Stripe Elements (PCI en el proveedor)
- [ ] Compra de punta a punta en test

## Fase 3 — Encargo y admin

- [ ] Formulario de piezas por encargo que arma URL `https://wa.me/...` con el brief
- [ ] Guía de tallas y cuidados de la pieza
- [ ] Formulario de contacto funcional
- [ ] Páginas: Inicio, Acerca de, Colecciones, Contacto (+ extra si aplica), con proceso artesanal
- [ ] Medusa Admin: alta, edición y baja de productos, variantes, categorías y colecciones
- [ ] Inventario por variante con alerta de stock bajo
- [ ] Pedidos: estatus (procesando, enviado, entregado), historial, cliente y guía de rastreo
- [ ] Promociones: porcentaje o monto fijo, con vigencia
- [ ] Exportación de reportes de venta
- [ ] Verificar que un pedido de prueba se ve en el admin

## Fase 4 — Integraciones y producción

- [ ] Correos (Resend o Postmark) en `order.placed` y `order.shipment_created`: confirmación, envío y entrega
- [ ] Carrito abandonado: Edge Function tras un delta de tiempo
- [ ] GA4 `dataLayer`: vista de producto, add to cart, compra
- [ ] Meta Pixel + Conversions API: `AddToCart`, `InitiateCheckout`, `Purchase`
- [ ] Feed ` /api/feed.xml` para Facebook Shop e Instagram Shopping
- [ ] Pasarela secundaria opcional: Mercado Pago o Conekta (SPEI, OXXO)
- [ ] Netlify para el storefront Nuxt
- [ ] Medusa y PostgreSQL en VPS con Docker; SSL/HTTPS en todo el flujo
- [ ] Aviso de privacidad, términos y política de devoluciones
- [ ] SEO: meta tags, Open Graph (Facebook, Instagram, WhatsApp), keywords
- [ ] Dominio: tres opciones en presupuesto base; DNS; SSL con renovación (aviso previo)
- [ ] Soporte 1 año: mantenimiento mensual, parches de seguridad, incidencias. Cambios extra van a soporte ampliado
- [ ] Reporte analítico trimestral: heatmap, tiempo en página, rebote, conversiones, secciones y productos más vistos, recomendaciones

## Fuera del MVP base

- Dominio adicional al incluido en el presupuesto
- Mejoras posteriores al año de soporte incluido

## Documentos

- Spec: `specs/arquitectura.md`, `specs/storefront.md`, `specs/admin.md`, `specs/integraciones.md`
- Roadmap: `roadmap.md`
- Tickets: `tickets/fase-1.md`, `tickets/fase-2.md`, `tickets/fase-3.md`, `tickets/fase-4.md`
