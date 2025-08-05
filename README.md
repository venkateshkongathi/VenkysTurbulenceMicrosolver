# VenkysTurbulenceMicrosolver
Houdini Pyro gas microsolver for organic turbulence details.
Compiled for Houdini 20.5.654

Place the .dll file in in C:\Users\USER\Documents\houdini20.5\dso\

add below text in C:\Users\USER\Documents\houdini20.5\houdini.env

HOUDINI_DSO_PATH = "C:/Users/USER/Documents/houdini20.5/dso;&"




https://youtu.be/73SDbIuSbzU


Often, working with Houdini’s Pyro Solver—or smoke solvers in general—means battling those smooth, baldy mushroom shapes that are difficult to break up and hard to add detail to. We spend a lot of time layering multiple noises using different mask fields.

The values that work for one simulation might not work for another. Every time the sim resolution changes, things behave differently. If the sourcing changes, you often have to re-tune the noise amplitudes and mask ranges to find the sweet spot.

Sometimes simulations look overly detailed or have similar-looking noise everywhere, resulting in a fuzzy, unnatural feel. Other times, they lack definition and look too soft.

I built this microsolver to help reduce the time spent wrestling with technical challenges, and give you more room to focus on creative choices. It’s designed to extract as much detail as possible from a given voxel resolution, and it adapts to resolution and speed changes automatically (though, of course, if your fluid is moving too fast, you’ll still need more substeps).

I’m excited to see what amazing things you’ll create with it.







<a href="https://creativecommons.org">VenkysTurbulence</a> © 2025 by <a href="https://creativecommons.org">Venkatesh Kongathi</a> is licensed under <a href="https://creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a>

Shield: [![CC BY-NC 4.0][cc-by-nc-shield]][cc-by-nc]

This work is licensed under a
[Creative Commons Attribution-NonCommercial 4.0 International License][cc-by-nc].

[![CC BY-NC 4.0][cc-by-nc-image]][cc-by-nc]

[cc-by-nc]: https://creativecommons.org/licenses/by-nc/4.0/
[cc-by-nc-image]: https://licensebuttons.net/l/by-nc/4.0/88x31.png
[cc-by-nc-shield]: https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg
