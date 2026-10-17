---
layout: default
title: Gift ideas for everyone on your list
---
<section class="hero">
<div class="hero-copy">
<div class="eyebrow">Gift guides, sorted by person</div>
<h1>Gifts that show you were paying attention.</h1>
<p>Short, opinionated picks for the people on your list. No 50-item lists.</p>
<a class="buy" href="#guides">Browse guides</a>
</div>
<div class="mosaic" aria-hidden="true"><div class="t red big">{% include icon.html name="gift" %}</div><div class="t yellow">{% include icon.html name="coffee" %}</div><div class="t green">{% include icon.html name="flower-tulip" %}</div><div class="t blue wide">{% include icon.html name="book-open" %}</div></div>
</section>
<section id="guides" class="bento">
{% assign gs = site.pages | where_exp: "p", "p.path contains 'guides/'" | sort: "date" | reverse %}
{% for g in gs %}<a class="card" href="{{ g.url | relative_url }}"><div class="card-art {{ g.tag_color }}">{% include icon.html name=g.icon %}</div><div class="card-body"><span class="tag {{ g.tag_color }}">{{ g.occasion | default: 'Guide' }}</span><h3>{{ g.title }}</h3><p>{{ g.description }}</p></div></a>
{% endfor %}
</section>
