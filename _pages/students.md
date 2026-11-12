---
layout: page
permalink: /students/
title: students
description: PhD, master's and undergraduate students I have supervised or co-supervised, past and present.
nav: true
nav_order: 9
---

<style>
  /* Uses the site's own theme variables (see _sass/_themes.scss), so colors stay in sync with the rest of the site. */
  .students-grid { display: grid; gap: 1.25rem; grid-template-columns: repeat(auto-fill, minmax(min(100%, 24rem), 1fr)); margin-bottom: 2rem; }
  .student-card { display: flex; gap: 1rem; padding: 1.1rem; border-radius: 12px; background: var(--global-card-bg-color); border: 1px solid var(--global-divider-color); }
  .student-photo { position: relative; flex: 0 0 96px; width: 96px; height: 96px; border-radius: 50%; overflow: hidden; display: flex; align-items: center; justify-content: center; font-weight: 700; font-size: 1.6rem; color: var(--global-theme-color); background: var(--global-bg-color); border: 2px solid var(--global-theme-color); }
  .student-photo img { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; }
  .student-name { margin: 0; font-size: 1.1rem; font-weight: 700; color: var(--global-text-color); }
  .student-meta { margin: 0.15rem 0 0.5rem; font-size: 0.8rem; color: var(--global-theme-color); }
  .student-project { margin: 0 0 0.4rem; font-weight: 600; font-size: 0.95rem; color: var(--global-text-color); }
  .student-desc { margin: 0; font-size: 0.88rem; line-height: 1.5; color: var(--global-text-color-light); }
  @media (max-width: 520px) { .student-card { flex-direction: column; align-items: center; text-align: center; } }
</style>

{% for category in site.data.students.categories -%}
{%- if category.students.size > 0 %}

<h2 id="{{ category.id }}">{{ category.label }}</h2>
<div class="students-grid">
{%- for student in category.students %}
  <article class="student-card">
    <div class="student-photo" role="img" aria-label="Photo of {{ student.name | escape }}">
      <span>{{ student.initials }}</span>
      <img src="{{ '/assets/img/' | append: student.photo | relative_url }}" alt="{{ student.name | escape }}" loading="lazy" onerror="this.remove()">
    </div>
    <div>
      <h3 class="student-name">{{ student.name }}</h3>
      <p class="student-meta">{{ student.role }} · {{ student.status }}</p>
      <p class="student-project">{{ student.title }}</p>
      <p class="student-desc">{{ student.description }}</p>
    </div>
  </article>
{%- endfor %}
</div>
{%- endif -%}
{%- endfor %}
