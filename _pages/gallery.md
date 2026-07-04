---
layout: page
title: gallery
permalink: /gallery/
description: A few moments I've captured through my lens 📸 — a work in progress.
nav: true
nav_order: 4
images:
  slider: true # enables the Swiper image slider used below
---

<!-- ─────────────────────────────────────────────────────────────────────
     Photo gallery.
     • Drop your photos into  assets/img/gallery/  (.jpg / .jpeg / .png / .gif).
       They appear here automatically, sorted by file name.
     • Tip: name files with a zero-padded prefix (01.jpg, 02.jpg, …) to control
       the order they show up in.
     • Browse with the arrows, the dots, or the ← → keys.
     ───────────────────────────────────────────────────────────────────── -->

{% assign gallery_pics = site.static_files | where_exp: "file", "file.path contains '/assets/img/gallery/'" | sort: "path" %}

<swiper-container class="gallery-swiper" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" keyboard="true" rewind="true">
{% for file in gallery_pics %}{% assign ext = file.extname | downcase %}{% if ext == ".jpg" or ext == ".jpeg" or ext == ".png" or ext == ".gif" %}{% assign p = file.path | remove_first: "/" %}
  <swiper-slide>{% include figure.liquid loading="eager" path=p class="img-fluid rounded z-depth-1" %}</swiper-slide>{% endif %}{% endfor %}
</swiper-container>

<p class="text-center mt-3" style="opacity: 0.7;">Use the arrows, the dots, or your ← → keys to browse. More coming soon.</p>
