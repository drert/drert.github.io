---js
const eleventyNavigation = {
	key: "Home",
	order: 1
};


const numberOfLatestPostsToShow = 3;

---

# Intro

Hi! I'm Alex, a recent CompSci graduate. Currently I'm looking for work in data science or [cyber]security, hoping to leverage my knowledge in machine/deep learning.

This is a (very informal) blog-style portfolio built with 11ty containing all of the things I'd want to share with any interested parties. Check out any of the <a href="/tags">tags</a>! You'll find my projects for school and personal reasons, as well as some hobby things, especially photography. 

If you are a recruiter, a copy of my resume is available <a href="/Resume_ASukennyk.pdf">here</a>, and the projects I'm happiest to share are below:

* <a href="\blog\recall\Bird-DCGAN\RecolorGAN" >GAN Grayscale Image Recoloring</a>
    * Recoloring grayscale bird images using small data sizes.
* <a href="\blog\recall\TCP-Study\TCP" target="_blank">TCP Improvement</a>
    * Experiments and Survey of improving TCP bandwidth grabbing with various methods.
<!-- * <a href="">Pixel-mod Multitool</a>
    * Ongoing project creating interesting image manipulation tools. -->


<br>



<div style="width:100% display:table;" >
<div style="display:table-row"> <!-- outer div -->

<div id="pincol">

# Pinned Posts
    
    {% set pinCount = collections["Pinned"] | length %}
    {% set pinPosts = collections["Pinned"] | head(pinCount) %}

    <ol reversed class="postlist" style="--postlist-index: {{ (pinCount or postslist.length) + 1 }}">
    {% for post in pinPosts %}
        <li class="postlist-item{% if post.url == url %} postlist-item-active{% endif %}"> 
            <a href="{{ post.url }}" class="postlist-link">{% if post.data.title %}{{ post.data.title }}{% else %}<code>{{ post.url }}</code>{% endif %}</a>
            <time class="postlist-date" datetime="{{ post.date | htmlDateString }}">{{ post.date | readableDate("LLLL yyyy") }}</time>
        </li>
    {% endfor %}
    </ol>

</div>


<div id="latcol">

    {% set postsCount = collections.posts | length %}
    {% set latestPostsCount = postsCount | min(numberOfLatestPostsToShow) %}
# Latest {{ latestPostsCount }} Post{% if latestPostsCount != 1 %}s{% endif %}

    {% set postslist = collections.posts | head(-1 * numberOfLatestPostsToShow) %}
    {% set postslistCounter = postsCount %}
    {% include "postslist.njk" %}

    {% set morePosts = postsCount - numberOfLatestPostsToShow %}
    {% if morePosts > 0 %}
    <p>{{ morePosts }} more post{% if morePosts != 1 %}s{% endif %} can be found in <a href="blog.njk">the archive</a>.</p>
    {% endif %}
</div>



</div> 
</div> 









<!-- List every content page in the project -->

<!-- <br><br>
<ul>
	{%- for entry in collections.all %}
	<li><a href="{{ entry.url }}"><code>{{ entry.url }}</code></a></li>
	{%- endfor %}
</ul> -->


