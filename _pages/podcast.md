---
layout: page
title: Podcast
permalink: /podcast/
description: Collection of podcast
nav: true
nav_order: 4
display_categories: [work, fun]
horizontal: false
---


<style>
.podcast-episode {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
  align-items: flex-start;
}

.podcast-episode img {
  max-width: 180px;
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
  margin-top: 0.5em;
}
</style>

<div class="podcast-episode">
  <img src="{{ 'assets/img/cover_podcast_capo_verde.png' | relative_url }}" alt="Copertina episodio 1">
  <div class="podcast-info">
    <h3>Episodio 01 – Identità e migrazione a Capo Verde</h3>
    <p>Con Martina Giuffrè e Giacomo Pozzi, tratto dalla rivista “LARES” (2023).</p>
    <audio controls>
      <source src="{{ '/assets/audio/cape_verdean_anthropology.mp3' | relative_url }}" type="audio/wav">
      Il tuo browser non supporta l'elemento audio.
    </audio>
  </div>
</div>

<div class="podcast-episode">
  <img src="{{ '/assets/img/podcast-cover-2.jpg' | relative_url }}" alt="Copertina episodio 2">
  <div class="podcast-info">
    <h3>Episodio 02 – [Titolo episodio]</h3>
    <p>Descrizione dell’episodio.</p>
    <audio controls>
      <source src="{{ '/assets/audio/2_altro_podcast.mp3' | relative_url }}" type="audio/mp3">
      Il tuo browser non supporta l'elemento audio.
    </audio>
  </div>
</div>

