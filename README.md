# Music Visualizer

Coursework of [COMP 5411 Advanced Computer Graphics](https://home.cse.ust.hk/~psander/hkust_only/comp5411/) at [HKUST](https://hkust.edu.hk/)

[![Music Visualizer](/preview.png)](https://tomnotch.top/Music-Visualizer)

It's also available [here](https://tomnotch.top/Music-Visualizer).
Feel free to play around with different controls/parameters, it won't break. 😉

## About

This is a rendering course project for [COMP 5411 Advanced Computer Graphics](https://home.cse.ust.hk/~psander/hkust_only/comp5411/) (PG level) at [HKUST](https://hkust.edu.hk/) done with Junkai (Abraham) Huang, and is written in Javascript using [WebGL](https://get.webgl.org/) and [Three.js](https://threejs.org/), where you can find so many cool projects unfolding in your browser.
There is no requirement on what this project must achieve, it just has to involve computer graphics and rendering.

## Working Principle

Before I talk about this, remember, many technologies lose some of their value once explained, which is also why tech patent holders are unwilling to unveil the specifications.
Potential buyers would say, "Oh I know how this works, it's so simple that you don't deserve the money." Yes, it might be simple, but it wasn't you who first came up with the idea.

To visualize music, let's first understand what is visualization.
[This](https://en.wikipedia.org/wiki/Visualization) is Wikipedia's explanation, I bet you've never googled it before.
Visualization in our context is often used to convey information that couldn't be perceived only by eyes.
e.g. we couldn't see UV/IR lights, so we map certain spectrums to visible light.
This goes the same for music visualization, for deaf people who couldn't hear music, we map sound to visual forms.
Thus, finding such a mapping function is the key to most music and more generally, sound visualizers.

The way we map music to visual forms is very simple.
We first find the [Fourier Spectrum](https://en.wikipedia.org/wiki/Fourier_transform) of a piece of music using Web API. Note that theoretically and ideally this is a one-to-one mapping from sound to numbers, but could be lossless or lossy in reality depending on the implementation.
We then map a wide band of the Fourier Spectrum to some visual forms. This part is purely out of imagination.

The way we perform it is by mesh deformation. We first assign and register a group of mesh vertices to a narrow band of the wide band.
The grouping method is according to the *Motion mode* in the control, so it could be slices or tiles on the mesh.
Then, we deform each group of vertices according to the power amplitude of their assigned narrow band. The direction of deformation is outwards from the mesh center.
That's it, it's that simple.

We didn't write any vertex/pixel shader, but the result is equally appealing. 😁
