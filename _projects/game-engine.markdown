---
layout: page
excerpt_separator: <!--more-->
order: 2
redirect_from: "/2016/11/10/new-site-old-projects/"
---

I've been working on a game engine for a while, written in [Rust](https://www.rust-lang.org){:target="_blank"} and primarily powered by [my scripting language](/projects/scripting-language). It's also the technology behind [_Way of Rhea_](/projects/way-of-rhea). Here's some screenshots of a renderer I built for the project back when I was working in C++ (the scene is just a  bunch of rectangular prisms with some [Pixar textures](https://community.renderman.pixar.com/article/114/library-pixar-one-twenty-eight.html){:target="_blank"} on it, obviously with [better art](/projects/misc) it'd be a little more impressive):

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

The engine [hot swaps in scripts and assets on save (early video)](https://twitter.com/AnthropicSt/status/1005490426692980739), and also provides feedback that can be displayed inline in external text editors:

<figure>
	<img src="/assets/sublime-messages.png" />
</figure>

Here's a screenshot of [_Way of Rhea_](/projects/way-of-rhea) which is being built in the engine:
<a href="/projects/monsters-and-sprites">
	<figure>
		<img src="/assets/monsters-and-sprites-screenshot.jpg" />
	</figure>
</a>