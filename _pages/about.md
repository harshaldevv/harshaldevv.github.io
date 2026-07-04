---
layout: about
title: about
permalink: /
# subtitle: <a href='#'>Affiliations</a>. Address. Contacts. Motto. Etc.
subtitle: Current Life Motto - A moving man will eventually meet his LUCK !!


profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  # more_info: >
  #   # <p>555 your office number</p>
  #   # <p>123 your address street</p>
  #   # <p>Your City, State 12345</p>

selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: true
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts

images:
  slider: true # enables the Swiper image slider used by the profile photo carousel below
---

<!-- ─────────────────────────────────────────────────────────────────────
     Rotating profile photo carousel.
     Replaces the theme's single static profile photo (in the .profile sidebar
     slot) with an auto-rotating Swiper carousel.
     • Add / remove images in  assets/img/profile_pics/  (.jpg / .jpeg / .png).
       They appear automatically, sorted by file name.
     • Auto-advances every 3.5s; use the arrows, the dots, or the ← → keys too.
     The <template> below is injected into the .profile slot by the script,
     replacing the static <img> the theme renders there. If JS is off, the
     static profile photo simply stays.
     ───────────────────────────────────────────────────────────────────── -->
{% assign profile_pics = site.static_files | where_exp: "file", "file.path contains '/assets/img/profile_pics/'" | sort: "path" %}
<template id="profile-carousel-tpl">
  <swiper-container class="profile-swiper" loop="true" autoplay="true" autoplay-delay="3500" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" keyboard="true">
  {% for file in profile_pics %}{% assign ext = file.extname | downcase %}{% if ext == ".jpg" or ext == ".jpeg" or ext == ".png" or ext == ".gif" %}{% assign p = file.path | remove_first: "/" %}
    <swiper-slide><img src="{{ p | relative_url }}" class="img-fluid z-depth-1 rounded" alt="Harshal Dev" loading="eager" /></swiper-slide>{% endif %}{% endfor %}
  </swiper-container>
</template>
<style>
  /* The carousel takes the place of the static profile photo in the sidebar. */
  .profile .profile-swiper { width: 100%; }
  .profile .profile-swiper swiper-slide img { width: 100%; height: 300px; object-fit: cover; }
</style>
<script>
  (function () {
    function mountProfileCarousel() {
      var tpl = document.getElementById("profile-carousel-tpl");
      var profile = document.querySelector(".profile");
      if (!tpl || !profile || profile.dataset.carouselMounted) return;
      var target = profile.querySelector("figure") || profile.querySelector("picture") || profile.querySelector("img");
      var node = tpl.content.cloneNode(true);
      if (target) { target.replaceWith(node); } else { profile.prepend(node); }
      profile.dataset.carouselMounted = "1";
    }
    if (document.readyState === "loading") {
      document.addEventListener("DOMContentLoaded", mountProfileCarousel);
    } else {
      mountProfileCarousel();
    }
  })();
</script>

My name is Harshal Dev (aka Dholchike). I am a Software Engineer based out of India 🇮🇳. I graduated from <a href='https://iiitd.ac.in/'>IIIT Delhi</a> with a Computer Science Engineering (B.Tech) where I played with 0s and 1s.

My interests include Software Engineering, Distributed Systems, Human-Computer Interaction and asking and seeking answers to "questions".

I am always up for a game of Badminton 🏸, Table Tennis 🏓 or Swimming 🏊‍♂️.

I have a penchant for (mobile) Photography — check out my [photo gallery](/gallery/) 📸 (still a work in progress)

I also upload videos on my <a href="https://www.youtube.com/@HarshalDev">YouTube channel</a> to document my life (or as a dumping ground to free up my phone's memory)

PS - I sometimes like to call myself as Self proclaimed chewing gum Connoisseur


<!-- My undergraduate research on UPI's impact on spending bheaviour kinda blew up. Check it out here at (link 1, link 2 , etc) -->

This website is still WIP 🚧⏳🔄🔜 (suggestions are always welcome !!)

<!-- Write your biography here. Tell the world about yourself. Link to your favorite [subreddit](https://www.reddit.com). You can put a picture in, too. The code is already in, just name your picture `prof_pic.jpg` and put it in the `img/` folder. -->

<!-- Put your address / P.O. box / other info right below your picture. You can also disable any of these elements by editing `profile` property of the YAML header of your `_pages/about.md`. Edit `_bibliography/papers.bib` and Jekyll will render your [publications page](/al-folio/publications/) automatically. -->

<!-- Link to your social media connections, too. This theme is set up to use [Font Awesome icons](https://fontawesome.com/) and [Academicons](https://jpswalsh.github.io/academicons/), like the ones below.  -->

<!-- Add your Facebook, Twitter, LinkedIn, Google Scholar, or just disable all of them. -->
