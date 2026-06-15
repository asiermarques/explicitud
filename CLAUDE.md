# Explicitud

Sitio web estático generado con **Hugo** que publica textos y microrelatos en español de Asier Marqués. Publicado en https://explicitud.com (desplegado en Netlify).

## Estructura

- `content/textos/` — los textos y microrelatos, un archivo por texto.
- `content/acerca-de.md` — página "Acerca de".
- `archetypes/default.md` — plantilla base para contenido nuevo.
- `hugo.toml` — configuración del sitio (idioma `es`, tema `hugo-theme-texty`).
- `themes/` — tema (submódulo git).
- `layouts/`, `assets/`, `static/` — personalizaciones del sitio.

## Formato de un texto

Cada texto vive en `content/textos/<slug>.md` con frontmatter **TOML** (delimitado por `+++`): `title`, `description`, `date` (formato TOML con zona horaria) y `draft`. El idioma del contenido es **español** y el slug del archivo va en kebab-case sin acentos.

Para crear un texto nuevo, usa el skill **`nuevo-texto`**, que genera el slug, el frontmatter y la fecha a partir del título.

## Comandos útiles

- `hugo server -D` — servidor local de desarrollo (incluye borradores).
- `hugo` — genera el sitio en `public/`.
