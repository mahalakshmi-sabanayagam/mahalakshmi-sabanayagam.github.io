---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<div class="publications-page">

  <p class="pub-note"><sup>*</sup> Equal contribution</p>

  {% assign grouped_publications = site.data.publications.publications | group_by: "year" %}

  {% for group in grouped_publications %}
    <section class="pub-year-section">

      <h2 class="pub-year">{{ group.name }}</h2>

      <div class="pub-list">
        {% for pub in group.items %}

          <article class="publication-card">

            <h3 class="pub-title">
              {{ pub.title }}
            </h3>

            <div class="pub-authors">
              {{ pub.authors }}
            </div>

            <div class="pub-details">

              {% for venue in pub.venues %}
                <div class="pub-meta-row">

                  <span
                    class="pub-venue"
                    {% if venue.full %}
                    title="{{ venue.full }}"
                    {% endif %}
                  >
                    {{ venue.label }}
                  </span>

                  {% if venue.highlights %}
                    {% for highlight in venue.highlights %}
                      <span class="pub-highlight pub-highlight--{{ highlight.type }}">
                        {% if highlight.type == "spotlight" or highlight.type == "award" %}
                          <i class="fas fa-star" aria-hidden="true"></i>
                        {% endif %}
                        {{ highlight.label }}
                      </span>
                    {% endfor %}
                  {% endif %}

                  {% if forloop.first and pub.links %}
                    <span class="pub-links">
                      {% for link in pub.links %}
                        <a
                          class="pub-action"
                          href="{{ link.url }}"
                          target="_blank"
                          rel="noopener noreferrer"
                        >
                          {% if link.icon %}
                            <i class="{{ link.icon }}" aria-hidden="true"></i>
                          {% endif %}
                          {{ link.label }}
                        </a>
                      {% endfor %}
                    </span>
                  {% endif %}

                </div>
              {% endfor %}

            </div>

          </article>

        {% endfor %}
      </div>

    </section>
  {% endfor %}


  <section class="pub-preprints">

    <h2 class="pub-section-title">Preprints</h2>

    <div class="pub-list">
      {% for pub in site.data.publications.preprints %}

        <article class="publication-card publication-card--preprint">

          <h3 class="pub-title">
            {{ pub.title }}
          </h3>

          <div class="pub-authors">
            {{ pub.authors }}
          </div>

          <div class="pub-meta-row">

            <span class="pub-venue pub-venue--preprint">
              Preprint
            </span>

            {% if pub.links %}
              <span class="pub-links">
                {% for link in pub.links %}
                  <a
                    class="pub-action"
                    href="{{ link.url }}"
                    target="_blank"
                    rel="noopener noreferrer"
                  >
                    {% if link.icon %}
                      <i class="{{ link.icon }}" aria-hidden="true"></i>
                    {% endif %}
                    {{ link.label }}
                  </a>
                {% endfor %}
              </span>
            {% endif %}

          </div>

        </article>

      {% endfor %}
    </div>

  </section>

</div>