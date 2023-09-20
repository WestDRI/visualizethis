+++
author = "SFU"
+++

<font size="+3">2023 *Visualize This!* Contest: two datasets</font>

<!-- <font size="+0"> -->
<!-- </font> -->

Hosted by [the Digital Research Alliance of Canada](https://alliancecan.ca) and its regional partners, and now
in its 6th year, *Visualize This!* is a Canada-wide competition that aims to celebrate the innovative ways
visualization can help researchers explore datasets and answer important scientific questions. *Visualize
This!* is your chance to challenge your creativity, experiment with cutting-edge visualization tools, and
contribute to the growth of data visualization in Canada!

<!-- Together with the Alliance's National Visualization Team, we want to bring your creative visualization ideas -->
<!-- and workflows to life and make them accessible to all Canadian researchers! -->

<!-- BC DRI, Prairies DRI, Compute Ontario, Calcul Québec, and ACENET -->

<!-- Other possible colours: #FF4500 #777777 #FC5900 #439596 -- see https://bit.ly/45cOl61 -->

<font color="#439596"> In this year's Contest you can work on one of the two datasets below. Both datasets
contain geospatial data, one from a numerical simulation, and the other compiled from several empirical
sources. </font>
To participate in the challenge, please {{<a "https://forms.gle/hYHvzQzRAqfMEvMHA" "register your interest">}}
-- this will add you to the "Visualize This 2023" Google group where we will post all updates and
announcements.

<!-- <br> -->

# Dataset 1: Halloween storm over Eastern Canada

The research group of {{<a "https://alejandro-diluca.uqam.ca" "Alejandro Di Luca">}} (Université du Québec à
Montréal) provided the first dataset. The data come from a numerical simulation of a storm over Eastern Canada
during Halloween 2019.

The animation below covers six days from October 31st to November 5th, 2019. The 3D volume features the
distribution of clouds (white), rain (green to cyan), and ice crystals (yellow) in the atmosphere, whereas the
2D surface at the bottom shows the snow accumulation on the ground. The 3D variables are also displayed in the
two projections, along the x- and y-axes, to highlight the relative vertical distribution of the three
variables.

<!-- {{< yt 3fpc2fFaLP4 63 >}} -->

<br>
<iframe width="756" height="477" src="https://www.youtube.com/embed/3fpc2fFaLP4?rel=0" title="Simulation of a storm over Eastern Canada" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<p style="line-height: 1.2;"> <font size="3"> <b>Figure 1:</b> Distribution of clouds (white), rain (green to
cyan), and ice crystals (yellow) over 6 days starting with the storm on October 31, 2019. </font> </p>
<br>

You can find more about this dataset [here](/data/storm/). The main challenge is to show the overlapping
distributions of several 3D variables, ideally (but no necessarily!) in the same visualization.

# Dataset 2: normalized difference vegetation index (NDVI)

The second dataset was provided by the research team of {{<a
"https://biology.ok.ubc.ca/about/contact/michael-j-noonan" "Michael Noonan">}} (University of British Columbia
at Okanagan). They compiled approximately one year of openly-available remotely sensed NDVI (normalized
difference vegetation index) data at the global scale. NDVI is a measure of greenness, widely used to measure
the ecosystem productivity. To limit the size of the dataset, here we provide data only for BC.

<!-- {{< yt 5hZ59mDdBnI 90 >}} -->

<br>
<iframe width="756" height="681" src="https://www.youtube.com/embed/5hZ59mDdBnI?rel=0" title="NDVI over time in BC" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<p style="line-height: 1.2;"> <font size="3"> <b>Figure 2:</b> NDVI as a function of time for BC. </font> </p>
<br>

You can find more about this dataset [here](/data/ndvi/). This dataset is simpler than the first one, as it
contains effectively only 2D data (that you can choose to view in 3D).

# Contest webinar

<br>
{{< yt MIlMQ3mcVW4 63 >}}
<br>

# Contest terms

Please only use open-source tools and libraries in the Contest, so that anyone can reproduce your solution
without having to pay for commercial / proprietary tools. Two commonly used 3D visualization tools are {{<a
"https://www.paraview.org" "ParaView">}} and {{<a "https://visit-dav.github.io/visit-website" "VisIt">}}, but
you are free to use any open-source package or library or any programming language -- there are many tools
readily available for visualizing these data. What you can do with these tools is really limited only by your
imagination.

Your submission in the Contest (both images/movies and the workflow) will be published under a <a
rel="license" href="http://creativecommons.org/licenses/by/4.0">Creative Commons Attribution 4.0
International License</a>.

<!-- {{<a "link" "text">}} -->
