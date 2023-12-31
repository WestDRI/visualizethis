---
title: "Tempête d'Halloween sur l'est du Canada"
description: "Jeu de données de tempête"
# date: "2019-02-28"
author: "SFU"
slug: /data/storm
math: true
<!-- menu: -->
<!--   subpage: -->
<!--     identifier: about-subpage-s -->
<!--     parent: about -->
<!--     name: About Subpage -->
<!--     title: About Subpage -->
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

Le jeu de données consiste en une simulation de la tempête et de ses suites entre le 31 octobre et le 2 novembre 2019. Les données volumétriques en 3D ont été préparées sur une maille sphérique à une résolution de $1060\times 1330$ horizontalement sur $16$ niveaux de pression verticale. Les niveaux de pression verticale peuvent être représentés comme élévation. Toutes les variables sont stockées dans des fichiers NetCDF.

Les données atmosphériques de la tempête sont contenues dans les trois variables en 3D dépendantes du temps suivantes :

1. la densité relative des nuage `MPQC(time,pres,rlat,rlon)`,
2. la densité relative de la pluie `MPQR(time,pres,rlat,rlon)`,
3. la densité relative de la glace `QTI1(time,pres,rlat,rlon)`.

dans les trois fichiers `dp2015090100_2019{1031,1101,1102}d.nc` pour le 31 octobre, le 1er novembre et le 2 novembre respectivement. Chaque fichier NetCDF contient 24 intervalles d'une heure.

L'effect de la tempête au sol est décrit par deux variables en 2D dépendantes du temps :

4. la quantité de neige (en mm d'équivalent d'eau) sur le sol `I5(time,rlat,rlon)` dans le fichier `pm2015090100_2019{1031,1101,1102}d.nc`,
5. la pression moyenne au niveau de la mer `PN(time,rlat,rlon)` dans le fichier `dm2015090100_2019{1031,1101,1102}d.nc`.

Enfin, la topographie est fournie par les variables statiques (pas de dépendance au temps) en 2D suivantes :

6. le masque terre-mer `MG(rlat,rlon)` dans le fichier `pm2015090100_00000000p.nc`,
7. l'élévation `ME(rlat,rlon)` (en m) dans le fichier `dm2015090100_00000000p.nc`.

Vous pouvez combiner les deux dernières variables en une seule variable `elevation = MG*ME` avec le filtre calculateur de ParaView.

### Télécharger les données

<!-- Les données seront publiées ici à la mi-septembre. -->

<!-- Instructions pour télécharger les fichiers par le biais de la ligne de commande Bash : -->

Vous pouvez télécharger les fichiers un par un grâce aux liens dans le tableau ci-dessous :

