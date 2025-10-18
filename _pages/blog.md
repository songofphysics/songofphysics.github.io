---
layout: default
permalink: /blog/
title: Blog
nav: true
nav_order: 2
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1 # The number of links before the current page
    after: 3 # The number of links after the current page
---

<div class="post">

{% assign blog_name_size = site.blog_name | size %}
{% assign blog_description_size = site.blog_description | size %}

{% if blog_name_size > 0 or blog_description_size > 0 %}

  <div class="header-bar">
    <h1>{{ site.blog_name }}</h1>
    <h2>{{ site.blog_description }}</h2>
  </div>
  {% endif %}

{% if site.display_tags and site.display_tags.size > 0 %}

<div class="tag-category-list">
  <ul class="p-0 m-0">
    {% for tag in site.display_tags %}
      <li>
        <i class="fa-solid fa-hashtag fa-sm"></i>
        <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">{{ tag }}</a>
      </li>
      {% unless forloop.last %}
        <p>&bull;</p>
      {% endunless %}
    {% endfor %}
  </ul>
</div>
{% endif %}

{% comment %}
Refactored posts listing template

- Uses `default: []` guards to avoid nil errors
- Uses `where_exp` to accept boolean or string `featured: true` front-matter
- Centralized read-time calculation using a capture block (DRY)
- Safer pagination guard
- Consistent separators and accessibility/security improvements for external links
- Friendly fallback message when no posts are available
  {% endcomment %}

{%- assign posts = site.posts | default: [] -%}
{%- assign sep = "&nbsp; &middot; &nbsp;" -%}

{%- comment -%}
Featured posts

- Accepts front-matter `featured: true` (boolean) or `featured: "true"` (string)
  {%- endcomment -%}
  {%- assign featured_posts = posts | where_exp: "p", "p.featured == true or p.featured == 'true'" -%}
  {%- if featured_posts.size > 0 -%}
  <br>
    <div class="container featured-posts">
      {%- assign is_even = featured_posts.size | modulo: 2 -%}
      <div class="row row-cols-{% if featured_posts.size <= 2 or is_even == 0 %}2{% else %}3{% endif %}">

      {%- for post in featured_posts -%}
        <div class="col mb-4">
          <a href="{{ post.url | relative_url }}">
            <div class="card hoverable">
              <div class="row g-0">
                <div class="col-md-12">
                  <div class="card-body">

                    <div class="float-right" aria-hidden="true">
                      <i class="fa-solid fa-thumbtack fa-xs"></i>
                    </div>

                    <h3 class="card-title text-lowercase">{{ post.title }}</h3>
                    <p class="card-text">{{ post.description }}</p>

                    {%- comment -%}
                    Centralized read-time: capture a source string then compute words/min
                    {%- endcomment -%}
                    {%- capture rt_source -%}
                      {%- if post.external_source == blank -%}
                        {{ post.content }}
                      {%- else -%}
                        {{ post.feed_content | strip_html }}
                      {%- endif -%}
                    {%- endcapture -%}
                    {%- assign read_time = rt_source | number_of_words | divided_by: 180 | plus: 1 -%}

                    {%- assign year = post.date | date: "%Y" -%}

                    <p class="post-meta">
                      {{ read_time }} min read {{ sep }}
                      <a href="{{ year | prepend: '/blog/' | relative_url }}">
                        <i class="fa-solid fa-calendar fa-sm" aria-hidden="true"></i> <span class="visually-hidden">Archive for</span> {{ year }}</a>
                    </p>

                  </div>
                </div>
              </div>
            </div>
          </a>
        </div>
      {%- endfor -%}

      </div>

    </div>
    <hr>
  {%- endif -%}

{%- comment -%}
Main post list — pagination-aware and safe when empty
{%- endcomment -%}

<ul class="post-list">

{%- if page.pagination and page.pagination.enabled -%}
{%- assign postlist = paginator.posts | default: [] -%}
{%- else -%}
{%- assign postlist = posts -%}
{%- endif -%}

{%- if postlist.size == 0 -%}

<li class="no-posts">
<div class="empty-state">
<h3>No posts yet</h3>
<p>There are no posts published on this site yet. Check back soon — or <a href="/about/">learn more</a> about this project.</p>
</div>
</li>
{%- else -%}

    {%- for post in postlist -%}
      {%- comment -%} compute read-time once per post using capture {%- endcomment -%}
      {%- capture rt_source -%}
        {%- if post.external_source == blank -%}
          {{ post.content }}
        {%- else -%}
          {{ post.feed_content | strip_html }}
        {%- endif -%}
      {%- endcapture -%}
      {%- assign read_time = rt_source | number_of_words | divided_by: 180 | plus: 1 -%}

      {%- assign year = post.date | date: "%Y" -%}
      {%- assign tags = post.tags | default: [] -%}
      {%- assign categories = post.categories | default: [] -%}

      <li>

        {%- if post.thumbnail -%}
          <div class="row">
            <div class="col-sm-9">
        {%- endif -%}

        <h3>
          {%- if post.redirect == blank -%}
            <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
          {%- elsif post.redirect contains '://' -%}
            <a class="post-title" href="{{ post.redirect }}" target="_blank" rel="noopener noreferrer">{{ post.title }}</a>
            <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
              <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
            </svg>
          {%- else -%}
            <a class="post-title" href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
          {%- endif -%}
        </h3>

        <p>{{ post.description }}</p>

        <p class="post-meta">
          {{ read_time }} min read {{ sep }}
          {{ post.date | date: '%B %d, %Y' }}
          {%- if post.external_source -%}
            {{ sep }} {{ post.external_source }}
          {%- endif -%}
        </p>

        <p class="post-tags">
          <a href="{{ year | prepend: '/blog/' | relative_url }}">
            <i class="fa-solid fa-calendar fa-sm" aria-hidden="true"></i> <span class="visually-hidden">Archive for</span> {{ year }}</a>

          {%- if tags.size > 0 -%}
            {{ sep }}
            {%- for tag in tags -%}
              <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">
                <i class="fa-solid fa-hashtag fa-sm" aria-hidden="true"></i> <span class="visually-hidden">Tag</span> {{ tag }}</a>
              {%- unless forloop.last -%}
                &nbsp;
              {%- endunless -%}
            {%- endfor -%}
          {%- endif -%}

          {%- if categories.size > 0 -%}
            {{ sep }}
            {%- for category in categories -%}
              <a href="{{ category | slugify | prepend: '/blog/category/' | relative_url }}">
                <i class="fa-solid fa-tag fa-sm" aria-hidden="true"></i> <span class="visually-hidden">Category</span> {{ category }}</a>
              {%- unless forloop.last -%}
                &nbsp;
              {%- endunless -%}
            {%- endfor -%}
          {%- endif -%}
        </p>

        {%- if post.thumbnail -%}
            </div>

            <div class="col-sm-3">
              <img class="card-img" src="{{ post.thumbnail | relative_url }}" style="object-fit: cover; height: 90%" alt="{{ post.title | escape }} thumbnail">
            </div>
          </div>
        {%- endif -%}

      </li>

    {%- endfor -%}

{%- endif -%}

</ul>

{%- if page.pagination and page.pagination.enabled -%}
{% include pagination.liquid %}
{%- endif -%}

{%- comment -%}
End of template

- If you'd like, I can also split the read-time logic into an `_includes/read_time.liquid` to make this file shorter.
  {%- endcomment -%}
