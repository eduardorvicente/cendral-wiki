# La Marca de Cendral — Wiki de campaña

Wiki para los **jugadores**, construida con [MkDocs Material](https://squidfunk.github.io/mkdocs-material/). Todo el contenido vive en archivos Markdown dentro de `docs/`, así que ampliarla es tan simple como escribir.

> ⚠️ **Importante:** esta wiki contiene SOLO material seguro para jugadores. Tus documentos con spoilers (encargos, conspiración, etc.) NO están aquí. Ver la sección **Material de GM** al final.

---

## 1. Vista previa en tu computadora

Necesitas [Python 3](https://www.python.org/downloads/) instalado. Luego, en una terminal dentro de esta carpeta:

```bash
pip install -r requirements.txt
mkdocs serve
```

Abre **http://127.0.0.1:8000** en el navegador. Cada vez que guardes un `.md`, la página se recarga sola.

Para generar la versión estática (carpeta `site/`, lista para subir a cualquier hosting):

```bash
mkdocs build
```

---

## 2. Publicarla gratis (para que entren los jugadores)

### Opción A — GitHub Pages (recomendada, sin tocar la terminal después)

1. Crea una cuenta en [github.com](https://github.com) y un repositorio nuevo (ej. `cendral-wiki`).
2. Sube esta carpeta al repo (con GitHub Desktop o `git push`).
3. En el repo: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. Listo. El archivo `.github/workflows/deploy.yml` ya incluido publica la wiki automáticamente en cada cambio. La URL será `https://TU_USUARIO.github.io/cendral-wiki/`.
5. Edita `site_url` (y descomenta `repo_url`) en `mkdocs.yml` con tu URL real.

Comparte ese enlace con tu mesa. Lo abren desde el celular o la computadora, con buscador incluido.

### Opción B — Netlify / Cloudflare Pages

Conecta el repo, pon como comando de build `mkdocs build` y como carpeta de publicación `site`. Despliegue gratuito con dominio propio opcional.

---

## 3. Cómo expandir la wiki

- **Página nueva:** crea un `.md` en la carpeta que toque dentro de `docs/` y añádelo a `nav:` en `mkdocs.yml`.
- **NPC nuevo:** copia cualquier ficha de `docs/personas/`, cambia el contenido, y enlázala desde `docs/personas/index.md` y `nav:`.
- **Enlaces internos:** usa rutas relativas, ej. `[Brek](../personas/brek.md)`.
- **Avisos de color:** `!!! tip`, `!!! warning`, `!!! danger`, `!!! quote` (admoniciones de Material).
- **Pestañas:** bloques `=== "Título"` (ver `clima/index.md`).
- **Buscador, modo claro/oscuro y navegación** ya están configurados.

Estructura actual:

```
docs/
├── index.md            (portada)
├── la-marca/           (región, geografía, vida, peligros, glosario)
├── cendral/            (ciudad y servicios)
├── agos/               (pueblo del sur)
├── veira/              (pueblo costero)
├── logia/             (la logia + crear agente)
├── personas/           (fichas de NPC)
├── clima/              (sistema de clima)
└── stylesheets/        (tema visual)
```

---

## 4. Material de GM (lo que NO va aquí)

La carpeta `_solo_gm/` está **fuera** de `docs/`, así que MkDocs nunca la publica. Tus documentos con spoilers van ahí (o, mejor, en una herramienta privada).

Lo que se dejó fuera deliberadamente, porque revelaría la trama: los tres encargos completos, la Onyx Alliance y la identidad real de ciertos NPCs, el hilo de los siete símbolos, las tablas de encuentros aleatorios y todas las notas marcadas «para el GM».

**Recomendación para tus notas privadas:** usa [Obsidian](https://obsidian.md) (gratis) sobre la carpeta `_solo_gm/`. Es ideal para enlazar NPCs ↔ locaciones ↔ encargos con backlinks y un grafo. Si quieres una *web* privada de GM, monta un segundo MkDocs igual que este pero detrás de contraseña (Cloudflare Access, o el password de Netlify en su plan de pago).

> Recordatorio de seguridad: en una web estática NO existe contraseña real —cualquiera puede leer el código fuente. Si algo es secreto, **no lo publiques**; déjalo local o en un sitio con autenticación de verdad.
