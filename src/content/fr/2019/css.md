---
part_number: I
chapter_number: '2'
title: CSS
description: Chapitre CSS du Web Almanac 2019 couvrant les requêtes de couleur, d'unités,
  de sélecteurs, de mise en page, de typographie et de polices, d'espacement, de décoration,
  d'animation et de supports.
authors: [una, argyleink]
reviewers: [meyerweb, huijing]
translators: [SilentJMA]
discuss: 1757
published: 2019-12-09T00:00:00.000Z
last_updated: 2019-12-09T00:00:00.000Z
---

## Introduction

Feuilles de Style en Cascade (CSS) sont utilisés pour peindre, formater et mettre en page des pages Web. Leurs capacités couvrent des concepts aussi simples que la couleur du texte en perspective 3D. Il comporte également des crochets permettant aux développeurs de gérer différentes tailles d'écran, contextes d'affichage et impressions. CSS permet aux développeurs de se disputer avec le contenu et de s’assurer qu’il s’adapte correctement à l’utilisateur.

Lorsque vous décrivez le CSS à ceux qui ne sont pas familiers avec la technologie Web, il peut être utile de le considérer comme le langage à utiliser pour peindre les murs de la maison. décrivant la taille et la position des fenêtres et des portes, ainsi que des décorations florissantes telles que du papier peint ou des plantes. Le côté amusant de cette histoire est que, selon l'utilisateur qui se promène dans la maison, un développeur peut l'adapter aux préférences ou au contexte de cet utilisateur!

Dans ce chapitre, nous allons inspecter, compiler et extraire des données sur l'utilisation du CSS sur le Web. Notre objectif est de comprendre globalement quelles fonctionnalités sont utilisées, comment elles sont utilisées et comment CSS se développe et adopté.

Prêt à creuser dans les données fascinantes?! Un grand nombre des nombres suivants peuvent paraître petits, mais ne les confondez pas avec le moins du monde! Cela peut prendre de nombreuses années avant que de nouvelles choses saturent le Web.

## Couleur

La couleur est une partie intégrante du thème et du style sur le Web. Voyons comment les sites Web ont tendance à utiliser la couleur.

### Types de couleur

L'hex est le moyen le plus populaire pour décrire la couleur de loin, avec une utilisation de 93%, suivi de RVB, puis de HSL. Fait intéressant, les développeurs tirent pleinement parti de l'argument de la transparence alpha en ce qui concerne ces types de couleurs: HSLA et RGBA sont bien plus populaires que HSL et RGB, leur utilisation étant presque le double! Même si la transparence alpha a été ajoutée plus tard aux spécifications Web, HSLA et RGBA sont pris en charge. [aussi loin que IE9](https://caniuse.com/#feat=css3-colors), afin que vous puissiez aller de l'avant et les utiliser aussi !

<figure>
  <a href="/static/images/2019/02_CSS/fig1.png">
    <img src="/static/images/2019/02_CSS/fig1.png" alt="Figure 1. Popularité des formats de couleur." aria-labelledby="fig1-caption" aria-describedby="fig1-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=1946838030&amp;format=interactive">
  </a>
  <div id="fig1-description" class="visually-hidden">Diagramme à barres illustrant l'adoption des formats de couleur HSL, HSLA, RGB, RGBA et hexadécimale. Hex est utilisé sur 93 % des pages de version desktop, RGBA sur 83 %, RGB sur 22 %, HSLA 19 % et HSL 1 %. L’adoption sur les versions desktop et les appareils mobiles est similaire pour tous les formats de couleur, à l’exception de la LGV, pour laquelle l’adoption mobile est de 9 % (9 fois plus élevée).</div>
  <figcaption id="fig1-caption">Figure 1. Popularité des formats de couleur.</figcaption>
</figure>

### Choix de couleur

Il y a [148 couleurs CSS nommées](https://www.w3.org/TR/css-color-4/#named-colors), non compris les valeurs spéciales `transparent` et `currentcolor`. Vous pouvez les utiliser par leur nom de chaîne pour un style plus lisible. Les couleurs nommées les plus populaires sont `black` et `white`, Sans surprise, suivi de `red` et `blue`.

<figure>
  <a href="/static/images/2019/02_CSS/fig2.png">
    <img src="/static/images/2019/02_CSS/fig2.png" alt="Figure 2. Top couleurs nommées." aria-labelledby="fig2-caption" aria-describedby="fig2-description" width="600" data-width="600" data-height="415" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=1985913808&amp;format=interactive">
  </a>
  <div id="fig2-description" class="visually-hidden">Graphique à secteurs montrant les couleurs nommées les plus populaires. Le blanc est le plus populaire à 40%, puis le noir à 22%, le rouge 11% et le bleu 5%.</div>
  <figcaption id="fig2-caption">Figure 2. Top Couleurs nommées.</figcaption>
</figure>

La langue est également intéressante inférée par la couleur. Il y a plus d'exemples du style-américain "gray" que le style-britannique "grey". Presque chaque instance de [couleurs gray](https://www.rapidtables.com/web/color/gray-color.html) (`gray`, `lightgray`, `darkgray`, `slategray`, etc.) avait presque une double utilisation quand orthographié avec un "a" au lieu d'un "e". Si gr[a/e]ys combinés, ils se classeraient plus haut que le bleu, se solidifiant à la #4 place. Cela pourrait être la raison `silver` est classé plus haut que `grey` avec un "e" Dans les tableaux !

### Nombre de couleurs

Combien de couleurs de police différentes sont utilisées sur le Web ? Donc, ce n'est pas le nombre total de couleurs uniques; c'est plutôt le nombre de couleurs différentes utilisé uniquement pour le texte. Les chiffres de ce tableau sont assez élevés et d’après notre expérience, nous savons que sans les variables CSS, les espaces, les tailles et les couleurs peuvent rapidement vous échapper et se fragmenter en une multitude de petites valeurs dans vos styles. Ces chiffres reflètent une difficulté de gestion du style et nous espérons que cela vous aidera à créer une perspective que vous pourrez ramener à vos équipes ou projets. Comment pouvez-vous réduire ce nombre à un montant gérable et raisonnable ?

<figure>
  <a href="/static/images/2019/02_CSS/fig3.png">
    <img src="/static/images/2019/02_CSS/fig3.png" alt="igure 3. Répartition des couleurs par page." aria-labelledby="fig3-caption" aria-describedby="fig3-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=1361184636&amp;format=interactive">
  </a>
  <div id="fig3-description" class="visually-hidden">Distribution montrant les 10, 25, 50, 75 et 90 pour cent de couleurs par page pour ordinateur et page mobile. Sur la version desktop, la distribution est la suivante: 8, 22, 48, 83 et 131. Les pages mobiles ont généralement davantage de couleurs de 1 à 10.</div>
<figcaption id="fig3-caption">Figure 3. Répartition des couleurs par page.</figcaption>
</figure>

### Duplication de couleur

Eh bien, nous sommes curieux ici et souhaitons vérifier le nombre de couleurs en double présentes sur une page. Sans un système CSS de classe réutilisable étroitement géré, les doublons sont assez faciles à créer. Il s'avère que la médiane a suffisamment des doublons pour mériter un passage pour les unifier avec des propriétés personnalisées.

<figure>
  <a href="/static/images/2019/02_CSS/fig4.png">
<img src="/static/images/2019/02_CSS/fig4.png" alt="Figure 4. Répartition des couleurs en double par page." aria-labelledby="fig4-caption" aria-describedby="fig4-description" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=326531498&format=interactive">
 </a> 
 <div id="fig4-description" class="visually-hidden">Diagramme à barres illustrant la répartition des couleurs par page. La page de version desktop médiane a 24 couleurs en double. Le dixième centile correspond à 4 couleurs en double et le 90e centile à 62. Les distributions pour les postes de versions desktop mobiles sont similaires.</div>
<figcaption id="fig4-caption">Figure 4. Répartition des couleurs en double par page.</figcaption>
</figure>

## Unités

En CSS, il existe de nombreuses façons d'obtenir le même résultat visuel en utilisant différents types d'unité: `rem`, `px`, `em`, `ch`, ou même `cm`! Alors, quels types d'unités sont les plus populaires ?

<figure>
  <a href="/static/images/2019/02_CSS/fig5.png">
    <img src="/static/images/2019/02_CSS/fig5.png" alt="Figure 5. Popularité des types d'unités." aria-labelledby="fig5-caption" aria-describedby="fig5-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=540111393&amp;format=interactive">
  </a>
  <div id="fig5-description" class="visually-hidden">Diagramme à barres de la popularité de divers types d'unités. px et em sont utilisés sur plus de 90% des pages. rem est le deuxième type d'unité le plus populaire sur 40% des pages et la popularité chute rapidement pour les types d'unités restants.</div>
  <figcaption id="fig5-caption">Figure 5. Popularité des types d'unités.</figcaption>
</figure>

### Longueur et dimensionnement

Sans surprise, dans la figure 5 ci-dessus, `px` est le type d'unité le plus utilisé, avec environ 95 % des pages Web utilisant des pixels sous une forme ou une autre (par exemple, la taille de l'élément, la taille de la police, etc.). Cependant, le `em` l'unité est presque aussi populaire, avec environ 90 % d'utilisation. Ceci est plus de 2x plus populaire que le `rem` unité, qui n’a que 40 % de fréquence dans les pages Web. Si vous vous demandez quelle est la différence, `em` est basé sur la taille de la police parente, alors que `rem` est basé sur la taille de police de base définie pour la page. Cela ne change pas par composant comme `em` pourrait, et permet donc d'ajuster tous les espacements de manière uniforme.

En ce qui concerne les unités basées sur l’espace physique, la `cm` (ou centimètre) est de loin le plus populaire, suivi de `in` (inches), et alors `Q`. Nous savons que ces types d’unités sont particulièrement utiles pour les feuilles de style d’impression, mais nous ne connaissions même pas la `Q` L'unité existait jusqu'à cette enquête ! et toi ?

<aside>Une version antérieure de ce chapitre traitait de l'inattendu pop<code>u</code>larity of the Q unit.<a href="https://discuss.httparchive.org/t/chapter-2-css/1757/6"> Grace à la communauté</a> discussion autour ce chapitre, nous avons identifié qu’il s’agissait d’un bogue dans notre analyse et nous avons mis à jour la figure 5 en conséquence.</aside>

### Unités basées sur une fenêtre

Nous avons constaté une grandes différences entre les types d’unités quand ça vient à l’utilisation mobile et la version desktop des unités basées sur une fenêtre. 36,8 % des sites mobiles utilisent `vh` (hauteur de la fenêtre d'affichage), contre seulement 31 % des sites pour la version desktop. Nous avons également constaté que `vh` est plus courant que` vw` (largeur de la fenêtre d'affichage) d'environ 11 %. `vmin` (viewport minimum) est plus populaire que` vmax` (viewport maximum), avec environ 8 % d'utilisation de `vmin` sur mobile, tandis que` vmax` n'est utilisé que par 1% des sites Web.

### Propriétés personnalisées

Les propriétés personnalisées sont ce que beaucoup appellent des variables CSS. Ils sont cependant plus dynamiques qu'une variable statique typique! Ils sont très puissants et en tant que communauté, nous découvrons encore leur

<figure>
  <div class="big-number">5%</div>
  <figcaption>Figure 6. Pourcentage de pages utilisant des propriétés personnalisées.</figcaption>
</figure>

Nous nous sommes sentis que ces informations intéressantes, car elles montrent une croissance saine de l’un de nos ajouts CSS préférés. Ils étaient disponibles dans tous les principaux navigateurs depuis 2016 ou 2017, il est donc juste de dire qu'ils sont relativement nouveaux. De nombreuses personnes sont encore en train de passer de leurs variables de préprocesseur CSS aux propriétés personnalisées CSS. Nous estimons qu'il faudra encore quelques années avant que les propriétés personnalisées deviennent la norme.

## Sélecteurs

### ID vs sélecteurs de classe

CSS a plusieurs façons de trouver des éléments sur la page à des fins de style, nous allons donc mettre les identifiants et les classes les unes contre les autres pour voir lequel est le plus répandu ! Les résultats ne devraient pas être trop surprenant: les classes sont
 plus populaire !
 
<figure>
  <a href="/static/images/2019/02_CSS/fig7.png">
    <img src="/static/images/2019/02_CSS/fig7.png" alt="Figure 7. Popularité des types de sélecteurs par page." aria-labelledby="fig7-caption" aria-describedby="fig7-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=1216272563&amp;format=interactive">
  </a>
  <div id="fig7-description" class="visually-hidden">Diagramme à barres illustrant l'adoption des types de sélecteurs d'identifiant et de classe. Les classes sont utilisées sur le 95 % des pages de bureau et mobiles. Les identifiants sont utilisés sur le 89 % des pages de version desktop et 87 % des pages mobiles.</div>
<figcaption id="fig7-caption">  Figure 7. Popularité de select ou types par page.</figcaption>
</figure>

Celui-ci est un bon tableau de suivi montrant que les classes occupent 93 % des sélecteurs présents dans une feuille de style.

<figure>
  <a href="/static/images/2019/02_CSS/fig8.png">
    <img src="/static/images/2019/02_CSS/fig8.png" alt="Figure 8. Popularité des types de sélecteurs par sélecteur." aria-labelledby="fig8-caption" aria-describedby="fig8-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=351006989&amp;format=interactive">
  </a>
  <div id="fig8-description" class="visually-hidden">Diagramme à barres montrant que 94 % des sélecteurs incluent le sélecteur de classe pour les versions desktop et mobiles, tandis que 7 % des sélecteurs de desktop incluent le sélecteur d'identifiant (8% pour les mobiles).</div>
<figcaption id="fig8-caption">Figure 8. Popularité des types de sélecteur par sélecteur.</figcaption></a>
</figure>

### Sélecteurs d'attributs

CSS a des sélecteurs de comparaison très puissants. Ce sont des sélecteurs comme `[target="_blank"]`, `[attribute^="value"]`, `[title~="rad"]`, `[attribute$="-rad"]` ou `[attribute*="value"]`. Est-ce que vous les utilisez? Vous pensez qu'ils sont beaucoup utilisés? Comparons leur utilisation avec les identifiants et les classes sur le Web.
<figure>
  <a href="/static/images/2019/02_CSS/fig9.png">
    <img src="/static/images/2019/02_CSS/fig9.png" alt="Figure 9. Popularité des opérateurs par sélecteur d'attribut ID." aria-labelledby="fig9-caption" aria-describedby="fig9-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=695879874&amp;format=interactive">
  </a>
  <div id="fig9-description" class="visually-hidden">Diagramme à barres illustrant la popularité des opérateurs utilisés par les sélecteurs d'attributs ID. Environ 4 % des pages pour version desktop et mobiles utilisent étoiles-égales et carétaux-égaux. 1 % des pages utilisent des égaux et des dollars égaux. 0 % utilise tilde-égal.</div>
<figcaption id="fig9-caption">  Figure 9. Popularité des opérateurs par sélecteur d'attribut ID.</figcaption></a>
</figure>

<figure>
  <a href="/static/images/2019/02_CSS/fig10.png">
    <img src="/static/images/2019/02_CSS/fig10.png" alt="Figure 10. Popularité des opérateurs par sélecteur d'attribut de classe." aria-labelledby="fig10-caption" aria-describedby="fig10-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=377805296&amp;format=interactive">
  </a>
  <div id="fig10-description" class="visually-hidden">Diagramme à barres illustrant la popularité des opérateurs utilisés par les sélecteurs d'attributs de classe. 57 % des pages utilisent des étoiles égales. 36 % utilisent caret-equals. 1 % utilisent égal et dollar égal. 0 % utilise tilde-égal.</div>
<figcaption id="fig10-caption">Figure 10. Popularité des sélecteurs d'attribut d'opérateurs par classe.</figcaption></a>
</figure>

Ces opérateurs sont beaucoup plus populaires auprès des sélecteurs de classe que les ID, ce qui semble naturel dans la mesure où une feuille de style comporte généralement moins de sélecteurs d’ID que de sélecteurs de classe, mais reste néanmoins pratique pour voir les utilisations de toutes ces combinaisons.

### Classes par élément

Avec la montée en puissance des stratégies CSS, atomiques, et OOCSS fonctionnelles pouvant composer 10 classes ou plus sur un élément afin d'obtenir un aspect de conception, nous pourrions peut-être voir des résultats intéressants. La requête est revenue sans énigme, la médiane sur mobile et desktop étant de 1 classe par élément.
<figure>
  <div class="big-number">1</div>
  <figcaption>Figure 11. Nombre médian d'attributs de noms de classe par classe (version desktop et mobiles).</figcaption>

## Mises en page

### Flexbox

[Flexbox](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Flexible_Box_Layout/Concepts_de_base_flexbox) est un style de conteneur qui dirige et aligne ses éléments; c'est-à-dire que cela aide à la mise en page d'une manière basée sur les contraintes. Les débuts sur le Web ont été plutôt difficiles, car ses spécifications ont subi deux ou trois changements radicaux entre 2010 et 2013. Heureusement, elle a été adoptée et mise en œuvre sur tous les navigateurs dès 2014. D'après cet historique, le taux d'adoption était lent, mais ça fait quelques années depuis! Il est assez populaire maintenant et contient de nombreux articles sur la manière de l'exploiter, mais il est encore nouveau par rapport aux autres tactiques de mise en page.

<figure>
  <a href="/static/images/2019/02_CSS/fig12.png">
    <img src="/static/images/2019/02_CSS/fig12.png" alt="Figure 12. Adoption du flexbox." aria-labelledby="fig12-caption" aria-describedby="fig12-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=2021161093&amp;format=interactive">
  </a>
  <div id="fig12-description" class="visually-hidden">Diagramme à barres montrant 49 % des versions desktop et 52 % des pages mobiles utilisant flexbox.
  </div>
  <figcaption id="fig12-caption">Figure 12. Adoption du flexbox.</figcaption>
</figure>

Tout à fait de la réussite illustrée ici, puisque près de 50 % du Web utilise des Flexbox dans ses feuilles de style.

### Grilles

Like flexbox, [grid](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Grid_Layout) a également connu quelques alternances de spécifications au début de sa vie, mais sans changer les implémentations dans les navigateurs déployés publiquement. Microsoft utilisait Grille dans les premières versions de Windows 8, en tant que moteur de disposition principal pour son style de conception à défilement horizontal. Il a d'abord été approuvé, puis transféré sur le Web, puis renforcé par les autres navigateurs jusqu'à sa version finale en 2017. Le lancement a été très réussi. Presque tous les navigateurs ont publié leurs implémentations en même temps. Les développeurs Web se sont donc réveillés. un jour au support de la grille superbe. Aujourd'hui, à la fin de 2019, la grille se sent toujours comme un nouvel enfant sur le bloc, alors que les gens sont toujours en train de prendre conscience de sa puissance et de ses capacités.

<figure>
  <div class="big-number">2%</div>
  <figcaption>Figure 13. Pourcentage de sites Web utilisant une grille.</figcaption>
</figure>

Cela montre à quel point la communauté du développement Web a peu exercé et exploré son dernier outil de présentation. Nous attendons avec impatience la prise de contrôle éventuelle de la grille en tant que moteur principal de la mise en page sur lequel les personnes s’appuient lors de la construction d’un site. Pour nous, auteurs, nous aimons écrire sur grille: nous l’atteignons d’abord, puis nous recomposons notre complexité à mesure que nous réalisons et itérons sur la mise en page. Il reste à voir ce que le reste du monde fera avec cette puissante fonctionnalité CSS au cours des prochaines années.

### Modes d'écriture

Le Web et le CSS sont des fonctionnalités de plate-forme internationales, et les modes d'écriture offrent au HTML et au CSS un moyen d'indiquer l'orientation préférée de l'utilisateur en matière de lecture et d'écriture au sein de nos éléments.
<figure>
  <a href="/static/images/2019/02_CSS/fig14.png">
    <img src="/static/images/2019/02_CSS/fig14.png" alt="Figure 14. Popularité des valeurs de direction." aria-labelledby="fig14-caption" aria-describedby="fig14-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=136847988&amp;format=interactive">
  </a>
  <div id="fig14-description" class="visually-hidden">Diagramme à barres illustrant la popularité des valeurs de direction ltr et rtl. 32 % des pages de version desktop et 40% des pages mobiles utilisent ltr. RTL est utilisé par 32 % des pages de bureau et 36 % des pages mobiles.</div>
<figcaption id="fig14-caption">Figure 14. Popularité des valeurs de direction.</figcaption></a>
</figure>

## Typographie

### Polices Web par page

Combien de polices Web chargez-vous sur votre page Web: 0 ? 10 ? Le nombre médian de polices Web par page est de 3 !

<figure>
  <a href="/static/images/2019/02_CSS/fig15.png">
    <img src="/static/images/2019/02_CSS/fig15.png" alt="Figure 15. Répartition du nombre de polices Web chargées par page." aria-labelledby="fig15-caption" aria-describedby="fig15-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=1453570774&amp;format=interactive">
  </a>
  <div id="fig15-description" class="visually-hidden">Répartition du nombre de polices Web chargées par page. Sur les ordinateurs de bureau, les 10, 25, 50, 75 et 90ème centile sont les suivants: 0, 1, 3, 6 et 9. Ce chiffre est légèrement supérieur à la distribution mobile, qui est une police de moins dans les 75ème et 90ème centile.</div>
<figcaption id="fig15-caption">Figure 15. Répartition du nombre de polices Web chargées par page.</figcaption>
</a>
</figure>

### Familles de polices populaires

Un suivi naturel à la recherche du nombre total de polices par page est: quelles polices sont-elles ?! Designers vous allez maintenant voir si vos choix correspondent ou non à ce qui est populaire.

<figure>
  <a href="/static/images/2019/02_CSS/fig16.png">
    <img src="/static/images/2019/02_CSS/fig16.png" alt="Figure 16. Top web fonts." aria-labelledby="fig16-caption" aria-describedby="fig16-description" width="600" data-width="600" data-height="450.5" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=1883567922&amp;format=interactive">
  </a>
  <div id="fig16-description" class="visually-hidden">Diagramme à barres des polices les plus populaires. Parmi les pages de version desktop, on trouve Open Sans (24 %), Roboto (15 %), Montserrat (5 %), Source Sans Pro (4 %), Noto Sans JP (3 %) et Lato (3 %). Sur mobile, les différences les plus notables sont qu'Open Sans est utilisé 22 % du temps (de 24 %) et Roboto est utilisé 19 % du temps (à partir de 15 %).</div>
  <figcaption id="fig16-caption">Figure 16. Top web fonts.</figcaption>
</figure>

Open Sans est un énorme gagnant ici, avec près de 1 déclaration CSS sur 4 `@font-family` qui le spécifie. Nous avons certainement utilisé Open Sans dans des projets d'agences.
Il est également intéressant de noter les différences entre l'adoption d'un ordinateur de bureau et d'une application mobile. Par exemple, les pages mobiles utilisent Open Sans un peu moins souvent que les versions desktop. Pendant ce temps, ils utilisent aussi Roboto un peu plus souvent.

### Tailles de police

C’est intéressant, car si vous demandiez à un utilisateur combien de tailles de police il estimait être sur une page, il renverrait en général un nombre de 5 ou nettement inférieur à 10. C’est la réalité ? Même dans un système de design, combien de tailles de police existe-t-il ? Nous avons interrogé le Web et avons trouvé que la médiane était 40 sur un mobile et 38 sur version desktop. Il serait peut-être temps de réfléchir sérieusement aux propriétés personnalisées ou à la création de classes réutilisables pour vous aider à distribuer votre rampe de type.<figure><a href="/static/images/2019/02_CSS/fig17.png"><img src="/static/images/2019/02_CSS/fig17.png" alt="Figure 17. Distribution of the number of distinct font sizes per page." aria-labelledby="fig17-caption" aria-describedby="fig17-description" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=1695270216&format=interactive"><div id="fig17-description" class="visually-hidden">

  
  
    
  
  Diagramme à barres illustrant la distribution de taille de police distincte par page. Pour les pages de bureau, les 10 ème, 25, 50, 75 et 90 ème centile sont les suivants: 8, 20, 40, 66 et 92 tailles de police. La distribution d'ordinateurs de bureau diverge du mobile au 75 ème percentile, où elle est plus grande de 7 à 13 tailles différentes.</div>
<figcaption id="fig17-caption">
  Figure 17. Répartition du nombre de tailles de police distincte par page.</figcaption></a></figure>

## Espacement
### Marges
Une marge est l'espace extérieur aux éléments, comme l'espace que vous demandez lorsque vous écartez les bras. Cela ressemble souvent à l'espacement entre les éléments, mais ne se limite pas à cet effet. Dans un site Web ou une application, l'espacement joue un rôle important dans l'UX et le design. Voyons combien de code d'espacement des marges dans une feuille de style, allons-nous?<figure><a href="/static/images/2019/02_CSS/fig18.png"><img src="/static/images/2019/02_CSS/fig18.png" alt="Figure 18. Distribution of the number of distinct margin values per page." aria-labelledby="fig18-caption" aria-describedby="fig18-description" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=4233531&format=interactive"><div id="fig18-description" class="visually-hidden">

  
  
    
  
  Diagramme à barres montrant la distribution de valeurs de marge distinctes par page. Pour les pages de version desktop, les 10, 25, 50, 75 et 90 ème centile sont: 12, 47, 96, 167 et 248 valeurs de marge distinctes. La distribution des versions desktop diffère du mobile au 75 ème centile, où elle est plus petite de 12 à 31 valeurs distinctes.</div>
<figcaption id="fig18-caption">
  Figure 18. Répartition du nombre de valeurs de marge distinctes par page.</figcaption></a></figure>

Beaucoup semble-t-il ! La page de version desktop médiane a 96 valeurs de marge distinctes et 104 sur mobile. Cela crée de nombreux moments d'espacement uniques dans votre design. Vous voulez savoir combien de marges vous avez sur votre site ? Comment rendre tous ces espaces plus gérables?</div>
<figure><div class="big-number">
<figcaption>
### Propriétés logiques

  0.6%
  Figure 19. Pourcentage de pages de version desktop et mobiles qui incluent des propriétés logiques.</figcaption>

Nous estimons que l'hégémonie de `margin-left` et `padding-top` est de durée limitée, bientôt complétée par leur direction d'écriture agnostique, successive, syntaxe de propriété logique. Bien que nous soyons optimistes, l'utilisation actuelle est assez faible à 0,67 % d'utilisation sur les pages de version desktop. Pour nous, cela ressemble à un changement d'habitude que nous devrons développer en tant qu'industrie, tout en espérant former de nouveaux développeurs à utiliser la nouvelle syntaxe.
### z-index
La superposition verticale, ou l'empilage, peut être gérée avec `z-index` dans le CSS. Nous étions curieux pour savoir combien de valeurs différentes les gens utilisent dans leurs sites. La gamme de ce `z-index` accepte est théoriquement infini, limité uniquement par les limitations de taille variable d'un navigateur. Toutes ces positions de pile sont-elles utilisées ? Voyons voir !<figure><a href="/static/images/2019/02_CSS/fig20.png"><img src="/static/images/2019/02_CSS/fig20.png" alt="Figure 20. Distribution of the number of distinct 'z-index' values per page." aria-labelledby="fig20-caption" aria-describedby="fig20-description" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQO5CabwLwQ5Lj1_9bbEFnFM1qEqCorymaBHrcaNiMSJ7sYDKHUI5iish5VAS-SxN447UTW-1-5-OjE/pubchart?oid=1320871189&format=interactive"><div id="fig20-description" class="visually-hidden">

  
  
    
  
  Diagramme à barres montrant la distribution de valeurs distinctes d'index z par page. Pour les pages de bureau, les 10, 25, 50, 75 et 90 ème centile sont: 1, 7, 16, 26 et 36 distincts z-index valeurs. La distribution sur ordinateur est beaucoup plus élevée que sur mobile, avec jusqu'à 16 valeurs distinctes au 90 ème centile.</div>
<figcaption id="fig20-caption">
  Figure 20. Distribution du nombre de valeurs distinctes du z-index par page.</figcaption></a></figure><code>

### Valeurs du z-index populaires
D'après notre expérience de travail, n'importe quel nombre de 9 semble être le choix le plus populaire. Même si nous nous sommes appris à utiliser le plus petit nombre possible, ce n'est pas la norme communautaire. Alors c'est quoi donc ?! Si les gens ont besoin de choses par dessus, quelles sont les numéros les plus populaires de `z-index` à passer ? Déposez votre boisson; celui-ci est assez drôle, vous pourriez le perdre.

  
  
    
  
  Diagramme de dispersion de toutes les valeurs du z-index connues et du nombre de fois où elles sont utilisées, pour version desktop et mobile. 1 et 2 sont les plus fréquemment utilisés, mais le reste des valeurs populaires explosent par ordre de grandeur: 10, 100, 1 000 et ainsi de suite jusqu'à des nombres avec des centaines de chiffres.
  Figure 21. Valeurs du z-index les plus fréquemment utilisées.


  999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999 ! 
important
  Figure 22. La plus grande valeur connue du z-index

## Décoration
### Filtres
Les filtres sont un moyen amusant et génial pour modifier les pixels que le navigateur a l'intention de dessiner à l'écran. Il s'agit d'un effet de post-traitement effectué sur une version plate de l'élément, du nœud ou du calque auquel il est appliqué. Photoshop les a rendus faciles à utiliser, puis Instagram les a rendus accessibles aux masses grâce à des combinaisons stylisées sur mesure. Ils existent depuis environ 2012, il y en a 10 et ils peuvent être combinés pour créer des effets uniques.


  78%
  Figure 23. Pourcentage de pages qui incluent une feuille de style avec la propriété Filter.

Nous avons été ravis de voir que 78% des feuilles de style contiennent la propriété `filter` ! Ce nombre était également si élevé qu'il semblait un peu louche, alors nous avons cherché à expliquer le nombre élevé. Parce que soyons honnêtes, les filtres sont bien mais ils ne font pas partie de toutes nos applications et projets. Sauf si !
Après une enquête plus approfondie, nous avons découvert que la feuille de style du [FontAwesome](https://fontawesome.com) est livrée avec certains `filter` utilisation, ainsi que l'intégration de [YouTube](https://youtube.com). Par conséquent, nous croyons que `filter` faufilé dans la porte arrière en passant par quelques feuilles de style très populaires. Nous pensons également que la présence de `-ms-filter` aurait également pu être incluse, contribuant au pourcentage élevé d'utilisation.
### Modes de fusion
Les modes de fusion sont similaires aux filtres dans la mesure où ils sont un effet de post-traitement exécuté contre une version plate de leurs éléments cibles, mais ils sont uniques en ce qu'ils concernent la convergence des pixels. D'une autre manière, les modes de fusion sont la façon dont 2 pixels devraient se toucher lorsqu'ils se chevauchent. Quel que soit l'élément situé en haut ou en bas, cela affectera la façon dont le mode de fusion manipule les pixels. Il existe 16 modes de fusion - voyons quels sont les plus populaires.


  8%
  Figure 24. Pourcentage de pages qui incluent une feuille de style avec la propriété *-blend-mode.

Dans l'ensemble, l'utilisation des modes de fusion est beaucoup plus faible que celle des filtres, mais est encore suffisante pour être considérée comme modérément utilisée.Dans une future édition du Web Almanac, il serait intéressant d'explorer l'utilisation du mode de fusion pour avoir une idée des modes exacte que les développeurs utilisent, comme multiply, screen, color-burn, lighten, etc.
## Animation
### Transitions
CSS a un formidable pouvoir d'interpolation qui peut être simplement utilisé en écrivant une seule règle sur la façon de faire la transition de ces valeurs. Si vous utilisez CSS pour gérer les états dans votre application, à quelle fréquence utilisez-vous des transitions pour effectuer la tâche? Interrogeons le web !

  
  
    
  
  Diagramme à barres montrant la répartition des transitions par page. Pour les pages de bureau, les 10, 25, 50, 75 et 90 ème centiles sont: 0, 2, 16, 49 et 118 transitions. La distribution des ordinateurs de bureau est bien inférieure à celle des mobiles, avec pas moins de 77 transitions au 90 ème centile.

  Figure 25. Répartition du nombre de transitions par page.

C'est plutôt bien ! Nous avons vu `animate.css` en tant que bibliothèque populaire à inclure, ce qui apporte une tonne d'animation de transition, mais il est toujours agréable de voir que les gens envisagent de faire la transition de leurs interfaces utilisateur.
### Animations d'images clés
Les animations d'images clés CSS sont une excellente solution pour vos animations ou transitions plus complexes. Ils vous permettent d'être plus explicite, ce qui offre un meilleur contrôle sur les effets. Ils peuvent être petits comme un effet d'image clé ou être grands avec de nombreux effets d'images clés composés dans une animation robuste. Le nombre médian d'animations d'images clés par page est bien inférieur aux transitions CSS.

  
  
    
  
  Diagramme à barres montrant la distribution des images clés par page. Pour les pages mobiles, les 10, 25, 50, 75 et 90 ème centiles sont: 0, 0, 3, 18 et 76 images clés. La distribution mobile est légèrement supérieure à celle des versions desktop de 6 images clés aux 75 ème et 90 ème centiles.

  Figure 26. Répartition du nombre d'images clés par page.

## Requêtes médias
Les requêtes multimédias permettent à CSS de se connecter à diverses variables au niveau du système afin de s'adapter de manière appropriée à l'utilisateur visiteur. Certaines de ces requêtes peuvent gérer les styles d'impression, les styles d'écran du projecteur et la taille de la fenêtre / écran. Pendant longtemps, les requêtes des médias ont été principalement exploitées pour leur connaissance de la fenêtre d'affichage. Les designers et les développeurs pouvaient adapter leurs dispositions pour les petits écrans, les grands écrans, etc. Plus tard, le Web a commencé à apporter de plus en plus de fonctionnalités et de requêtes, ce qui signifie que les requêtes multimédias peuvent désormais gérer les fonctionnalités d'accessibilité en plus des fonctionnalités de la fenêtre d'affichage.Un bon endroit pour commencer par les requêtes multimédias, c'est à peu près combien été utilisées par page ? À combien de moments ou de contextes différents la page type a-t-elle l'impression de vouloir répondre ? 

  
  
    
  
  Diagramme à barres montrant la répartition des requêtes média par page. Pour les pages de version desktop, les 10, 25, 50, 75 et 90 ème centiles sont: 0, 3, 14, 27 et 43 images clés. La distribution de version desktop est similaire à la distribution mobile.

  Figure 27. Répartition du nombre de requêtes média par page.

### Tailles des points d'arrêt des requêtes multimédias populaires

Pour les requêtes de support de fenêtre tout type d'unité CSS peut être transmise à l'expression de requête pour évaluation. Auparavant, les gens passaient `em` et `px` dans la requête, mais plus d'unités ont été ajoutées au fil du temps, ce qui nous rend très curieux de savoir quels types de tailles sont généralement trouvés sur le Web. Nous supposons que la plupart des requêtes multimédias suivront les tailles d'appareils populaires, mais au lieu de supposer, regardons les données!

  
  
    
  
  Diagramme à barres des points d'accrochage aux requêtes multimédias les plus populaires. 768px et 767px sont les plus populaires avec 23 % et 16 %, respectivement. La liste disparaît rapidement après cela, avec 992px utilisés 6 % du temps et 1200px utilisés 4 % du temps. Le bureau et le mobile ont une utilisation similaire.

  Figure 28. Points d'accrochage les plus fréquemment utilisés dans les requêtes multimédias.

La figure 28 ci-dessus montre qu'une partie de nos hypothèses étaient correctes: il y a certainement une grande quantité de tailles spécifiques au téléphone, mais il y en a aussi qui ne le sont pas. Il est également intéressant de voir comment il est très dominant en pixels, avec quelques entrées qui utilisent `em` au-delà de la portée de ce tableau.
### Utilisation portrait vs landscape
La valeur de requête la plus populaire parmi les tailles de point d'arrêt populaires semble être `768px`, ce qui nous a rendus curieux. Cette valeur a-t-elle été principalement utilisée pour passer à une mise en page portrait, car elle pourrait être basée sur l'hypothèse que `768px` représente la fenêtre de portrait mobile typique ? Nous avons donc effectué une requête de suivi pour voir la popularité de l'utilisation des modes portrait et paysage:

  
  
    
  
  Diagramme à barres montrant l'adoption des modes d'orientation portrait et paysage des requêtes multimédias. 31 % des pages spécifient le paysage, 8 % spécifient le portrait et 7 % spécifient les deux. L'adoption est la même pour les pages version desktop et mobiles.
  Figure 29. Adoption des modes d'orientation des requêtes multimédias.

Intéressant, `portrait` n'est pas très utilisé, alors que `landscape` est utilisé beaucoup plus. Nous pouvons seulement supposer que `768px` a été suffisamment fiable comme cas de mise en page portrait qu'il est atteint pour beaucoup moins. Nous supposons également que les gens sur une version desktop, testant leur travail, ne peuvent pas déclencher le portrait pour voir leur mise en page mobile aussi facilement qu'ils peuvent simplement écraser le navigateur. Difficile à dire, mais les données sont fascinantes.
### Types d'unités les plus populaires
Dans les requêtes de médias de largeur et de hauteur que nous avons vues jusqu'à présent, les pixels ressemblent à l'unité dominante de choix pour les développeurs qui cherchent à adapter leur interface utilisateur aux fenêtres. Nous voulions cependant interroger exclusivement cela et vraiment jeter un coup d'œil aux types d'unités que les gens utilisent. Voici ce que nous avons trouvé.

  
  
    
  
  Graphique à barres montrant 75 % des points d'accrochage de requête multimédia spécifiant des pixels, 8 % spécifiant des ems et 1% spécifiant des rems
   Figure 30. Adoption d'unités dans les points d'accrochage aux requêtes multimédias.

### `min-width` vs `max-width`
Lorsque les gens écrivent une requête multimédia, recherchent-ils généralement une fenêtre qui se trouve au-dessus ou en dessous d'une plage spécifique,_ou_ les deux, vérifier si c'est entre une gamme de tailles? Demandons au web !

  
  
    
  
  Graphique à barres montrant 74% des pages version desktop en utilisant la largeur maximale, 70 % en utilisant la largeur minimale et 68 % en utilisant les deux propriétés. L'adoption est similaire pour les pages mobiles.
   Figure 31. Adoption des propriétés utilisées dans les points d'accrochage aux requêtes multimédias.

Aucun gagnant clair ici; `max-width` et `min-width` sont presque également utilisés.
### Print et speech
Les sites Web ressemblent à du papier numérique, non? En tant qu'utilisateurs, il est généralement connu que vous pouvez simplement appuyer sur imprimer depuis votre navigateur et transformer ce contenu numérique en contenu physique. Un site Web n'est pas obligé de se changer pour ce cas d'utilisation mais il peut le faire s'il le souhaite ! Moins connue est la possibilité d'ajuster votre site Web dans le cas où il serait lu par un outil ou un robot. Alors, à quelle fréquence ces fonctionnalités sont-elles exploitées?

  
  
    
  
  Diagramme à barres montrant 35 % des pages de bureau utilisant le "all" type de requête multimédia, 46 % utilisant l'impression, 72 % utilisant l'écran et 0 % utilisant la parole. L'adoption est inférieure d'environ 5 points de pourcentage pour la version desktop par rapport au mobile.
   Figure 32. Adoption des types de requêtes multimédias all, print, screen et speech.

## Statistiques au niveau de la page
### Feuilles de style
À combien de feuilles de style faites-vous référence depuis votre page d'accueil? Combien de vos applications ? Servez-vous plus ou moins sur mobile ou sur ordinateur ? Voici un tableau de tout le monde !

  
  
    
  
  Répartition du nombre de feuilles de style chargées par page. Desktop et mobile ont des distributions identiques avec 10, 25, 50, 75 et 90 ème centiles: 1, 3, 6, 12 et 20 feuilles de style par page.
   Figure 33. Répartition du nombre de feuilles de style chargées par page.

### Noms des feuilles de style

Comment nommez-vous vos feuilles de style? Avez-vous été constant tout au long de votre carrière? Avez-vous lentement convergé ou divergé de façon constante? Ce graphique montre un petit aperçu de la popularité de la bibliothèque, mais impse intar names  files.      <figure>
  <table>
    <thead>
      <tr>
        <th>Nom de la feuille de style</th>
        <th>Desktop</th>
        <th>Mobile</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>style.css</td>
        <td class="numeric">2.43%</td>
        <td class="numeric">2.55%</td>
      </tr>
      <tr>
        <td>font-awesome.min.css</td>
        <td class="numeric">1.86%</td>
        <td class="numeric">1.92%</td>
      </tr>
      <tr>
        <td>bootstrap.min.css</td>
        <td class="numeric">1.09%</td>
        <td class="numeric">1.11%</td>
      </tr>
      <tr>
        <td>BfWyFJ2Rl5s.css</td>
        <td class="numeric">0.67%</td>
        <td class="numeric">0.66%</td>
      </tr>
      <tr>
        <td>style.min.css?ver=5.2.2</td>
        <td class="numeric">0.64%</td>
        <td class="numeric">0.67%</td>
      </tr>
      <tr>
        <td>styles.css</td>
        <td class="numeric">0.54%</td>
        <td class="numeric">0.55%</td>
      </tr>
      <tr>
        <td>style.css?ver=5.2.2</td>
        <td class="numeric">0.41%</td>
        <td class="numeric">0.43%</td>
      </tr>
      <tr>
        <td>main.css</td>
        <td class="numeric">0.43%</td>
        <td class="numeric">0.39%</td>
      </tr>
      <tr>
        <td>bootstrap.css</td>
        <td class="numeric">0.40%</td>
        <td class="numeric">0.42%</td>
      </tr>
      <tr>
        <td>font-awesome.css</td>
        <td class="numeric">0.37%</td>
        <td class="numeric">0.38%</td>
      </tr>
      <tr>
        <td>style.min.css</td>
        <td class="numeric">0.37%</td>
        <td class="numeric">0.37%</td>
      </tr>
      <tr>
        <td>styles__ltr.css</td>
        <td class="numeric">0.38%</td>
        <td class="numeric">0.35%</td>
      </tr>
      <tr>
        <td>default.css</td>
        <td class="numeric">0.36%</td>
        <td class="numeric">0.36%</td>
      </tr>
      <tr>
        <td>reset.css</td>
        <td class="numeric">0.33%</td>
        <td class="numeric">0.37%</td>
      </tr>
      <tr>
        <td>styles.css?ver=5.1.3</td>
        <td class="numeric">0.32%</td>
        <td class="numeric">0.35%</td>
      </tr>
      <tr>
        <td>custom.css</td>
        <td class="numeric">0.32%</td>
        <td class="numeric">0.33%</td>
      </tr>
      <tr>
        <td>print.css</td>
        <td class="numeric">0.32%</td>
        <td class="numeric">0.28%</td>
      </tr>
      <tr>
        <td>responsive.css</td>
        <td class="numeric">0.28%</td>
        <td class="numeric">0.31%</td>
      </tr>
    </tbody>
  </table>
  <figcaption>Figure 34. Noms de feuilles de style les plus fréquemment utilisés.</figcaption>
</figure>

Regardez tous ces noms de fichiers créatifs! style, styles, principal, par défaut, tout. L'un d'entre eux s'est cependant démarqué, le voyez-vous? `BfWyFJ2Rl5s.css` prend la place de numéro quatre pour les plus populaires. Nous avons fait des recherches un peu et notre meilleure supposition est que c'est lié à Facebook "like" boutons. Savez-vous quel est ce fichier? Laissez un commentaire, car nous aimerions entendre l'histoire.

### Taille de la feuille de style

Quelle est la taille de ces feuilles de style? Notre taille CSS doit-elle inquiéter? À en juger par ces données, notre CSS n'est pas un délinquant principal pour le ballonnement des pages.

  
  
    
  
  Répartition du nombre d'octets de feuilles de style chargée par page. Les 10, 25, 50, 75 et 90 ème centile de la page de version desktop sont: 8, 26, 62, 129 et 240 Ko. La distribution de bureau est légèrement supérieure à la distribution mobile de 5 à 10 Ko.   Figure 35. Répartition du nombre d'octets de feuilles de style (Ko) chargé par page.
Voir le [Page Weight](./page-weight) pour un examen plus approfondi du nombre d'octets que les sites Web chargent pour chaque type de contenu.
### Bibliothèques
Il est courant, populaire, pratique et puissant d'atteindre une bibliothèque CSS pour démarrer un nouveau projet. Bien que vous ne soyez peut-être pas du genre à atteindre une bibliothèque, nous avons interrogé le Web en 2019 pour voir ceux qui mènent le. Si les résultats vous étonnent, comme ils nous l'ont fait, je pense que c'est un indice intéressant de voir à quel point une bulle de développeur dans laquelle nous pouvons vivre est petite. Les choses peuvent sembler massivement populaires, sur le Web, mais un peu différentes.

 <figure>
  <table>
    <thead>
      <tr>
        <th>Library</th>
        <th>Desktop</th>
        <th>Mobile</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Bootstrap</td>
        <td class="numeric">27.8%</td>
        <td class="numeric">26.9%</td>
      </tr>
      <tr>
        <td>animate.css</td>
        <td class="numeric">6.1%</td>
        <td class="numeric">6.4%</td>
      </tr>
      <tr>
        <td>ZURB Foundation</td>
        <td class="numeric">2.5%</td>
        <td class="numeric">2.6%</td>
      </tr>
      <tr>
        <td>UIKit</td>
        <td class="numeric">0.5%</td>
        <td class="numeric">0.6%</td>
      </tr>
      <tr>
        <td>Material Design Lite</td>
        <td class="numeric">0.3%</td>
        <td class="numeric">0.3%</td>
      </tr>
      <tr>
        <td>Materialize CSS</td>
        <td class="numeric">0.2%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td>Pure CSS</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.1%</td>
      </tr>
      <tr>
        <td>Angular Material</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.1%</td>
      </tr>
      <tr>
        <td>Semantic-ui</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.1%</td>
      </tr>
      <tr>
        <td>Bulma</td>
        <td class="numeric">0.0%</td>
        <td class="numeric">0.0%</td>
      </tr>
      <tr>
        <td>Ant Design</td>
        <td class="numeric">0.0%</td>
        <td class="numeric">0.0%</td>
      </tr>
      <tr>
        <td>tailwindcss</td>
        <td class="numeric">0.0%</td>
        <td class="numeric">0.0%</td>
      </tr>
      <tr>
        <td>Milligram</td>
        <td class="numeric">0.0%</td>
        <td class="numeric">0.0%</td>
      </tr>
      <tr>
        <td>Clarity</td>
        <td class="numeric">0.0%</td>
        <td class="numeric">0.0%</td>
      </tr>
    </tbody>
  </table>
  <figcaption>Figure 36. Pourcentage de pages contenant une bibliothèque CSS donnée.</figcaption>
</figure>

Ce graphique suggère que [Bootstrap](https://getbootstrap.com/) est une bibliothèque précieuse à connaître pour vous aider à trouver un emploi. Regardez toutes les opportunités qui s’offrent à vous! Il convient également de noter qu'il ne s'agit que d'un diagramme de signal positif: le total des calculs ne donne pas 100%, car tous les sites n'utilisent pas de framework CSS. Un peu plus de la moitié de tous les sites n'utilisent pas un framework CSS connu. Très intéressant, non ?!
### Réinitialiser les utilitaires
Les utilitaires de réinitialisation CSS ont l'intention de normaliser ou de créer une base de référence pour les éléments Web natifs. Si vous ne le saviez pas, chaque navigateur envoie sa propre feuille de style pour tous les éléments HTML, et chaque navigateur prend ses propres décisions quant à son apparence ou à son comportement. Les utilitaires de réinitialisation ont examiné ces fichiers, ont trouvé un terrain d’entente (ou non) et ont résolu toutes les différences afin que vous, développeur, puissiez styler dans un navigateur et avoir la certitude raisonnable qu’il aura la même apparence dans un autre.
Voyons maintenant combien de sites en utilisent un! Leur existence semble tout à fait raisonnable, alors combien de personnes sont d'accord avec leur tactique et les utilisent sur leurs sites ?

  
  
    
  
  Diagramme à barres illustrant l'adoption de trois utilitaires de réinitialisation CSS: Normalize.css (33 %), Réinitialiser CSS (3 %), CSS  est pure (0%). 
 Il n'y a pas de différence d'adoption entre les pages de version desktop et mobiles.
  Figure 37. Adoption des utilitaires de réinitialisation CSS.

Il s’avère qu’environ un tiers du Web utilise [`normalize.css`](https://necolas.github.io/normalize.css), ce qui pourrait être considéré comme une approche plus douce de la tâche qu’une réinitialisation. Nous avons regardé un peu plus loin, et il s’avère que Bootstrap inclut `normalize.css`, ce qui explique sans doute une grande partie de son utilisation. Il convient également de noter que `normalize.css` a plus d’adoption que Bootstrap, aussi de nombreuses personnes l’utilisent-ils tout seul.
### `@supports` et `@import`
CSS `@supports` est un moyen pour le navigateur de vérifier si une combinaison propriété-valeur particulière est analysée comme valide, puis d'appliquer des styles si la vérification renvoie la valeur true.

  
  
    
  
  Diagramme à barres illustrant la popularité des règles @import et @supports "at". Sur la version desktop, @import est utilisé sur 28 % des pages et @supports sur 31 %. Pour mobile, @import est utilisé sur 26 % des pages et @supports sur 29 %.
  Figure 38. Popularité des règles CSS "at".</code>
</div></figure></figure></figure>

Considérant `@supports` a a été mis en œuvre sur la plupart des navigateurs en 2013, il n’est pas surprenant de constater une utilisation et une adoption élevées. Nous sommes impressionnés par la conscience des développeurs ici. C'est du codage attentionné ! 30 % des sites Web recherchent un support lié à l'affichage avant de l'utiliser.

Une suite intéressante à cela est qu'il y a plus d'utilisation de `@supports` que `@imports` ! Nous ne nous attendions pas à ça ! `@import` est dans les navigateurs depuis 1994.

## Conclusion

Il y a tellement plus ici de données à explorer ! Beaucoup des résultats nous ont surpris et nous ne pouvons qu'espérer qu'ils vous ont surpris également. Ce jeu de données surprenant à rendre le résumé très amusant et nous a laissés de nombreux indices et pistes à explorer si nous voulons rechercher les raisons pour lesquelles *pourquoi* certains des résultats obtenus sont tels qu'ils sont.

Quels résultats avez-vous trouvés les plus alarmants?
Quels sont les résultats qui vous incitent à consulter rapidement votre base de code?

Nous pensons que la principale conséquence de ces résultats est que les propriétés personnalisées offrent le meilleur rapport qualité-prix en matière de performances, de sécheresse et d'évolutivité de vos feuilles de style. Nous sommes impatients de nettoyer à nouveau les feuilles de style d'Internet, à la recherche de nouveaux datums et de nouvelles graphes provocantes. Contactez [@Una](https://twitter.com/una) ou [@argyleink](https://twitter.com/argyleink) dans les commentaires avec vos requêtes, questions et assertions. Nous aimerions les entendre!
