---
title: "Data"
description: "Hugo, the world’s fastest framework for building websites"
# date: "2023-06-30"
aliases: ["about-us","about-hugo","contact"]
author: "SFU"
math: true
# menu:
#   subpage:
#     identifier: about-subpage
#     parent: about
#     name: About Subpage
#     title: About Subpage
#     url: /data/subpage/
#     weight: 1
#   subpage2:
#     identifier: about-subpage2
#     parent: about
#     name: Second About Subpage
#     title: Second About Subpage
#     url: /data/subpage2/
#     weight: 10
---

*Depending on which dataset you work on, please read one of the two sections below.*

<br>

# Halloween storm over Eastern Canada

<!-- ➽ grid numerical resolution, axes -->

<!-- time, pres, rlat, rlon -->

<!--         time = UNLIMITED ; // (24 currently) -->
<!--         pres = 16 ; -->




3D volumetric data are provided on a spherical mesh at resolution $1060\times 1330$ (horizontal) at 16
vertical pressure levels. For visualization purposes, the pressure levels can be treated as elevation. All
variables are stored in compressed NetCDF files.

The storm atmospheric data are described with the following 3D time-dependent variables:

1. the mass mixing ratio of cloud MPQC(time,pres,rlat,rlon) ,
2. the mass mixing ratio of rain MPQR(time,pres,rlat,rlon), and
3. the mass mixing ratio of ice QTI1(time,pres,rlat,rlon).

inside the three files `dp2015090100_2019{1031,1101,1102}d.nc`, for October 31<sup>st</sup>, November
1<sup>st</sup>, and November 2<sup>nd</sup>, respectively. Each NetCDF file contains 24 hourly steps.

There are also 2D (surface-level) time-dependent variables:

4. the amount of snow (in water equivalent mm) I5(time,rlat,rlon) inside
   `pm2015090100_2019{1031,1101,1102}d.nc`, and
5. the mean sea level pressure PN(time,rlat,rlon) inside `dm2015090100_2019{1031,1101,1102}d.nc`.

Finally, the topography is described by the following 2D static (no time dependency) variables:

1. land-sea mask MG(rlat,rlon) inside `pm2015090100_00000000p.nc`,
2. elevation ME(rlat,rlon) (in meters) inside `dm2015090100_00000000p.nc`,

➽ You can combine these two variables into a single variable `elevation = MG*ME` in a file `topo.pvd` on a
Cartesian mesh.





