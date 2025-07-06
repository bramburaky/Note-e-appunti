---
layout: post
title: Capo Verde Stories
category: work
importance: 1
image: assets/img/cover_podcast_stories.png
description: Una serie di storie e studi sulle isole di Capo Verde.
permalink: /podcast/cape_verde_podcast_stories/
hidden: false
---

<style>
.podcast-episode {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
  align-items: flex-start;
}

.podcast-episode img {
  max-width: 100%;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.podcast-info {
  flex: 1;
}

.podcast-info h3 {
  margin-top: 0;
  margin-bottom: 0.3em;
}

audio {
  width: 100%;
  min-width: 200px;
  max-width: 100%;
  margin-top: 0.5em;
  display: block;
}

/* Layout orizzontale su schermi medio-grandi */
@media (min-width: 576px) {
  .podcast-episode {
    flex-direction: row;
  }

  .podcast-episode img {
    max-width: 180px;
  }
}
</style>


<div class="podcast-episode">
  <img src="{{ 'assets/img/cover_podcast_capo_verde2.png' | relative_url }}" alt="Copertina episodio 1">
  <div class="podcast-info">
    <h3>Episodio 01 – Identità e migrazione a Capo Verde</h3>
    <p>Con Martina Giuffrè e Giacomo Pozzi, tratto dalla rivista “LARES” (2023).</p>
    <audio controls>
      <source src="{{ '/assets/audio/cape_verdean_anthropology.mp3' | relative_url }}" type="audio/mpeg">
      Il tuo browser non supporta l'elemento audio.
    </audio>
  </div>
</div>
