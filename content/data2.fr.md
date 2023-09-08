---
title: "Indice de végétation par différence normalisée (IVDN)"
description: "Jeu de données IVDN"
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

Ce jeu de données est une compilation de données d'IVDN (indice de végétation par différence normalisée) disponibles gratuitement pour la Colombie Britannique. L'IVDN est une mesure de verdeur calculée par spectrométrie sur deux bandes (rouge et proche de l'infrarouge). Il est régulièrement utilisé pour mesurer la productivité d'un écosystème.

L'IVDN est défini par le ratio $(\eta_{\rm NIR}-\eta_{\rm red})/ (\eta_{\rm NIR}+\eta_{\rm red})$, où $\eta_{\rm NIR}$ et $\eta_{\rm red}$ sont les valeurs de réflectance dans le rouge et proche de l'infrarouge respectivement. L'IVDN est toujours compris entre $-1$ et $+1$ et peut mettre en évidence les habitats suivantes :

<br>

| Habitat | Caractéristique | gamme IVDN |
| ------------- | --------------- | ----------------- |
| Canopée de forêt dense, par ex. en Amazonie | sombre dans le rouge et brillant dans le NIR | proche de +1 |
| Végétation dense | sombre dans le rouge et brillant dans le NIR | 0.6 -- 0.8 |
| Végétation éparse (arbustes et prairie) | plus brillant dans le NIR | 0.2 -- 0.3 |
| Terre sèche dépourvue de végétation | réflectance presque égale dans le rouge et le NIR | 0 -- 0.1 |
| Neige, glaciers, nuages | réflectance faible dans le rouge et encore plus faible dans le NIR | -0.5 -- 0 |
| Masse d'eau | réflectance faible dans le rouge et presque nulle dans le NIR | proche de -1 |

<br>

Pour plus d'information sur l'IVDN, vous pouvez consulter [la page Wikipedia](https://en.wikipedia.org/wiki/Normalized_difference_vegetation_index) et l'article [*5 Things To Know About NDVI*](https://up42.com/blog/5-things-to-know-about-ndvi).

### Description des données

Les valeurs moyennes d'IVDN ont été calculées depuis les années 70, mais ce qui rend ce jeu de données unique est qu'il est l'un des premiers à essayer de représenter la variance d'IVDN au cours du temps et à travers l'espace. La moyenne d'IVDN et sa variance proviennent d'un MAG (modèĺe additif généralisé) à l'échelle de la Colombie Britannique sur un jeu de données de base de plusieurs GB.

Le jeu de données contient 5 935 736 points et 53 intervalles de temps. Les points ne sont pas connectés (c'est à dire qu'ils ne forment pas une surface lisse. Les 53 intervalles de temps sont répartis uniformément du 1er janvier (premier intervalle) au 31 décembre (dernier intervalle) 2022.

Les données sont fournies sous deux formats : VTK et CSV compressé. Chaque format contient toutes les données (vous n'avez besoin que du format de votre choix).

1. Dans les fichiers VTK, chaque point est positionné dans l'espace tridimensionnel grâce à des coordonnées cartésiennes ($x$, $y$, $z$). Trois variables sont associées à chaque point : l'IVDN moyen ($\mu$), sa variance ($\sigma_2$) et l'*élévation* en km.

2. Dans le format CSV compressé, chaque ligne correspond à un point de données avec *longitude*, *latitude* et *élévation* en km, deux coordonnées horizontales ($x_{\rm alb}$, $y_{\rm alb}$) dans le cône de projection à aire égale d'Albers, l'IVDN moyen ($\mu$) et sa variance ($\sigma_2$).

### Télécharger les données

Les données seront publiées ici à la mi-septembre.

### Charger les données dans ParaView

Tous les formats de fichiers peuvent être lus facilement par ParaView. Pour les fichiers CSV, vous devez transformer les points avec le filtre `Table To Points`.

Veuillez noter que vous ne verrez pas les points après les avoir lus car ils sont extrêmement petits. Cependant, vous pouvez représenter les données :

- en utilisant une représentation gaussienne des points, ou
- en utilisant des Glyphes, ou
- en triangulant ou en projetant les données sur une maille (uniforme ou pas).

Vous pouvez facilement manipuler les données à l'intérieur de ParaView avec le filtre programmable. Par exemple, après avoir lu les données à partir du format CSV compressé, vous pouvez utiliser un nouveau filtre avec `Output Type = Same as Input` et le code Python suivant à l'intérieur du filtre :

```py
import numpy as np
npoints = inputs[0].Points.shape[0]
lon = np.radians(inputs[0].Points[:,0])
lat = np.radians(inputs[0].Points[:,1])
points = vtk.vtkPoints()
radius = 6371
for i in range(npoints):
    r = radius + inputs[0].Points[i,2]
    x = r * np.cos(lon[i]) * np.cos(lat[i])
    y = r * np.sin(lon[i]) * np.cos(lat[i])
    z = r * np.sin(lat[i])
    points.InsertNextPoint(x,y,z)

output.SetPoints(points)
output.PointData.append(inputs[0].PointData['mu'], 'mu')
output.PointData.append(inputs[0].PointData['sigma2'], 'sigma2')
```

Ceci va créer un nouveau jeu de points dans un espace en 3D à partir de leur *longitude*, *latitude* et *élévation*. Pour plus d'information sur le filtre programmable de ParaView, vous pouvez regarder {{<a "https://training.westdri.ca/tools/visualization/#programmable" "notre webinaire de janvier 2021.">}}

### Carte des couleurs IVDN

Si vous le souhaitez, vous pouvez utiliser [la carte des couleurs IVDN blue-marron-vert](../../../ndvi.json.gz) qui va des valeurs $-1$ à $+1$.

### Charger les données avec Python

Pour lire des fichiers VTK avec Python, vous pouvez utiliser [la librairie officielle VTK](https://pypi.org/project/vtk) ou d'autres librairies comme par exemple [meshio](https://github.com/nschloe/meshio).

Les fichiers compressés de type CSV peuvent être lus directement avec Pandas :

```py
import pandas as pd
data = pd.read_csv('step000.csv.gz')
print(data.shape)
print(data.columns)
```

puis exportés vers NumPy ou xarray.

### Référence

N. Pettorelli, S. Ryan, T. Mueller, N. Bunnefeld, B. Jędrzejewska, M. Lima, K. Kausrud (2011):
   [The Normalized Difference Vegetation Index (NDVI): unforeseen successes in animal ecology](http://dx.doi.org/10.3354/cr00936). Climate
   Research **46**, 15-27.

### Remerciements

Données fournies par {{<a "https://biology.ok.ubc.ca/about/contact/michael-j-noonan" "Michael Noonan">}} et {{<a
"https://github.com/StefanoMezzini" "Stefano Mezzini">}} de l'Université de la Colombie-Britannique en Okanagan.
