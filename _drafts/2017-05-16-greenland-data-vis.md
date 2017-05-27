---
layout: post
title:  "Dashboard Design: The Tale of Two Greenlands"
thumbnail: /images/posts/thumbs/greenland.png
categories: dashboard-design, front-end-web, d3, javascript, animation
---
> **Team Size:** 3 people <br/>
**Time Period:** 3 weeks <br/>
**Role:** Front end developer <br/>
**Tools:** D3.js, Sketch, SVG <br/> <br/>
As a project for my Interaction Design Studio 2 class, we were asked to create a dashboard that displays biodiversity information to make it easier for policy makers to make decisions. For this project, we chose to create a webpage that uses a combination of svg generated from the vector program Sketch for the static graphs and D3.js for animated graphs.

<br />

---

<br />

## Dashboard Design

<div class="row">
  <div class="small-12 medium-4 post-inline-image-container">

    <img class="post-image-banner" src="https://c1.staticflickr.com/2/1546/24248097515_809e145452_b.jpg"/>

  </div>

  <div class="small-12 medium-8 columns">
    <p class="columns">A dashboard is a centralized location for information that an individual consults in order to make informed decisions. Let's put that into perspective. If you're like me who drives a manual, you might check if the rpm (revolutions per minute) of your engine is high enough to warrant a gear shift up. If you decelerate quickly and need to shift into a lower gear, you probably look at what speed you're at to make that decision. You get all of this information from your car dashboard.

    <br/><br/>

    For a dashboard to be effective, it must:
    </p>

    <ul>
      <li>— Provide all of the information a person needs</li>
      <li>— Make the information it's providing very easy to understand</li>
      <li>— Provide the right information at the right time</li>
    </ul>
  </div>
</div>

<br />

### The Greenland Dashboard

<div class="row">
  <div class="small-12 medium-4 post-inline-image-container">

    <br/>

    <div class="columns">
      <img class="post-image-banner" src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Greenland_%28orthographic_projection%29.svg/553px-Greenland_%28orthographic_projection%29.svg.png"/>
    </div>

    <br/>

    <p class="post-image-caption">By <a href="//commons.wikimedia.org/wiki/User:Connormah" title="User:Connormah">Connormah</a> - <span class="int-own-work" lang="en" xml:lang="en">Own work</span>, <a href="http://creativecommons.org/licenses/by-sa/3.0" title="Creative Commons Attribution-Share Alike 3.0">CC BY-SA 3.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=6921540">Link</a></p>

  </div>

  <div class="small-12 medium-8 columns">
    <p class="columns">For this specific project we needed to create a dashboard that will display climate change and biodiversity information for Greenland. This information will be used by policy makers to make informed decisions on policies that may directly or indirectly affect the environment.

    <br/>

    The challenges we had to face for this project were:
    </p>

    <ul>
      <li><p><b>Information Heirarchy and Organization</b></p></li>

      <ul>
        <li>— What kind of metrics makes sense for the given context?</li>
        <li>— How can we take advantage of position to attain effective progressive disclosure?</li>
      </ul>

      <li><p><b>Data visualization</b></p></li>

      <ul>
        <li>— How can we use sight, the human sense with the highest bandwidth, to make it easier to interpret the information?</li>
      </ul>

      <li><p><b>Animation</b></p></li>

      <ul>
        <li>— How can we show relationships between metrics through animation?</li>
        <li>— How can use animation to create a sense of urgency whenever a metric crosses a critical threshold?</li>
      </ul>
    </ul>
  </div>
</div>

<br/>

---

<br/>

## Exploration

> I did some initial sketches on paper for an idea of how we wanted our dashboard to look like. When we struggled a bit with how we would take the feedback we got to get to a direction we wanted to take, I created a mindmap of our best idea so far to get us all on the same page.

### Metrics That Make Sense

Before we can make a dashboard that displays information, we first need to figure out what specific pieces of information to display. Imagine seeing an indicator on your car dashboard that tells you how many peope are currently seated in your two seat sports car. I'd imagine that that's not very useful.

So for our domain we chose metrics that make sense for Greenland:

<ul>
  <li><p><b>Salmon Population</b></p></li>

  <ul>
    <li>– Salmon naturally migrates to Greenland and can be easily affected by human activity within Greenland</li>
  </ul>

  <li><p><b><a href="https://en.wikipedia.org/wiki/Firn">Firn</a> saturation</b></p></li>

  <ul>
    <li>– The amount of melted ice captured in the firn is a good thing to monitor because if it reaches a certain threshold that means that melted ice will start escaping to the ocean, possibly increasing sea water levels</li>
  </ul>

  <li><p><b>Ice Sheet Size</b></p></li>

  <ul>
    <li>– A good indicator of how much ice has melted over time is how the shore line of the ice sheet has changed through the years</li>
  </ul>

  <li><p><b><a href="https://en.wikipedia.org/wiki/Gross_domestic_product">GDP</a> vs <a href="https://en.wikipedia.org/wiki/Arable_land">Arable Land</a></b></p></li>

  <ul>
    <li>– When ice melts, more land gets exposed. This land can be ripe for agriculture which lends to an expansion of a market that might increse the GDP of the country</li>
  </ul>

  <li><p><b>Temperature</b></p></li>

  <ul>
    <li>– Almost anything from salmon to ice melting to human activity can be affected by temperature, so it's pretty important to have this on the dashboard</li>
  </ul>

  <li><p><b>Bear Encounters and Killings</b></p></li>

  <ul>
    <li>– </li>
  </ul>
</ul>

<br/>

### Greenland Customer Journey Map

<img class="post-image-large center materialboxed responsive-img" src="/images/posts/main/greenland/journey-map.jpg"/>

<br/>

Our first attempt at a "visualization of data" was quite literal. We took the data about salmon and made bar graphs out of fish icons, each black fish representing an arbitrary unit of salmon and the red fish representing a threshold. I can't even remember what the graph on the bottom of the ice sheet is but my best guess would be

### Tale of Two Greenlands

<br/>

---

## Implementation
<br/>
### Sketch
<br/>
### D3

{% include jquery.html %}
{% include materialize.html %}
