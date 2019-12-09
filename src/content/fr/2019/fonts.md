---
part_number: I
chapter_number: '6'
title: Polices
description: Chapitre sur les Polices du Web Almanac 2019 qui traite le lieu de chargement des polices, les formats de Polices, la performances de chargement des Polices, les Polices variables et la couleur de Polices.
authors: [zachleat]
reviewers: [hyperpress, AymenLoukil]
translators: [SilentJMA]
discuss: 1761
published: 2019-11-11T00:00:00.000Z
last_updated: 2019-12-09T00:00:00.000Z
---

## Introduction

Les polices permettent une belle typographie fonctionnelle sur le Web. L'utilisation des fontes de caractères du Web renforce non seulement le design mais elle démocratise un sous-ensemble de design, car elle permet un accès facile à ceux qui ne possèdent pas des compétences fortes en design. Cependant, malgré les bien qu’elles puissent faire, les polices du Web peuvent endommager gravement les performances de votre site si elles ne sont pas chargées correctement.

Sont-ils un net positif pour le web? Fournissent-ils plus d'avantages que des inconvenants? Les chemins balisés du Web standardisé sont-ils suffisamment balisés pour encourager les meilleurs pratiques de chargement des polices par défaut? Si non que faille-t-il changer? à partir des données si nous pouvons répondre à ces questions ou non, comment les polices du Web sont utilisées sur le Web aujourd'hui.

## Où avez-vous obtenu ces polices du Web?

La plus importante première question: la performance. Un chapitre entier est consacré à [la performance](./performance) mais nous irons plus loin un peu aux problèmes de performances spécifiques aux polices.

L'utilisation des polices hébergées sur le Web facilite l'implémentation et la maintenance, mais l'auto-hébergement offre une meilleure performance. Étant donné que les polices du Web rendent par défaut le texte invisible pendant le chargement de la police du Web (également connu sous le nom [Flash de Texte Invisible](https://css-tricks.com/fout-foit-foft/), ou FOIT), la performance des polices du Web peut être plus critique que des éléments non bloquants tels que des images.

### Les polices sont-elles hébergées sur le même hébergement ou par un différent hébergement?

Différencier entre l’auto-hébergement et l’hébergement par des tiers est de plus en plus pertinent sur [HTTP/2](./http2) monde, où l'écart de performance entre le même hébergement et une connexion d'un hébergement différent peut être plus large. Les demandes d'un même hébergement ont un énorme avantage d'un meilleur potentiel de hiérarchisation par rapport aux autres demandes du même hôte dans la cascade.

Les recommandations pour réduire les coûts de performance liés au chargement de polices du Web à partir d’un autre hébergement incluent l’utilisation de `preconnect`, `dns-prefetch`, and `preload` [resource hints](./resource-hints),mais les polices du Web avec une haute priorité doivent être des demandes émanant du même hébergement afin de minimiser l'impact des polices Web sur les performances. Ceci est particulièrement important pour les polices utilisées avec un contenu très visible ou une copie de corps occupant la majorité de la page.

<figure>
  <a href="/static/images/2019/06_Fonts/fig1.png">
    <img src="/static/images/2019/06_Fonts/fig1.png" alt="Figure 1. Popular web font hosting strategies." aria-labelledby="fig1-description" aria-describedby="fig1-caption" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQDogXDb3BwZZHrBT39qccP_LJoCScD3QEi_FmjT_8VDPD_1Srpz-g7ZuuTUEb8pYXBpDmQzZ1hQh7q/pubchart?oid=1546332659&amp;format=interactive">
  </a>
  <div id="fig1-description" class="visually-hidden">Diagramme à barres illustrant la popularité des stratégies tierces et d’auto-hébergement pour les polices Web. 75 % des pages Web mobiles utilisent des hébergements tiers et 25 % sont auto-hébergées. Les sites Web de version desktop ont une utilisation similaire.</div>
  <figcaption id="fig1-caption">Figure 1. Stratégies populaires d’hébergement de polices Web.</figcaption>
</figure>

