---
permalink: /fr/
title: "Hello !"
layout: single
toc: true
toc_label: "News"
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
lang: fr
ref: home
---


Je suis physicien théoricien, intéressé par l'étude des systèmes complexes inspirés par la biologie à l'aide d'outils venant des processus stochastiques, de la physique statistique et de la thermodynamique.

Je suis actuellement postdoc à <a href="https://amolf.nl/"> AMOLF</a>  à Amsterdam, dans le groupe de <a href="https://amolf.nl/research-groups/biochemical-networks">Pieter Rein ten Wolde</a>. Avant ça, j'étais postdoc indépendant au <a href="https://www.pks.mpg.de/">Max Planck Institute for the Physics of Complex Systems</a> à Dresde, en Allemagne. J'ai obtenu ma [thèse](https://pastel.archives-ouvertes.fr/tel-03980960) avec [David Lacoste](https://www.pct.espci.fr/~david/) au laboratoire [Gulliver](https://www.gulliver.espci.fr/?-home-&lang=fr) à Paris. Investi dans l'[enseignement](/fr/teaching/), qui me tient à coeur, et passioné d'[histoire](/fr/history/) et de philosophie des sciences, allez visiter les pages dédiées !

<!---  Random picture -->

<figure id="home-random-figure" class="home-random-figure is-loading">
  <img id="home-random-image" src="" alt="">
  <figcaption id="home-random-caption"></figcaption>
</figure>

<script>
document.addEventListener("DOMContentLoaded", function () {

  const pictures = {{ site.data.home_images | jsonify }};
  const imageBase = "{{ '/images/homepage/' | relative_url }}";

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

  if (image.naturalHeight > image.naturalWidth) {
    figure.classList.add("portrait");
  } else {
    figure.classList.add("landscape");
  }

  /*
   * Wait until the browser has completely decoded the image
   * before making it visible.
   */
  if (image.decode) {
    try {
      await image.decode();
    } catch (error) {
      /* Continue even if decode() is unavailable or fails. */
    }
  }

  figure.classList.remove("is-loading");

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
<i class="fas fa-lightbulb" aria-hidden="true"></i>  Vous pouvez basculer entre les modes sombre et clair avec le bouton en haut à droite de l'écran ! 

<br/>

🇬🇧  This website is available in english, just click the flag in the top right-hand corner!
</div>

<div class="large-hidden-home">
<i class="fas fa-lightbulb" aria-hidden="true"></i>  Vous pouvez basculer entre les modes sombre et clair avec le bouton dans le menu déroulant "Plus" ! 

<br/>

🇬🇧  This website is available in english, just click the flag in the drop-down menu "Plus"!
</div>

<i class="fas fa-fw fa-envelope" aria-hidden="true"></i>  a (dot) genthon (at) amolf (dot) nl
