# Physique des fluides
Pour comprendre la physique des fluides, on peut :
- Faire des simulation comme le repo avec PINNs

![p_field_lbfgs](https://github.com/user-attachments/assets/9672b411-99b1-4921-835b-f7dbf04671b9)

- Faire des expérimentation comme avec la PIV

![gif_PIV](https://github.com/user-attachments/assets/c487a1e5-c439-4746-ab53-3201ff085d66)

Dans ce repo, nous allons étudier la PIV.

### Penser à faire une introduction afin d'expliquer le fonctionnement des caméra et l'optique.

# Particle Image Velocimetry
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



