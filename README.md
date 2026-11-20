# Quaerens — plantilla para GitHub Pages

Una web estática minimalista para ensayos, notas técnicas y fragmentos literarios. Está diseñada para publicarse **gratis con GitHub Pages**, utilizando **Jekyll**, que procesa automáticamente archivos Markdown. No necesita base de datos, CMS ni herramientas de compilación para publicar desde GitHub. Tampoco carga scripts de terceros por defecto.

## 1. Publicar

1. Crea una cuenta de GitHub separada si no quieres que esta web quede asociada a tu identidad habitual. No uses tu nombre real en el usuario, el perfil ni los datos de autor de Git.
2. Crea un repositorio público llamado `TUUSUARIO.github.io` (sustituye TUUSUARIO por el nombre exacto de la cuenta).
3. Sube el contenido **de esta carpeta** a la raíz del repositorio (`_config.yml`, `index.html`, etc. deben quedar en el nivel superior, no dentro de otra carpeta).
4. En el repositorio, entra en **Settings → Pages**. Selecciona **Deploy from a branch**; elige `main` y `/(root)` y guarda.
5. La web quedará en `https://TUUSUARIO.github.io/` cuando termine el despliegue.

Esta plantilla usa `baseurl: ""`, el valor adecuado para una página de usuario con nombre `TUUSUARIO.github.io`.

## 2. Cambiar el nombre y los subtemas

- En `_config.yml`, edita `title: "Quaerens"` y `description:`. El título aparece en cabecera, portada y título del navegador.
- En `index.html`, modifica si quieres `Una búsqueda sin conclusión.` y el texto pequeño de la portada.
- Los colores, el tamaño de letra y las separaciones están al principio de `assets/css/style.css`.
- El favicon SVG muestra la letra Q; si cambias el nombre, puedes cambiar esa letra en `assets/favicon.svg`.
- Para añadir un subtema, añade su `id` y `nombre` en `temas.filosofia` o `temas.ia` en `_config.yml`. Crea una carpeta con ese `id` bajo `_filosofia/` o `_ia/` (las carpetas son opcionales, pero ayudan a organizar).

## 3. Escribir y publicar nuevos textos

**Cada texto es un archivo `.md` independiente.** Puedes editarlo en GitHub con el botón "Add file → Create new file" o directamente desde tu ordenador.

Estructura de contenidos:

```
_filosofia/
  metafisica/
    lo-que-significa-buscar.md
_ia/
  kge/
    representar-relaciones.md
_fragmentos/
  una-forma-de-silencio.md
```

Los tres textos incluidos son **ejemplos** para comprobar el aspecto de los artículos. Bórralos o sustitúyelos antes de publicar.

Ejemplo para Filosofía, archivo `_filosofia/epistemologia/el-limite-del-conocimiento.md`:

```md
---
title: "El límite del conocimiento"
date: 2026-11-20
tema: epistemologia
lang: es
---

Aquí comienza el ensayo.

## Primera cuestión

Aquí sigue el texto.
```

Ejemplo para IA, archivo `_ia/nn/una-nota-sobre-redes.md`:

```md
---
title: "Una nota sobre redes neuronales"
date: 2026-11-20
tema: nn
lang: es
---

Escribe aquí tu análisis técnico.
```

Ejemplo para Fragmentos, archivo `_fragmentos/o-xeito-de-mirar.md`:

```md
---
title: "O xeito de mirar"
date: 2026-11-20
lang: gl
---

Escribe aquí o teu fragmento.
```

Para alternar entre español y gallego, solo cambia `lang: es` por `lang: gl` en el texto. La navegación permanece en español, pero el atributo de idioma de cada artículo cambia correctamente.

**Importante:** el campo `tema:` debe coincidir exactamente con un `id` de `_config.yml`, si no, el texto no aparecerá en el índice temático. Si le pones una fecha futura, Jekyll puede no mostrarlo hasta esa fecha.

### Fórmulas matemáticas en IA (opcional)

Si un escrito necesita fórmulas LaTeX, añade `math: true` a su cabecera YAML y utiliza la sintaxis de Kramdown:

```md
---
title: "Un modelo de KGE"
date: 2026-11-20
tema: kge
lang: es
math: true
---

Una expresión en línea: $$ f(h,r,t) $$.

$$
f(h,r,t) = -\lVert \mathbf{h}+\mathbf{r}-\mathbf{t}\rVert_2
$$
```

Solo en esos artículos se carga **MathJax** desde un CDN externo; esto puede exponer a ese proveedor datos de conexión de los lectores. Si prefieres cero peticiones externas, evita `math: true` y podremos incorporar una biblioteca matemática local más adelante.

## 4. Dónde hacer cambios

| Qué quieres modificar | Archivo |
| --- | --- |
| Nombre de la web | `_config.yml` |
| Frase de portada | `index.html` |
| Colores y tipografía | `assets/css/style.css` |
| Añadir o cambiar subtemas | `_config.yml` |
| Menú de navegación | `_includes/cabecera.html` |
| Cabecera de los artículos | `_layouts/escrito.html` |
| Pie de página | `_includes/pie.html` |
| Introducciones de cada sección | `filosofia/index.html`, `ia/index.html`, `fragmentos/index.html` |

## 5. Anonimato: precauciones importantes

En GitHub Pages gratuito, el repositorio es **público**, y cualquiera puede abrir el perfil de GitHub, ver el código y consultar los metadatos de las contribuciones. **Un seudónimo en la web no garantiza anonimato.** Para limitar la relación con tu identidad:

- Considera una cuenta de GitHub separada, con usuario, correo de registro, avatar y nombre de perfil no asociados a tu identidad habitual.
- En **Settings → Emails**, activa **Keep my email addresses private** y **Block command line pushes that expose my email**.
- Si trabajas con Git local, configura el nombre de autor seudónimo y **exactamente la dirección `noreply` que GitHub muestre para tu cuenta** antes de realizar los commits. Evita reutilizar la configuración personal previa.
- Revisa las imágenes y archivos antes de subirlos: los documentos y fotos pueden revelar nombres, rutas, ubicación u otros metadatos.
- No publiques biografía, enlaces a redes personales, formularios, analítica o servicios vinculados a tus cuentas habituales.
- El sitio no incorpora tipografías externas, comentarios, cookies o analítica. MathJax solo se carga desde un CDN si activas `math: true` en un artículo.
- Si utilizas otros servicios externos en el futuro, vuelve a revisar la privacidad.

El historial de Git puede conservar información aunque luego borres archivos. Comprueba el contenido y los datos de autor **antes del primer push**.

## 6. Vista local (opcional)

Si instalas Ruby y Jekyll, desde la carpeta ejecuta:

```sh
bundle install
bundle exec jekyll serve
```

Después abre `http://localhost:4000/`.

También puedes trabajar **sin** instalar Ruby, editando los Markdown desde GitHub y dejando que GitHub Pages genere la web automáticamente.

## 7. Cosas que la plantilla no incorpora deliberadamente

- Autores visibles, correo, formularios y comentarios.
- Contadores de lectura, etiquetas extra en las páginas individuales o fechas de modificación.
- Cuentas de analítica, cookies, contenido embebido o tipografías descargadas de terceros.
- Renderización matemática externa por defecto: solo se activa en los textos que incluyan `math: true`.
