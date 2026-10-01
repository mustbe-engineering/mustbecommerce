# Especificación — Storefront

Mobile-first. Breakpoints de Tailwind para celular, tablet y escritorio. Modo claro/oscuro con `prefers-color-scheme` y override en `localStorage`.

## Páginas

Inicio, Acerca de, Colecciones, Contacto y Guía (tallas y cuidados). Máximo cinco. Cada pieza muestra el proceso artesanal en la ficha.

## PLP

- Lista por colección y por categoría, paginada desde Medusa.
- Tarjeta: imagen, nombre, precio, metal disponible. CTA a la ficha.
- Estado vacío si la colección no tiene piezas publicadas.

## PDP

- Galería: imágenes con lazy-load, zoom al hover o tap, y un video HTML5 si el producto trae `metadata.video_url`.
- Selectores de variante: talla de anillo, tipo de metal, acabado. El precio y el stock siguen la variante elegida.
- Grabado: input de texto, máximo 24 caracteres, sin saltos de línea. Se envía como `metadata.engraving`. Si va vacío, la línea no lleva esa clave.
- Agregar al carrito deshabilitado si la variante no tiene stock.

## Carrito

- Drawer lateral. Pinia es la fuente en pantalla; Medusa es la fuente del total.
- Agregar, quitar y cambiar cantidad. Cantidad mínima 1.
- El grabado se muestra en la línea y no se puede editar sin quitar la línea.
- El `cart_id` sobrevive al refresh. Si Medusa responde 404, se crea carrito nuevo.

## Checkout (un paso)

- Datos de contacto y dirección, zona de envío, impuesto, código promo y pago en la misma vista.
- Opciones: envío por zona o recolección en tienda.
- Stripe Elements en modo test para tarjeta y débito. MSI solo si la cuenta Stripe MX lo tiene activo.
- Error de pago deja el carrito abierto y muestra el mensaje de Stripe.

## Encargo por WhatsApp

- Campos requeridos: nombre, contacto, tipo de pieza, metal, descripción (mínimo 20 caracteres).
- Al validar, abre `https://wa.me/{NUXT_PUBLIC_WHATSAPP_E164}?text={brief}` con el texto codificado.
- No crea orden en Medusa.

## Contacto

- Nombre, correo, mensaje. Envío por el mismo proveedor de correo transaccional. Éxito y error visibles en la página.
