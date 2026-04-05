---
layout: default
title: Home
body_class: page-home
permalink: /
---

<!-- HERO -->
<section class="hero">
  <div class="hero-bg-text" aria-hidden="true">WRITER</div>
  <div class="hero-content">
    <div class="hero-eyebrow">Welcome to my corner of the internet</div>
    <h1 class="hero-name">{{ site.title | split: " " | first }}<br><em>{{ site.title | split: " " | last }}</em></h1>
    <p class="hero-tagline">{{ site.tagline }}</p>
    <div class="hero-cta-row">
      <a href="{{ '/chronicles/' | relative_url }}" class="btn btn-primary">Read the Chronicles</a>
      <a href="{{ '/about/' | relative_url }}" class="btn btn-ghost">About Me</a>
    </div>
  </div>
  <div class="hero-scroll-hint" aria-hidden="true">
    <span>scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- ABOUT INTRO -->
<section class="intro section">
  <div class="container intro-grid">
    <div class="intro-text">
      <h2>A little about <em>this place</em></h2>
      <p>This is where I write. Every week I sit down, pick something that caught my attention — a conversation, a trip, a book, a thought at 2am — and I try to make sense of it in words.</p>
      <p>No algorithm. No brand. Just honest writing, published on a schedule I hold myself to.</p>
      <a href="{{ '/chronicles/' | relative_url }}" class="text-link">Browse all posts →</a>
    </div>
    <div class="intro-stats">
      <div class="stat-card">
        <span class="stat-num">{{ site.posts | size }}</span>
        <span class="stat-label">Posts published</span>
      </div>
      <div class="stat-card">
        <span class="stat-num">52</span>
        <span class="stat-label">Weeks per year, always writing</span>
      </div>
      <div class="stat-card">
        <span class="stat-num">1</span>
        <span class="stat-label">Voice. Always mine.</span>
      </div>
    </div>
  </div>
</section>

<!-- WHAT I WRITE ABOUT -->
<section class="topics section">
  <div class="container">
    <h2 class="section-title">What I write about</h2>
    <div class="topics-grid">
      <div class="topic-item">
        <span class="topic-icon">✍️</span>
        <h3>Personal Essays</h3>
        <p>Observations from everyday life, shaped into stories worth sharing.</p>
      </div>
      <div class="topic-item">
        <span class="topic-icon">🌍</span>
        <h3>Travel &amp; Place</h3>
        <p>The textures, sounds and small moments that make a place unforgettable.</p>
      </div>
      <div class="topic-item">
        <span class="topic-icon">📚</span>
        <h3>Books &amp; Ideas</h3>
        <p>What I'm reading, thinking about, and how it changes the way I see things.</p>
      </div>
      <div class="topic-item">
        <span class="topic-icon">🤔</span>
        <h3>Long-form Reflection</h3>
        <p>The slow-burning questions that don't fit in a tweet.</p>
      </div>
    </div>
  </div>
</section>

<!-- LATEST POST -->
{% if site.posts.size > 0 %}
{% assign latest = site.posts.first %}
<section class="latest section">
  <div class="container">
    <div class="latest-header">
      <h2>Latest from the Chronicles</h2>
      <a href="{{ '/chronicles/' | relative_url }}" class="text-link">See all →</a>
    </div>
    <div class="latest-card">
      <div class="latest-card-inner">
        {% if latest.tag %}<span class="latest-tag">{{ latest.tag }}</span>{% endif %}
        <h3 class="latest-title">
          <a href="{{ latest.url | relative_url }}">{{ latest.title }}</a>
        </h3>
        <p class="latest-excerpt">{{ latest.excerpt | strip_html | truncatewords: 40 }}</p>
        <div class="latest-meta">
          <time datetime="{{ latest.date | date_to_xmlschema }}">{{ latest.date | date: "%d %B %Y" }}</time>
          <span>·</span>
          {% if latest.read_time %}<span>{{ latest.read_time }}</span>{% else %}<span>{{ latest.content | number_of_words | divided_by: 200 | plus: 1 }} min read</span>{% endif %}
        </div>
        <a href="{{ latest.url | relative_url }}" class="btn btn-primary" style="margin-top:1.5rem">Read Post →</a>
      </div>
    </div>
  </div>
</section>
{% endif %}
