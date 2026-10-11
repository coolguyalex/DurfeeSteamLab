---
title: "Resources"
---

<!--
FRONT MATTER: the block between the two --- lines above. It is settings for this page, not page text.
  title:  the page title (the heading, the browser tab, and links that point to it)

THE RESOURCES LANDING PAGE. It is a section page (_index.md), so Hugo uses
layouts/_default/list.html. Each tool lives in its own folder under content/resources/:
  circuits/  music/  arduino/  sound/  data-science/  design/
Each folder has an _index.md (the landing page for that tool). Some also have a lab-guide.md,
which is the lab's own step-by-step material, kept on one page.
To add a new tool: make a folder with an _index.md, then add a card for it below.
The web address of a page is its path inside content/, so
content/resources/circuits/_index.md is served at /resources/circuits/.
-->

Guides to the tools and ideas behind lab projects. Each page gives a suggested order, mixing the best outside material with the lab's own guides. Use what's useful.

## Foundations

<div class="cards">
<a class="card link" href="/resources/circuits/">
<h3>Circuits</h3>
<p>Voltage, current, switches and what +, − and GND mean. Start here before Arduino or VCV Rack.</p>
</a>
<a class="card link" href="/resources/music/">
<h3>Music &amp; Sound Basics</h3>
<p>Pitch and frequency, rhythm, the harmonic series, timbre, scales and what "in key" means.</p>
</a>
</div>

## Tools

<div class="cards">
<a class="card link" href="/resources/arduino/">
<h3>Arduino</h3>
<p>Programming boards that read sensors and drive lights, motors and sound.</p>
</a>
<a class="card link" href="/resources/sound/">
<h3>Sound Tools</h3>
<p>VCV Rack, Strudel, SuperCollider and Pure Data: what each is for, and where to start.</p>
</a>
<a class="card link" href="/resources/data-science/">
<h3>Data Science</h3>
<p>Python in a notebook: load, clean, chart and listen to data.</p>
</a>
<a class="card link" href="/resources/design/">
<h3>Design</h3>
<p>3D modelling in Onshape for parts, enclosures and mounts that can be printed.</p>
</a>
</div>

## Also

- [Software at a glance](/resources/software/): every tool in one table, with cost, account and whether it runs in the browser.
- [Arduino cheat sheet](/resources/arduino/lab-guide/#reference): code, parts at a glance, and what to check when nothing works.
- [Science Fair &amp; Deadlines](/fair/)
- [Schedule &amp; Info](/schedule/)
