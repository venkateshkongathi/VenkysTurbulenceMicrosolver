# VenkysTurbulenceMicrosolver
Houdini Pyro gas microsolver for organic turbulence details.
Compiled for Houdini 20.5.654

Place the .dll file in in C:\Users\USER\Documents\houdini20.5\dso\

add below text in C:\Users\USER\Documents\houdini20.5\houdini.env

HOUDINI_DSO_PATH = "C:/Users/USER/Documents/houdini20.5/dso;&"




https://youtu.be/73SDbIuSbzU


Working with Houdini’s Pyro Solver—or smoke solvers in general—often means battling those smooth, blobby mushroom shapes that are difficult to break up and hard to add detail to. The usual approach involves layering disturbance, turbulence, and using extra fields as masks. We spend a lot of time stacking multiple noise patterns with different mask fields, tweaking values through a time-consuming trial-and-error process.

What works for one simulation often doesn’t work for another. If the simulation resolution changes, everything behaves differently. When the sourcing changes, you’ll likely need to retune the noise amplitudes and mask ranges to find the right balance.

Sometimes, simulations end up looking overly detailed with repetitive noise everywhere, giving them a fuzzy, unnatural appearance. Other times, they lack definition and feel too soft.

I created this microsolver to help reduce the technical struggle and give you more freedom to focus on creative decisions. It’s designed to extract maximum detail from a given voxel resolution and adapt automatically to resolution and speed changes. (Of course, if your fluid is moving very fast, you’ll still need additional substeps.)

To understand its potential, try breaking up the left-side smoke column in the example file using only conventional techniques. Aim for the best possible results, and track how long it takes. Then, try the same using this microsolver—perhaps even apply it to an older project by removing the traditional disturbance and turbulence setups.

In terms of performance, it behaves similarly to conventional microsolvers when using face-sampled velocities, and slightly slower when using center-sampled velocities.

Use this microsolver to add fine detail—ideally after applying the forces that shape the overall silhouette of your simulation.

I’m looking forward to seeing the amazing results you'll achieve with it.






<a href="https://creativecommons.org">VenkysTurbulence</a> © 2025 by <a href="https://creativecommons.org">Venkatesh Kongathi</a> is licensed under <a href="https://creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a>

Shield: [![CC BY-NC 4.0][cc-by-nc-shield]][cc-by-nc]

This work is licensed under a
[Creative Commons Attribution-NonCommercial 4.0 International License][cc-by-nc].

[![CC BY-NC 4.0][cc-by-nc-image]][cc-by-nc]

[cc-by-nc]: https://creativecommons.org/licenses/by-nc/4.0/
[cc-by-nc-image]: https://licensebuttons.net/l/by-nc/4.0/88x31.png
[cc-by-nc-shield]: https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg
