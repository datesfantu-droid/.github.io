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
      <div class="tags">{% for t in m.tags %}<span class="tag">{{ t }}</span>{% endfor %}</div>
      <p class="model-card__actions">
        <a class="md-button md-button--primary" href="../{{ m.app }}">Launch the experience</a>
        {% if m.size %}<span class="model-card__size">{{ m.size }}</span>{% endif %}
      </p>
    </div>
  </article>
  {% else %}
  <article class="model-card">
    {% if m.src %}
    {% set base = "" if m.src.startswith("http") else "../" %}
    <model-viewer src="{{ base }}{{ m.src }}"{% if m.ios_src %} ios-src="{{ base }}{{ m.ios_src }}"{% endif %}{% if m.poster %} poster="{{ base }}{{ m.poster }}"{% endif %}
      alt="{{ m.title }}" camera-controls auto-rotate shadow-intensity="1"
      ar ar-modes="webxr scene-viewer quick-look" loading="lazy">
      <button slot="ar-button" class="ar-button">View in your space</button>
    </model-viewer>
    {% else %}
    <div class="model-placeholder">
      <svg class="model-placeholder__icon" viewBox="0 0 24 24" aria-hidden="true"><path d="M17 22v-2h3v-3h2v3.5c0 .39-.16.74-.46 1.04s-.65.46-1.04.46zM7 22H3.5c-.39 0-.74-.16-1.04-.46S2 20.89 2 20.5V17h2v3h3zM17 2h3.5c.39 0 .74.16 1.04.46s.46.65.46 1.04V7h-2V4h-3zM7 2v2H4v3H2V3.5c0-.39.16-.74.46-1.04S3.11 2 3.5 2zm6 15.25 4-2.3v-4.59l-4 2.3zm-1-6.33 4-2.29-4-2.35-4 2.35zm-5 4.03 4 2.3v-4.59l-4-2.3zm11.23-7.36c.5.32.77.75.77 1.32v6.32c0 .57-.27 1-.77 1.32l-5.48 3.18q-.75.48-1.5 0l-5.48-3.18c-.5-.32-.77-.75-.77-1.32V8.91c0-.57.27-1 .77-1.32l5.48-3.18c.25-.13.5-.19.75-.19s.5.06.75.19z"/></svg>
      <span class="model-placeholder__label">Coming soon</span>
    </div>
    {% endif %}
    <div class="model-card__body">
      <h3>{{ m.title }}</h3>
      <p>{{ m.description }}</p>
      <div class="tags">{% for t in m.tags %}<span class="tag">{{ t }}</span>{% endfor %}</div>
    </div>
  </article>
  {% endif %}
{% endfor %}
</div>

## How to view the models

<div class="grid cards" markdown>

-   :material-monitor:{ .lg } **Computer**

    ---

    Drag to rotate, scroll to zoom, right-click and drag to pan.

-   :material-cellphone:{ .lg } **Phone or tablet – AR**

    ---

    Tap **View in your space** to place the model on your table or floor using augmented reality
    (Android with ARCore, iPhone/iPad with iOS 12+).

-   :material-virtual-reality:{ .lg } **VR headset**

    ---

    Open this page in the headset's browser (e.g. Meta Quest Browser) and choose
    **View in your space** for an immersive WebXR experience.

</div>

## Where the data comes from

The models are produced from field data collected with the project's equipment – the uncrewed
surface vehicle (USV) for shallow-water bathymetry, the multibeam system with IMU-GNSS motion
correction, drones and 360° cameras – and from DELTA-Hub numerical models. They are presented to
the public at Open Days, European Researchers' Night and other outreach events using the mobile
component of the laboratory.
