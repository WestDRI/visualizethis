---
title: "Halloween storm over Eastern Canada"
description: "Storm dataset"
# date: "2019-02-28"
author: "SFU"
slug: /data/storm
math: true
<!-- menu: -->
<!--   subpage: -->
<!--     identifier: about-subpage-s -->
<!--     parent: about -->
<!--     name: Storm dataset -->
<!--     title: Storm dataset -->
<!--     url: /data/subpage/ -->
<!--     weight: 1 -->
<!--   subpage2: -->
<!--     identifier: about-subpage2-s -->
<!--     parent: about -->
<!--     name: Second About Subpage -->
<!--     title: Second About Subpage -->
<!--     url: /data/subpage2/ -->
<!--     weight: 10 -->
---

<!-- time, pres, rlat, rlon -->
<!--         time = UNLIMITED ; // (24 currently) -->
<!--         pres = 16 ; -->

We provide simulation data for three days from October 31<sup>st</sup> to November 2<sup>nd</sup>, covering
the storm and some of its aftereffects. The 3D volumetric data was prepared on a spherical mesh at resolution
$1060\times 1330$ (horizontal) at 16 vertical pressure levels. For visualization purposes, the pressure levels
can be treated as elevation. All variables are stored in compressed NetCDF files.

The storm atmospheric data are presented with the following three 3D time-dependent variables:

1. the mass mixing ratio of cloud MPQC(time,pres,rlat,rlon),
2. the mass mixing ratio of rain MPQR(time,pres,rlat,rlon), and
3. the mass mixing ratio of ice QTI1(time,pres,rlat,rlon)

inside three files `dp2015090100_2019{1031,1101,1102}d.nc` for Oct-31, Nov-01, and Nov-02, respectively. Each
NetCDF file contains 24 hourly steps.

The effect of the storm at the surface is described by two 2D time-dependent variables:

4. the amount of snow (in water equivalent mm) on the ground I5(time,rlat,rlon) inside
   `pm2015090100_2019{1031,1101,1102}d.nc`, and
5. the mean sea level pressure PN(time,rlat,rlon) inside `dm2015090100_2019{1031,1101,1102}d.nc`.

Finally, the topography is provided by the following 2D static (no time dependency) variables:

6. land-sea mask MG(rlat,rlon) inside `pm2015090100_00000000p.nc`,
7. elevation ME(rlat,rlon) (in meters) inside `dm2015090100_00000000p.nc`.

You can combine the last two variables into a single variable `elevation = MG*ME` with the Calculator Filter
in ParaView.

<!-- in a file `topo.pvd` on a Cartesian mesh -->








<!-- for f in contestData/*; do -->
<!--     ln -s $f ${f/contestData\//} -->
<!-- done -->







### Downloading the data

Data will be published here in mid-September.





### Loading the data in ParaView

ParaView can read NetCDF files natively. Pay attention to the Dimension drop-down menu to navigate to the
right subset of input variables.

Since all variables are on a spherical mesh, you might want to use non-default *vertical scale* and *vertical
bias* when loading data. Alternatively, you can project any spherical variable to a Cartesian mesh using the
Programmable Filter with Output Type = vtkImageData, e.g.

```py
ext = inputs[0].GetExtent()
var = inputs[0].PointData["inputName"]

output.SetOrigin(0., 0., 0.)
output.SetSpacing(1., 1., 1.)
output.SetDimensions(ext[1]-ext[0]+1, ext[3]-ext[2]+1, ext[5]-ext[4]+1)
output.SetExtent(ext)
output.AllocateScalars(vtk.VTK_FLOAT, 1)

vtk_data_array = vtk.util.numpy_support.numpy_to_vtk(var, deep=True, array_type=vtk.VTK_FLOAT)
vtk_data_array.SetNumberOfComponents(1)
vtk_data_array.SetName("outputName")
output.GetPointData().SetScalars(vtk_data_array)
```

To learn more about ParaView's Programmable Filter, watch
{{<a "https://training.westdri.ca/tools/visualization/#programmable" "our January 2021 webinar">}}.


### Loading the data in Python

In Python you can read data into an xarray.Dataset containing multiple variables, each stored as a NumPy
array:

```py
import xarray as xr
data = xr.open_dataset("/path/to/dp2015090100_20191031d.nc")
print(data)               # show all variables inside this dataset
print(data.MPQC.shape)    # this is a 24x16x1060x1330 numpy array
print(data.MPQC.values)   # access the values
print(data.time)          # time steps
print(data.lon.values)    # 2D array of longitudes
print(data.lat.values)    # 2D array of latitudes
```

Alternatively, you can use the traditional netCDF4 Python interface:

```py
import netCDF4 as nc
all = nc.Dataset("/path/to/dp2015090100_20191031d.nc", "r")
print(all)                            # show all variables inside this dataset
print(all.variables['MPQR'][:,:,:])   # this is a 24x16x1060x1330 numpy array
print(all.variables['time'][:])       # time steps
print(all.variables['lon'][:,:])      # 2D array of longitudes
```

### References

<!-- 1. M. H. Shahnas, W. R. Peltier, Z. Wu, R. Wentzcovitch (2011): [The high pressure electronic spin transition in iron: potential impacts upon mantle mixing](http://dx.doi.org/10.1029/2010JB007965). J. Geophys. Res. **116**, B08205 -->
<!-- 1. M. H. Shahnas, R. N. Pysklywec, and D. A. Yuen (2016): [Spawning superplumes from the midmantle: The impact of spin transitions in the mantle](https://doi.org/10.1002/2016GC006509). Geochemistry, Geophysics, Geosystems **17**, 4051-4063 -->
<!-- 1. M. H. Shahnas, D. A. Yuen, R.N. Pysklywec (2017): [Mid-mantle heterogeneities and iron spin transition in the lower mantle: Implications for mid-mantle slab stagnation](http://dx.doi.org/10.1016/j.epsl.2016.10.052). Earth and Planetary Science Letters **458**, 293–304 -->
<!-- 1. [Researcher's page](http://www.atmosp.physics.utoronto.ca/~shahnas/htmls/Research.htm) at the University of Toronto -->

### Acknowledgments

Data courtesy of {{<a "https://alejandro-diluca.uqam.ca" "Alejandro Di Luca">}} and François Roberge from
l'Université du Québec à Montréal. The simulation was conducted using the Alliance's Narval cluster.

<!-- Data storage services provided by Cedar team at Simon Fraser University, Canada. -->



<!-- {{<a "link" "text">}} -->
