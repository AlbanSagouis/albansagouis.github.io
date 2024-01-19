---
# permalink: /about/
title: "About me"
image: /assets/images/portrait_with_scarf.jpeg
order: 1
author_profile: true
layout: single
classes: wide
header:
    excerpt: "This piece of text could be shown on top of the overlay_image, just under the title"
    show_overlay_excerpt: false
    overlay_image: assets/images/landscape_cundinamarca.jpg
    overlay_filter: 0.1
related: true
---

My name is Alban Sagouis and this is my personal professional website.

There is a dynamic CV that aggregates my blog posts described as professional _experiences_ and also blog posts about photography or other topics.

<!-- {% include module_left.html image_path="assets/images/portrait_with_scarf.jpeg" width="280px" title="Title" description="longer text" %} -->

### Current job

I currently work at iDiv, the German Biodiversity Synthesis Center, as a Scientific programmer. In [Jon Chase's group][chaselab]:

1. I extract, aggregate, restructure, check and standardise data from the literature
2. I assist colleagues with R problems
3. I implement and encourage scientific software reproducibility practices, notably containerisation and automatic testing
4. I frequently talk about how indispensable is the [`renv`][renv] package
5. I use all of the above to build and grow research compendia extracting, restructuring, standardising and checking data in a documented and reproducible environment, publishing and archiving code and data.
6. I write monthly newsletters to my colleagues which you can find [here][link_to_tech_news]
7. I occasionally build a package of functions used for a specific project such as the [`sRealmTools`][gh_srealmtools] package or [`BioTIMEr`][gh_biotimer]
8. I co-maintain [`mobsim`][gh_mobsim], a community simulation R package that we use for work, for [teaching][gh_biodiv_patterns] and publish on [CRAN][cran_mobsim]

### Other activities
With [rOpenSci][ropensciorg], I maintain or co-maintain [`parzer`][ro_parzer] and [`rgnparser`][ro_rgnparser].

### Building this website
I used the template Minimal Mistake by Michael Rose and develop and build locally in Visual Studio Code. I wrote about this process in [a blog post][website_building_1]. And clearly, it is still under construction...

<!-- [CV]:                 {% link _pages/cv.md %} -->
[chaselab]:           https://www.idiv.de/en/groups-and-people/core-groups/synthesis.html
[gh_srealmtools]:     https://github.com/sRealmWG/sRealmTools
[gh_biotimer]:        https://github.com/bioTIMEHub/BioTIMEr
[link_to_tech_news]:  {% post_url /tech-news/2023-07-21-tech-news-1 %}
[renv]:               https://rstudio.github.io/renv/index.html
[website_building_1]: {% post_url 2024-01-10-website-building-1 %}
[ropensciorg]:        https://ropensci.org
[gh_mobsim]:          https://github.com/MoBiodiv/mobsim
[gh_biodiv_patterns]: https://github.com/chase-lab/biodiv-patterns-course-2024/tree/main/week%202/3%20-%20Wednesday
[cran_mobsim]:        https://cran.r-project.org/package=mobsim
[ro_parzer]:          https://docs.ropensci.org/parzer/
[ro_rgnparser]:       https://docs.ropensci.org/rgnparser/