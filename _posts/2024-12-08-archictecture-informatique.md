---
layout: post
title: archictecture d'informatique
date: 2024-12-08 15:11:00
description: les bases, système logique, algèbre binaire, fonctions logiques, table vérité, bascules, nombres signés
tags: archi
categories: sample-posts
---
## **Les bases**
  Pour comprendre les bases il faut imaginer que la base designe le nombre de possibilités pour chaque position dans l'écriture des nombres. Par exemple, dans la base 10, pour une seule position, on a 10 possibilités: 0, 1, 2, 3, 4, 5, 6, 7, 8 et 9. Par convention, à partir de la droite on va prendre le premier chiffre et multiplier par sa base exposé son poids. C'est quoi le poids? Bon, le poids on peut dire que c'est ”l'importante” de ce numéro. Le chiffre plus à droite est celui qui a le poids le plus petit, donc il sera 0. Celui à côté a le poids de 1, jusqu'à N-1 avec N le nombre de chiffres qui compose notre nombre.

  Analysons l'exemple suivant avec le numéro $54$ dans la base $10$:
  
  $$
    54 = 10^1 \times 5 + 10^0 \times 4 
  $$
  $$
    54 = 50 + 4
  $$

  Pour les autres bases ça sera pareil. Pour la base 8, au lieu d'aller de 0 à 9, nous allons de 0 à 7 (et pas 8) car entre 0 et 7 nous avons bien 8 chiffres, donc 8 possibilités. Vous pensez, peut-être, et alors pour la base 16? Comment nous allons faire? Dans ce cas, après le 9, nous allons prendre les lettred e l'alphabet jusqu'à avoir 16 possibilités, donc nous allons avoir 0 jusqu'à 9 et puis A, B, C, D, E et F.

#### Formules Mathématiques
  $$
    (a_n,a_{n-1}\dots a_1,a_0) = a_nB^n+a_{n-1}B^{n-1}+\dots a_1B^1+a_0B^0 = \sum_{i=0}^{n} a_iB^i
  $$

  Il faut pas avoir peur! $a$ c'est bien le chiffre, par exemple, dans le nombre $83$, on a $a_0=3$ et $a_1 = 8$, et $B$ c'est bien la base exposé à son poids, donc $83 = 8 \times 10^1 + 3 \times 10^0$.

#### Base 2 (binaire)
  La base 2 utilise un alphabet binaire avec 2 valeurs $= \{0, 1\}$ et tout nombre binaire commence par %.  
  ex.: `0%1100 1011`
  
#### Base décimale en base binaire


  On utilise les restes successibles d'une division euclidienne par 2.   
  <div class="row mt-3">
      <div class="col-sm mt-3 mt-md-0">
          {% include figure.liquid loading="eager" path="assets/img/archi/base10-2.png" class="img-fluid rounded z-depth-1" zoomable=true %}
      </div>
  </div>

#### Base 16 (hexadecimal)
  La base 16 utilise un alphabet hexadecimal avec 16 valeurs $= \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F\}$.
  - Tout nombre en hexadecimal commence par `0x`.
	ex.: `0x2AF`
	
  $$
	  = 2 \times 16^2 + 10 \times 16^1 + 15 \times 16^0 \newline
	  = 687
	$$

#### Base décimale en base hexadecimale
  On utilise les restes successibles d'une division euclidienne par 16.
  <div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/archi/base10-16.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
  </div>

#### Base binaire en base hexadecimale
  Pour trouver la base hexadecimale à partir de la base binaire, on va utiliser un tableau pour nous aider.

  | Decimal | Hexadecimal | Binaire (4bits) |
  | ------- | ----------- | --------------- |
  | 0       | 0           | 0000            |
  | 1       | 1           | 0001            |
  | 2       | 2           | 0010            |
  | 3       | 3           | 0011            |
  | 4       | 4           | 0100            |
  | 5       | 5           | 0101            |
  | 6       | 6           | 0110            |
  | 7       | 7           | 0111            |
  | 8       | 8           | 1000            |
  | 9       | 9           | 1001            |
  | 10      | A           | 1010            |
  | 11      | B           | 1011            |
  | 12      | C           | 1100            |
  | 13      | D           | 1101            |
  | 14      | E           | 1110            |
  | 15      | F           | 1111            |

  On fait des paquets de 4 bits en partant de la droite, on remplace chaque paquet par son équivalent hexadecimal.

  ex.: 
  `0%11110101111 = 0%0111 1010 1111 = 0x7AF`

#### Base hexadecimale en binaire
  On fait l'inverse, on remplace chaque caractère hexa par 4 bits correspondants.

  ex.:
  `0x3B2C = %0011 1011 0010 1100`

## **Système Logique**
  <div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/archi/diagrame-01.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
  </div>

  - **description:** une lumière L est allumée si on appuie
  - **texte:** sur un inter A ou si on appuie simultanément sur inter B et sur inter C.
  - **proposition logique:** L est tactif si A est actif ou (B et C actifs).
  - **equation**: `L = A ou (B et C)`
  La table de vérité:
  
  | ABC | L |
  | --- | - |
  | 000 | 0 |
  | 001 | 0 |
  | 010 | 0 |
  | 011 | 1 |
  | 100 | 1 |
  | 101 | 1 |
  | 110 | 1 |
  | 111 | 1 |


## Algèbre Binaire et Fonctions Logiques

