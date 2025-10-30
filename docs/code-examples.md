### Title

```yaml title="idk.yml" linenums="1" hl_lines="7-8"
markdown_extensions:
  - attr_list
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - pymdownx.superfences
```

```yaml title="idk.yml" linenums="1" hl_lines="10-14"
site_name: My Docs
site_url: http://mkdocs.nedevski.com
theme:
  name: material
  icon:
    logo: fontawesome/solid/blog
  palette:
    - scheme: slate
      toggle:
        icon: material/weather-sunny
        name: Dark mode
      primary: green
      accent: deep purple
    - scheme: default
      toggle:
        icon: material/weather-night
        name: Light mode
      primary: green
      accent: deep purple
```
