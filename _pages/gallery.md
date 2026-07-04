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
       They appear both in the big viewer AND the thumbnail strip automatically,
       sorted by file name (use 01.jpg, 02.jpg, … to control the order).
     • The thumbnail strip below is a long, scrollable row; the photo currently
       in focus is highlighted. Click a thumbnail, use the arrows, or the ← → keys.
     ───────────────────────────────────────────────────────────────────── -->

{% assign gallery_pics = site.static_files | where_exp: "file", "file.path contains '/assets/img/gallery/'" | sort: "path" %}

<div class="gallery-viewer" style="max-width: 820px; margin: 0 auto;">

  <!-- Main viewer -->
  <swiper-container class="gallery-main" navigation="true" keyboard="true" rewind="true" space-between="10" thumbs-swiper=".gallery-thumbs">
  {% for file in gallery_pics %}{% assign ext = file.extname | downcase %}{% if ext == ".jpg" or ext == ".jpeg" or ext == ".png" or ext == ".gif" %}{% assign p = file.path | remove_first: "/" %}
    <swiper-slide>{% include figure.liquid loading="eager" path=p class="img-fluid rounded z-depth-1" %}</swiper-slide>{% endif %}{% endfor %}
  </swiper-container>

  <!-- Scrollable thumbnail strip (active thumb is highlighted) -->
  <swiper-container class="gallery-thumbs" space-between="10" slides-per-view="auto" free-mode="true" watch-slides-progress="true">
  {% for file in gallery_pics %}{% assign ext = file.extname | downcase %}{% if ext == ".jpg" or ext == ".jpeg" or ext == ".png" or ext == ".gif" %}
    <swiper-slide><img src="{{ file.path | relative_url }}" class="rounded" alt="gallery thumbnail" /></swiper-slide>{% endif %}{% endfor %}
  </swiper-container>

</div>

<style>
  .gallery-main { width: 100%; }
  .gallery-thumbs { margin-top: 12px; box-sizing: border-box; }
  .gallery-thumbs swiper-slide { width: 96px; height: 64px; opacity: 0.45; cursor: pointer; transition: opacity 0.2s ease; }
  .gallery-thumbs swiper-slide img { width: 100%; height: 100%; object-fit: cover; border-radius: 6px; display: block; }
  .gallery-thumbs .swiper-slide-thumb-active { opacity: 1; }
  .gallery-thumbs .swiper-slide-thumb-active img { outline: 3px solid var(--global-theme-color); outline-offset: -1px; }
</style>

<p class="text-center mt-3" style="opacity: 0.7;">Click a thumbnail, use the arrows, or your ← → keys to browse. More coming soon.</p>