#### Algèbre binaire
  Toute variable binaire ne peut prendre que 2 valeurs:
  - 0, faux (**inactif**)
  - 1, vrai (**actif**)

  Il existe trois fonctions de base:
  - `non`, répresenté par une barre $^{––}$ 
  - `ou`, répresenté par un $+$ (se lit "ou")
  - `et`, répresenté par un $⋅$ (se lit "et") 

## Postulats
  - **Commutative:**

      $A + B = B + A$
      $A ⋅ B = B ⋅ A$
  - **Associativité:**

      $(A + B) + C = A + (B + C)$
      $(A ⋅ B) ⋅ C = A ⋅ (B ⋅ C)$
  - **Distributivité:**

      $A \cdot (B + C) = (A \cdot B) + (A \cdot C)$
      $A + (B \cdot C) = (A + B) \cdot (A + C)$
  - **Élément neutre:**

      $A + 0 = A$
      $A \cdot 1 = A$
  - **Élément absorbant:**

      $A + 1 = 1$
      $A \cdot 0 = 1$
  - **Complémentarité:**

      $A + \overline{A} = 1$
      $A \cdot 0 = 0$
  - **Idempotence:**

      $A + A = A$
      $A \cdot A = A$
  - **Involution:**

      $\overline{\overline{A}} = A$ 
  - **Absorption:**

      $A + (A \cdot B) = A$
      $A \cdot (A + B) = A$
  - **Loi De Morgan:**

      $\overline{A + B} = \overline{A} \cdot \overline{B}$
      $\overline{A \cdot B} = \overline{A} + \overline{B}$

### Fonctions logiques
  <div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/archi/image-1-1.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
  </div>

### Determiner l'équation à partir de la table de vérité
  <div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/archi/image-1-2.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
  </div>

## Bascules
  Un système est combinatoire si les sorties ne dépendent que d'entrées. Un système est séquentiel si les sorties dépendent des sorties et éventuellement d'entrées.
  
  Un système est synchrone si toutes les sorties changent à des moments déterminés.

#### Bascule R.S (reset set)
  Une bascule R.S possède deux entrées de contrôle: set et reset; et n'a pas d'entrée de donnée. Les deux signaux de sortie $Q$ et $\overline{Q}$ sont présents. Le fonctionnement de cette bascule est le suivant:
  - mise à 1 de S (Set): la sortie Q passe à 1;
  - mise à 1 de R (Reset): la sortie Q passe à 0;
  - R = S = 0: état mémoire: la sortie Q maintient sa valeur précédente q.

  | $R$ $S$ | $Q$                                       | $\overline{Q}$   |
  | ------- | ----------------------------------------- | ---------------- |
  | 0 0     | $Q^-$ mémorisation d'état précédent       | $\overline{Q^-}$ |
  | 0 1     | 1     SET (mise à 1)                      | 0                |
  | 1 0     | 0    RESET (mise à 0)                     | 1                |
  | 1 1     | 1    (état interdit mais SET prioritaire) | 0                |

  <div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/archi/image-2.svg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
  </div>

#### Bascule D
  Une bascule D possède une entrée de contrôle, notée H, et une entrée de données, notée D. On retrouve les deux signaux de sorite $Q$ et $\overline{Q}$. Le fonctionnement de cette bascule est le suivant:
  - quand H est à 0, la sortie maintient son état, quel que soit le niveau appliqué à D;
  - quand H est à 1, la sortie Q recopie l'état de D.
  La sortie juste après le ==front montant== prend la valeur présente sur l'entrée D avant le front montant. 

  > #### Quand est-ce que la sortie peut changer?
  >
  > 
  > Attention! Entre 2 fronts montants la sortie ne peut pas changer.
  {: .block-warning}

  <div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/archi/image-3.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
  </div>

## Nombres signés
- tout nombre signé utilise un format (nombre de bits)
- tout nombre signé négatif a un poids fort (bit à gauche) 1.

ex.:
<br>
avec 8 bits: `%1000 0000` représente $-128$, et `0111 1111`représente $+127$.

#### Complement à 2:
`COMP2(x)` = $\overline{X} + 1 = -X$
<br>
$\overline{X}$ —> le complement bit à bit
<br>
$+$ —> plus
<br>
$-$ —> moins
	
ex. au format 8 bits: <br>
	`COMP2(%10110010) = -%01001101 + 1` <br>
	`COMP2(%10110010) = -%01001110 = -78`

Pour trouver le complément à 2 d'un nombre binaire, on recopie à partir de la droite jusqu'au premier 1 inclus, et puis on inverse le reste.

ex:<br>
	`COMP2(%11001==100==) = - %00110==100== = - 52` <br>
	`COMP2(%11011010==1==) = -%00100101==1== = -37`

## Virgule fixe
Toujours à complément à 2 (signé et format)

ex.: <br>
sur 8 bits avec 3 bits après la virgule.<br>
	`%0 1 1 0 1,0 1 1` <br>
	   $2^4$
     $2^3$
     $2^2$
     $2^1$
     $2^0$
     $2^{-1}$
     $2^{-2}$ 
     $2^{-3}$
	`= 13,375` <br>
regardons:<br> `%01101011 = 107`:
	$\frac{107}{2^3}=13,375$

#### Decimal -> binaire
ex.: sur 8 bits et 4 bits après la virgule.
$-5,2$
$-5,2 = -5,2 \times 2^4 = -83,2$ 

