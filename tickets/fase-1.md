# Tickets — Fase 1 Andamiaje

## SEAM-001 Compose local

PostgreSQL 16 y Redis 7 en Docker Compose, red interna, volúmenes persistentes.
**Depende de:** —
**Hecho cuando:** `docker compose up` deja ambos healthy y los datos sobreviven a un restart.

## SEAM-002 Medusa

Medusa contra ese Postgres y Redis. Región `mx`, moneda `mxn`, sales channel Storefront, publishable key.
**Depende de:** SEAM-001
**Hecho cuando:** `GET /store/products` responde 200 con la publishable key.

## SEAM-003 Nuxt

Nuxt 3 SSR, Tailwind y Pinia. `cart_id` se guarda en `localStorage`.
**Depende de:** —
**Hecho cuando:** la home SSR responde y el store de carrito rehidrata tras refresh.

## SEAM-004 Cliente API

Módulo servidor que llama a Medusa con `x-publishable-api-key`. La key no va al cliente.
**Depende de:** SEAM-002, SEAM-003
**Hecho cuando:** una página Nuxt pinta el título de un producto devuelto por Medusa.

## SEAM-005 Tokens de marca

Paleta, tipografía y grid de SEAMAN en Tailwind. Claro/oscuro con sistema y override persistido.
**Depende de:** SEAM-003
**Hecho cuando:** un layout base cambia de tema sin recargar y usa solo tokens.
