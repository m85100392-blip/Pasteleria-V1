# A&A Sweet Bakery — sitio web de pastelería

Landing/e-commerce front-end responsive para venta de pasteles. Incluye catálogo filtrable, carrito, constructor de pastel personalizado, formulario de newsletter, navegación móvil y diseño adaptable.

## 1. Estructura

```text
dulce-atelier/
├── index.html      # Estructura y contenido
├── styles.css      # Diseño, responsive y componentes
├── script.js          # Productos, filtros, carrito e interacciones
├── README.md       # Instalación y mantenimiento
└── assets/         # Carpeta para imágenes/logos futuros
```

## 2. Instalación rápida

No requiere dependencias ni compilación.

### Opción A — abrir directamente
1. Descomprime la carpeta.
2. Abre `index.html` en Chrome, Edge, Firefox o Safari.

### Opción B — servidor local recomendado
Con VS Code instala la extensión **Live Server**, abre la carpeta y pulsa **Go Live**.

También puedes usar Python:

```bash
cd dulce-atelier
python -m http.server 8080
```

Luego visita `http://localhost:8080`.

## 3. Personalización inicial

### Nombre, textos y contacto
Edita `index.html` y reemplaza “A&A Sweet Bakery”, email, teléfono, horarios y textos por los datos reales del negocio.

### Colores
En `styles.css`, modifica las variables del bloque `:root`:

```css
:root {
  --ink: #342723;
  --cream: #fffaf5;
  --rose: #e9b9b0;
  --rose2: #f7ded7;
  --wine: #733f3e;
}
```

### Productos y precios
En `script.js`, modifica el arreglo `products`. Cada producto contiene `id`, `name`, `cat`, `price`, `desc`, `emoji`, `tone` y `tag`.

Para producción se recomienda sustituir los emojis por fotografías optimizadas en WebP/AVIF dentro de `/assets` y adaptar el componente de producto.

## 4. Qué funciona actualmente

- Diseño responsive para escritorio, tablet y móvil.
- Menú móvil.
- Catálogo y filtros por categoría.
- Carrito lateral con cantidades y subtotal.
- Estimador básico para pasteles personalizados.
- Formularios con feedback visual.
- Navegación por secciones.

Los pagos, inventario, emails y pedidos son demostrativos y deben conectarse a servicios reales antes de publicar una tienda transaccional.

## 5. Preparar para producción

### Pagos
Conecta el botón de checkout a Stripe Checkout, Shopify, WooCommerce u otro proveedor. Nunca guardes números de tarjeta directamente en este front-end.

### Pedidos y formularios
Conecta los formularios a un backend/API, Formspree, Resend, Supabase, Firebase o CRM. Añade validación del servidor, protección anti-spam y mensajes de error reales.

### Base de datos
Para administrar productos/pedidos de forma dinámica, migra el arreglo `products` a una base de datos o CMS. Opciones habituales: Supabase/PostgreSQL, Firebase, Sanity, Contentful o un backend propio.

### Imágenes
- Preferir WebP/AVIF.
- Mantener cada imagen idealmente por debajo de 200–300 KB.
- Usar `alt` descriptivo.
- Crear tamaños responsive para móvil y escritorio.

### SEO
Antes del lanzamiento:
- Cambia `title` y `meta description`.
- Añade dominio canónico.
- Crea `robots.txt` y `sitemap.xml`.
- Añade Open Graph para redes sociales.
- Implementa datos estructurados de `LocalBusiness`/`Product` cuando existan datos reales.

### Legal
Añade páginas de privacidad, términos, política de reembolso/cancelación, alérgenos y cookies según corresponda al negocio y jurisdicción.

## 6. Despliegue

### Netlify / Vercel / Cloudflare Pages
Al ser un sitio estático, puedes subir esta carpeta directamente o conectarla a un repositorio Git. No hay comando de build; el directorio público es la raíz del proyecto.

### Hosting tradicional
Sube `index.html`, `styles.css`, `script.js` y `/assets` a la carpeta pública (`public_html`, `www` o equivalente) mediante el panel del hosting o SFTP.

## 7. Mantenimiento

