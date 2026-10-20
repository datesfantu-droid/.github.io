---
title: 3D & VR
hide:
  - navigation
  - toc
---

<div class="page-intro" markdown>
<span class="eyebrow">DELTA-Hub Visualisation Laboratory</span>

# 3D, VR & AR models

Explore the Danube Delta in three dimensions: bathymetric and topographic models, simulation
animations and virtual tours created by the DELTA-Hub Visualisation and Science Outreach Laboratory.
Models open directly in the browser – on a computer, a phone (augmented reality) or a VR headset.
</div>

{% set device_icons = {
  "computer": "M21 16H3V4h18m0-2H3c-1.11 0-2 .89-2 2v12a2 2 0 0 0 2 2h7v2H8v2h8v-2h-2v-2h7a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2",
  "phone": "M17 19H7V5h10m0-4H7c-1.11 0-2 .89-2 2v18a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V3a2 2 0 0 0-2-2",
  "headset": "M20.74 6H3.2C2.55 6 2 6.57 2 7.27v10.46c0 .7.55 1.27 1.23 1.27H8c.54 0 1-.32 1.16-.79l1.39-3.47c.24-.58.8-.99 1.45-.99s1.21.41 1.45.99l1.39 3.47c.19.47.62.79 1.11.79h4.79c.71 0 1.26-.57 1.26-1.27V7.27c0-.7-.55-1.27-1.26-1.27M7.22 14.58C6 14.58 5 13.55 5 12.29 5 11 6 10 7.22 10s2.21 1 2.21 2.29c0 1.26-.99 2.29-2.21 2.29m9.56 0c-1.22 0-2.21-1.03-2.21-2.29S15.56 10 16.78 10 19 11.03 19 12.29s-1 2.29-2.22 2.29"
} %}
{% set ready = models | selectattr("src") | list %}
{% if ready %}
<script type="module" src="https://unpkg.com/@google/model-viewer@3.5.0/dist/model-viewer.min.js"></script>
{% endif %}

<div class="model-grid">
{% for m in models %}
  {% if m.app %}
  <article class="model-card model-card--app">
    <a class="model-card__media" href="../{{ m.app }}">
      <img src="../{{ m.poster }}" alt="{{ m.title }}" loading="lazy">
      <span class="model-card__play" aria-hidden="true"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></span>
    </a>
    <div class="model-card__body">
      <span class="badge badge--done">Live</span>
      <h3>{{ m.title }}</h3>
      <p>{{ m.description }}</p>
      {% if m.devices %}
      <ul class="devices" aria-label="Works on">
        {% for d in m.devices %}
        <li><svg viewBox="0 0 24 24" aria-hidden="true"><path d="{{ device_icons[d.icon] }}"/></svg><span><strong>{{ d.label }}</strong>{{ d.note }}</span></li>
        {% endfor %}
      </ul>
      {% endif %}
      <div class="tags">{% for t in m.tags %}<span class="tag">{{ t }}</span>{% endfor %}</div>
      <p class="model-card__actions">
        <a class="md-button md-button--primary" href="../{{ m.app }}">Launch the experience</a>
        {% if m.size %}<span class="model-card__size">{{ m.size }}</span>{% endif %}
      </p>
    </div>
  </article>
  {% elif m.src %}
  <article class="model-card">
    {% set base = "" if m.src.startswith("http") else "../" %}
    <model-viewer src="{{ base }}{{ m.src }}"{% if m.ios_src %} ios-src="{{ base }}{{ m.ios_src }}"{% endif %}{% if m.poster %} poster="{{ base }}{{ m.poster }}"{% endif %}
      alt="{{ m.title }}" camera-controls auto-rotate shadow-intensity="1"
      ar ar-modes="webxr scene-viewer quick-look" loading="lazy">
      <button slot="ar-button" class="ar-button">View in your space</button>
    </model-viewer>
    <div class="model-card__body">
      <h3>{{ m.title }}</h3>
      <p>{{ m.description }}</p>
      <div class="tags">{% for t in m.tags %}<span class="tag">{{ t }}</span>{% endfor %}</div>
    </div>
  </article>
  {% endif %}
{% endfor %}
</div>

## How to use it

<p class="howto-hint">Hover over a device (or tap it on a phone or headset) to see the instructions.</p>

<div class="howto">
{% set howto = [
  {"icon": "computer", "title": "Computer", "sub": "Chrome, Edge or Firefox",
   "steps": ["Click <strong>Launch the experience</strong> and wait for the delta to load.",
             "Press <strong>▶ Începe turul</strong> for the 30-second guided tour, or <strong>Explorează direct</strong> to skip it.",
             "Drag to rotate, scroll to zoom, right-click and drag to move the map.",
             "Click anywhere on the delta to read the water level, depth and current speed.",
             "Open <strong>☰ Meniu</strong> and press <strong>▶ Play</strong> to watch the flood unfold day by day."]},
  {"icon": "phone", "title": "Phone & tablet", "sub": "Android or iPhone / iPad",
   "steps": ["Use Wi-Fi if you can – the experience is about 70 MB.",
             "Start the guided tour, or explore directly.",
             "Drag with one finger to rotate, pinch to zoom, tap the delta to measure.",
             "<strong>Android + Chrome:</strong> tap <strong>START AR</strong> and point the camera at a table or the floor to place the delta in your room.",
             "iPhone and iPad show the 3D view; AR is not available there (Safari does not support WebXR)."]},
  {"icon": "headset", "title": "Headset", "sub": "Meta Quest – mixed reality",
   "steps": ["Open this page in the <strong>Quest Browser</strong> and launch the experience.",
             "Tap <strong>START AR</strong> – the delta appears in your room.",
             "Pinch or grab to move the map; use two hands to rotate and resize it.",
             "Point and press the <strong>trigger</strong>, or touch the delta with your finger, to measure the water.",
             "Press the Meta button to exit."]}
] %}
{% for h in howto %}
  <div class="howto__card" tabindex="0">
    <div class="howto__head">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="{{ device_icons[h.icon] }}"/></svg>
      <div><strong>{{ h.title }}</strong><span>{{ h.sub }}</span></div>
    </div>
    <ol class="howto__steps">
      {% for st in h.steps %}<li>{{ st }}</li>{% endfor %}
    </ol>
  </div>
{% endfor %}
</div>
