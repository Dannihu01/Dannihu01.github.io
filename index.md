---
layout: about
permalink: /
published: true
---

<div class="availability-note">
  <strong>🔎 I'm seeking a research internship for summer 2027.</strong>
  Check out my <a href="{{ '/CV/' | relative_url }}">CV</a> and
  <a href="{{ '/publications/' | relative_url }}">publications</a>.
</div>

<div class="profile-card right">
  <img class="profile" src="{{ '/assets/images/danni_profile.jpg' | relative_url }}" alt="Danniell Hu">
  <p class="profile-contact">dannihu [at] umich [dot] edu</p>
</div>

Hi! My name is Danniell, but I usually go by Danni.


I'm a PhD Candidate in Computer Science at the University of Michigan, advised by [**Elizabeth Bondi-Kelly**](https://sites.google.com/view/elizabethbondi) in the [**Realize Lab**](https://sites.google.com/view/realize-lab) and [**Westley Weimer**](https://web.eecs.umich.edu/~weimerw/) in the Weimer Research Group. 


<div class="research-highlight">
  <strong>I build use-inspired AI systems for real-world deployment, and I study human-AI interaction.</strong>

  Human context (needs, constraints, values) often gets lost during development, and deployed AI changes users' decisions, skills, and capacities. My research addresses both directions: stakeholder-grounded AI design, and evaluation of how AI affects real users. I work primarily in health contexts — currently prenatal care planning and physical therapy.
</div>


<hr class="section-rule">

Previously, I was an R&D Embedded Software Engineer at [**Stryker**](https://www.stryker.com/us/en/index.html), where I developed PCBs and software for hospital bed ecosystems and medical monitoring technologies. I primarily worked in the medical division.

Outside of research, music is a huge part of my life. I've been playing violin for 18 years (and counting!) and continue to be involved by playing in the University of Michigan's [**Campus Symphony Orchestra**](https://sites.google.com/a/umich.edu/campus-orchestras/). I also love sewing, crocheting, cooking, and playing multiplayer competitive video games. 

<hr class="section-rule">

{% assign featured_pubs = site.publications | where: "featured", true | sort: "year" | reverse %}
{% if featured_pubs.size > 0 %}
<div class="news-section-heading"><h2>Selected Publications</h2></div>

<ul class="home-pub-list">
  {% for pub in featured_pubs %}
    <li class="home-pub">
      <div class="home-pub-meta">
        <span class="home-pub-venue">{{ pub.venue_short | default: pub.journal }}</span>
        <span class="home-pub-year">{{ pub.year }}</span>
      </div>
      <div class="home-pub-body">
        <span class="home-pub-title">
          {% if pub.external_url %}<a href="{{ pub.external_url }}" target="_blank" rel="noopener">{{ pub.title }}</a>{% else %}{{ pub.title }}{% endif %}
        </span>
        <span class="home-pub-authors">{{ pub.authors }}</span>
      </div>
    </li>
  {% endfor %}
</ul>

<p class="news-see-all">
  <a href="{{ '/publications/' | relative_url }}">All publications →</a>
</p>

<hr class="section-rule">
{% endif %}

<div class="news-section-heading"><h2>News</h2></div>

{% include news-list.html limit=5 excerpt_words=30 %}

<p class="news-see-all">
  <a href="{{ '/news/' | relative_url }}">See all news →</a>
</p>
