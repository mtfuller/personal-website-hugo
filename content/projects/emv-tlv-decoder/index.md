---
title: "EMV TLV decoder"
description: "Paste the hex from a terminal log and get every EMV tag named and explained, including what each flag in the TVR means."
date: 2026-10-07
status: "Planned"
category: "Payments"
weight: 20
highlights:
  - "Runs entirely in the browser; logs never leave your machine"
  - "Explains TVR and TSI bit flags in plain language"
  - "Shareable links for debugging with your team"
stack: ["TypeScript", "EMV"]
note: "Demo coming soon"
preview: |-
  <span class="k">9F02</span> 06 000000004217  <span class="v">Amount  42.17</span>
  <span class="k">5F2A</span> 02 0840          <span class="v">Currency USD</span>
  <span class="k">9F1A</span> 02 0840          <span class="v">Country  US</span>
  <span class="k">95  </span> 05 0000008000    <span class="v">TVR</span>
       <span class="c">└ byte 4: exceeds floor limit</span>
# Listed on the site, but no page until there's a write-up to show.
build:
  render: never
draft: false
---
