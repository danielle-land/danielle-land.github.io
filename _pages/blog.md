---
layout: single
title: "Blog Spot"
permalink: /blog/
author_profile: true
header:
  overlay_image: /assets/blog/blog_banner.jpg
  overlay_filter: 0.3
---

A space for me to share some of my thoughts about current happenings and events (opinions are my own)!

---

<div class="entries-grid">
  {% assign sorted_posts = site.posts | sort: "date" | reverse %}
  {% for post in sorted_posts %}
    {% unless post.categories contains "sample" %}
      <div class="blog-card">

        <a href="{{ post.url | relative_url }}">
          {% if post.header.teaser %}
            <img src="{{ post.header.teaser | relative_url }}" alt="{{ post.title | escape }}">
          {% else %}
            <div class="blog-photo-placeholder">Photo coming soon</div>
          {% endif %}
        </a>

        <div class="blog-card-content">
          <small>{{ post.date | date: "%B %d, %Y" }}</small>

          <h3>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </h3>

          <p>{{ post.excerpt | strip_html | truncatewords: 25 }}</p>

          <a href="{{ post.url | relative_url }}">Read more →</a>
        </div>

      </div>
    {% endunless %}
  {% endfor %}
</div>

<style>
.entries-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.blog-card {
  min-width: 0;
  overflow: hidden;
}

.blog-card img,
.blog-photo-placeholder {
  width: 100%;
  aspect-ratio: 16 / 10;
  object-fit: cover;
  border-radius: 5px;
}

.blog-photo-placeholder {
  background: #353a43;
  color: #b6bbc3;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
}

.blog-card-content {
  padding: 0.8rem 0;
}

.blog-card-content small {
  color: #aeb5be;
  font-size: 0.7rem;
}

.blog-card-content h3 {
  font-size: 1.05rem;
  margin: 0.5rem 0;
  line-height: 1.35;
}

.blog-card-content p {
  font-size: 0.8rem;
  line-height: 1.6;
}

.blog-card-content a {
  text-decoration: none;
}

@media (max-width: 650px) {
  .entries-grid {
    grid-template-columns: 1fr;
  }
}
</style>