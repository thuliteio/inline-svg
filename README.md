# Hyas inline SVG

Official inline SVG integration for Hyas.

## Status

[![npm (scoped)](https://img.shields.io/npm/v/@hyas/inline-svg?style=flat-square)](https://www.npmjs.com/package/@hyas/inline-svg)


## Installation

```bash
npm i -D @hyas/inline-svg
```

### Icon set

Optionally, install one or more icon sets, e.g., [Tabler Icons](https://tabler-icons.io/) and [Bootstrap Icons](https://icons.getbootstrap.com/):

```bash
npm i -D @tabler/icons bootstrap-icons
```

## Setup

Add mounts to `./config/_default/module.toml`:

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
  source = "node_modules/@hyas/inline-svg/layouts"
  target = "layouts"

[[mounts]]
  source = "assets"
  target = "assets"

[[mounts]]
  source = "layouts"
  target = "layouts"
```

Set the default icon set directory `icon_set_dir` in `./config/_default/params.yml`:

```yml
inline_svg:
  icon_set_dir: "bootstrap-icons" # null (default), tabler-icons, or bootstrap-icons
```

## How to use

See the Hyas documentation:

- [Inline SVG](https://docs.gethyas.com/guides/integrations-guide/inline-svg/)

## Credits

This npm package is based on the Hugo module:

- [hugo-mod-svg-icon-system](https://github.com/UtkarshVerma/hugo-modules/tree/main/svg-icon-system)
