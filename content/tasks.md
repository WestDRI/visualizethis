---
title: "Tasks"
# description: ""
# date: "2023-06-30"
aliases: ["about-us","about-hugo","contact"]
author: "SFU"
---

These guidelines are just suggestions, not the instructions. We would like to see unusual approaches and novel
visualizations of these datasets. Please experiment with your tool of choice, and don't be afraid to try
something new!

*Depending on the dataset you work on, please read the corresponding section below.*

<br>

# Halloween storm over Eastern Canada

1. Show time-dependent distributions of clouds, rain and ice particles in the atmosphere over the three days,
   both relative to topography and to each other.
1. Show how these distributions affect the land snow cover and the sea surface pressure.

<br>

# Normalized difference vegetation index

1. How does the relationship between the mean NDVI and its variance vary spatially? We would like to see
   different ways of representing this relationship.
1. In a 3D visualization it would be interesting to see the relation between NDVI and elevation. One could
   easily plot NDVI vs. elevation, e.g. as a scatter plot, but it would be interesting to display this
   relationship in real space.
1. Animations and perhaps interactive visualizations. We would also welcome more artistic submissions, e.g. a
   flyover above BC.





<!-- Not sure what you mean by "projected". If you referring to projection onto a sphere (if their rendering is 3D) -->
<!-- or a cartographic projection (if 2D), then we’ll leave it to participants. The goal of the contest is to see -->
<!-- unusual ideas and approaches, so I’d rather not limit to a specific view. -->





<!-- question to Stefano: -->
<!-- - how is V(NDVI) defined exactly? Is it spatial or temporal variance? -->








<!-- ========================================================================================== -->

<!-- - Visualize eddies in 3D, at a single snapshot, and over time. -->
<!-- - Visualize transport/advection of temperature and salinity -->
<!-- - Visualize correlation between the transport/advection of temperature and salinity -->
<!-- - Visualize statistics in eddies' ensembles and associated uncertainties in 3D, over time -->

<!-- 1. Visualize stagnated or diverted cold slabs (descending mantle material) at ~660 km (upper and lower mantle boundary) depth. <\!-- avalanches -\-> -->
<!-- 1. Visualize stagnated or diverted cold slabs at ~1600 km (mid-mantle) depth. <\!-- avalanches -\-> -->
<!-- 1. Visualize stagnated or diverted hot plumes (rising hot mantle material) at ~1600 km depth and their rise to the upper -->
<!--    regions of the lower mantle. -->
<!-- 1. Visualize stagnated or diverted hot plumes at ~660 km depth. -->
<!-- 1. Visualize correlations between the variables and the flow patterns described below. -->

<!-- Additional points will be given for: -->

<!-- - best cover visualization, and -->
<!-- - best representation of the 3D velocity field. -->

<!-- The slice visualization below and the [front-page](/) animation were produced with very simple ParaView workflows. The -->
<!-- overall goals of this contest is to produce better visualizations than these and to come up with novel analysis -->
<!-- techniques and ideas that are unique to the problem. -->

<!-- Ideally, all submissions should be reproducible and use only open-source tools, so that anyone could benefit from your -->
<!-- work. -->

<!-- You can check the IEEE SciVis Contest [2020 session](https://kaust-vislab.github.io/SciVis2020/results.html) to see the -->
<!-- previous year's winning entries. -->

<!-- <\!-- These are the most important outcomes of this modeling and study. -\-> -->






<!-- #### Physical variables and the flow patterns -->

<!-- The flow patterns (e.g. avalanches or stagnations) at 660 km depth and 1600 km depth are very different in nature, -->
<!-- making their visualization independent of each other. The former are caused by the endothermic phase transition at 660 -->
<!-- km which has been known for the past few decades. The latter are due to the iron spin transition in the lower mantle -->
<!-- minerals starting at ~1500 km depth. -->

<!-- The best way to track these two physical processes is by using the <ins>temperature anomaly</ins>. For the phase -->
<!-- transition at (660±10) km depth, you can look at depths above and below 660 km. Above this depth check for cold, -->
<!-- horizontally-extended material. Below this depth the hot rising material may be stagnated for a while before rising -->
<!-- above 600 km. -->

<!-- You can look for similar effects caused by the spin transition at 1600 km depth. Note that spin transition starts at -->
<!-- ~1500 km depth and is completed at the core-mantle boundary at the bottom of the model. -->

<!-- In addition to the temperature anomaly, you may use the <ins>spatial velocity</ins> to find these flow patterns. -->

<!-- For spin transition only you may also use the <ins>spin transition-induced density anomaly</ins> variable. Above 1500 km -->
<!-- depth the anomaly is zero (no spin transition effect). Between 1500 km and 1600 km, this density anomaly may become -->
<!-- negative in certain regions, slowing down or completely stopping cold sinking material (check the temperature -->
<!-- anomaly). This density anomaly becomes positive for the cold material after passing the 1600 km depth causing the -->
<!-- downward acceleration of the flow (avalanche). -->

<!-- Similarly, for hot plumes originating at the core-mantle boundary, this density anomaly is negative, helping their -->
<!-- acceleration. Near 1600 km depth the density anomaly in hot plumes becomes positive and may slow down or completely stop -->
<!-- them. -->

<!-- <\!-- - thermal conductivity [Watt/m/K], -\-> -->
<!-- <\!-- - thermal expansivity [1/K], -\-> -->





<!-- <\!-- Q: How can one differentiate between the endothermic phase transition at 660 km and the spin transition in iron in the -\-> -->
<!-- <\!-- lower mantle minerals at 1600 km when looking only at the 3D data, besides obviously the depth? Is there anything in the -\-> -->
<!-- <\!-- 3D variables that you gave me that can distinguish the two types of transitions? -\-> -->

<!-- <br> -->

<!-- ![Temperature and density anomalies](../images/dTdRho.png) -->

<!-- <\!-- <img src="../images/dT-dRho.jpg" alt="Temperature and density anomalies" style="float: left; margin-right: 10px;" /> -\-> -->

<!-- <p style="line-height: 1.2;"> <font size="3"> <b>Figure 2:</b> Temperature anomaly (left) and the corresponding spin -->
<!-- transition-induced density anomaly (right) at two timesteps separated by 20 Myrs (earlier at the top) in a cross-section -->
<!-- and at the inner, core-mantle boundary. You can see a descending cold slab that becomes first lighter and then heavier -->
<!-- (red and blue regions on the right panels) which can initially slow and then accelerate the mantle flow at mid-mantle -->
<!-- depths (bottom left panel). You can see similar effects in the hot rising plumes. These two effects can cause plume or -->
<!-- slab stagnation at mid-mantle depths with subsequent sudden avalanches. </font> </p> -->

<!-- <\!-- The spin transition-induced density for the model I have sent you is based D4 in Table 2 in the attached paper. In order to calculate the spin transition-induced density anomaly, we calculate the laterally average of this density and subtract it from the spin transition-induced density (i.e. anomaly = dRho - dRho_ave) (see the four lines at the bottom of page 5 in this paper). -->
<!-- <\!-- For depths above ~1500 km there is no spin transition, and therefore no spin transition-induced density (and hence no density anomaly). -\-> -->
<!-- <\!-- Temperature anomaly is calculated in similar way (T-Tave) (T_ave: average of temperature at each depth). -\-> -->
