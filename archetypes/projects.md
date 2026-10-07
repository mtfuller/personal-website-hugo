---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
description: ""
# Short status shown on the card, e.g. "Shipped 2026", "In design", "Planned".
status: ""
status_accent: false
category: ""
# Lower numbers show first.
weight: 100
highlights: []
stack: []
repo: ""
demo: ""
# Shown in the card footer when there's no write-up or repo yet.
note: ""
# Either a featured_image in this bundle's images/ folder...
featured_image: ""
image_alt: ""
# ...or a small code preview. Spans: <span class="k">key</span>, <span class="v">value</span>, <span class="c">comment</span>.
preview: ""
# Remove this block once the project has a write-up worth its own page.
build:
  render: never
draft: true
---