Le fait que les trois quarts soient hébergés n’est peut-être pas surprenant compte tenu de la domination de Google Fonts sur laquelle nous discuterons [ci-dessous] (# les hébergements tiers les plus populaires).

Google sert les polices en utilisant des fichiers CSS tiers hébergés sur `https://fonts.googleapis.com`. Les développeurs ajoutent des requêtes à ces feuilles de style en utilisant `<link>` balises dans leur balisage. Bien que ces feuilles de style bloquent le rendu, elles sont très petites. Cependant, les fichiers de polices sont hébergés sur un autre domaine, `https://fonts.gstatic.com`. Le modèle qui exige deux sauts distincts dans deux domaines différents rend `preconnect` une excellente option ici pour la deuxième demande qui ne sera pas découverte avant le téléchargement du CSS.

Notez que tandis que `preload` serait un bon ajout à charger les fichiers de police plus haut dans la cascade de la demande (rappelez-vous que `preconnect` établit la connexion, il ne demande pas le contenu du fichier), `preload` n'est pas encore disponible avec Google Fonts. Google Fonts génère des URL uniques pour leurs fichiers de polices [qui sont susceptibles de changer](https://github.com/google/fonts/issues/1067).

### Quels sont les hébergements tiers les plus populaires?

<figure>
  <table>
    <thead>
      <tr>
        <th>Hébergement</th>
        <th>Desktop</th>
        <th>Mobile</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>fonts.gstatic.com</td>
        <td class="numeric">75.4%</td>
        <td class="numeric">74.9%</td>
      </tr>
      <tr>
        <td>use.typekit.net</td>
        <td class="numeric">7.2%</td>
        <td class="numeric">6.6%</td>
      </tr>
      <tr>
        <td>maxcdn.bootstrapcdn.com</td>
        <td class="numeric">1.8%</td>
        <td class="numeric">2.0%</td>
      </tr>
      <tr>
        <td>use.fontawesome.com</td>
        <td class="numeric">1.1%</td>
        <td class="numeric">1.2%</td>
      </tr>
      <tr>
        <td>static.parastorage.com</td>
        <td class="numeric">0.8%</td>
        <td class="numeric">1.2%</td>
      </tr>
      <tr>
        <td>fonts.shopifycdn.com</td>
        <td class="numeric">0.6%</td>
        <td class="numeric">0.6%</td>
      </tr>
      <tr>
        <td>cdn.shopify.com</td>
        <td class="numeric">0.5%</td>
        <td class="numeric">0.5%</td>
      </tr>
      <tr>
        <td>cdnjs.cloudflare.com</td>
        <td class="numeric">0.4%</td>
        <td class="numeric">0.5%</td>
      </tr>
      <tr>
        <td>use.typekit.com</td>
        <td class="numeric">0.4%</td>
        <td class="numeric">0.4%</td>
      </tr>
      <tr>
        <td>netdna.bootstrapcdn.com</td>
        <td class="numeric">0.3%</td>
        <td class="numeric">0.4%</td>
      </tr>
      <tr>
        <td>fast.fonts.net</td>
        <td class="numeric">0.3%</td>
        <td class="numeric">0.3%</td>
      </tr>
      <tr>
        <td>static.dealer.com</td>
        <td class="numeric">0.2%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td>themes.googleusercontent.com</td>
        <td class="numeric">0.2%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td>static-v.tawk.to</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.3%</td>
      </tr>
      <tr>
        <td>stc.utdstc.com</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td>cdn.jsdelivr.net</td>
        <td class="numeric">0.2%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td>kit-free.fontawesome.com</td>
        <td class="numeric">0.2%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td>open.scdn.co</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.1%</td>
      </tr>
      <tr>
        <td>assets.squarespace.com</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.1%</td>
      </tr>
      <tr>
        <td>fonts.jimstatic.com</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.2%</td>
      </tr>
    </tbody>
  </table>
  <figcaption>Figure 2. Top 20 des hébergements de polices par pourcentage de demandes.</figcaption>
</figure>

La domination de Google Fonts à la fois était à la fois surprenante et peu surprenante. Ce n’était pas surprenant, car je pensais que le service serait le plus populaire et le plus surprenant de par la dominance de sa popularité. 75 % des demandes de polices sont stupéfiantes. TypeKit était une deuxième place distante à un chiffre, la bibliothèque Bootstrap représentant une troisième place encore plus éloignée.

<figure>
  <div class="big-number">29%</div>
  <figcaption>Figure 3. Pourcentage de pages comportant un lien de feuille de style Google Fonts dans le document <code>&lt;head></code>.
</figcaption>
</figure>

Bien que l'utilisation de Google Fonts soit très impressionnante, il convient également de noter que 29 % seulement des pages incluaient un Google Fonts. `<link>` élément. Cela pourrait signifier quelques choses:

- Lorsque les pages utilisent Google Fonts, elles utilisent un lot de Google Fonts. Ils sont fournis sans frais, après tout. Peut-être sont-ils utilisés dans un éditeur WYSIWYG populaire? Cela semble être une explication très probable.
- Ou une histoire plus improbable est que cela pourrait signifier que beaucoup de gens utilisent Google Fonts avec `@import` au lieu de `<link>`.
- Ou, si nous voulons nous écarter des scénarios les plus improbables, cela pourrait signifier que beaucoup de gens utilisent Google Fonts avec un [HTTP `Link:` entête](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Link).

<figure>
  <div class="big-number">0.4 %</div>
  <figcaption>Figure 4. Pourcentage de pages incluant un lien de feuille de style de polices Google en tant que premier partie du document <code>&lt;head></code>.</figcaption>
</figure>

La documentation de Google Fonts encourage le `<link>` pour que Google Fonts CSS soit placé en tant que premier partie du `<head>` d'une page. C'est une grosse demande! En pratique, cela n’est pas courant car seulement un demi pour cent de toutes les pages (environ 20 000 pages) suivaient ce conseil.

Plus encore, si une page utilise `preconnect` ou `dns-prefetch` comme des éléments `<link>` ,ceux-ci viendraient de toute façon avant le CSS des polices de Google. Lisez la suite pour plus d'informations sur ces astuces de ressources.

### Accélérer l'hébergement tiers

Comme mentionné ci-dessus, un moyen très simple d’accélérer les demandes de polices Web à un hôte tiers est d’utiliser le `preconnect` [resource hint](./resource-hints).

<figure>
  <div class="big-number">1.7 %</div>
  <figcaption>Figure 5. Pourcentage de pages mobiles se connectant à un hébergement de polices Web.</figcaption>
</figure>

Wow! Moins de 2 % des pages utilisent [`preconnect`](https://web.dev/uses-rel-preconnect)! Étant donné que Google Fonts est à 75 %, cela devrait être plus élevé! Développeurs: si vous utilisez Google Fonts, utilisez `preconnect`! Google Fonts: prosélytisme `preconnect` plus!

En effet, si vous utilisez Google Fonts, ajoutez-le à votre `<head>` si ce n'est pas déjà là:

`<link rel="preconnect" href="https://fonts.gstatic.com/">`

### Caractères les plus populaires


<figure markdown="">
  <table>
      <thead>
        <tr>
          <th>Classement</th>
          <th>Famille de polices</th>
          <th>Desktop</th>
          <th>Mobile</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="numeric">1</td>
          <td>Open Sans</td>
          <td class="numeric">24 %</td>
          <td class="numeric">22 %</td>
        </tr>
        <tr>
          <td class="numeric">2</td>
          <td>Roboto</td>
          <td class="numeric">15 %</td>
          <td class="numeric">19 %</td>
        </tr>
        <tr>
          <td class="numeric">3</td>
          <td>Montserrat</td>
          <td class="numeric">5 %</td>
          <td class="numeric">4 %</td>
        </tr>
        <tr>
          <td class="numeric">4</td>
          <td>Source Sans Pro</td>
          <td class="numeric">4 %</td>
          <td class="numeric">3 %</td>
        </tr>
        <tr>
          <td class="numeric">5</td>
          <td>Noto Sans JP</td>
          <td class="numeric">3 %</td>
          <td class="numeric">3 %</td>
        </tr>
        <tr>
          <td class="numeric">6</td>
          <td>Lato</td>
          <td class="numeric">3 %</td>
          <td class="numeric">3 %</td>
        </tr>
        <tr>
          <td class="numeric">7</td>
          <td>Nanum Gothic</td>
          <td class="numeric">4 %</td>
          <td class="numeric">2 %</td>
        </tr>
        <tr>
          <td class="numeric">8</td>
          <td>Noto Sans KR</td>
          <td class="numeric">3 %</td>
          <td class="numeric">2 %</td>
        </tr>
        <tr>
          <td class="numeric">9</td>
          <td>Roboto Condensed</td>
          <td class="numeric">2 %</td>
          <td class="numeric">2 %</td>
        </tr>
        <tr>
          <td class="numeric">10</td>
          <td>Raleway</td>
          <td class="numeric">2 %</td>
          <td class="numeric">2 %</td>
        </tr>
        <tr>
          <td class="numeric">11</td>
          <td>FontAwesome</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">12</td>
          <td>Roboto Slab</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">13</td>
          <td>Noto Sans TC</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">14</td>
          <td>Poppins</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">15</td>
          <td>Ubuntu</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">16</td>
          <td>Oswald</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">17</td>
          <td>Merriweather</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">18</td>
          <td>PT Sans</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">19</td>
          <td>Playfair Display</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
        <tr>
          <td class="numeric">20</td>
          <td>Noto Sans</td>
          <td class="numeric">1 %</td>
          <td class="numeric">1 %</td>
        </tr>
      </tbody>
    </table>
  <figcaption>Figure 6. Top 20 des familles de polices exprimées en pourcentage pour toutes les déclarations de polices.</figcaption>
</figure>
Il n’est pas surprenant que les entrées les plus importantes ici semblent correspondre très [Liste des polices de Google Fonts triées par popularité](https://fonts.google.com/?sort=popularity).
## Quels sont les formats de police utilisés?
[WOFF2 est assez bien pris en charge](https://caniuse.com/#feat=woff2) aujourd'hui dans les navigateurs Web. Google Fonts sert WOFF2, un format qui offre une compression améliorée par rapport à son prédécesseur WOFF qui était déjà une amélioration par rapport aux autres formats de polices existants.
<figure>
  <a href="/static/images/2019/06_Fonts/fig7.png">
  
 <img src="/static/images/2019/06_Fonts/fig7.png" alt="Figure 7. Popularity of web font MIME types." aria-labelledby="fig7-caption" aria-describedby="fig7-description" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQDogXDb3BwZZHrBT39qccP_LJoCScD3QEi_FmjT_8VDPD_1Srpz-g7ZuuTUEb8pYXBpDmQzZ1hQh7q/pubchart?oid=998584594&format=interactive">   </a>
  <div id="fig7-description" class="visually-hidden">
  Diagramme à barres illustrant la popularité des types de polices Web MIME. WOFF2 est utilisé sur 74 % des polices, suivi de 13 % WOFF, 6 % octet-stream, 3 % TTF, 2 % Plain, 1 % HTML, 1 % SFNT et moins de 1 % pour tous les autres types. Desktop et mobile ont des distributions similaires</div>.<figcaption id="fig7-caption">
  Figure 7. Popularité des types MIME de polices Web</figcaption></figure>.

Pour moi, un argument pourrait être avancé pour utiliser WOFF2 uniquement pour les polices Web après avoir visualisé les résultats ici. Je me demande d'où vient l'utilisation à deux chiffres du WOFF? Peut-être que les développeurs continuent à utiliser des polices Web pour Internet Explorer?
Troisième place `octet-stream` (et `plain` un peu plus bas) semblerait suggérer que de nombreux serveurs Web sont configurés d'une manière incorrecte, envoyant un type MIME incorrect avec des demandes de fichiers de polices Web.
Creusons un peu plus loin et regardons la `format()` valeurs utilisées dans le `src:` propriété de `@font-face` déclarations<figure>:
<a href="/static/images/2019/06_Fonts/fig8.png">
  
 <img src="/static/images/2019/06_Fonts/fig8.png" alt="Figure 8. Popularity of font formats in <code>@font-face</code> declarations." aria-labelledby="fig8-caption" aria-describedby="fig8-description" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQDogXDb3BwZZHrBT39qccP_LJoCScD3QEi_FmjT_8VDPD_1Srpz-g7ZuuTUEb8pYXBpDmQzZ1hQh7q/pubchart?oid=700778025&format=interactive"> 
 </a>   <div id="fig8-description" class="visually-hidden">
  
 Diagramme à barres illustrant la popularité des formats utilisés dans les déclarations de polices. 69 % des pages version desktop' @font-face les déclarations spécifient le format WOFF2, 11 % WOFF, 10 % TrueType, 8 % SVG, 2 % EOT et moins de 1 % OpenType, TTF et OTF. La distribution pour les pages mobiles est si</div>mil<figcaption id="fig8-caption">aire.
  Figure 8. Popularité des forma<code>ts ts de police dans @fon</code>t-face declara</figcaption>t</figure>ions.

J'espérais voir [polices SVG](https://caniuse.com/#feat=svg-fonts) sur le déclin. Ils sont bogués et les implémentations ont été supprimées de tous les navigateurs sauf Safari. Il est temps de laisser tomber ceux-ci.
Le point de données SVG ici me fait également me demander quel type MIME sert ces polices SVG. Je ne vois pas `image/svg+xml`N'importe où dans la figure 7. Quoi qu'il en soit, ne vous inquiétez pas pour cela, mais débarrassez-vous-en!

### WOFF2-only

<figure>
  <table>
    <thead>
      <tr>     
  <th>Classement</th> 
  <th>Combinaisons de format</th>
  <th>Desktop</th>
  <th>Mobile</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="numeric">1</td>
        <td>woff2</td>
        <td class="numeric">84.0%</td>
        <td class="numeric">81.9%</td>
      </tr>
      <tr>
        <td class="numeric">2</td>
        <td>svg, truetype, woff</td>
        <td class="numeric">4.3%</td>
        <td class="numeric">4.0%</td>
      </tr>
      <tr>
        <td class="numeric">3</td>
        <td>svg, truetype, woff, woff2</td>
        <td class="numeric">3.5%</td>
        <td class="numeric">3.2%</td>
      </tr>
      <tr>
        <td class="numeric">4</td>
        <td>eot, svg, truetype, woff</td>
        <td class="numeric">1.3%</td>
        <td class="numeric">2.9%</td>
      </tr>
      <tr>
        <td class="numeric">5</td>
        <td>woff, woff2</td>
        <td class="numeric">1.8%</td>
        <td class="numeric">1.8%</td>
      </tr>
      <tr>
        <td class="numeric">6</td>
        <td>eot, svg, truetype, woff, woff2</td>
        <td class="numeric">1.2%</td>
        <td class="numeric">2.1%</td>
      </tr>
      <tr>
        <td class="numeric">7</td>
        <td>truetype, woff</td>
        <td class="numeric">0.9%</td>
        <td class="numeric">1.1%</td>
      </tr>
      <tr>
        <td class="numeric">8</td>
        <td>woff</td>
        <td class="numeric">0.7%</td>
        <td class="numeric">0.8%</td>
      </tr>
      <tr>
        <td class="numeric">9</td>
        <td>truetype</td>
        <td class="numeric">0.6%</td>
        <td class="numeric">0.7%</td>
      </tr>
      <tr>
        <td class="numeric">10</td>
        <td>truetype, woff, woff2</td>
        <td class="numeric">0.6%</td>
        <td class="numeric">0.6%</td>
      </tr>
      <tr>
        <td class="numeric">11</td>
        <td>opentype, woff, woff2</td>
        <td class="numeric">0.3%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td class="numeric">12</td>
        <td>svg</td>
        <td class="numeric">0.2%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td class="numeric">13</td>
        <td>eot, truetype, woff</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.2%</td>
      </tr>
      <tr>
        <td class="numeric">14</td>
        <td>opentype, woff</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.1%</td>
      </tr>
      <tr>
        <td class="numeric">15</td>
        <td>opentype</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.1%</td>
      </tr>
      <tr>
        <td class="numeric">16</td>
        <td>eot</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.1%</td>
      </tr>
      <tr>
        <td class="numeric">17</td>
        <td>opentype, svg, truetype, woff</td>
        <td class="numeric">0.1%</td>
        <td class="numeric">0.0%</td>
      </tr>
      <tr>
        <td class="numeric">18</td>
        <td>opentype, truetype, woff, woff2</td>
        <td class="numeric">0.0%</td>
        <td class="numeric">0.0%</td>
      </tr>
      <tr>
        <td class="numeric">19</td>
        <td>eot, truetype, woff, woff2</td>
        <td class="numeric">0.0%</td>
        <td class="numeric">0.0%</td>
      </tr>
      <tr>
        <td class="numeric">20</td>
        <td>svg, woff</td>
        <td class="numeric">0.0%</td>
        <td class="numeric">0.0%</td>
      </tr>
    </tbody>
 </table>
  <figcaption>Figure 9. Top 20 format de police combinations.</figcaption>
</figure>

Ce jeu de données suggére que la majorité des gens utilisent déjà WOFF2-seulement dans leur `@font-face` blocs. Mais ceci est trompeur, d’après notre discussion précédente sur la domination de Google Fonts dans l'ensemble de données. Google Fonts utilise des méthodes de détection pour servir un fichier CSS simplifié et inclut uniquement les fichiers les plus modernes. `format()`. Sans surprise, WOFF2 domine les résultats ici pour cette raison, car la prise en charge du navigateur pour WOFF2 est assez large depuis quelque temps.
Il est important de noter que ces données particulières ne soutiennent pas vraiment le cas de WOFF2, mais il reste une idée attrayante.

## Combattre le texte invisible

L’outil numéro un pour lutter contre le comportement de chargement des polices Web par défaut de "invisible pendant le chargement" (aussi connu sous le nom FOIT), est `font-display`. Ajouter `font-display: swap` à ton `@font-face` bloc est un moyen facile pour indiquer au navigateur d’afficher du texte de fallback pendant le chargement de la police Web.
[Support du navigateur](https://caniuse.com/#feat=mdn-css_at-rules_font-face_font-display) c'est super aussi. Internet Explorer et pre-Chromium Edge ne prend pas en charge, mais ils rendent également le texte de fallback par défaut lors du chargement d'une police Web (aucun FOIT autorisé ici). Pour nos tests Chrome, quelle est la fréquence des `font-display` utiliser?

<figure>
  <div class="big-number">26%</div>
  <figcaption>Figure 10. Pourcentage de pages mobiles qui utilis<code>ent le <code>font-display</code> style.</figcaption>

Je suppose que cela va ramper avec le temps, surtout maintenant que [Google Fonts ajoute `font-display` à tous les nouveaux extraits de code](https://www.zachleat.com/web/google-fonts-display/) copié de leur site.
Si vous utilisez Google Fonts, mettez à jour vos extraits! Si vous n'utilisez pas Google Fonts, utilisez `font-display`! En savoir plus sur `font-display` sur [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display).

Voyons ce que `font-display` les valeurs sont populaire:

<figure>
  <a href="/static/images/2019/06_Fonts/fig11.png">
 <img src="/static/images/2019/06_Fonts/fig11.png" alt="Figure 11. Usage of 'font-display' values." aria-labelledby="fig11-caption" aria-describedby="fig11-description" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQDogXDb3BwZZHrBT39qccP_LJoCScD3QEi_FmjT_8VDPD_1Srpz-g7ZuuTUEb8pYXBpDmQzZ1hQh7q/pubchart?oid=1988783738&format=interactive"> 
 </a> 
 <div id="fig11-description" class="visually-hidden">   
  
  Diagramme à barres illustrant l'utilisation du font-display style. 2.6 % des pages mobiles définir ce style en "swap", 1.5 % à "auto", 0.7 % à "block", 0.4% à "fallback", 0.2 % à optionnel, et 0.1 % à "swap" entre guillemets, ce qui est invalide. La distribution de version desktop est similaire sauf "swap" l'utilisation est inférieure par 0.4 percentage points et "auto" l'utilisation est plus élevée par 0.1 percentage points.</div>  
  <figcaption id="fig11-caption">
  Figure 11. L'utilisation de <code>font-display</code> valeurs.</figcaption></figure>

Moyen facile d’afficher du texte de fallback pendant le chargement d’une police Web, `font-display: swap` règne suprérieur et est la valeur la plus commune. `swap` est également la valeur par défaut utilisée par les nouveaux extraits de code de Google Fonts. J'aurais attendu `optional` (ne rendre que s'il est mis en cache) d’avoir un peu plus d’utilisation ici, car quelques évangélistes de développeurs éminents ont fait pression pour cela, mais pas de risques.

## Combien de polices Web ? Sont-elles trop nombreuses?

C'est une question qui nécessite une certaine nuance. Comment les polices sont-elles utilisées? Pour combien de contenu sur la page? Où ce contenu vit-il dans la mise en page? Comment les polices sont-elles rendues? Au lieu de nuance, passons maintenant à une analyse large et lourde spécifiquement centrée sur la demande<figure> co<a href="/static/images/2019/06_Fonts/fig12.png">mpte.<img src="/static/images/2019/06_Fonts/fig12.png" alt="Figure 12. Distribution of font requests per page." aria-labelledby="fig12-caption" aria-describedby="fig12-description" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQDogXDb3BwZZHrBT39qccP_LJoCScD3QEi_FmjT_8VDPD_1Srpz-g7ZuuTUEb8pYXBpDmQzZ1hQh7q/pubchart?oid=451821825&format=interactive">

 </a> 
 <div id="fig12-description" class="visually-hidden">Diagramme à barres illustrant la distribution des demandes de polices par page. Les pourcentages 10, 25, 50, 75 et 90 pour la version Desktop sont: 0, 1, 3, 6 et 9 demandes de police. La distribution pour mobile est identique jusqu'au 75 et 90 pour cents, où les pages mobiles demandent 1 Moins polices.</div>
 
 <figcaption id="fig12-caption">Figure 12. Distribution des demandes de police par page.</figcaption></figure>

La page Web médiane fait trois demandes de polices Web. Au 90 pour cent, demandé six et neuf polices Web sur mobile et desktop, re<figure>spe<a href="/static/images/2019/06_Fonts/fig13.png">ctive<img src="/static/images/2019/06_Fonts/fig13.png" alt="Figure 13. Histogram of web fonts requested per page." aria-labelledby="fig13-description" aria-describedby="fig13-caption" width="600" data-width="600" data-height="371" data-seamless="" data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQDogXDb3BwZZHrBT39qccP_LJoCScD3QEi_FmjT_8VDPD_1Srpz-g7ZuuTUEb8pYXBpDmQzZ1hQh7q/pubchart?oid=1755200484&format=interactive">ment.</a>

 <div id="fig13-description" class="visually-hidden">Histogramme montrant la distribution du nombre de demandes de polices par page. Le nombre le plus populaire de demandes de polices est 0, avec 22 % des pages du version desktop. La distribution chute à 9 % des pages comportant une police, puis atteint 10 % pour 2 à 4 polices avant de diminuer le nombre de polices augmente. Les distributions desktop et mobile sont similaires, malgré la distribution mobile penche légèrement pour avoir moins de polices par page.</div>
 <figcaption id="fig13-caption">Figure 13. Histogramme des demandes des polices Web par page.</figcaption>
</figure>

Il semble assez intéressant que les demandes de polices Web semblent être assez stables sur les versions web et le mobiles. Je suis content de voir la [recommandation de cacher `@font-face` blocs à l'intérieur d'un `@media` des requêtes](https://css-tricks.com/snippets/css/using-font-face/#article-header-id-6) n'a pas attiré (ne pas avoir d'idées).
Ce qu'il fait, il y a légèrement plus de demandes de polices effectuées sur des appareils mobiles. Mon impression ici c'est que moins de polices sont disponibles sur les appareils mobiles, ce qui signifie moins de polices. `local()` hits dans Google Fonts CSS, en revenant aux demandes du réseau pour ces derniers.

### Tu ne veux pas gagner ce prix

<figure>
  <div class="big-number">718</div>
  <figcaption>Figure 14. Le plus grand nombre de demandes de polices Web sur une seule page.</figcaption></figure>

Le prix pour la page qui demande le plus grand nombre de polices Web va au site qui a fait ** 718 ** demandes de polices Web!

Après avoir plongé dans le code, toutes ces 718 demandes vont à Google Fonts! Il semblerait qu'un plug-in d'optimisation "Au-dessus du pli de la page" ne fonctionnant pas correctement sur WordPress soit devenu une mauvaise idée sur ce site et qu'il demande (DDoS-ing?) Toutes les polices de Google - oups!

Il est ironique qu'un plugin d'optimisation des performances puisse aggraver vos performances!

## Correspondance plus précise avec `unicode-range`

<figure>
  <div class="big-number">56%</div>
  <figcaption>Figure 15. Pourcentage de pages mobiles déclarant une police Web avec le <code>unicode-range</code> propriété.</figcaption></figure>

[`unicode-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/%40font-face/unicode-range) est une excellente propriété CSS permettant au navigateur de savoir précisément quel code la page aimerait utiliser dans le fichier de police. Si la `@font-face` declaration a un `unicode-range`, le contenu de la page doit correspondre à l'un des points de code de la plage avant que la police ne soit demandée. C'est une très bonne chose.

C’est une autre mesure qui, je pense, était faussée par l’utilisation de Google Fonts, car celle-ci utilise `unicode-range` dans la plupart (sinon la totalité) de ses CSS. J’espère que cela soit moins courant dans les pays utilisateurs, mais peut-être que filtrer les demandes de Google Fonts dans la prochaine édition de l'Almanach pourrait être possible.

## Ne demandez pas de polices Web si un system font exists

<figure>
  <div class="big-number">59%</div>
  <figcaption>Figure 16. Pourcentage de pages mobiles déclarant un site Web avec <code>local()</code> propriété.</figcaption>

`local()` est un bon moyen de référencer une police système dans votre `@font-face` `src`. Si la `local()` police existe, il n’est pas nécessaire de demander une police Web. Ceci est très utilisé et controversé par Google Fonts, ce qui en fait un autre exemple de données asymétriques si nous essayons de dégager des modèles de la part des utilisateurs.
Il convient également de noter ici que des personnes plus intelligentes que moi (Bram Stein de TypeKit) ont dit que [en utilisant `local()` peut être imprévisible car les versions installées des polices peuvent être obsolètes et peu fiables](https://bramstein.com/writing/web-font-anti-patterns-local-fonts.html).
## Condensed fonts et `font-stretch`

<figure>
  <div class="big-number">7%</div>
  <figcaption>Figure 16. Pourcentage de pages de desktop et mobiles qui incluent un style avec le <code>font-stretch</code> propriété.</figcaption>

Historiquement, `font-stretch` a souffert d'un support de navigateur médiocre et n'était pas bien connu `@font-face` propriété. En savoir plus sur [`font-stretch` sur MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/font-stretch). Mais [support du navigateur](https://caniuse.com/#feat=css-font-stretch) a élargi.

Il a été suggéré que l'utilisation de polices condensées dans des fenêtres plus petites permet d'afficher davantage de texte, mais cette approche n'est pas couramment utilisée. Cela dit, l'utilisation de cette propriété d'un demi-point de plus sur les ordinateurs de bureau que sur les mobiles est inattendue, et 7 % semble beaucoup plus élevé que je ne l'aurais prédit.

## Les polices variables sont l'avenir

[Polices variables](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Fonts/Guide_polices_variables) permettre à plusieurs poids et styles de police d'être inclus dans le fichier d'une police.

<figure>
  <div class="big-number">1.8%</div>
  <figcaption>Figure 16. Pourcentage de pages contenant une police variable.</figcaption>
</figure>

Même à 1,8%, c'était plus élevé que prévu, même si je suis ravi de voir ce décollage. [Google Fonts v2](https://developers.google.com/fonts/docs/css2) inclut une certaine prise en charge des polices variables.

<figure>
  <a href="/static/images/2019/06_Fonts/fig17.png">
    <img src="/static/images/2019/06_Fonts/fig17.png" alt="Figure 17. Usage of 'font-variation-settings' axes." aria-labelledby="fig17-caption" aria-describedby="fig17-description" width="600" data-width="600" data-height="371" data-seamless data-frameborder="0" data-scrolling="no" data-src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQDogXDb3BwZZHrBT39qccP_LJoCScD3QEi_FmjT_8VDPD_1Srpz-g7ZuuTUEb8pYXBpDmQzZ1hQh7q/pubchart?oid=699343351&amp;format=interactive">
  </a> 
  
  <div id="fig17-description" class="visually-hidden">Diagramme à barres illustrant l'utilisation de la propriété font-variation-settings. 42 % des propriétés des pages de bureau sont définies sur la valeur "opsz", 32 % sur "wght", 16 % sur "wdth", 2 % ou moins sur "roun", "crsb", "slnt", "inln" , et plus. Les différences les plus notables entre les pages de bureau et les pages mobiles sont 26% d’utilisation de "opsz", 38 % de "poids", </div>et<figcaption id="fig17-caption"> 23 % de "wdth".</div>
  <figcaption id="fig17-caption">Figure 17. L'utilisation de <code>font-variation-settings</code> axes.</figcaption>
</figure>

D'après cet ensemble de données volumineux, les échantillons sont très petits. Prenez ces résultats avec un grain de sel. Cependant, `opsz` en tant qu'axe le plus courant sur les pages de bureau est remarquable, suivi de` wght` et `wdth`. D'après mon expérience, les démonstrations d'introduction pour les polices variables sont généralement basées sur le poids.

## Color fonts might also be the future?

<figure>
  <div class="big-number">117</div>
  <figcaption>Figure 18. Le nombre de pages Web de version desktop qui incluent une police de couleur.</figcaption>
</figure>

L'utilisation est pratiquement inexistante, mais vous pouvez consulter l'excellente ressource [Polices de couleur ! WTF ?](https://www.colorfonts.wtf/) pour plus d'informations. Similaire (mais pas du tout) au format SVG pour les polices (ce qui est mauvais et va disparaître), vous permet d'intégrer SVG dans des fichiers OpenType, ce qui est génial et cool.

## Conclusion

Le plus important ici c'est que google Fonts domine la discussion sur les polices Web. Des profondes approches ont été adoptées sur les données que nous avons notées ici. Les points positifs ici sont un accès facile aux polices Web, bons formats de polices (WOFF2), et des configurations gratuites `unicode-range`. Les inconvénients ici sont les inconvénients de performance associés à l'hébergement tiers, aux demandes d'hébergement différent et à l'absence d'accès à `preload`.

J'éspere au futur nous assistions à la "Leverage de la police de variables". Ceci *devrait* être associé à une diminution des demandes de polices Web, les polices variables combinent plusieurs fichiers de polices individuels en un seul fichier de polices composites. Mais l’histoire nous a montré que ce qui se passe habituellement ici, c’est que nous optimisons une chose puis on n'ajoutes plus de choses pour remplir le vide.

Il sera intéressant de voir si la popularité des polices de couleur augmente. J’espère ce qu'ils soient beaucoup plus spécialisés que les polices variables, mais on peut voir une ligne de vie dans l'espace des polices.

Gardez ces polices glacées, tout le monde.
