---
layout: page
excerpt_separator: <!--more-->
order: 1
redirect_from: "/2016/11/10/new-site-old-projects/"
---

I've been working on a 3D game engine for a while, written in [Rust](https://www.rust-lang.org){:target="_blank"} and primarily powered by [my scripting language](/projects/scripting-language). Here's some screenshots of a renderer I built for the project back when I was working in C++ (the scene is just a  bunch of rectangular prisms with some [Pixar textures](https://community.renderman.pixar.com/article/114/library-pixar-one-twenty-eight.html){:target="_blank"} on it, obviously with [better art](/projects/misc) it'd be a little more impressive):

<figure>
	<img src="/assets/too-bright.png" />
	<figcaption>I know what you’re thinking–waay too much bloom. IIRC I was testing out an adaptive exposure shader, and took this screenshot right after turning away from a dark area.</figcaption>
</figure>

<!--more-->

<figure>
	<img src="/assets/shadows-soft.png" />
	<figcaption>I was also super excited about <a href="http://developer.download.nvidia.com/shaderlibrary/docs/shadow_PCSS.pdf" target="_blank">percentage closer soft shadows</a>. You can’t tell in the picture, but I had the light set up to rotate around the scene which made watching the shadows stretch out and blur and such super fun.</figcaption>
</figure>

<figure>
	<img src="/assets/obligatory-overdone-sponza-ssao.png" />
	<figcaption>And of course, the obligatory <a href="http://www.crytek.com/cryengine/cryengine3/downloads" target="_blank">sponza</a> SSAO test. Unfortunately I can't find any screenshots of the full renders of this scene right now.</figcaption>
</figure>

Most engines are built to satisfy the needs of large teams of which not all members can expected to be technical--on the contrary, this engine is being built to suit the needs of small teams. Rather than hide an enormous amount of complexity behind a GUI functionality is provided to the user via direct APIs to the various engine subsystems.

This is a lower level way of approaching game dev, but not at the expense of your workflow: your scripts are all immediately recompiled and hot swapped in on save, giving you instant feedback both in game and in your editor of choice.

<figure>
	<img src="/assets/sublime-messages.png" />
	<figcaption>Cut me some slack on the verbose type names and the shader API here, these things will all be improved before there's a public release. :)</figcaption>
</figure>