| File   |  Size      |  MD5 checksum |
|--------|------------|---------------|
| [dm2015090100_00000000p.nc](https://nextcloud.computecanada.ca/index.php/s/DpB98GLxGjsLNZt) | 5.1M | 5a4b0af90fc3129ca6dba95942061dae |
| [dm2015090100_20191031d.nc](https://nextcloud.computecanada.ca/index.php/s/9p4nSf8EYwA7zwk) | 46M  | 2b202060bba4d8e3005bd2a95923202b |
| [dm2015090100_20191101d.nc](https://nextcloud.computecanada.ca/index.php/s/eAysq2ctkokNDx2) | 44M  | d17dd34b2d3db207aaace49ac97a8e34 |
| [dm2015090100_20191102d.nc](https://nextcloud.computecanada.ca/index.php/s/Pp5CtZJb2bo74Mn) | 43M  | 69c6f8fa8afb1d626b098336729dbfb9 |
| [dp2015090100_20191031d.nc](https://nextcloud.computecanada.ca/index.php/s/WEM3JCWoMBb7BDj) | 396M | 2fd61a2cba4a1638731871ab844e8e4c |
| [dp2015090100_20191101d.nc](https://nextcloud.computecanada.ca/index.php/s/W3ED2qHqxrCy6WJ) | 330M | d94f015edffd59bf985df223847aab98 |
| [dp2015090100_20191102d.nc](https://nextcloud.computecanada.ca/index.php/s/QCQSfzdwbg5ofdG) | 246M | a7eb5e8b268002fb8708b00e69f65e7b |
| [pm2015090100_00000000p.nc](https://nextcloud.computecanada.ca/index.php/s/82r5ciD9Z7Z4gpk) | 4.1M | fbc4b1e1f987b7392b14a50767489fcc |
| [pm2015090100_20191031d.nc](https://nextcloud.computecanada.ca/index.php/s/n5cpjC4J3PeN9SC) | 23M  | 61b20877923943beedb84d2083d29b34 |
| [pm2015090100_20191101d.nc](https://nextcloud.computecanada.ca/index.php/s/TAg7DL7HzNngtTR) | 27M  | 1ece29fade591f65a9aea4cb22c3c5fe |
| [pm2015090100_20191102d.nc](https://nextcloud.computecanada.ca/index.php/s/9G7Pok7QTE6d3Xd) | 28M  | ca9dee21c598a76275357f4faa7ca1b1 |

ou vous pouvez télécharger tous les fichiers en même temps avec les commandes Bash suivantes :

```
urls=( DpB98GLxGjsLNZt 9p4nSf8EYwA7zwk eAysq2ctkokNDx2 Pp5CtZJb2bo74Mn
       WEM3JCWoMBb7BDj W3ED2qHqxrCy6WJ QCQSfzdwbg5ofdG 82r5ciD9Z7Z4gpk
       n5cpjC4J3PeN9SC TAg7DL7HzNngtTR 9G7Pok7QTE6d3Xd )
names=( dm2015090100_00000000p dm2015090100_20191031d dm2015090100_20191101d dm2015090100_20191102d
        dp2015090100_20191031d dp2015090100_20191101d dp2015090100_20191102d pm2015090100_00000000p
        pm2015090100_20191031d pm2015090100_20191101d pm2015090100_20191102d )
for i in $(seq 0 10); do
    wget https://nextcloud.computecanada.ca/index.php/s/"${urls[$i]}"/download -O "${names[$i]}".nc
done
```

Après avoir téléchargé les fichiers, vous pouvez vérifier que le téléchargement s'est bien passé grâce à la
somme de contrôle md5 fournie.









### Charger les données dans ParaView

ParaView peut lire les fichiers NetCDF directement. Faites attention au menu déroulant de Dimension pour accéder à la bonne catégorie de variables.

Vu que toutes les variables sont sur une maille sphérique, il est peut-être bon d'utiliser une *échelle verticale* et un *biais vertical* autres que les défauts lors de l'importation des données. Alternativement, vous pouvez projeter toute variable sphérique sur une maille cartésienne grâce au filtre programmable avec `Output Type = vtkImageData`. Par exemple :

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

Pour plus d'information sur le filtre programmable de ParaView, vous pouvez regarder {{<a "https://training.westdri.ca/tools/visualization/#programmable" "notre webinaire de janvier 2021.">}}

### Charger les données avec Python

Avec Python, vous pouvez créer un `xarray.Dataset` contenant plusieurs variables, chacune stockée sous la forme d'un tableau NumPy :

```sh
pip install xarray netcdf4
```

```py
import xarray as xr
data = xr.open_dataset("/chemin/du/fichier/dp2015090100_20191031d.nc")
print(data)               # imprime toutes les variables de ce jeu de données
print(data.MPQC.shape)    # tableau NumPy 24x16x1060x1330
print(data.MPQC.values)   # accès aux valeurs
print(data.time)          # intervalles de temps
print(data.lon.values)    # tableau en 2D des longitudes
print(data.lat.values)    # tableau en 2D des latitudes
```

Alternativement, vous pouvez utiliser l'interface netCDF4 classique de Python :

```py
import netCDF4 as nc
all = nc.Dataset("/chemin/du/fichier/dp2015090100_20191031d.nc", "r")
print(all)                            # imprime toutes les variables
print(all.variables['MPQR'][:,:,:])   # tableau NumPy 24x16x1060x1330
print(all.variables['time'][:])       # intervalles de temps
print(all.variables['lon'][:,:])      # tableau en 2D des longitudes
```

<!-- ### Références -->

### Remerciements

Données fournies par {{<a "https://alejandro-diluca.uqam.ca" "Alejandro Di Luca">}} et François Roberge de l'Université du Québec à Montréal. La simulation a été réalisée sur la grappe Narval de l'Alliance.
