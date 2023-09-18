---
title: ""
# description: ""
# date: "2023-06-30"
aliases: ["data"]
author: "SFU"
math: true
slug: /webinar
---

<font size="+3">2023 *Visualize This!* Contest</font>

Last Friday (Sep-15) we launched the *Visualize This!* Contest.

### Who are we?

We are the Alliance's {{<a "https://ccvis.netlify.app/about" "National Visualization Team">}} comprised of HPC
analysts from the Alliance's regional partners (ACENET, Calcul Québec, Compute Ontario) and universities in
Western Canada (SFU, Univ of Alberta, Univ of Calgary).
- Hosted by [the Digital Research Alliance of Canada](https://alliancecan.ca) and its regional / institutional partners

### Now in its 6th year

- {{<a "https://visualizethis.netlify.app" "2023:">}} Halloween storm over Eastern Canada <ins>and</ins> the
  Normalized difference vegetation index
- {{<a "https://scivis2021.netlify.app" "2020-2021:">}} Earth's Mantle Convection
  {{< figure src="https://ccvis.netlify.app/ieee2021.png" title="Figure 1: In 2020-2021 we partnered with IEEE Vis to host the international 2021 SciVis Contest" >}}
- {{<a "https://scivis2021.netlify.app/2019" "2019:">}} Incompressible transitional air flow over a wind turbine
  section <ins>or</ins> bring your own data
- {{<a "https://scivis2021.netlify.app/2018" "2018:">}} Interaction of a large protein structure with a cell's membrane
  <ins>and</ins> Linked humanities data
- {{<a "https://scivis2021.netlify.app/2017" "2017:">}} Airflow around counter-rotating wind turbines
- {{<a "https://scivis2021.netlify.app/2016" "2016:">}} Visualizing multiple variables in a global ocean model

### Why we host these contests

1. **Train**: popularize and teach open-source software visualization tools and techniques that researchers can
   apply to their own data. We regularly teach visualization workshops and courses, and we find that a
   visualization contest is a perfect venue for early-career researchers to learn these tools and sharpen
   their data analysis skills.
1. **Outreach**: tell all Canadian academic researchers about our visualization support, including
   *support@tech.alliancecan.ca* and your local/regional HPC support.
1. **Learn**: see novel visualization ideas, learn from you.

### Who can participate

Targeting primarily graduate students and postdocs from Canadian universities, but anyone can participate
irrespective of their affiliation or career stage.

### Contest terms

Please read our [Contest terms](/#contest-terms) before sending us your work.
1. Only use open-source (not proprietary or commercial) tools so that anyone can reproduce your visualization.
1. Your submission may be published on our website and in other communication materials, with all credits
   preserved.

<u>Don't be afraid to experiment!</u> With 3D visualization I usually find the interactive data exploration
process a lot of fun, and the more you play with the data, the more ideas you typically have. We expect that
most participants will be absolute beginners with 3D visualization, so the idea is to learn in the process.

### Datasets

You can work on one of two datasets:
- both datasets contain *Canadian geospatial data*: one from a numerical simulation, and the other compiled
  from several empirical sources
- both are available for downloading now
- both can be visualized on personal computers (no need for HPC)

1. Simulation of a storm over Eastern Canada
- more difficult, involves multiple overlapping 3D scalar fields
- data kindly provided by Alejandro Di Luca and François Roberge from l'Université du Québec à Montréal
- simulation was conducted using the Alliance's Narval cluster

<br>
<iframe width="756" height="477" src="https://www.youtube.com/embed/3fpc2fFaLP4?rel=0" title="Simulation of a storm over Eastern Canada" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<p style="line-height: 1.2;"> <font size="3"> <b>Figure 2:</b> Distribution of clouds (white), rain (green to
cyan), and ice crystals (yellow) over 6 days starting with the storm on October 31, 2019. </font> </p>
<br>

2. Normalized difference vegetation index (NDVI) over BC throughout 2022
- less complex, almost 2D data
- data kindly provided by Michael Noonan and Stefano Mezzini from the University of British Columbia at Okanagan

<br>
<iframe width="756" height="681" src="https://www.youtube.com/embed/5hZ59mDdBnI?rel=0" title="NDVI over time in BC" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<p style="line-height: 1.2;"> <font size="3"> <b>Figure 3:</b> NDVI as a function of time for BC. </font> </p>
<br>

### Timeline

<!-- | Date | Stage | -->
<!-- | -------- | -------- | -->

- 2023-Sep-15 -- contest announcement, datasets published
- 2023-Sep-19 -- today's webinar
- December 10th, midnight Pacific Time -- submission deadline
- Mid- to late December -- review of submissions
- Early January 2024 -- announcement of results

### For more information

- Contest website https://visualizethis.netlify.app (English) and https://visualizethis.netlify.app/fr (French)
- For quick questions about the Contest, [use this form](https://forms.gle/kLo2mL5NM2FMtXoz9)
- Join the [2023 *Visualize This!* Google group](https://groups.google.com/d/forum/visualize-this-2023); to read and
  post messages, please {{<a "https://forms.gle/hYHvzQzRAqfMEvMHA" "register your interest">}} in the Contest,
  and we will add you to the group

### Let's take a look at the data!

# Dataset 1: simulation of a storm over Eastern Canada

Let's load the data in Python:

- len(data.time) = 24 inside each 3D file
- (rlat, rlon) are *the coordinates in the rotated grid* used by the model
- the geographical coordinates lon(rlat, rlon) and lat(rlat, rlon) are inside the data files
- type(data.lon.values)
- data.MPQR.values.shape = (24, 16, 1060, 1330)

Let's check an example of a complete workflow `a14.py` in ParaView. This file is not shared with the participants.

Let's create a flat topography file in ParaView:

1. load the land-sea mask MG(rlat,rlon) from `pm2015090100_00000000p.nc`, selecting (rlat,rlon) variables
2. load the topographical elevation ME(rlat,rlon) from `dm2015090100_00000000p.nc`, selecting  (rlat,rlon) variables
3. apply Append Attributes to both
4. apply Calculator: elevation = MG*ME
5. apply the Programmable Filter
Output Type = vtkImageData
```py
ext = inputs[0].GetExtent()
elevation = inputs[0].PointData["elevation"]

output.SetOrigin(0., 0., 0.)
output.SetSpacing(1., 1., 3.)
output.SetDimensions(ext[1]-ext[0]+1, ext[3]-ext[2]+1, ext[5]-ext[4]+1)
output.SetExtent(ext)
output.AllocateScalars(vtk.VTK_FLOAT, 1)

vtk_data_array = vtk.util.numpy_support.numpy_to_vtk(elevation, deep=True, array_type=vtk.VTK_FLOAT)
vtk_data_array.SetNumberOfComponents(1)
vtk_data_array.SetName("elevation")
output.GetPointData().SetScalars(vtk_data_array)
```
6. apply Threshold to throw away 0<elevation<0.1
7. last object | Save Data as `topo.pvd`
8. optionally apply Warp by Scalar coeff=0.003

You can visualize everything in curved / spherical coordinates. Here is an example for a 3D array:

1. load the mass mixing ratio of cloud `MPQC(time,pres,rlat,rlon)` from `dp2015090100_20191101d.nc`, selecting
   (pres,rlat,rlon) variables and using `vertical scale = 1` and `vertical bias = 1e4` to force a narrow
   radial section
2. try Surface &nbsp;🡒&nbsp; can't see anything ...
3. try Volume representation &nbsp;🡒&nbsp; *very, very slow* ... trying to do ray tracing in curved geometry
3. Isosurface might work in this geometry &nbsp;🡒&nbsp; try a range on a log scale

If instead you prefer to transition to a flat geometry (*much faster* in Volume representation), here is how
you could do it with a 3D array:

1. load the mass mixing ratio of cloud `MPQC(time,pres,rlat,rlon)` from `dp2015090100_20191101d.nc`, selecting
   (pres,rlat,rlon) variables; vertical scale/bias are not important here
2. apply the Programmable Filter
Output Type = vtkImageData
```py
ext = inputs[0].GetExtent()
mpqr = inputs[0].PointData["MPQR"]

output.SetOrigin(0., 0., 0.)
output.SetSpacing(1., 1., 9.)
output.SetDimensions(ext[1]-ext[0]+1, ext[3]-ext[2]+1, ext[5]-ext[4]+1)
output.SetExtent(ext)
output.AllocateScalars(vtk.VTK_FLOAT, 1)

vtk_data_array = vtk.util.numpy_support.numpy_to_vtk(mpqr, deep=True, array_type=vtk.VTK_FLOAT)
vtk_data_array.SetNumberOfComponents(1)
vtk_data_array.SetName("rain")
output.GetPointData().SetScalars(vtk_data_array)
```
- apply Contour at 0.0001
- make all white
- also show the Volume representation

### Plotting all timesteps inside a single NetCDF file

In the previous visualization, let's go back to Contour at 1.e-4. Also show the outline. Use "Play" button to
play it back. How can you save this animation.

<u>Traditional approach:</u>

1. File | Save Animation... as PNG images
2. use [*ffmpeg* command-line utility](https://ffmpeg.org) to merge them into a movie at let's say 10fps

<u>Scripting approach:</u>
1. File | Save State... as a Python code `animOneDay.py`
1. You can even test it via File | Load State... to make sure everything looks good
1. Edit this Python code:  
    a. look for the line with `dp2015090100_20191031dnc = NetCDFReader`  
    b. rename `dp2015090100_20191031dnc` to `data` everywhere in the script  
    c. remove any existing `SaveScreenshot`  
    d. add the following near the end of your script:
```py
time = data.TimestepValues
print(time)
for t in time:
    print("processing step", t)
    data.UpdatePipeline(t)
    renderView1.ViewTime = t
    SaveScreenshot('/path/to/frame%04d'%(t)+'.png', renderView1, ImageResolution=[1920, 1080])
```
4. Run the script:
```sh
pvpython animOneDay.py
```

### Challenge: visualize multiple 3D fields and their relative positions

- use different colour maps for different variables
- avoid overlapping and too much data in one plot
- use different representations for different variables

Check out [Tasks](../tasks).

# Dataset 2: NDVI over BC

Presenter: play back `~/Documents/09-visualizeThisWebinar/mu_both.mp4`. This file is not shared with the
participants.

Let's load the CSV data in Python:

- each row is a data point, no underlying mesh

Let's load the VTK data in ParaView

1. each point has three variables: elev, NDVI $\mu$ , and its variance $\sigma_2$
1. use Point Gaussian representation with a plain circle, adjust radius
1. colour by NDVI
1. switch to the blue-to-brown-to-green NDVI colour map

Let's load the CSV data in ParaView -- this takes a while. Pass the data through the Table To Points filter.

### Suggestions

Check out [Tasks](../tasks).

<!-- Please note that there are some artifacts in the data related to a model fit, e.g. if you look at *elevation*, -->
<!-- there is one data point above 7km. You can either remove this point, or ignore it in your analysis -- it -->
<!-- should not affect the visualization part. -->
