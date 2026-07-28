---
title: Publications
layout: default
permalink: /publications/
published: true
---

<div class="publications-container">
  <h1>Publications</h1>

  <p>More information about publications can be found on my <a href="https://scholar.google.com/citations?user=AUVET5QAAAAJ&hl" target="_blank">Google Scholar profile</a>.</p>

  {% assign sorted_publications = site.publications | sort: 'year' | reverse %}

  {% for publication in sorted_publications %}
    <div class="publication-entry" id="publication-{{ publication.title | slugify }}">
      <div class="publication-venue-bubble">
        <span class="publication-venue-name">{{ publication.venue_short | default: publication.journal }}</span>
        <span class="publication-venue-year">{{ publication.year }}</span>
      </div>

      <div class="publication-details">
        <h2 class="publication-title">
          {% if publication.external_url %}
            <a href="{{ publication.external_url }}" target="_blank">{{ publication.title }}</a>
          {% else %}
            {{ publication.title }} <span class="publication-link-soon">(link coming soon)</span>
          {% endif %}
        </h2>

        <p class="publication-authors">{{ publication.authors }}</p>
        <p class="publication-journal">
          <em>{{ publication.journal }}</em>{% if publication.acceptance_rate %} <span class="publication-rate">· {{ publication.acceptance_rate }}</span>{% endif %}
        </p>

        <div class="publication-links">
          {% if publication.external_url %}
            <a href="{{ publication.external_url }}" target="_blank">Paper</a>
          {% endif %}
          {% if publication.abstract %}
            <details class="publication-toggle publication-abstract">
              <summary>Abstract</summary>
              <p>{{ publication.abstract }}</p>
            </details>
          {% endif %}
          {% if publication.bibtex %}
            <details class="publication-toggle publication-cite">
              <summary>Cite</summary>
              <div class="cite-box">
                <button class="cite-copy" type="button" aria-label="Copy BibTeX">Copy</button>
                <pre class="cite-bibtex">{{ publication.bibtex }}</pre>
              </div>
            </details>
          {% endif %}
        </div>
      </div>
    </div>
  {% endfor %}
</div>

<script>
  document.querySelectorAll('.cite-copy').forEach(function (btn) {
    btn.addEventListener('click', function () {
      var pre = btn.parentElement.querySelector('.cite-bibtex');
      if (!pre) return;
      var text = pre.innerText;
      var done = function () {
        var original = btn.textContent;
        btn.textContent = 'Copied!';
        btn.classList.add('is-copied');
        setTimeout(function () {
          btn.textContent = original;
          btn.classList.remove('is-copied');
        }, 1500);
      };
      if (navigator.clipboard && navigator.clipboard.writeText) {
        navigator.clipboard.writeText(text).then(done, function () {});
      } else {
        var range = document.createRange();
        range.selectNode(pre);
        var sel = window.getSelection();
        sel.removeAllRanges();
        sel.addRange(range);
        try { document.execCommand('copy'); done(); } catch (e) {}
        sel.removeAllRanges();
      }
    });
  });
</script>
