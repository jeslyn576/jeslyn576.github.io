---
#
# Here you can change the text shown in the Home page before the Latest Posts section.
#
# Edit jekyll-theme-simple-blog's home layout in _layouts instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
#
layout: home
permalink: /index.html
header:
  image: /assets/img/yyy.jpg
tagline: 梦不会逃走，逃走的一直是自己
excerpt: 梦不会逃走，逃走的一直是自己
# repository:
#   is_project_page: true
#   show_downloads: true
#   repository_url: https://gitlab.com/lorepirri/jekyll-theme-simple-blog
#   zip_url: https://gitlab.com/lorepirri/jekyll-theme-simple-blog/repository/master/archive.zip
#   tar_url: https://gitlab.com/lorepirri/jekyll-theme-simple-blog/repository/master/archive.tar.gz
ref: home
lang: en
---

![要坚强](/assets/img/dd.jpg)

**Einstein argued that there must be simplified explanations of nature**, 

**because God is not capricious or arbitrary**, 

**No such faith comforts the software engineer**.

  ——***Fred Brooks***

<h1>Latest Articles</h1>
<div>&nbsp;</div>
{% include list-category-posts.html lang=page.lang category="articles" max_posts=3 max_post_tags=3 %}
