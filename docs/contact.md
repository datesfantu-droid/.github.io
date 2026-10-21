---
title: Contact
hide:
  - navigation
  - toc
---

<div class="page-intro" markdown>
<span class="eyebrow">Get in touch</span>

# Contact
</div>

<div class="grid cards" markdown>

-   :material-account-outline:{ .lg } **Contact person**

    {{ project.contact.person }}

-   :material-email-outline:{ .lg } **Email**

    [{{ project.contact.email }}](mailto:{{ project.contact.email }})

{% if project.contact.phone or project.contact.fax %}
-   :material-phone-outline:{ .lg } **Phone / Fax**

    {% if project.contact.phone %}Phone: {{ project.contact.phone }}<br>{% endif %}
    {% if project.contact.fax %}Fax: {{ project.contact.fax }}{% endif %}
{% endif %}

-   :material-map-marker-outline:{ .lg } **Address**

    {{ project.contact.address }}

-   :material-share-variant-outline:{ .lg } **Follow DELTA-Hub**

    {% for s in project.contact.social %}[:fontawesome-brands-{{ s.icon }}: {{ s.name }}]({{ s.url }}){% if not loop.last %} · {% endif %}{% endfor %}

</div>

**Coordinator:** [{{ project.coordinator.name }}]({{ project.coordinator.url }}) –
{{ project.coordinator.unit }}
