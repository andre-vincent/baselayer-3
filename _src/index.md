---
title: Commencer
mainHeading: Premiers pas avec Baselayer
layout: base.njk
nextPage: "/typography/"
nextLink: "Typography"
---

## Introduction

<p class="t-lg">Conçu comme un bon point de départ, Baselayer peut être tout ce dont vous avez besoin pour les petits projets tels que les sites Web statiques et les blogs. Ou vous pouvez l'utiliser comme <em>baselayer</em> pour démarrer rapidement votre méga projet.</p>

Prêt à être utilisé tel quel, la feuille de style {{ metadata.filesize }} (minifiée) de Baselayer vous donne tout cela :

* Une réinitialisation CSS moderne

* Éléments typographiques et de forme sans classe de style minimaliste

* Fonctionnalités d'accessibilité fiables pour les utilisateurs de technologies d'assistance

* Un système léger de classes utilitaires pour contrôler les dimensions, le positionnement, l'espacement, les bordures, le texte et les images

* `@container` interroge les utilitaires de mise en page réactifs à l'aide de la grille CSS et de la flexbox

* Typographie, mise en page et espacement réactifs à l'aide des rampes `clamp()`

* Un système compact de luminosité des couleurs basé sur `color-mix(in OKLCH)` pour le texte, les bordures et les arrière-plans

* Mode sombre intégré utilisant `light-dark()`

* Contrôle de thématisation à l'aide de variables CSS

* Et plus encore

## Technologies CSS modernes

