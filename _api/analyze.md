---
collection: api
platform: API
title: Data Analysis API
subtitle: Using Liquid API
version: Analyze
navbar:
  - title: Data Analysis API
    slug: data-analysis-api
    subcategories:
      - title: GET /users/:id
        slug: get-users
---

{% for article in page.navbar %}
  {% assign loop = forloop.index %}
  <article class='documentation-article'>
    <header>
      <h2 id='{{ article.slug }}'>{{ article.title }}</h2>
      {% capture article_header %}{{ page.version | downcase }}/{{ article.slug }}.html{% endcapture %}
      {% include_relative {{ article_header }} %}
    </header>
    {% for section in article.subcategories %}
      {% capture contents %}
        {% capture article_body %}{{ page.version | downcase }}/sections/{{ loop }}-{{ forloop.index }}-{{ section.slug }}.md{% endcapture %}
        {% include_relative {{ article_body }} %}
      {% endcapture %}
      <section>
        <header>
          <h3 id='{{ section.slug }}'>{{ section.title }}</h3>
        </header>
        {{ contents | markdownify }}
      </section>
    {% endfor %}
  </article>
{% endfor %}
