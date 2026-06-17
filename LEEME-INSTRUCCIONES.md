# 🌐 Página Web Pública de Akimel — Guía de Instalación

Tu nueva página web está **conectada a la misma base de datos Firebase** que tu app interna. Cuando registras un arriendo en tu app, la web actualiza la disponibilidad **automáticamente y en tiempo real**.

---

## 📁 Qué incluye esta carpeta

```
akimel-web/
├── web-akimel.html     ← Tu página web (esto se ve en www.akimel.cl)
├── vercel.json         ← Hace que la web cargue en la raíz del dominio (Vercel)
├── _redirects          ← Lo mismo, pero para Netlify
├── firestore.rules     ← Reglas de seguridad de Firebase (IMPORTANTE)
├── img/                ← Las 13 fichas de tus juegos
└── LEEME-INSTRUCCIONES.md  ← Este archivo
```

> ℹ️ El archivo se llama `web-akimel.html` (no `index.html`) para que no lo confundas con el de tu app interna. Los archivos `vercel.json` y `_redirects` se encargan de que `www.akimel.cl` igual cargue tu página directamente, sin tener que escribir `/web-akimel.html` al final.

---

## ⚠️ PASO 1 (OBLIGATORIO): Permitir que la web lea la disponibilidad

Tu web necesita permiso para **leer** los arriendos y calcular qué está libre. Sin esto, la sección de disponibilidad mostrará un error.

1. Entra a https://console.firebase.google.com
2. Selecciona el proyecto **base-de-datos-akimel-arriendos**
3. Menú izquierdo → **Firestore Database**
4. Pestaña **Reglas** (Rules)
5. Reemplaza todo el contenido por el del archivo `firestore.rules`
6. Clic en **Publicar**

> 💡 Lee la nota de privacidad al final de `firestore.rules`. Para empezar funciona así, pero a futuro conviene separar los datos de clientes.

---

## 🚀 PASO 2: Subir la web a internet (GRATIS con Vercel)

### Opción rápida — Arrastrar y soltar

1. Entra a https://vercel.com y crea una cuenta gratis
2. En el panel, busca la opción de subир proyecto / **Add New → Project**
3. Cuando te pida el código, elige la opción de **subir carpeta** (deploy manual)
4. Arrastra **toda la carpeta `akimel-web`** (con el index.html y la carpeta img dentro)
5. Clic en **Deploy**
6. En segundos te dará una URL tipo `https://akimel-web.vercel.app`

> ⚠️ Importante: sube la **carpeta completa** `akimel-web` (con el `web-akimel.html`, la carpeta `img` y el `vercel.json` dentro). Si subes solo el HTML, las imágenes de los juegos no se verán y el dominio no cargará en la raíz.

### Alternativa — Netlify (también gratis y muy fácil)

1. Entra a https://app.netlify.com/drop
2. Arrastra la carpeta `akimel-web` completa
3. Listo, te da una URL al instante

---

## 🔗 PASO 3: Conectar tu dominio www.akimel.cl

Una vez que la web esté en Vercel/Netlify y funcione:

### En Vercel
1. Entra a tu proyecto → **Settings → Domains**
2. Escribe `akimel.cl` y agrégalo
3. Vercel te mostrará unos **Nameservers** o registros **DNS**

### En NIC.CL
1. Entra a tu panel de NIC.CL → tu dominio `akimel.cl`
2. En **Configuración Técnica**, elige **Servidores DNS**
3. Ingresa los nameservers que te dio Vercel
4. Guarda

⏱️ Espera 24–48 horas para que el dominio propague. Después, `www.akimel.cl` mostrará tu web. El usuario nunca verá la URL de Vercel.

---

## 🔄 Cómo funciona la sincronización

```
┌─────────────────────┐         ┌──────────────────────┐
│   TU APP INTERNA    │         │   PÁGINA WEB PÚBLICA │
│   (index dashboard) │         │   (www.akimel.cl)    │
└──────────┬──────────┘         └───────────┬──────────┘
           │                                │
           │   escribe arriendos            │   lee disponibilidad
           │                                │   (en tiempo real)
           ▼                                ▼
        ┌──────────────────────────────────────┐
        │      FIREBASE (misma base de datos)   │
        │      base-de-datos-akimel-arriendos   │
        │      colección: arriendos             │
        └──────────────────────────────────────┘
```

- Registras un arriendo en tu app → ocupa un juego para esa fecha
- La web detecta el cambio **al instante** (sin recargar) y muestra ese juego como ocupado o agotado
- Todo sale de la **misma fuente**, así nunca hay información desalineada

---

## ✅ Qué hace la web automáticamente

- 📅 El cliente elige una fecha y ve **qué juegos están libres** ese día
- 🟢 Verde = disponible · 🟠 Naranja = quedan pocos · 🔴 Rojo = agotado
- 💬 Cada juego tiene botón directo a **WhatsApp** con un mensaje pre-armado
- 🖼️ Al tocar un juego, muestra su **ficha completa** (la misma de tu catálogo)
- 📱 Funciona perfecto en **celular y computador**

---

## 🛠️ Datos que usé (puedes pedirme que los cambie)

- **Teléfono WhatsApp:** +56 9 5080 3204 *(extraído de tu catálogo)*
- **Precios:** Inflables $40.000 · Interior 1×$28.000 / 2×$42.000 / 3×$55.000
- **Inventario:** los 19 juegos de tu app, con sus cantidades reales
- **Testimonios:** son de ejemplo — reemplázalos por reseñas reales cuando las tengas

---

## ❓ ¿Necesitas que ajuste algo?

Puedo cambiar fácilmente:
- Precios o promociones
- Textos, colores o el orden de las secciones
- Agregar/quitar juegos
- Cambiar el teléfono o agregar redes sociales
- Mejorar la privacidad creando la colección separada de disponibilidad

Solo avísame. 🚀