Baselayer ne prend en charge que les navigateurs Web à jour (2023 à partir de) [compatibilité de base](https://developer.mozilla.org/en-US/docs/Glossary/Baseline/Compatibility) (Safari, Firefox, Chrome, Edge, etc.). Tels que :

* [Container queries (inline-size)](https://caniuse.com/css-container-queries)
* [CSS Grid](https://caniuse.com/css-grid)
* [Math functions (e.g. clamp)](https://caniuse.com/?search=css%20math%20functions)
* [Custom properties (variables)](https://caniuse.com/css-variables)
* [color-mix() function](https://caniuse.com/?search=color-mix())
* [light-dark() function](https://caniuse.com/mdn-css_types_color_light-dark)
* [CSS class nesting](https://caniuse.com/css-nesting)
* [Cascade layers](https://caniuse.com/css-cascade-layers)

## La philosophie de conception de Baselayer

La philosophie de conception derrière le projet Baselayer CSS est la suivante :

* Visez à être un bon point de départ - une _couche de base_ pour un projet de conception Web.

* Étant si petit ({{ metadata.filesize }}), il y a moins que vous devez écraser afin de le styliser à votre façon (et la plupart des choses dans Baselayer peuvent être remodelées par des variables CSS). Ainsi, il n'y a pas besoin d'un processus de purge pour supprimer une lourde charge utile de styles Baselayer inutilisés.

* PostCSS uniquement - pas de préprocesseurs.

## Construit à l'aide de PostCSS

Baselayer est construit à l'aide de [PostCSS](https://postcss.org) et de certains plugins. Les plugins utilisés par Baselayer sont :

* [Postcss-import](https://github.com/postcss/postcss-import) - afin que Baselayer puisse être construit à partir de fichiers CSS séparés

* [Cssnano](https://cssnano.co) - pour supprimer les commentaires et réduire la sortie `baselayer.min.css`

**Remarque :** ni [postcss-preset-env](https://preset-env.cssdb.org) ni [autoprefixer](https://github.com/postcss/autoprefixer) n'ont été utilisés dans Baselayer. Et les préprocesseurs tels que Sass, Less, Stylus, etc. ne sont pas nécessaires.

## Une réinitialisation CSS moderne

La réinitialisation de la couche de base est une combinaison "meilleure des deux" de [réinitialisation CSS personnalisée de Josh W Comeau](https://www.joshwcomeau.com/css/custom-css-reset/) et [réinitialisation CSS (plus) moderne d'Andy Bell](https://andy-bell.co.uk/a-more-modern-css-reset/).

Sur cette base, Baselayer s'occupe ensuite des bases en définissant une typographie et des styles minimalistes et faciles à lire pour les boutons et les formulaires.

## Fonctionnalités d'accessibilité intégrées de Baselayer

Baselayer a deux fonctionnalités d'accessibilité "indispensables" intégrées.

### (1,) États de mise au point

Après avoir expérimenté et testé divers styles d'état de mise au point, j'ai décidé de baser ceux du service national de santé britannique [système de conception NHS.uk](https://design-system.service.gov.uk/get-started/focus-states/) et du gouvernement britannique [système de conception GOV.UK](https://design-system.service.gov.uk/get-started/focus-states/).

1. Les liens reçoivent un fond ambré, un texte noir et un soulignement noir épais sur `:focus-visible` - de sorte que l'élément est clairement visible dans un large éventail de contextes.

2. Les éléments interactifs tels que les entrées de formulaire, les boutons de formulaire, les détails pliables et les éléments avec un contenu débordant ont ce qui ressemble à une "double bordure" jaune et noire qui apparaît sur `:focus` (en fait, il est créé par un contour et une ombre de boîte).

**Note:** Un `<button>` qui ne se trouve pas dans un `<form>`, et un `<button type="button">` ne recevront pas l'anneau `:focus` (mais il recevra l'anneau sur `:focus-visible`). C'est vrai pour la plupart des navigateurs, à l'exception de Safari : Safari n'affiche pas les anneaux `:focus` sur les boutons, et il ne place pas l'accent sur les éléments débordants, ni sur l'entrée du sélecteur de couleurs.

Ces états de mise au point sont visibles sur un large éventail d'arrière-plans colorés, dans des thèmes clairs et sombres. (Voir aussi [couleurs et accessibilité]({{ "/colors/#colors-and-accessibility" | url }}).) Une augmentation de l'indice z a été ajoutée pour empêcher l'anneau de mise au point de se replier sous un élément voisin, par exemple dans les groupes d'entrée/boutons.

Exemples:

<form class="my-3">
  <fieldset class="flex">
    <legend>Exemple d'abonnement à une lettre d'information électronique</legend>
    <input class="w-100%" type="email" id="example-input-email" placeholder="Votre email">
    <input type="submit" name="submit" value="Subscribe">
  </fieldset>
</form>


Utilisez la touche TAB de votre clavier pour afficher le focus de ces liens et boutons :


<div class="my-3 b-thin">
  <div class="grid sm:equal-4-cols">
    <div class="p-3 flex flex-column flex-center flex-middle bg-white bg-dark-invert">
    <p><a href="/#">Link</a></p>
    <p><button type="button">Button</button></p>
    </div>
    <div class="p-3 flex flex-column flex-center flex-middle bg-blue bg-700">
    <p><a class="t-blue t-200 hover:t-300" href="/#">Link</a></p>
    <p><button class="r-2" type="button">Button</button></p>
    </div>
    <div class="p-3 flex flex-column flex-center flex-middle bg-red bg-500 bg-dark-invert">
    <p><a class="t-blue t-200 hover:t-300" href="/#">Link</a></p>
    <p><button class="r-2" type="button">Button</button></p>
    </div>
    <div class="p-3 flex flex-column flex-center flex-middle bg-black bg-dark-invert">
    <p><a class="t-blue t-200 t-dark-invert hover:t-300" href="/#">Link</a></p>
    <p><button class="r-pill" type="button">Button</button></p>
    </div>
  </div>
</div>

### (2.) La classe `visually-hidden` 

La classe `visually-hidden` est utilisée pour fournir du contenu supplémentaire aux lecteurs d'écran, pour une meilleure accessibilité. Par exemple, il est préférable d'avoir "sauter le lien" au-dessus de la barre de navigation supérieure de votre site Web, mais de le cacher (visuellement) pour les utilisateurs malvoyants.

```
<a href="#main-content"
  tabindex="1"
  class="block p-2 visually-hidden"
>
  Passer au contenu de la page
</a>

<!-- Logo et menu de navigation du site ici -->

<div id="main-content">
  ...
</div>
```
