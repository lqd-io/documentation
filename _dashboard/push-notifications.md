---
collection: dashboard
platform: Dashboard
title: Push notifications
subtitle: Configuring Push notifications
version: Push-notifications
navbar:
  - title: Push notifications
    slug: push-notifications
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
