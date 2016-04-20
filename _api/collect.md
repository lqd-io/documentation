---
collection: api
platform: API
title: Data Collection API
subtitle: Using Liquid API
version: Collect
navbar:
  - title: Data Collection API
    slug: data-collection-api
    subcategories:
      - title: POST /data_points
        slug: post-data-points
      - title: POST /aliases
        slug: post-aliases
  - title: Structure of a data point
    slug: structure-of-a-data-point
    subcategories:
      - title: Entities
        slug: entities
      - title: Examples
        slug: examples
      - title: Good practices
        slug: good-practices
---

{% for article in page.navbar %}
  {% assign loop = forloop.index %}
  <article class='documentation-article'>
    <header>
      <h2 id='{{ article.slug }}'>{{ article.title }} <a href="https://github.com/lqd-io/documentation/edit/gh-pages/_{{ page.collection }}/{{ page.version | downcase }}/{{ article.slug }}.html" target="new" class="btn btn-xs btn-default btn-edit"><span class="fa fa-pencil"></span> Edit</a></h2>
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
          <h3 id='{{ section.slug }}'>{{ section.title }} <a href="https://github.com/lqd-io/documentation/edit/gh-pages/_{{ page.collection }}/{{ page.version | downcase }}/sections/{{ loop }}-{{ forloop.index }}-{{ section.slug }}.md" target="new" class="btn btn-xs btn-default btn-edit"><span class="fa fa-pencil"></span> Edit</a></h3>
        </header>
        {{ contents | markdownify }}
      </section>
    {% endfor %}
  </article>
{% endfor %}
