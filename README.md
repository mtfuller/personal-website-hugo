# personal-website-hugo

Source for [thomasfuller.codes](https://thomasfuller.codes), built with [Hugo](https://gohugo.io).

## Run it locally

```sh
hugo server
```

Then open http://localhost:1313. `hugo --minify` builds the site into `public/`.

## Where things live

| What | Where |
|---|---|
| Homepage hero copy | `content/_index.md` (`hero:` front matter) |
| Homepage experience rows | `data/experience.yaml` |
| "In progress" posts on the homepage | `data/upcoming.yaml` (turn off with `showUpcoming` in `config.toml`) |
| Résumé, with employers | `content/about/index.md` |
| Posts | `content/blog/<slug>/index.md`, images in the same folder |
| Projects | `content/projects/<slug>/index.md` |
| Social links, email, form endpoint, analytics | `[params]` in `config.toml` |
| Styles (both themes) | `assets/css/main.css` |
| Templates | `layouts/` |

New content: `hugo new blog/my-post/index.md` or `hugo new projects/my-tool/index.md`. The archetypes list every supported field.

## Themes

The site has a dark and a light palette, defined as CSS variables at the top of `assets/css/main.css`. On first visit it follows the visitor's system setting; the toggle in the nav overrides that and is remembered in `localStorage`.

## Featured post

Set `featured: true` on one post to pin it to the homepage. Without one, the newest post is featured.
