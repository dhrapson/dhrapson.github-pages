# dhrapson.com blog

This repo contains the source for [dhrapson.com], a jekyll-based blog that is published on Github Pages.

## Building

Github Pages does offer building of Jekyll websites, however it only permits a very limited set of gems.
Due to the fact that I had moved the website over from Wordpress & had a number of links in place with Google based on category e.g. [dhrapson/category/cloud], I used the `_tag_gen.rb` plugin to generate category pages.

This means the site has to be built locally using `jekyll serve`, and the contents of the `_site` directory should be checked into git as the `docs/` folder. The github project is configured to look in docs for the site content.

## Technology

This jekyll repo uses Jekyll and has a style based on Jekyll Now.

**Jekyll** is a static site generator that's perfect for GitHub hosted blogs ([Jekyll Repository](https://github.com/jekyll/jekyll))

**Jekyll Now** makes it easier to create your Jekyll blog, by eliminating a lot of the up front setup.
