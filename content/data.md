---
title: "Data"
# description: ""
# date: "2023-06-30"
aliases: ["about-us","about-hugo","contact"]
author: "SFU"
math: true
menu:
  subpage:
    identifier: about-subpage
    parent: about
    name: Storm dataset
    title: Storm dataset
    url: /data/storm/
    weight: 1
  subpage2:
    identifier: about-subpage2
    parent: about
    name: NDVI dataset
    title: NDVI dataset
    url: /data/ndvi/
    weight: 2
---

*Depending on which dataset you work on, please read one of the two sections above.*












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




<!-- <\!-- storage 416800580*250/1024**3 = 97.04GB uncompressed -\-> -->
<!-- <\!-- After you have downloaded some or all .tgz files you can check against the provided md5 -\-> -->
<!-- <\!-- checksum to see if the download succeeded. -\-> -->

<!-- {{<a "link" "text">}} -->
