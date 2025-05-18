---js
const eleventyNavigation = {
	key: "Home",
	order: 1
};

const numberOfLatestPostsToShow = 3;
---
# Intro

Hi! I'm Alex, a recent CompSci graduate. Currently I'm looking for work in data science or [cyber]security, hoping to leverage my knowledge in machine/deep learning.

This is a blog-style portfolio built with 11ty containing all of the things I'd want to share with any interested parties. Check out any of the <a href="/Tags">tags</a>! You'll find my projects for school and personal reasons, as well as some hobby things, especially photography. 

If you are a recruiter, a copy of my resume is available <a href="/Resume_ASukennyk.pdf">here</a>, and the projects I'm happiest to share are below:

* <a href="\ASUKENNYK_FINAL.pdf" target="_blank">GAN Grayscale Image Recoloring</a>
    * Recoloring grayscale bird images using small data size.
* <a href="\TCP.pdf" target="_blank">TCP Improvement</a>
    * Experiments and Survey of improving TCP bandwidth grabbing with various methods.
<!-- * <a href="">Pixel-mod Multitool</a>
    * Ongoing project creating interesting image manipulation tools. -->


{% set postsCount = collections.posts | length %}
{% set latestPostsCount = postsCount | min(numberOfLatestPostsToShow) %}
<h1>Latest {{ latestPostsCount }} Post{% if latestPostsCount != 1 %}s{% endif %}</h1>

{% set postslist = collections.posts | head(-1 * numberOfLatestPostsToShow) %}
{% set postslistCounter = postsCount %}
{% include "postslist.njk" %}

{% set morePosts = postsCount - numberOfLatestPostsToShow %}
{% if morePosts > 0 %}
<p>{{ morePosts }} more post{% if morePosts != 1 %}s{% endif %} can be found in <a href="blog.njk">the archive</a>.</p>
{% endif %}

<!-- List every content page in the project -->

<!-- <ul>
	{%- for entry in collections.all %}
	<li><a href="{{ entry.url }}"><code>{{ entry.url }}</code></a></li>
	{%- endfor %}
</ul> -->


