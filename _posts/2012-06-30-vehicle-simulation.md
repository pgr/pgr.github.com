---
layout: post
title: Vehicle Performance &amp; Handling Simulation (Engineering Bachelors Thesis)
---

{{ page.title }}
================

<p class="meta">2011 - 2012</p>
<p class="meta">Filed under: Vehicle Dynamics, Vehicle Simulation</p>

In completion of my undergraduate bachelors in mechanical engineering, I undertook 12 months of applied research culminating in the submission of a final thesis. This research focused primarily around characterising not just a vehicle's performance, but also its handling traits. The results of this research focused on developing tools to aid decision making regarding both vehicle design and vehicle setup.

Initial high level studies looked at which aspect of a vehicle's setup had the biggest influence on performance. These studies looked at a variety of vehicle types on a variety of tracks and sought to determine where development would be best spent to improve overall performance. The remaining resulting studies centered around these aspects that were deemed most important.

Vehicle Model
-------------

A full vehicle kinematics model was built from the x,y,z location of the physical pickup points for a given chassis. 

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/kinematics_setup.png" width="500" height="" alt="" />
<p class="meta">Above: A kinematic model built to represent the vehicles suspension. (Built in OptimumKinematics).</p>

The position and orientation of each wheel was then mapped to inputs of steering angle and chassis roll angle, which allowed the vehicle kinematic properties (ranging from caster, trail, camber and motion ratios fro each corner all the way through to half track, wheelbase and instant centers) to be calculated for any vehicle state (for a given pitch angle and heave displacement).

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/low_caster.png" width="500" height="" alt="" />
<p class="meta">Above: The relationship between steering and chassis roll on the front left and front right camber angles, for a low caster setup (zero static camber present).</p>

<p class="meta">Below: Shifting the upper wishbone points longitudinally along the chassis yields a change in relationship between steering, roll and camber angle. It is evident that the higher caster angle has a more pronounced effect on the camber change with steering (some negative static camber present).</p>

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/high_caster.png" width="500" height="" alt="" />

The tire models used for the simulation work were pure lateral slip implementations. In order to fit these models, software was developed to fit model coefficients using a Levenberg–Marquardt (Damped Least-Squares) algorithm. The resulting tyre coefficients were then validated against raw data, with the model's scaling factors adjusted to ensure that the model was representative of the surfaces the tyre would run on. 

The loads through the chassis were determined by a chassis stiffness model which incorporated the ride springs, anti-roll springs and overall chassis torsional stiffness. Taking this stiffness model, and the values from the kinematic model formed the inputs to the tyre model on each corner. 


Simulation Work &amp; Visualisation
-----------------------------------

The bulk of the simulation work centered around quantifying the vehicles performance and handling via the following metrics:

* Lateral acceleration (maximum and steady state / "trimmed")
* Vehicle balance (understeer / oversteer tendancy)
* Vehicle stability and control (agility / sensitivity to inputs) 
* Drive-ability (sensitivity at maximum lateral acceleration states)

The basic methodology utilised to determine these parameters relied heavily on the generation of yaw moment diagrams (yaw moment method) presented by Milliken and Milliken. This method compares the lateral acceleration of a vehicle against it's balance, providing an envelope which dictates both the performance and handling characteristics.

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/clean_cut_ymm.png" width="500" height="" alt="" />

<p class="meta">Above: The lateral acceleration (grip level) compared to the angular acceleration (or vehicle balance, which is essentially the level of understeer or oversteer). Coloured by chassis slip angle (&beta;).</p>

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/ymm_tip.png" width="500" height="" alt="" />

<p class="meta">Above and below: Automatic classification of both the trimmed (steady state) and untrimmed maximum lateral accelerations (for both the standard and counter steering cases).</p>

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/ymm_tip_opt.png" width="500" height="" alt="" />

Once these metrics had been quantified for a specified vehicle setup, the results were also analysed in a qualitative fashion. This provided an idea as to how sensitive each model input was, and which inputs had the most impact on these metrics.

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/grip.png" width="500" height="" alt="" />

<p class="meta">
Above: The effect of altering the static camber front and rear analysed for their effect on total vehicle grip. For this vehicle setup, there is a large "sweet spot" where the cornering grip is not particularly sensitive (lower-right). Some numerical noise is also seen around the -1 to zero front static camber region.
</p>

<p class="meta">
Below: For the same vehicle setup, we can see how the vehicle balance is influenced by static camber. As the rear static camber moves towards zero, the vehicle tends towards oversteer (or positive values of balance).
</p>

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/balance.png" width="500" height="" alt="" />

From these qualitative visualisations, we can see the changes that need to be made to alter the vehicles grip whilst maintaining a desired balance. Likewise, we can see how to adjust the vehicle balance without compromising grip. 

If we look at single point of these visualisations, we can further qualify the vehicle state, investigating how effectively (and efficiently) each tire is being used.

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/shib_tire_utilisation_max_limit_fy.png" width="500" height="" alt="" />

<p class="meta">Above: The front left, front right, rear left and rear right tyres of a single vehicle state are analysed (with the effects of weight transfer and camber thrust clearly visible).
</p>

Interface Work
==============

Throughout the course of development, two distinct interfaces were built to run these simulations. The first was a graphical interface used to assess the general impact of a range of parameters. This allowed for a more general exploration and understanding on how vehicle performance and handling changed with certain parameters. This graphical interface utilises a slightly simplified kinematics model (linearised coefficients) in order to run interactively on a standard laptop.

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/gui_sage_interface.png" width="500" height="" alt="" />

<p class="meta">Above: The user friendly, slightly simplified, interactive interface.</p>

Alternatively, the full vehicle model (using kinematics mapped against chassis roll angle and applied steering angle) can be farmed out on demand to a custom, cloud based high performance computing cluster, capable of running numerous simulations in parallel. Whilst less user friendly and requiring an internet connection, this approach facilitates running large scale, on demand simulations quickly and efficiently. 

<a href="https://s3.amazonaws.com/github_image_storage/thesis_post/top_ec2.png" alt="Cloud based parallel interface" title="Cloud based parallel interface">
<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/thesis_post/top_ec2.png" width="500" height="" alt="" /></a>

<p class="meta">Above: The interface for large scale parallel simulations, showing two individual cluster nodes of 32 processors each (so, 64 CPU's humming along).</p>