<!-- for f in contestData/*; do -->
<!--     ln -s $f ${f/contestData\//} -->
<!-- done -->







### Downloading the data

### Loading the data in ParaView

### Loading the data in Python

### References

### Acknowledgments

<br>

# Normalized difference vegetation index

Description.

### Downloading the data

### Loading the data in ParaView

### Loading the data in Python

### References

### Acknowledgments








<!-- The dataset consists of a time series (251 steps) of 3D scalar fields on a spherical 180x201x360 grid covering 500 Myr -->
<!-- of geological time. Each time step is 2 Myrs, and the fields are: -->

<!-- - temperature [degrees K], -->
<!-- - three Cartesian velocity components [m/s], -->
<!-- - thermal conductivity anomaly [Watt/m/K], -->
<!-- - thermal expansivity anomaly [1/K], -->
<!-- - temperature anomaly [degrees K], and -->
<!-- - spin transition-induced density anomaly [kg/m^3]. -->

<!-- The simulation was performed in double precision, however, to reduce downloading time, we provide the data in single -->
<!-- precision. Each file was saved in a NetCDF Climate and Forecast (CF) convention format, with each 3D scalar field being -->
<!-- a function of latitude [degrees north], longitude [degrees east], and radius [km]. The model's inner and outer radii are -->
<!-- 3485 km and 6371 km, respectively. -->




<!-- The spin transition-induced density anomaly is formally defined at the top of the second column of page 11 in Shahnas et -->
<!-- al. (2011) -- paper [1] below. Without going into complex physics, you can think of it as the local anomaly (compared to -->
<!-- the laterally-averaged value) of the density with the spin transition taken into account. -->

<!-- All four anomalies above (thermal conductivity, thermal expansivity, temperature, and spin transition-induced density) -->
<!-- were computed relative to the laterally-averaged values of the respective variables and consequently will be positive in -->
<!-- some regions and negative in others. -->





<!-- #### References -->

<!-- 1. M. H. Shahnas, W. R. Peltier, Z. Wu, R. Wentzcovitch (2011): [The high pressure electronic spin transition in iron: potential impacts upon mantle mixing](http://dx.doi.org/10.1029/2010JB007965). J. Geophys. Res. **116**, B08205 -->
<!-- 1. M. H. Shahnas, R. N. Pysklywec, and D. A. Yuen (2016): [Spawning superplumes from the midmantle: The impact of spin transitions in the mantle](https://doi.org/10.1002/2016GC006509). Geochemistry, Geophysics, Geosystems **17**, 4051-4063 -->
<!-- 1. M. H. Shahnas, D. A. Yuen, R.N. Pysklywec (2017): [Mid-mantle heterogeneities and iron spin transition in the lower mantle: Implications for mid-mantle slab stagnation](http://dx.doi.org/10.1016/j.epsl.2016.10.052). Earth and Planetary Science Letters **458**, 293–304 -->
<!-- 1. [Researcher's page](http://www.atmosp.physics.utoronto.ca/~shahnas/htmls/Research.htm) at the University of Toronto -->











<!-- # Accessing the Dataset -->

<!-- The 251 steps are grouped into 25 gzipped tar files `mantle{01..25}.tgz` -- see the table below. To start working on the -->
<!-- project, you can download only `mantle01.tgz`, but for a production-quality animation you will need all 25 files. -->

<!-- <br> -->

<!-- | File   |  Timestep range   |    Size      |  MD5 checksum | -->
<!-- |----------|-------------|------|----------| -->
<!-- | [mantle01.tgz](https://nextcloud.computecanada.ca/index.php/s/edS6be3sk8oQ58N/download) | 001..010 | 3.2GB | 6aa435a58ac9487f48291c363eccde6e | -->
<!-- | [mantle02.tgz](https://nextcloud.computecanada.ca/index.php/s/infBBW2Rc9TJwf7/download) | 011..020 | 3.2GB | dbc46f9cffb665a5bccfc95a4a864079 | -->
<!-- | [mantle03.tgz](https://nextcloud.computecanada.ca/index.php/s/76Esj3yDP9EiaGc/download) | 021..030 | 3.2GB | cffe250d3388bbd317a44eda88ccf0df | -->
<!-- | [mantle04.tgz](https://nextcloud.computecanada.ca/index.php/s/AZmt47d48prCZZF/download) | 031..040 | 3.2GB | 84979f5daf4470eb81b9cbdb0c981fa6 | -->
<!-- | [mantle05.tgz](https://nextcloud.computecanada.ca/index.php/s/9fZ4A7ENGR6sQrc/download) | 041..050 | 3.2GB | 4dce2df4da2a7ef4b5b174b5a49af4d0 | -->
<!-- | [mantle06.tgz](https://nextcloud.computecanada.ca/index.php/s/B8HC3H4oqwcsWB3/download) | 051..060 | 3.2GB | 97bd7e2ae99b49ac1732ced3b20ba77d | -->
<!-- | [mantle07.tgz](https://nextcloud.computecanada.ca/index.php/s/t3zLJWWeirR5zmG/download) | 061..070 | 3.2GB | 5a4fab7180456d99fbb19175a05ea3b1 | -->
<!-- | [mantle08.tgz](https://nextcloud.computecanada.ca/index.php/s/YmkYgxM7xxrNAwj/download) | 071..080 | 3.2GB | 4caaea5992f66e391535e079575e29f6 | -->
<!-- | [mantle09.tgz](https://nextcloud.computecanada.ca/index.php/s/rMma6W9MBtQH9LX/download) | 081..090 | 3.2GB | e282bbd474529a858ddddb627204f88f | -->
<!-- | [mantle10.tgz](https://nextcloud.computecanada.ca/index.php/s/MzcZBCaxaojTZJx/download) | 091..100 | 3.2GB | 1899ecec0756540957f2d18094c39948 | -->
<!-- | [mantle11.tgz](https://nextcloud.computecanada.ca/index.php/s/dfP6NXHmekQQrHR/download) | 101..110 | 3.2GB | daaac28e6989f68bd4bff4117a2645d5 | -->
<!-- | [mantle12.tgz](https://nextcloud.computecanada.ca/index.php/s/2GnLRgPi8W2Dt5p/download) | 111..120 | 3.2GB | e335c9fed2448ca7bfc24a01a78759e6 | -->
<!-- | [mantle13.tgz](https://nextcloud.computecanada.ca/index.php/s/MqtoESg2d9DsF2P/download) | 121..130 | 3.2GB | 01a85d3402c89d964b9158ca6bc6665d | -->
<!-- | [mantle14.tgz](https://nextcloud.computecanada.ca/index.php/s/ysGoJK6B3pLYaDB/download) | 131..140 | 3.2GB | c1195cd3ba48b17874507f5f03ed0dd5 | -->
<!-- | [mantle15.tgz](https://nextcloud.computecanada.ca/index.php/s/Ae32XwCpt7bHo9D/download) | 141..150 | 3.2GB | 8c25f1996c5eaf5ac0a50114170cd436 | -->
<!-- | [mantle16.tgz](https://nextcloud.computecanada.ca/index.php/s/AysWSPnxFS6e5B2/download) | 151..160 | 3.2GB | 5659e592a8dbbc7d6d3f6ebc10a1e3c0 | -->
<!-- | [mantle17.tgz](https://nextcloud.computecanada.ca/index.php/s/4NcnJkPYWpkXrmb/download) | 161..170 | 3.2GB | e59fccb6cabb87e232f30a6c7ce2cbbb | -->
<!-- | [mantle18.tgz](https://nextcloud.computecanada.ca/index.php/s/mBRfrnfEEEaKJ9m/download) | 171..180 | 3.2GB | 38a0007cf2676e64eac91ec9c9f3034c | -->
<!-- | [mantle19.tgz](https://nextcloud.computecanada.ca/index.php/s/J63KxeCppK8ssGc/download) | 181..190 | 3.2GB | 8ee1cf466264303d5822aede27477151 | -->
<!-- | [mantle20.tgz](https://nextcloud.computecanada.ca/index.php/s/NeqnHBNPWx4PRwd/download) | 191..200 | 3.2GB | 9c6163d659ebac7d9d8f72b6592a3994 | -->
<!-- | [mantle21.tgz](https://nextcloud.computecanada.ca/index.php/s/JdzZQCKiHaRfL9L/download) | 201..210 | 3.2GB | fabba593dd5274d98aa9c48d5fea701a | -->
<!-- | [mantle22.tgz](https://nextcloud.computecanada.ca/index.php/s/DXnWtA5fymHBsxA/download) | 211..220 | 3.2GB | 8e4ce089409629c7f5122c1c6f19d6db | -->
<!-- | [mantle23.tgz](https://nextcloud.computecanada.ca/index.php/s/HzgtF42Pf9AnxGm/download) | 221..230 | 3.2GB | a78d3fd385baf8c1ec78eda7b69a2394 | -->
<!-- | [mantle24.tgz](https://nextcloud.computecanada.ca/index.php/s/yy8FASeC8Dm54Sy/download) | 231..240 | 3.2GB | d551765802f1aa9b399763beadf8f44e | -->
<!-- | [mantle25.tgz](https://nextcloud.computecanada.ca/index.php/s/TC8QekmjokmBkWA/download) | 241..251 | 3.5GB | eff0d9d0b62522559a53a4eb11aea579 | -->

<!-- <br> -->

<!-- To download all files in bash command line: -->

<!-- ``` -->
<!-- urls=( edS6be3sk8oQ58N infBBW2Rc9TJwf7 76Esj3yDP9EiaGc AZmt47d48prCZZF -->
<!--        9fZ4A7ENGR6sQrc B8HC3H4oqwcsWB3 t3zLJWWeirR5zmG YmkYgxM7xxrNAwj -->
<!--        rMma6W9MBtQH9LX MzcZBCaxaojTZJx dfP6NXHmekQQrHR 2GnLRgPi8W2Dt5p -->
<!--        MqtoESg2d9DsF2P ysGoJK6B3pLYaDB Ae32XwCpt7bHo9D AysWSPnxFS6e5B2 -->
<!--        4NcnJkPYWpkXrmb mBRfrnfEEEaKJ9m J63KxeCppK8ssGc NeqnHBNPWx4PRwd -->
<!--        JdzZQCKiHaRfL9L DXnWtA5fymHBsxA HzgtF42Pf9AnxGm yy8FASeC8Dm54Sy -->
<!--        TC8QekmjokmBkWA ) -->
<!-- for i in $(seq 0 24); do -->
<!--     wget https://nextcloud.computecanada.ca/index.php/s/"${urls[$i]}"/download -O mantle"$(printf "%02d\n" $((i+1)))".tgz -->
<!-- done -->
<!-- ``` -->



<!-- <\!-- storage 416800580*250/1024**3 = 97.04GB uncompressed -\-> -->
<!-- <\!-- After you have downloaded some or all .tgz files you can check against the provided md5 -\-> -->
<!-- <\!-- checksum to see if the download succeeded. -\-> -->






<!-- # Loading the Data in ParaView -->

<!-- The dataset can be read directly in ParaView (tested in 5.5 and 5.8), both as single files and as a time series. -->

<!-- The 3D velocity vector can be assembled via the Calculator filter -->

<!-- ``` -->
<!-- velocity = (iHat*vx + jHat*vy + kHat*vz) * 1e9 -->
<!-- ``` -->

<!-- where we recommend to change the scaling to [nm/s] to avoid dealing with very small numbers. -->






<!-- # Loading the Data in Python -->

<!-- In Python you can read each time step into an `xarray.Dataset` containing multiple variables: -->

<!-- ~~~ -->
<!-- import xarray as xr -->
<!-- data = xr.open_dataset('spherical001.nc') -->
<!-- print(data)                         # show all variables inside this dataset -->
<!-- print(data.temperature.values)      # this is a 180x201x360 numpy array -->
<!-- print(data.r)                       # radial discretization -->
<!-- ~~~ -->

<!-- Alternatively, you can use the traditional netCDF4 Python interface: -->

<!-- ~~~ -->
<!-- import netCDF4 as nc -->
<!-- all = nc.Dataset('spherical001.nc', 'r') -->
<!-- print(all)                                   # show all variables inside this dataset -->
<!-- print(all.variables['temperature'][:,:,:])   # this is a 180x201x360 numpy array -->
<!-- print(all.variables['r'][:])                 # radial discretization -->
<!-- ~~~ -->

<!-- # Acknowledgments -->

<!-- Data courtesy of the Pysklywec Lab (Russell Pysklywec and Hosein Shahnas) at the University of Toronto. The simulation -->
<!-- was conducted using Compute Canada's Niagara cluster. -->

<!-- <\!-- Data storage services provided by Cedar team at Simon Fraser University, Canada. -\-> -->
