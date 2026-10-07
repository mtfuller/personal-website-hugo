---
title: "Payments MCP server"
description: "Gives coding agents real payments tools, so they can read terminal logs and authorization messages alongside you instead of guessing."
date: 2026-10-07
status: "In design"
status_accent: true
category: "Payments × AI"
weight: 10
highlights:
  - "Decodes EMV TLV and ISO 8583 as agent tools"
  - "Masks card numbers before anything reaches the model"
  - "Works with any MCP-capable coding agent"
stack: ["Go", "MCP", "ISO 8583"]
note: "Repo coming soon"
preview: |-
  <span class="k">→ decode_iso8583(msg)</span>
    MTI   0100  <span class="c">authorization request</span>
    DE2   4761 •••• •••• 0010
    DE4   000000004217  <span class="v">$42.17</span>
    DE49  840           <span class="v">USD</span>
    <span class="c">PAN masked before the model sees it</span>
# Listed on the site, but no page until there's a write-up to show.
build:
  render: never
draft: false
---
