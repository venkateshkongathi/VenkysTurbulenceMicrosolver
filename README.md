# VenkysTurbulenceMicrosolver
Houdini Pyro gas microsolver for organic turbulence details.
Compiled for Houdini 20.5.654

Place the .dll file in in C:\Users\USER\Documents\houdini20.5\dso\

add below text in C:\Users\USER\Documents\houdini20.5\houdini.env

HOUDINI_DSO_PATH = "C:/Users/USER/Documents/houdini20.5/dso;&"



[https://youtu.be/73SDbIuSbzU](https://youtu.be/jnuaG3a33xI)


Working with Houdini’s Pyro Solver—or smoke solvers in general—often means battling those smooth, blobby mushroom shapes that are difficult to break up and hard to add detail to. The usual approach involves layering disturbance, turbulence, and using extra fields as masks. We spend a lot of time stacking multiple noise patterns with different mask fields, tweaking values through a time-consuming trial-and-error process.

What works for one simulation often doesn’t work for another. If the simulation resolution changes, things behaves differently. When the sourcing or velocities changes, you’ll likely need to retune the noise amplitudes and mask ranges to find the right balance.

Sometimes, simulations end up looking overly detailed with repetitive noise everywhere, giving them a fuzzy, unnatural appearance. Other times, they lack definition and feel too soft.

I made this microsolver to help reduce the technical struggle and give you more freedom to focus on creative decisions. It’s designed to extract maximum detail from a given voxel resolution and adapt automatically to resolution and speed changes. (Of course, if your fluid is moving very fast, you’ll still need additional substeps.)

To understand its potential, try breaking up the left-side smoke column in the example file using only conventional techniques. Aim for the best possible results, and track how long it takes. Then, try the same using this microsolver—perhaps even apply it to an older project by removing the traditional disturbance and turbulence setups.

In terms of performance, it behaves similarly to conventional microsolvers when using face-sampled velocities, and slightly slower when using center-sampled velocities.

Use this microsolver to add fine detail—ideally after applying the forces that shape the overall silhouette of your simulation.

I’m looking forward to seeing the amazing results you'll achieve with it.


I have tried to lay out parameters in the most intuitive way possible.
For optimal results use BFECC advection method with at least 2 max substeps and single projection. If you can afford, use Face Sampling Velocities.

Before you add this microsolver first make sure your sim works without any artefacts. Set the right forces to define the shape of your sim. Then you can add this so you know exactly what to expect.

Air Factor:

This defines how the air surrounding the smoke plume affects its turbulence. Increasing this value will increase turbulence on the outer edges of the smoke, especially when the solver is in Full Physical mode.
Recommended Values:
For denser volumes, values from 0.1 to 0.2 will simulate a real-world Air Entrainment Coefficient when in Full Physical mode.
For thin smoke or dust, you can use higher values, closer to 1.

Smoke Density:

This represents the real-world density of various smoke types and is useful for matching your simulation's behavior to real materials. Increasing this value also increases turbulence.
Wood smoke: approx. 1.2-1.4 kg/m^3
Plastic smoke: approx. 1.5-2.5 kg/m^3
Oil smoke: approx. 1.5-2.5 kg/m^3
Diesel smoke: approx. 1.5-2.5 kg/m^3
Wildfire smoke: Highly variable, but you can assign an average for simulation purposes.

Dynamic Viscosity:

This is also based on real-world values and affects how the smoke flows and becomes turbulent. Lower values make the smoke more turbulent, while higher values make it less so.
In my experience I didn’t push it beyond 10-15 most of the time, that too when smoke density is close to 2.5.
Wood smoke: 2-8
Diesel exhaust: 2.5-4
Cigarette smoke: 5-20
Industrial smoke: 1-100+ (varies by source and composition)
If you googled, the units are in x 10^-5 Pa.s, but you can ignore the sciencey part and just use the numeric value (e.g., when you see 5 x 10^-5 Pa.s means enter 5)

Emulate Scale:

This parameter, measured in meters, emulates the phenomenon of turbulence at different scales. For example, a campfire's smoke has a scale of about 0.5 to 1 meter, while a large bonfire has a 2-3 meter scale. Volcano craters can range from hundreds of meters to several kilometers. When you want to match something in the real world, you know what to do.
Density Threshold
This setting controls the physics of the turbulence.
When the Density Threshold is positive, the turbulence is partially physical, which should work fine for most cases.
Setting it to a negative value makes the simulation fully physical, but this comes with a bit of a performance cost. Full Physical mode adds natural air drag on the smoke volume and keeps the overall silhouette much more cohesive.
You can also increase the positive threshold to define the density at which turbulence begins. This helps improve computation time and keeps low-density areas free of artifacts. If you see artifacts, try increasing the Density Threshold slightly.

Turb Strength:

This is your typical amplitude. You should only need to adjust this for artistic reasons.

Swirl Size:

Increasing the Swirl Size makes the simulation more billowy! A value of 1 means the turbulence swirl is the same size as your simulation's voxel resolution. I recommend a Swirl Size of 4, where each swirl occupies a 4x4 voxel cube, as this produces fewer artifacts.
When scaling up your simulation from a low resolution to a high resolution:
To get the most detail possible in your high-res simulation, leave the Swirl Size the same as it was in your low-res sim.
To make the high-res simulation's shapes resemble the low-res version, you need to scale the Swirl Size. For example, if your low-res sim used a voxel size of 0.02 and your high-res sim will use 0.01, that's a 200% increase. You would multiply your original Swirl Size by 2. If your Swirl Size was 4, your new Swirl Size would be 8.
You can use this simple expression to calculate the new Swirl Size automatically:
Original Swirl Size * (Low Res Voxel Size / High Res Voxel Size)

Pulse Length:

Change this value to alter the look of the turbulence, similar to changing a random seed but keep it within 0 - 1.




<a href="https://creativecommons.org">VenkysTurbulence</a> © 2025 by <a href="https://creativecommons.org">Venkatesh Kongathi</a> is licensed under <a href="https://creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a>

Shield: [![CC BY-NC 4.0][cc-by-nc-shield]][cc-by-nc]

This work is licensed under a
[Creative Commons Attribution-NonCommercial 4.0 International License][cc-by-nc].

[![CC BY-NC 4.0][cc-by-nc-image]][cc-by-nc]

[cc-by-nc]: https://creativecommons.org/licenses/by-nc/4.0/
[cc-by-nc-image]: https://licensebuttons.net/l/by-nc/4.0/88x31.png
[cc-by-nc-shield]: https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg
