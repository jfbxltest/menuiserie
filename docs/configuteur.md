# Notes sur le configurateur menuiserie

L'idée de base est de créer une démarche descendante: chaque étape est "relative" à la précédente

- on commence par le rendu final (dimensions)
- on crée succesivement les étapes suivantes sous forme de calques relatif au précédent (le calque parent)
- on imagine un type de calque spécial, spécifique à la division (du calque parent direct) appelé "calque de division".
  - La division de calque doit être comprise comme une partition (partage) d'un calque.
    _exemple: Diviser en largeur un calque de largeur totale "LT" en "N" parties égales ("N>1") nommée "PE" (avec "PE=LT/N")_
    > On crée une première partition de largeur "PE", il en resulte 2 parties de largeur "PE" et "(N-1)*PE" (si "N=2" alors "N-1=1")
    > On remarquera que pour les partitions succésives, chaque partition dépendra de la précédente, avec comme opération "(N-1)*PE/(N-1)", c-a-d "PE" !!!

## La division de calques

- La division de calque est une directive relative a un axe donné (largeur, hauteur, etc...)
- La division peut être "automatique" ou "contrainte"

  - Automatique: Diviser (selon un axe donné) le calque parent en "N" parties égales.
  - Contrainte: Diviser (selon un axe donné) le calque parent, dont une des partie a une contrainte de dimension.

    - ### _Contrainte simple: contrainte en début, en fin ou centrée_
      > _On note "D" la dimension totale (selon l'axe donné) du parent, "C" celle de la contrainte_ D=100; C=20
      >
      > #### Contrainte "en début":
      >
      > La première partition est positionnée à "0"et a comme dimension "C" _20_.
      > La seconde partition est positionnée à "C" _20_ et a comme dimension "D-C" _80_.
      > Cette dernière peut alors être divisée de manière "Automatique".
      >
      > #### Contrainte "en fin":
      >
      > La première partition est positionnée à "D-C" _80_ et a comme dimension "C" _20_.
      > La seconde partition est positionnée à "0" et a comme dimension "D-C" _80_.
      > Cette dernière peut alors être divisée de manière "Automatique".
      >
      > #### Contrainte "centrée":
      >
      > La première partition est positionnée à "(D-C)/2" _40_ et a comme dimension "C"_20_.
      > Une deuxième partition est positionnée à "0" et a comme dimension "(D-C)/2" _40_.
      > Une troisième partition est positionnée à "D-{(D-C)/2}" _60_ et a comme dimension "(D-C)/2" _40_.
    - ### _contrainte complexe, contrainte qui est "positionnée"_
      **NB: dans ce cas de figure la division crée plusieurs calque "enfants**
      > _On note "P" le positionement de la contrainte_ D=100; C=50; P=10
      > La dépendance d'origine et la dépendance de taille
      > Le premier enfant est positionné à "0" et a comme dimension "P" _10_.
      > Le second enfant est positionné à "P+C" _60_ et a comme dimension "D-(P+C)" _40_.

    >
