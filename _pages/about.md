---
permalink: /
title: "Hello!"
layout: single
seo_title: "Arthur Genthon"
toc: true
toc_label: "News"
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
# The following are core pages of academic pages, redirected to / for the moment because filled by default:
  - /cv/
  - /markdown/
  - /archive-layout-with-content/
  - /categories/
  - /collection-archive/
  - /non-menu-page/
  - /page-archive/
  - /portfolio/
  - /sitemap/
  - /tags/
  - /talkmap.html
  - /talks/
  - /terms/
  - /year-archive/
lang: en
ref: home
---


I am a theoretical physicist working on complex systems inspired by biology, with tools from stochastic processes, statistical physics and thermodynamics.

I am currently a postdoc in <a href="https://amolf.nl/"> AMOLF</a> in Amsterdam, in the group of <a href="https://amolf.nl/research-groups/biochemical-networks">Pieter Rein ten Wolde</a>. Before that, I was an independent postdoc at the <a href="https://www.pks.mpg.de/">Max Planck Institute for the Physics of Complex Systems</a> in Dresden, Germany. I obtained my [PhD](https://pastel.archives-ouvertes.fr/tel-03980960) with [David Lacoste](https://www.pct.espci.fr/~david/) at the [Gulliver](https://www.gulliver.espci.fr/?-home-&lang=fr) laboratory in Paris. Besides, I am also invested in [teaching](/teaching/), and fond of [history](/history/) and philosophy of sciences! 


<!---  Random picture -->

<figure id="home-random-figure"
        class="home-random-figure"
        style="display: none;">
  <img id="home-random-image" src="" alt="">
  <figcaption id="home-random-caption"></figcaption>
</figure>

<script>
document.addEventListener("DOMContentLoaded", function () {

  const pictures = {{ site.data.home_images | jsonify }};
  const imageBase = "{{ '/images/homepage_web/' | relative_url }}";

  if (!Array.isArray(pictures) || pictures.length === 0) {
    return;
  }

  /*
   * Avoid displaying the same picture twice in a row.
   * localStorage remembers the previous image even after
   * the visitor closes and reopens the browser.
   */
  let previousFile = null;

  try {
    previousFile = localStorage.getItem("previousHomeImage");
  } catch (error) {
    /* localStorage may be disabled; random selection still works. */
  }

  let availablePictures = pictures.filter(function (picture) {
    return picture.file !== previousFile;
  });

  /* Necessary when there is only one picture. */
  if (availablePictures.length === 0) {
    availablePictures = pictures;
  }

  const randomIndex =
    Math.floor(Math.random() * availablePictures.length);

  const selectedPicture = availablePictures[randomIndex];

  const figure = document.getElementById("home-random-figure");
  const image = document.getElementById("home-random-image");
  const caption = document.getElementById("home-random-caption");

  caption.innerHTML = selectedPicture.caption || "";
  image.alt = selectedPicture.alt || "";

  /*
   * Detect automatically whether the selected image is
   * portrait or landscape.
   */
  image.addEventListener("load", async function () {

  /* Determine the final size first. */
  if (image.naturalHeight > image.naturalWidth) {
    figure.classList.add("portrait");
  } else {
    figure.classList.add("landscape");
  }

  /*
   * Wait until the browser has fully decoded the image.
   * This avoids seeing a progressive top-to-bottom JPEG render.
   */
  if (image.decode) {
    try {
      await image.decode();
    } catch (error) {
      /* If decode() fails, still display the loaded image. */
    }
  }

  /* Only now make the complete figure visible. */
  figure.style.display = "block";

}, { once: true });

  image.src = imageBase + selectedPicture.file;

  try {
    localStorage.setItem(
      "previousHomeImage",
      selectedPicture.file
    );
  } catch (error) {
    /* Nothing to do if localStorage is unavailable. */
  }

});
</script>


<!--- Page footers, button switches + email -->

<div class="small-hidden-home">
<i class="fas fa-lightbulb" aria-hidden="true"></i>  You can switch between dark and light mode with the button in the top right corner! 

<br/>

🇫🇷  Ce site est disponible en français, en cliquant sur le drapeau en haut à droite de l'écran !
</div>

<div class="large-hidden-home">
<i class="fas fa-lightbulb" aria-hidden="true"></i>  You can switch between dark and light mode in the menu <i class="fas fa-cog" aria-hidden="true"></i>

<br/>

🇫🇷  Ce site est disponible en français dans le menu <i class="fas fa-cog" aria-hidden="true"></i>
</div>

<i class="fas fa-fw fa-envelope" aria-hidden="true"></i>  a (dot) genthon (at) amolf (dot) nl
