---
title: Publications
description: Here are my selected publications
background: "https://miro.medium.com/v2/resize:fit:1400/1*G_VQZcr12g15PZRLifCsGQ.jpeg"
permalink: /publications/
---

[//]: # ({:.alert .alert-warning})

## Journal Articles
{% for group in site.data.publications.journal_articles %}
### {{ group.year }}
{% for item in group.items %}
- {{ item | replace: "Alfarisy, G.A.", "**Alfarisy, G.A.**" | replace: "Gusti Ahmad Fanshuri Alfarisy", "**Gusti Ahmad Fanshuri Alfarisy**" | replace: "Ahmad Fanshuri Alfarisy, G.", "**Ahmad Fanshuri Alfarisy, G.**" }}
{% endfor %}
{% endfor %}

## Conference Proceedings
{% for group in site.data.publications.conference_proceedings %}
### {{ group.year }}
{% for item in group.items %}
- {{ item | replace: "Alfarisy, G.A.", "**Alfarisy, G.A.**" | replace: "Gusti Ahmad Fanshuri Alfarisy", "**Gusti Ahmad Fanshuri Alfarisy**" | replace: "Ahmad Fanshuri Alfarisy, G.", "**Ahmad Fanshuri Alfarisy, G.**" }}
{% endfor %}
{% endfor %}