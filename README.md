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

https://youtu.be/wmtyb8EL8wI?si=dltqKlWGLb9H6NYn -> GUI AVEC CODE MODIFIABLE 

- TracTrac :

https://github.com/jorishey1234/tractrac

https://perso.univ-rennes1.fr/joris.heyman/PDF/tractrac_final.pdf -> Article

- trackpy

http://soft-matter.github.io/trackpy/v0.6.4/tutorial/walkthrough.html

### MATLAB

- PIVLab

https://fr.mathworks.com/matlabcentral/fileexchange/27659-pivlab-particle-image-velocimetry-piv-tool-with-gui

https://pivlab.blogspot.com/ -> Beaucoup de documentation et tutos

- Openopticalflow_piv

https://openresearchsoftware.metajnl.com/articles/10.5334/jors.326 -> article / hybride crosscorr et optical flow

- OpenPIV

## Ressources pour l'apprentissage
https://youtu.be/OZ6AKMA7zFY?si=AXmaHDIn1C-699RG
https://youtu.be/sz5YCi6Cz20?si=Fq9buvXCkTVgUrec

Au lieu d'afficher image par image, on peut flouter un peu les images et faire une moyenne sur par exemple 5 images afin d'avoir le tracé des particles, ce qui nous permet d'observer les déplacements

![piv_average_frame](https://github.com/user-attachments/assets/16aa8f2e-0415-450f-a9dc-3c435272fbb7)

Ensuite faire la corrélation croisé afin d'obtenir les vecteurs de vitesse

![img_velocity_vector](https://github.com/user-attachments/assets/4e4ac5c4-7e90-40bc-8d62-2ac4ed3a7167)


![IMG_0370](https://github.com/user-attachments/assets/f72595e2-c657-49b2-a9a1-a51bf5e6e7f2)
![IMG_0369](https://github.com/user-attachments/assets/f174935c-927b-49de-af1a-34f76f31dde4)
![IMG_0368](https://github.com/user-attachments/assets/ce4111d5-3e08-4215-826c-dff390a63878)
![IMG_0365](https://github.com/user-attachments/assets/3b2ffac6-8f35-4e76-ae9a-4c8540e2ca3b)
![IMG_0363](https://github.com/user-attachments/assets/6cd85a7b-65ae-41fb-a91b-0bda3a3fb180)
![IMG_0362](https://github.com/user-attachments/assets/9c5927d5-1ac4-46b4-ad0c-29462953476d)
![IMG_0364](https://github.com/user-attachments/assets/06b6f4fa-4bcd-4afa-b041-4a19f7e59316)
![IMG_0361](https://github.com/user-attachments/assets/eb54ae65-fe88-4be0-870e-2235dc1eed92)
![IMG_0358](https://github.com/user-attachments/assets/2a84fcec-85a1-4740-8671-420b4d97d3c1)
![IMG_0366](https://github.com/user-attachments/assets/503bfde9-d4e9-417c-a8e6-56436d09a931)
![IMG_0360](https://github.com/user-attachments/assets/85d04544-61ec-43f3-86b1-d5269e2a1a4d)
![IMG_0357](https://github.com/user-attachments/assets/658151eb-ef56-4768-9d16-611092c351e7)
![IMG_0356](https://github.com/user-attachments/assets/a212adbb-1489-44fc-88d0-4f611c2b8ece)

# PIV traditionnelle, utilisation de la cross correlation

![piv1](https://github.com/user-attachments/assets/909ca20a-d888-43e6-8d11-d83e9a4ad528)
![piv2](https://github.com/user-attachments/assets/f1d5812a-7526-437e-9bd5-50f3eaaa8d5e)
![piv3](https://github.com/user-attachments/assets/a5bfb461-17f8-4ec5-b13c-a9ed33d793de)

# Introduction au flow optique avec l'algorithme de Lucas-Kanade

![of1](https://github.com/user-attachments/assets/80836053-1b67-4601-96e2-c11aee11396d)
![of2](https://github.com/user-attachments/assets/46f24d33-b9a4-45de-9e5c-5ef11511deca)
![of3](https://github.com/user-attachments/assets/092fb70a-46e2-4536-9ab5-67aef597d599)

