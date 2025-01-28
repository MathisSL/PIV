# Physique des fluides
Pour comprendre la physique des fluides, on peut :
- Faire des simulation comme le repo avec PINNs

![p_field_lbfgs](https://github.com/user-attachments/assets/9672b411-99b1-4921-835b-f7dbf04671b9)

- Faire des expérimentation comme avec la PIV

![gif_PIV](https://github.com/user-attachments/assets/c487a1e5-c439-4746-ab53-3201ff085d66)

Dans ce repo, nous allons étudier la PIV.

### Penser à faire une introduction afin d'expliquer le fonctionnement des caméra et l'optique.

# Particle Image Velocimetry
## Introduction
La PIV (Particle Image Velocimetry) est une méthode utilisée en mécanique des fluides pour
mesurer les champs de vitesse dans les écoulements (air, eau, etc.).
De petites particules (souvent des gouttelettes ou des particules solides microniques) sont in-
troduites dans le fluide. Ces particules doivent être suffisamment petites et légères pour suivre
fidèlement l’écoulement, mais suffisamment grandes pour être capturées par la caméra.
Un laser éclaire une section du fluide, où les particules sont présentes.
Une ou plusieurs caméras haute vitesse sont utilisées pour capturer des paires d’images des
particules à des intervalles de temps très courts (de l’ordre de quelques microsecondes à millise-
condes). Ces images montrent les positions successives des particules dans le champ d’écoulement.

![image_piv](https://github.com/user-attachments/assets/72d5fa94-7ea2-4ef6-af46-3937ea04009a)

Chaque paire d’images est divisée en petites zones appelées "interrogation windows". Une
technique de corrélation croisée est utilisée pour comparer les positions des particules entre les
deux images dans ces fenêtres, permettant de déterminer leur déplacement entre les deux prises.
Le déplacement est ensuite divisé par l’intervalle de temps entre les deux images pour obtenir la
vitesse locale du fluide dans la zone considérée.

![piv_overveiw](https://github.com/user-attachments/assets/44e26f13-97a4-4e79-85af-1a4a6fb36ada)

Construction du champ de vitesse :
Une fois que les déplacements des particules ont été calculés pour l’ensemble des fenêtres, un
champ de vitesse est construit, montrant la distribution des vitesses dans le fluide sur la zone
étudiée.

![résultats_piv](https://github.com/user-attachments/assets/d7327d57-f98e-477a-b164-f469fdd515d5)

Cependant, elle présente plusieurs limitations dans ses méthodes traditionnelles, affectant la
précision et la résolution des mesures.

## Problèmes rencontrés
— 1. Résolution spatiale limitée La PIV repose sur l’ensemencement du fluide avec des
particules et l’acquisition d’images de ces particules pour calculer les vecteurs de vitesse.
La résolution spatiale est limitée par la taille des particules et la capacité du système op-
tique à distinguer des distances réduites. Cela peut poser problème dans les écoulements
avec des gradients de vitesse importants, en particulier près des parois.

— 2. Sensibilité au mouvement tridimensionnel La méthode PIV traditionnelle est sou-
vent limitée à des mesures en deux dimensions. Si l’écoulement présente une composante
tridimensionnelle importante, comme dans les écoulements turbulents ou complexes, les
résultats peuvent être incomplets ou inexacts. Pour résoudre ce problème, des méthodes
comme la tomographie PIV (Tomo-PIV) ou la PIV stéréoscopique (Stereo-PIV) sont né-
cessaires, bien qu’elles augmentent la complexité.

![Tomo_piv_image](https://github.com/user-attachments/assets/8dd30cb4-408b-446e-9518-ffc7fcc8cdf6)


— 3. Choix des particules et conditions d’ensemencement Le choix des particules
est crucial pour la qualité des mesures. Si les particules sont trop lourdes ou trop légères,
elles ne suivront pas correctement le flux du fluide, entraînant des erreurs. Un mauvais
ensemencement peut également conduire à des zones non couvertes (absence de particules)
ou à une mauvaise corrélation entre les images.

— 4. Effets des réflexions et de la lumière parasite La PIV dépend d’une bonne visua-
lisation des particules dans le fluide. Des réflexions parasites ou une mauvaise illumination
peuvent dégrader la qualité des images et introduire du bruit, ce qui complique la corré-
lation entre les images.

— 5. Limitation temporelle (mesures instantanées) Les mesures de vitesse obtenues
par la PIV sont des instantanés des champs de vitesse. Pour capturer les variations tem-
porelles dans des écoulements transitoires ou turbulents, il faut acquérir des images très
rapidement, ce qui peut devenir coûteux avec des systèmes de caméras à haute vitesse et
des lasers pulsés.


— 6. Corrélation croisée et erreurs de calcul La précision des vecteurs de vitesse dépend
de l’algorithme de corrélation croisée utilisé pour suivre les déplacements des particules
entre deux images. Des erreurs peuvent apparaître si les particules sont trop dispersées
ou si le champ de vitesse présente des gradients importants. Des méthodes comme la cor-
rélation adaptative peuvent réduire ces erreurs, mais elles augmentent la complexité du
traitement.

— 7. Post-traitement intensif Le traitement des images pour extraire les champs de vi-
tesse est gourmand en ressources et en temps. L’analyse des données PIV, en particulier
pour des mesures 3D ou sur des échantillons temporels longs, nécessite souvent des al-
gorithmes complexes et des ordinateurs puissants pour traiter les grandes quantités de
données.

— 8. Fluctuations de température et propriétés optiques du fluide Les variations
de température ou de concentration des particules dans le fluide peuvent modifier les pro-
priétés optiques du milieu (réfraction, absorption), ce qui peut introduire des distorsions
dans les images.

### Conclusion
Les méthodes PIV traditionnelles, bien que puissantes pour l’analyse des écoule-
ments fluides, présentent des limitations importantes en termes de résolution spatiale, de sen-
sibilité aux écoulements tridimensionnels et de précision des mesures dans des environnements
complexes. Des techniques avancées telles que la Tomo-PIV et la Stereo-PIV, ainsi que l’utilisa-
tion de fenêtres adaptatives et d’algorithmes de corrélation améliorés, permettent de surmonter
certains de ces problèmes, mais nécessitent un équipement plus sophistiqué et un traitement
intensif des données.

## Outils pour la PIV trouvé après recherches
### Python
- OpenPIV : -> Permet d'utiliser le GPU pour calculs plus rapide

https://openpiv.readthedocs.io/en/latest/src/piv_basics.html

https://github.com/OpenPIV/openpiv-python-gpu

- tractrac :

https://github.com/jorishey1234/tractrac

https://perso.univ-rennes1.fr/joris.heyman/PDF/tractrac_final.pdf -> Article

- trackpy

http://soft-matter.github.io/trackpy/v0.6.4/tutorial/walkthrough.html

### MATLAB

- PIVLab

https://fr.mathworks.com/matlabcentral/fileexchange/27659-pivlab-particle-image-velocimetry-piv-tool-with-gui

https://pivlab.blogspot.com/ -> Beaucoup de documentation et tutos

- OpenPIV

## Ressources pour l'apprentissage
https://youtu.be/OZ6AKMA7zFY?si=AXmaHDIn1C-699RG
https://youtu.be/sz5YCi6Cz20?si=Fq9buvXCkTVgUrec








