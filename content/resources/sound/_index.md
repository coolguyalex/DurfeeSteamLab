---
title: "Sound Tools"
---

<!--
FRONT MATTER: the block between the two --- lines above. It is settings for this page, not page text.
  title:  the page title (the heading, the browser tab, and links that point to it)

THE SOUND TOOLS LANDING PAGE. Unlike the other tools this page covers four tools (VCV Rack,
Strudel, SuperCollider, Pure Data), because students are meant to try several.

Headings like  ## VCV Rack {#vcv-rack}  carry a fixed address in the {#...} part. That is what
lets other pages link straight to the section with /resources/sound/#vcv-rack.
If you rename a heading, keep its {#...} part the same so existing links keep working.
-->

Several tools are worth trying here, and each teaches something different. Start with the one that fits what you want to make.

New to sound? Do [Music & Sound Basics](/resources/music/) alongside this page. Patching in VCV Rack is easier if you have done [Circuits](/resources/circuits/).

## Suggested progression

1. **Understand synthesis.** [VCV Rack](#vcv-rack) shows how a sound is built from separate modules, and Ableton's [Learning Synths](https://learningsynths.ableton.com) lets you play with a synth in the browser while you learn its parts.
2. **Make music with code, in the browser.** [Strudel](#strudel) runs in the browser, so it should work on school computers.
3. **Go deeper with code.** [SuperCollider](#supercollider) is the main code route, with a steeper start and a high ceiling.
4. **Fallback and visual patching.** [Pure Data](#pure-data) is the fallback if SuperCollider proves too hard, and the lab has its own guide for it.

| Tool | Good for | Runs | In the lab |
| --- | --- | --- | --- |
| VCV Rack | Learning how synthesis works | Desktop app | Not installed yet |
| Strudel | Live coding patterns and beats | Browser | <span class="todo">[test on a school computer]</span> |
| SuperCollider | Generative music, data sonification, precise control | Desktop app | Not installed yet |
| Pure Data | Building instruments and effects from boxes and wires | Desktop app | Lab guide written |

## VCV Rack {#vcv-rack}

A free virtual modular synthesizer. Modules are placed in a rack and patched together with virtual cables, as on a hardware Eurorack system. It is the quickest way to see what each part of a synth does. Download from [vcvrack.com](https://vcvrack.com). The free version is all the lab needs.

- *Video* · [Your first minutes in VCV Rack 2](https://www.youtube.com/watch?v=c-27PRPxwTg) - Omri Cohen. A short tour and a first patch. Start here.
- *Video* · [New to modular? Watch this first](https://www.youtube.com/playlist?list=PLiECaNQx239s0Z1WmH5jQAcEZf3mLLHnX) - Omri Cohen. A playlist on the core ideas of modular synthesis.
- *Video* · [Let's Learn Eurorack (ft. VCV Rack)](https://www.youtube.com/watch?v=BTcP3DofZLY) - Red Means Recording. A multi-part series; the first video is linked.
- *Video* · [From Zero to Synth](https://www.youtube.com/watch?v=FhjkkYn9OLk) - Sonic Academy. Builds a sound from nothing.
- *Read* · [VCV Rack manual](https://vcvrack.com/manual/), starting with [Getting Started](https://vcvrack.com/manual/GettingStarted), and the community's [getting-started list](https://community.vcvrack.com/t/getting-started-with-vcv-rack-video-tutorials/11204).

## Strudel {#strudel}

A live-coding environment that runs in the browser: type short patterns and hear music immediately. It is the official JavaScript port of TidalCycles, and no JavaScript or TidalCycles experience is needed. Open it at [strudel.cc](https://strudel.cc).

- *Interactive* · [Strudel workshop: first sounds](https://strudel.cc/workshop/first-sounds/) - the official lessons, with a playable editor in each page. Start here.
- *Read* · [Getting started](https://strudel.cc/workshop/getting-started/) and the [showcase](https://strudel.cc/intro/showcase/) - the official introduction, and examples of what people make.

## SuperCollider {#supercollider}

A free, open-source platform for audio synthesis and algorithmic composition. Sound is described in code. Download from [supercollider.github.io](https://supercollider.github.io/). The installers are hosted on GitHub, which school devices block. <span class="todo">[work out an install route: IT, or a USB stick]</span>

- *Read* · [Getting Started with SuperCollider](https://docs.supercollider.online/Tutorials/Getting-Started/01-Introductory-Remarks.html) - the official tutorial. Start here.
- *Video* · [Eli Fieldsteel's tutorials](https://www.youtube.com/@elifieldsteel/playlists) - the standard video series; choose the SuperCollider playlist.
- *Book* · [SuperCollider for the Creative Musician](https://academic.oup.com/book/55790) - Eli Fieldsteel. Paid, and the most complete route in.
- *Reference* · [Documentation](https://docs.supercollider.online), [sccode.org](https://sccode.org/) (shared patches) and the [forum](https://scsynth.org).

## Pure Data {#pure-data}

A free visual programming environment for sound: instruments and effects built from boxes and wires, with no typed code. Download from [puredata.info](https://puredata.info). <span class="todo">[a browser version is still to be chosen and tested; add its link here]</span>

- *Lab guide* · [Pure Data Lab Guide](/resources/sound/pure-data-guide/) - PD1 to PD5: a steady tone, pitch and volume, waveforms, filters, then delay and melodies from data. Draft; not yet tested.
- *Read* · [Pd Tutorial: Programming Electronic Music in Pd](http://www.pd-tutorial.com) - Johannes Kreidler's free online book.
- *Read* · [Theory and Techniques of Electronic Music](https://msp.ucsd.edu/techniques.htm) - Miller Puckette's free book, by the author of Pd. Best once you want to know why things work.
- Pd's built-in help: right-click any object and choose Help to open a working example.

## Connections to other tools

Any of these can be driven by data from [Arduino](/resources/arduino/) and [Data Science](/resources/data-science/), and that is how a sensor log becomes a piece of music.
