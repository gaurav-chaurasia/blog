---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<div class="featured-blogs">
  <h1>📌 Featured Blogs</h1>
  <div class="cards-container mt-6">
    {% for path in site.featured_posts %}
      {% assign post = site.pages | where: "permalink", path | first %}
      {% if post %}
        <div class="blog-card">
          <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          <p class="date">{{ post.date | date: "%B %d, %Y" }}</p>
          <p class="description">{{ post.description }}</p>
          <a class="read-more" href="{{ post.url | relative_url }}">Read More →</a>
        </div>
      {% endif %}
    {% endfor %}
  </div>
</div>


---

> # *It's just me talking to myself about myself and some other techy stuff you know!!!! 😅💻*

{: .no_toc }

<br>

<div class="container">
  <div class="row">
    <div class="col-xs-12 col-sm-12 col-md-8">
      <div class="text-center">
          <a href="/"> 
            <button id="home" class="btn">
              Back to home
            </button>
          </a>
        </div>
    </div>
  </div>
</div>
