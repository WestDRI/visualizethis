---
title: "Normalized difference vegetation index (NDVI)"
description: "NDVI dataset"
# date: "2019-02-28"
author: "SFU"
slug: /data/ndvi
math: true
<!-- menu: -->
<!--   subpage: -->
<!--     identifier: about-subpage-s2 -->
<!--     parent: about -->
<!--     name: About Subpage -->
<!--     title: About Subpage -->
<!--     url: /data/subpage/ -->
<!--     weight: 1 -->
<!--   subpage2: -->
<!--     identifier: about-subpage2-s2 -->
<!--     parent: about -->
<!--     name: Second About Subpage -->
<!--     title: Second About Subpage -->
<!--     url: /data/subpage2/ -->
<!--     weight: 10 -->
---

This dataset is a compilation of openly available remote-sensed NDVI (normalized difference vegetation index)
data for BC. NDVI is a measure of greenness calculated from spectrometric data at two specific bands (red and
near-infrared) and regularly used as a measure of ecosystem productivity.

Formally, NDVI is defined as the ratio $(\eta_{\rm NIR}-\eta_{\rm red})/ (\eta_{\rm NIR}+\eta_{\rm red})$,
where $\eta_{\rm NIR}$ and $\eta_{\rm red}$ are the values of the reflectance in the near-infrared and in the
red band, respectively. NDVI always falls between -1 and +1 and can highlight the following features:

<br>

<!-- with vegetation (dark in the red band and bright in the NIR) producing higher values closer to 1, dry land -->
<!-- with nothing growing having an NDVI of zero, open water (bright in the red and dark in the NIR) yielding an -->
<!-- NDVI of -1, and snow / glaciers and clouds producing somewhat negative values between -1 and 0 -->

| Feature | Specs | NDVI range |
| ------------- | --------------- | ----------------- |
| Dense forest canopy, e.g. in the Amazon | dark in red and bright in NIR | close to +1 |
| Dense vegetation | dark in red and bright in NIR | 0.6 -- 0.8 |
| Sparse vegetation (shrub and grassland) | brighter in NIR | 0.2 -- 0.3 |
| Dry land with nothing growing | almost equal reflectance | 0 -- 0.1 |
| Snow, glaciers, clouds | low reflectance in red, even lower NIR reflectance | -0.5 -- 0 |
| Open water | low reflectance in red, almost no NIR reflectance | close to -1 |

<br>

You can find more about the NDVI on
[Wikipedia](https://en.wikipedia.org/wiki/Normalized_difference_vegetation_index) and in
[*5 Things To Know About NDVI*](https://up42.com/blog/5-things-to-know-about-ndvi).




### Contest dataset

What makes the current dataset unique <!-- novel --> is that -- while the mean NDVI has been calculated since
the 1970s -- this dataset is one of the first attempts to map the variance in NDVI over space and time. Both
the mean NDVI and its variance provided here were produced by a global-scale hierarchical GAM (generalized
additive model) over a multi-GB raw dataset, and for a given location and time, the mean and the variance are
formed by data close in time or space.

The Contest dataset contains 5,939,758 points and 53 timesteps. At each point we provide its coordinates
(longitude, latitude, elevation in km) and two variables: mean NDVI ($\mu$) and its variance ($\sigma_2$). The
points are not connected, i.e. they do not form a smooth surface. The 53 time steps are uniformly spread
throughout 2022 from Jan-01 (first step) to Dec-31 (last step).

Data are provided in two formats: VTK and compressed CSV. In the compressed CSV format, in addition to regular
geographic coordinates, for each point we provide two horizontal coordinates ($x_{\rm alb}$, $y_{\rm alb}$) in
the Albers projection. We feel that with the VTK format there is no need to provide these, as you would
typically load a VTK file into ParaView where *longitude*, *latitude*, and *elevation* already map each point
into the 3D space.






<!-- timesteps: day of year (doy) -->



  
<!-- - , every 16 days, either local (available now) or global scale (still in preparation) -->
<!-- - using statistical models to describe spatial and temporal trends in both the mean and variance in NDVI -->
<!-- - local mean and variance in ecosystem productivity as a function of space (maps) and time -->
<!-- - research aim: understand and describe trends in ecosystem productivity, and also whether ecosystems are -->
<!--   becoming more stochastic (unpredictable) -->
<!-- - BC data now: mean and variance in NDVI -->
<!-- - won't be able to fit the global models by the end of August -->









### Downloading the data

Data will be published here in mid-September.

### Loading the data in ParaView

Each data format can be easily loaded into ParaView. When loading from CSV, you have to pass points through
the Table To Points filter.

Please note that when you load points, you will normally not see them (they are infinitely small points!), but
you can render data by:

- using the Point Gaussian representation, or
- using Glyphs, or
- triangulating or projecting data onto a mesh (uniform or not).
Cartesian, polygonal

### Loading the data in Python

To read VTK files in Python, you can use the official [VTK Python library](https://pypi.org/project/vtk), as
well as a number of 3rd-party libraries, e.g. [meshio](https://github.com/nschloe/meshio).

CSV data can be read directly with Pandas:

```py
import pandas as pd
data = pd.read_csv('step000.csv.gz')
print(data.shape)
print(data.columns)
```

and then exported to numpy or xarray.




### References

1. N. Pettorelli, S. Ryan, T. Mueller, N. Bunnefeld, B. Jędrzejewska, M. Lima, K. Kausrud (2011):
   [The Normalized Difference Vegetation Index (NDVI): unforeseen successes in animal ecology](http://dx.doi.org/10.3354/cr00936). Climate
   Research **46**, 15-27




<!-- 1. M. H. Shahnas, W. R. Peltier, Z. Wu, R. Wentzcovitch (2011): [The high pressure electronic spin transition in iron: potential impacts upon mantle mixing](http://dx.doi.org/10.1029/2010JB007965). J. Geophys. Res. **116**, B08205 -->
<!-- 1. M. H. Shahnas, R. N. Pysklywec, and D. A. Yuen (2016): [Spawning superplumes from the midmantle: The impact of spin transitions in the mantle](https://doi.org/10.1002/2016GC006509). Geochemistry, Geophysics, Geosystems **17**, 4051-4063 -->
<!-- 1. M. H. Shahnas, D. A. Yuen, R.N. Pysklywec (2017): [Mid-mantle heterogeneities and iron spin transition in the lower mantle: Implications for mid-mantle slab stagnation](http://dx.doi.org/10.1016/j.epsl.2016.10.052). Earth and Planetary Science Letters **458**, 293–304 -->
<!-- 1. [Researcher's page](http://www.atmosp.physics.utoronto.ca/~shahnas/htmls/Research.htm) at the University of Toronto -->

### Acknowledgments

Data courtesy of {{<a "https://biology.ok.ubc.ca/about/contact/michael-j-noonan" "Michael Noonan">}} and {{<a
"https://github.com/StefanoMezzini" "Stefano Mezzini">}} from the University of British Columbia at Okanagan.



<!-- {{<a "link" "text">}} -->
