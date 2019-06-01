# Personal Page for Islay Malter

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