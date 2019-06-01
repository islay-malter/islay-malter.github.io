# Islay Malter's Blog

This is an attempt at setting up a site using GitHub Pages and Jekyll.

{% for post in site.posts %}

- [{{ post.title }}]({{ post.url }}) - {{ post.date | date_to_string }}

{% endfor %}

## Tasks

- ~~create repo~~
- ~~enable GitHub pages~~
- ~~set theme~~
- ~~clone locally~~
- ~~install Ruby + bundler + github-pages + Jekyll + zlib + ...~~
- ~~run Jekyll locally~~
- ~~modify config file for custom attributes~~
- ~~create first blog post~~
- ~~create home page with all blogs linked~~

- custom 404 page
- favicon
- custom domain + HTTPS
- `_includes` folder for layouts e.g. _page_ and _posts_
- Google Analytics
- DISQUS commenting
- find security issues