### Semanal
- Revisar que formularios y checkout funcionen.
- Confirmar precios, disponibilidad y horarios.
- Revisar pedidos de prueba después de cualquier cambio importante.

### Mensual
- Optimizar imágenes nuevas.
- Comprobar enlaces rotos y experiencia móvil.
- Revisar métricas de velocidad y Core Web Vitals.
- Actualizar contenido estacional.

### Antes de cada cambio
1. Crear una copia de seguridad o commit de Git.
2. Probar localmente.
3. Revisar móvil y escritorio.
4. Publicar.
5. Verificar formulario, carrito y checkout en producción.

## 8. Control de versiones recomendado

```bash
git init
git add .
git commit -m "Sitio inicial A&A Sweet Bakery"
```

Después de cada cambio estable:

```bash
git add .
git commit -m "Descripción del cambio"
```

## 9. Seguridad

- No pongas claves privadas/API secrets en `script.js` ni en HTML.
- Las claves secretas deben vivir en variables de entorno del backend.
- Usa HTTPS en producción.
- Valida pedidos y precios en el servidor; no confíes únicamente en valores enviados por el navegador.
- Mantén copias de seguridad y accesos del hosting protegidos con 2FA.

## 10. Siguiente fase recomendada

Para convertir esta demo en tienda completa: fotos reales + dominio + backend/CMS + checkout + confirmaciones por email + panel de pedidos + analytics + páginas legales.

## Idiomas / Languages

La interfaz incluye un selector **ES / EN** en la navegación. El cambio se realiza en el navegador sin recargar la página y la preferencia queda guardada en `localStorage` con la clave `dulce-language`.

Las traducciones están centralizadas en el objeto `translations` dentro de `script.js`. Para cambiar un texto, edita la misma clave dentro de `es` y `en`. Los productos también contienen `desc` y `tag` en ambos idiomas.

### Añadir otro idioma
1. Añade un nuevo objeto dentro de `translations` (por ejemplo `fr`).
2. Traduce todas las claves existentes.
3. Añade un botón `<button class="lang-btn" data-lang="fr">FR</button>` al selector del `index.html`.
4. Añade traducciones para `desc` y `tag` de cada producto.

---

The interface includes an **ES / EN** language selector in the navigation. Switching happens in the browser without a page reload, and the selected language is stored in `localStorage` under `dulce-language`.

Translations are centralized in the `translations` object inside `script.js`. To update copy, edit the matching key in both `es` and `en`. Product descriptions and tags are bilingual as well.

### Adding another language
1. Add a new language object inside `translations` (for example `fr`).
2. Translate every existing key.
3. Add `<button class="lang-btn" data-lang="fr">FR</button>` to the language selector in `index.html`.
4. Add the new language to each product's `desc` and `tag` fields.

---

## Temas de color / Color themes

La página incluye tres temas seleccionables desde la navegación: **Azul, Negro y Rosa**. El tema elegido se guarda en `localStorage` con la clave `dulce-theme`, por lo que se conserva al recargar o volver a visitar la página.

Los colores base de cada tema están definidos al final de `styles.css` mediante variables CSS. Para cambiar un color, edita los bloques `body.theme-black` y `body.theme-pink`; el tema blanco usa las variables de `:root`. La función `applyTheme()` de `script.js` controla el cambio de tema.

The website includes three selectable themes in the navigation: **White, Black, and Pink**. The selected theme is saved in `localStorage` under `dulce-theme`, so it remains active after refreshing or revisiting the website.

Each theme's base colors are defined near the end of `styles.css` using CSS variables. To customize them, edit `body.theme-black` and `body.theme-pink`; the white theme uses the default `:root` variables. The `applyTheme()` function in `script.js` handles theme switching.


## Branding / Marca
El proyecto incluye el logo de **A&A Sweet Bakery** en `assets/aa-sweet-bakery-logo.jpg`. El tema claro original fue reemplazado por **Azul**; Negro y Rosa se mantienen. / The project includes the **A&A Sweet Bakery** logo in `assets/aa-sweet-bakery-logo.jpg`. The original light theme was replaced by **Blue**; Black and Pink remain available.
