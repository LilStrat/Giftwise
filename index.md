---
layout: default
title: Gift ideas for everyone on your list
---
{% assign gs = site.pages | where_exp: "p", "p.path contains 'guides/'" | sort: "date" | reverse %}
<section class="hero">
<div class="hero-copy">
<h1>Gifts that show you were paying <em>attention.</em></h1>
<p>Short, opinionated picks for the people on your list. No 50-item lists, no filler.</p>
<div class="ctas"><a class="btn primary" href="#guides">Browse guides</a><a class="btn ghost" href="#occasions">Shop by occasion</a></div>
</div>
<div class="collage">
<div class="c1">{% include photo.html src="https://images.unsplash.com/photo-1513885535751-8b9238bd345a" alt="Wrapped gift boxes" icon="gift" color="red" w=900 loading="eager" %}</div>
<div class="c2">{% include photo.html src="https://images.unsplash.com/photo-1549465220-1a8b9238cd48" alt="A gift tied with ribbon" icon="heart" color="yellow" w=600 loading="eager" %}</div>
<div class="c3">{% include photo.html src="https://images.unsplash.com/photo-1512909006721-3d6018887383" alt="Presents under soft lights" icon="tree-evergreen" color="green" w=600 loading="eager" %}</div>
</div>
</section>

{% assign next = site.data.occasions | first %}
<section class="next">
<div class="next-icon">{% include icon.html name=next.icon %}</div>
<div class="next-copy"><h2>{{ next.key }} is {{ next.when }}.</h2><p>Our picks are ready now, so you can order early and skip the last-minute scramble.</p></div>
<a class="btn light" href="#guides">See {{ next.key }} gifts</a>
</section>

<section id="occasions" class="occasions">
<h2>Shop by occasion</h2>
<div class="occ-row">
{% for o in site.data.occasions %}{% assign n = gs | where: "occasion", o.key | size %}
<a class="occ {{ o.color }}" href="{% if n > 0 %}#guides{% else %}#occasions{% endif %}"{% if n == 0 %} aria-disabled="true"{% endif %}>
<span class="occ-icon">{% include icon.html name=o.icon %}</span>
<strong>{{ o.key }}</strong><span class="occ-when">{{ o.when }}</span>
<span class="occ-count">{% if n > 0 %}{{ n }} guide{% if n > 1 %}s{% endif %} ready{% else %}Coming soon{% endif %}</span>
</a>{% endfor %}
</div>
</section>

<section id="guides" class="latest">
<h2>Latest guides</h2>
{% assign odd = gs.size | modulo: 2 %}
<div class="grid">
{% for g in gs %}<a class="card{% if forloop.first and odd == 1 %} feature{% endif %}" href="{{ g.url | relative_url }}">
{% include photo.html src=g.image alt=g.title icon=g.icon color=g.tag_color w=1000 %}
<div class="card-body"><span class="tag {{ g.tag_color }}">{{ g.occasion | default: 'Guide' }}</span><h3>{{ g.title }}</h3><p>{{ g.description }}</p><span class="more">Read the guide <span aria-hidden="true">&rarr;</span></span></div></a>
{% endfor %}
</div>
</section>

<section class="how">
<h2>How we pick</h2>
<ol>
<li><strong>Fewer, better picks.</strong> Each guide has a handful of ideas we would actually give, grouped by the kind of person you are shopping for.</li>
<li><strong>A reason for every pick.</strong> We say who it suits and what to look for, so you can choose with confidence.</li>
<li><strong>Timed for the occasion.</strong> Guides go up weeks ahead, with order-by dates so gifts arrive on time.</li>
</ol>
</section>
