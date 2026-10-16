# Estimation du volume de citrons par imagerie

Estimation du volume d'un citron à partir d'une photo de sa coupe transversale, par la méthode des disques (intégration numérique d'un solide de révolution), et comparaison avec un réseau de neurones.

## Données

- 100 citrons, dont le volume exact a été mesuré un par un (en les immergeant dans l'eau et en calculant le volume d'eau deplacé).
- Une photo par citron, normalisée, donnant une coupe transversale.
- Volumes et références des images regroupés dans une base de données .

## Méthode 1 : méthode des disques

On suppose que le citron est un solide de révolution autour d'un axe. Si $r(x)$ est la distance entre l'axe et le bord au point d'abscisse $x$ de l'axe, son volume est

$$V = \pi \int_a^b r(x)^2 \, dx .$$

Il est approché par une somme de Riemann :

1. Tracer l'axe de révolution sur la coupe.
2. Subdiviser l'axe avec un pas constant très petit $\Delta x$.
3. À chaque pas $x_i$, tracer la droite perpendiculaire à l'axe jusqu'au bord du citron, et mesurer sa longueur $r_i$ .
4. Sommer les volumes des cylindres de rayon $r_i$ et de hauteur $\Delta x$ :

$$V \approx \sum_i \pi\, r_i^2\, \Delta x .$$

Le pas $\Delta x$ vaut [À COMPLÉTER] et l'échelle pixels → centimètres [À COMPLÉTER].

## Méthode 2 : réseau de neurones

Un réseau est entraîné sur les citrons dont le volume est connu, puis prédit le volume des autres.

La méthode géométrique est plus proche de la réalité : la base de données (256 citrons) est trop petite pour que le réseau généralise bien, alors que la méthode des disques exploite directement la forme.
