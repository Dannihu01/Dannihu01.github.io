---
title: Gallery
description:
layout: default
permalink: /gallery/
published: true
---

<p class="gallery-intro">
  Click a tab below to switch galleries and see what I've been up to.
</p>

<div class="tabs" role="tablist" aria-label="Gallery categories">
  <button class="tablink active" onclick="openTab(event, 'orchestra')">Violin & Orchestra</button>
  <button class="tablink" onclick="openTab(event, 'travel')">Travel & Nature</button>
  <button class="tablink" onclick="openTab(event, 'food')">Food</button>
  <button class="tablink" onclick="openTab(event, 'wedding')">Our Wedding ♥️</button>
</div>

<!-- Violin & Orchestra Tab -->
<div id="orchestra" class="tabcontent active">
  <h2>Violin & Orchestra</h2>
  <p class="tab-description">I've been playing violin for 18+ years and absolutely love it.</p>

  <figure class="video-figure">
    <div class="video-embed">
      <iframe
        src="https://www.youtube.com/embed/M450rkYvtC0"
        title="YouTube video player"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        allowfullscreen>
      </iframe>
    </div>
    <figcaption class="caption">
      Senior Year Concerto Competition (2019), Zigeunerweisen by Sarasate
    </figcaption>
  </figure>

  {% include gallery-folder.html folder="/assets/images/Orchestra/" alt_prefix="Orchestra" %}
</div>

<!-- Travel and Nature Tab -->
<div id="travel" class="tabcontent">
  <h2>Travel & Nature</h2>
  <p class="tab-description">A non-exhaustive collection of places I've explored. Click a destination to expand it.</p>

  {% assign base_path = "/assets/images/Travel&Nature/" %}
  {% assign folders = "" | split: "" %}

  {% for file in site.static_files %}
    {% if file.path contains base_path %}
      {% assign relative = file.path | remove: base_path %}
      {% assign folder = relative | split: "/" | first %}
      {% unless folders contains folder %}
        {% assign folders = folders | push: folder %}
      {% endunless %}
    {% endif %}
  {% endfor %}

  {% for folder in folders %}
    {% capture folder_path %}{{ base_path }}{{ folder }}/{% endcapture %}
    <details class="travel-destination">
      <summary class="travel-destination-title">
        {{ folder | replace: "-", " " | replace: "_", " " }}
      </summary>
      <div class="gallery-section">
        {% include gallery-folder.html folder=folder_path alt_prefix=folder %}
      </div>
    </details>
  {% endfor %}
</div>

<!-- Food Tab -->
<div id="food" class="tabcontent">
  <h2>Food 😋</h2>
  <p class="tab-description">I love cooking and trying new foods. Here are some highlights.</p>
  {% include gallery-folder.html folder="/assets/images/Food/" alt_prefix="Food" %}
</div>

<!-- Wedding Tab -->
<div id="wedding" class="tabcontent">
  <h2>Our Wedding ♥️</h2>
  <p class="tab-description">December 20, 2025 — the best day.</p>
  <p class="wedding-credit">
    Photos by
    <a href="https://www.instagram.com/tabronstudios_/?hl=en" target="_blank" rel="noopener">Kalynn Tabron</a>
    with
    <a href="https://www.oncelikeaspark.com/" target="_blank" rel="noopener">Once Like a Spark</a>
  </p>
  {% include gallery-folder.html folder="/assets/images/Wedding/" alt_prefix="Wedding" %}
</div>

<p class="gallery-page-footer">
  &copy; 2026 Danniell Hu. All rights reserved.
  These images may not be used or reproduced without permission.
</p>

<div id="imageModal" class="modal" role="dialog" aria-modal="true" aria-label="Enlarged image" onclick="closeModal()">
  <span class="close" role="button" aria-label="Close image" onclick="closeModal()">&times;</span>
  <img class="modal-content" id="modalImage" alt="">
</div>

<script>
  function openTab(event, tabId) {
    document.querySelectorAll('.tabcontent').forEach(c => c.classList.remove('active'));
    document.querySelectorAll('.tablink').forEach(l => {
      l.classList.remove('active');
      l.setAttribute('aria-selected', 'false');
    });
    document.getElementById(tabId).classList.add('active');
    event.currentTarget.classList.add('active');
    event.currentTarget.setAttribute('aria-selected', 'true');
  }

  function openModal(img) {
    var modal = document.getElementById('imageModal');
    var modalImg = document.getElementById('modalImage');
    modalImg.src = img.src;
    modalImg.alt = img.alt || 'Enlarged image';
    modal.style.display = 'block';
  }

  function closeModal() {
    document.getElementById('imageModal').style.display = 'none';
  }

  // Close the lightbox with the Escape key
  document.addEventListener('keydown', function (e) {
    if (e.key === 'Escape') closeModal();
  });

  // Let tab buttons respond to arrow keys / Enter for keyboard users
  (function () {
    var tabs = Array.prototype.slice.call(document.querySelectorAll('.tablink'));
    tabs.forEach(function (tab, i) {
      tab.setAttribute('role', 'tab');
      tab.setAttribute('aria-selected', tab.classList.contains('active') ? 'true' : 'false');
      tab.addEventListener('keydown', function (e) {
        if (e.key === 'ArrowRight' || e.key === 'ArrowLeft') {
          e.preventDefault();
          var next = e.key === 'ArrowRight' ? tabs[i + 1] || tabs[0] : tabs[i - 1] || tabs[tabs.length - 1];
          next.focus();
          next.click();
        }
      });
    });
  })();
</script>
