---
name: nuevo-texto
description: Crea un nuevo archivo de texto/microrelato en content/textos/ a partir del título que da el usuario. Genera el slug del nombre de archivo, el frontmatter TOML (title, description, date, draft) y la fecha actual con zona horaria. Úsalo cuando el usuario quiera empezar un texto nuevo, crear una entrada nueva o diga "nuevo texto/relato con el título ...".
---

# Crear un nuevo texto

Crea un archivo nuevo en `content/textos/` para el sitio Hugo "Explicitud" a partir del título que indique el usuario.

## Pasos

1. **Obtén el título.** Si el usuario no lo ha dado, pídeselo. El título es lo único imprescindible.

2. **Genera el slug** del nombre de archivo a partir del título:
   - Todo en minúsculas.
   - Sustituye espacios por guiones (`-`).
   - Elimina acentos y diéresis: á→a, é→e, í→i, ó→o, ú→u, ü→u, ñ→n.
   - Elimina signos de puntuación y caracteres especiales.
   - Ejemplos: "Tortilla de patatas" → `tortilla-de-patatas`, "Pinza" → `pinza`, "El navío" → `el-navio`.

3. **Comprueba que no exista** ya `content/textos/<slug>.md`. Si existe, avisa al usuario y pregunta si quiere otro nombre antes de sobrescribir nada.

4. **Obtén la fecha actual** con la zona horaria correcta. Usa `date "+%Y-%m-%dT%H:%M:%S%z"` y conviértela al formato TOML con dos puntos en el offset (ej.: `2026-06-15T12:38:00+02:00`). En España el offset es `+02:00` en horario de verano y `+01:00` en invierno.

5. **Crea el archivo** `content/textos/<slug>.md` con este contenido:

   ```toml
   +++
   title = 'Título tal cual lo dio el usuario'
   description = ''
   date = <fecha actual en formato TOML>
   draft = true
   +++

   ```

   - `title`: el título literal del usuario, con comillas simples. Respeta sus mayúsculas; si lo da todo en minúsculas, pon la primera letra en mayúscula (estilo frase).
   - `description`: déjala vacía salvo que el usuario indique una.
   - `draft = true`: empieza como borrador. El usuario lo pondrá a `false` al publicar.
   - Deja el cuerpo vacío (una línea en blanco) para que el usuario empiece a escribir, salvo que haya facilitado contenido.

6. **Confirma** al usuario la ruta del archivo creado y recuérdale que está en borrador (`draft = true`).

## Notas

- No publiques ni hagas commit salvo que el usuario lo pida.
- Si el usuario facilita también una descripción o el cuerpo del texto, inclúyelos.
