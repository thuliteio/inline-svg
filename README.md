# Hyas inline SVG

Official inline SVG integration for Hyas.

## Status

[![CodeQL](https://github.com/gethyas/inline-svg/actions/workflows/codeql.yml/badge.svg)](https://github.com/gethyas/inline-svg/actions/workflows/codeql.yml)

## Installation

```bash
npm i -D @hyas/inline-svg
```

### Icon set

Optionally, install one or more icon sets, e.g. [Tabler Icons](https://tabler-icons.io/) and [Bootstrap Icons](https://icons.getbootstrap.com/):

```bash
npm i -D @tabler/icons bootstrap-icons
```

## Setup

Add to `./config/_default/module.toml`:

```toml
[[mounts]]
  source = "node_modules/bootstrap-icons/icons"
  target = "assets/svgs/bootstrap-icons"

[[mounts]]
  source = "node_modules/@tabler/icons/icons"
  target = "assets/svgs/tabler-icons"

[[mounts]]
  source = "assets/svgs"
  target = "assets/svgs"

[[mounts]]
  source = "node_modules/@hyas/inline-svg-dev/layouts"
  target = "layouts"

[[mounts]]
  source = "assets"
  target = "assets"

[[mounts]]
  source = "layouts"
  target = "layouts"
```

Set default `icon_set_dir` in `params.yml`:

```yml
inline_svg:
  icon_set_dir: "bootstrap-icons" # tabler-icons (default)
```

## Usage

### Partial

Insert an icon from an icon set:

```md
{{ partial "inline-svg" "rubber-stamp" }}
```

Insert any SVG (path relative to `./assets/`):

```md
{{ partial "inline-svg" "svgs/logos/logo-netlify-small-fullcolor-darkmode.svg" }}
```

Specify a custom title and description for the SVG:

```md
{{ partial "inline-svg" (dict "icon" "rubber-stamp" "title" "Rubber stamp" desc="Rubber stamp") }}
```

Specify SVG attributes, for example:

```md
{{ partial "inline-svg" (dict "icon" "rubber-stamp" "stroke" "#d32e9d" "stroke-width" "1" "height" "3rem" "width" "3rem" "class" "svg-inline-custom") }}
```

### Shortcode

Insert an icon from an icon set:

```md
{{< inline-svg "rubber-stamp" >}}
```

Insert any SVG (path relative to `./assets/`):

```md
{{< inline-svg "svgs/logos/logo-netlify-small-fullcolor-darkmode.svg" >}}
```

Specify a custom title and description for the SVG:

```md
{{< inline-svg src="rubber-stamp" title="Rubber stamp" desc="Rubber stamp">}}
```

Specify SVG attributes, for example:

```md
{{< inline-svg src="rubber-stamp" stroke="#d32e9d" stroke-width="1" height="3rem" width="3rem" class="svg-inline-custom" >}}
```

Insert an SVG from page resources:

```
{{< inline-svg src="alien.svg" fill="yellowgreen" stroke="#1d2d35" stroke-width="1" height="3rem" width="3rem" class="svg-inline-custom" >}}
```

### CSS

An SVG gets inserted with two classes: `<filename>` and `svg-inline`. Use the `svg-inline-custom` class for overriding the global `svg-inline` definition.

```css
.content .svg-inline {
  margin-bottom: 1.5rem;
}

.content .svg-inline:not(.svg-inline-custom) {
  height: 1.5rem;
  width: 1.5rem;
  stroke-width: 1.5;
}

.rubber-stamp.svg-inline {
  stroke: red;
}
```

## Credits

Based on [hugo-mod-svg-icon-system](https://github.com/UtkarshVerma/hugo-modules/tree/main/svg-icon-system)
