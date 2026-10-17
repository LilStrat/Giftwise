---
layout: default
title: Gift ideas for everyone on your list
---
<section class="hero">
<div class="hero-copy">
<h1>Gifts that show you were paying <em>attention.</em></h1>
<p>Short, opinionated picks for the people on your list. No 50-item lists.</p>
<a class="buy" href="#guides">Browse guides</a>
</div>
<div class="mosaic" aria-hidden="true"><div class="t red big">{% include icon.html name="gift" %}</div><div class="t yellow">{% include icon.html name="coffee" %}</div><div class="t green">{% include icon.html name="flower-tulip" %}</div><div class="t blue wide">{% include icon.html name="book-open" %}</div></div>
</section>

{% assign gs = site.pages | where_exp: "p", "p.path contains 'guides/'" | sort: "date" | reverse %}
<section id="occasions" class="occasions">
<h2>Shop by occasion</h2>
<div class="occ-row">
{% for o in site.data.occasions %}{% assign n = gs | where: "occasion", o.key | size %}
<a class="occ" href="{% if n > 0 %}#guides{% else %}#occasions{% endif %}"{% if n == 0 %} aria-disabled="true"{% endif %}>
<span class="occ-icon {{ o.color }}">{% include icon.html name=o.icon %}</span>
<strong>{{ o.key }}</strong><span class="occ-when">{{ o.when }}</span>
<span class="occ-count">{% if n > 0 %}{{ n }} guide{% if n > 1 %}s{% endif %}{% else %}Coming soon{% endif %}</span>
</a>{% endfor %}
</div>
</section>

<section id="guides" class="latest">
<h2>Latest guides</h2>
<div class="bento">
{% for g in gs %}<a class="card" href="{{ g.url | relative_url }}"><div class="card-art {{ g.tag_color }}">{% include icon.html name=g.icon %}</div><div class="card-body"><span class="tag {{ g.tag_color }}">{{ g.occasion | default: 'Guide' }}</span><h3>{{ g.title }}</h3><p>{{ g.description }}</p><span class="more">Read the guide <span aria-hidden="true">&rarr;</span></span></div></a>
{% endfor %}
</div>
</section>
