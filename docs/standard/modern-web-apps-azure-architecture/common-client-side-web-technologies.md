---
title: "Technologies web côté client courantes"
description: "Architecture des Applications Web avec ASP.NET Core et Azure | Technologies web côté client courantes"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 1084aee3d81a5df6ac99d6ec0e2ef647b4173c24
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="common-client-side-web-technologies"></a>Technologies Web côté Client courantes

> « Sites Web doivent apparaîtront correctement à partir de l’intérieur et du délai d’attente ».  
> _-Paul Cookson_

## <a name="summary"></a>Résumé

Les applications ASP.NET Core sont des applications web et ils s’appuient généralement sur des technologies web côté client telles que HTML, CSS et JavaScript. En séparant le contenu de la page (HTML) à partir de sa mise en page et de style (CSS) et son comportement (via JavaScript), les applications web complexes peuvent tirer parti du principe de la séparation des intérêts. Les modifications ultérieures à la structure, la conception ou le comportement de l’application peuvent être apportées plus facilement quand ces problèmes ne sont pas étroitement liés.

Alors que HTML et CSS sont relativement stable, JavaScript, au moyen de l’infrastructure d’application et les développeurs d’utilitaires utiliser pour générer des applications web, évolue à vitesse blindée. Ce chapitre examine quelques méthodes que JavaScript est utilisé par les développeurs de web dans le cadre du développement d’applications, comme fournit une vue d’ensemble des bibliothèques de côté client angulaire et réagir.

## <a name="html"></a>HTML

HTML (HyperText Markup Language) est le langage de balisage standard utilisé pour créer des pages web et des applications web. Ses éléments forment les blocs de construction des pages, qui représente le texte mis en forme, des images, des entrées de formulaire et d’autres structures. Lorsqu’un navigateur effectue une demande à une URL, si l’extraction d’une page ou une application, la première qui est retourné est un document HTML. Inclure des informations supplémentaires sur son apparence et la disposition sous la forme de CSS, ou le comportement dans l’écran de JavaScript ou faire référence à ce document HTML.

## <a name="css"></a>CSS

CSS (Cascading Style Sheets) est utilisé pour contrôler l’apparence et la disposition des éléments HTML. Styles CSS peuvent être appliquées directement à un élément HTML, définies séparément dans la même page, ou définis dans un fichier distinct et référencés par la page. Styles de mise en cascade selon comment ils sont utilisés pour sélectionner un élément HTML donné. Par exemple, un style peut-être s’appliquer à un document entier, mais il est substitué par un style appliqué à un élément particulier. De même, un élément style est substitué par un style appliqué à une classe CSS qui a été appliquée à l’élément, qui à son tour est substitué par un style ciblant une instance spécifique de l’élément (via son id). Figure 6-1

**Figure 6-1.** Règles CSS spécificité, dans l’ordre.

![](./media/image6-1.png)

Il est préférable de conserver les styles dans leurs propres fichiers de feuille de style distincte et à utiliser en fonction de sélection en cascade pour implémenter les styles cohérentes et réutilisables dans l’application. Placement des règles de style dans le code HTML doit être évitée, et appliquer des styles à des éléments individuels (plutôt que des classes ensemble d’éléments ou d’éléments qui ont une classe particulière de CSS appliquée) doit être l’exception, pas la règle.

### <a name="css-preprocessors"></a>Préprocesseurs CSS

Feuilles de style CSS ne disposent pas de prise en charge de la logique conditionnelle, variables et autres fonctionnalités de langage de programmation. Par conséquent, des feuilles de style volumineux incluent souvent un grand nombre de répétitions, comme la même couleur, la police ou autre paramètre est appliqué à plusieurs types d’éléments HTML et des classes CSS. Les Préprocesseurs CSS peuvent aider à vos feuilles de style suivent la [principe sec](http://deviq.com/don-t-repeat-yourself/) en ajoutant la prise en charge pour les variables et logique.

Les plus populaires Préprocesseurs CSS sont Sass et inférieure. Les deux étendent CSS et présentent une compatibilité descendante, ce qui signifie qu’un fichier CSS simple est un Sass valide ou le fichier. Sass est basé sur Ruby inférieur est basé sur JavaScript et généralement s’exécutent tous deux dans le cadre de votre processus de développement local. Ont tous deux disponible, ainsi que d’intégrés de prise en charge dans Visual Studio pour exécuter les outils en ligne de commande à l’aide de tâches Gulp ou Grunt.

## <a name="javascript"></a>JavaScript

JavaScript est un langage de programmation dynamique, interprété qui a été normalisé dans la spécification du langage ECMAScript. Il est le langage de programmation du web. Comme CSS, JavaScript peut être définie en tant qu’attributs dans les éléments HTML, en tant que blocs de script dans une page ou dans des fichiers distincts. CSS, comme il a généralement recommandé pour organiser les JavaScript en fichiers distincts, mettez-le séparés autant que possible du code HTML trouvée sur les pages web individuelles ou des vues de l’application.

Lorsque vous travaillez avec JavaScript dans votre application web, il existe quelques tâches que vous devrez généralement effectuer :

-   Sélection d’un élément HTML et la récupération et/ou sa valeur de la mise à jour

-   Interrogation d’une API Web pour les données

-   Envoi d’une commande à une API Web (et répond à un rappel avec son résultat)

-   Exécution de la validation

Vous pouvez effectuer toutes ces tâches avec JavaScript autonome, mais de nombreuses bibliothèques existent pour simplifier ces tâches. Le premier et le plus de succès de ces bibliothèques est jQuery, qui continue à être un choix très répandu pour simplifier ces tâches sur les pages web. Pour les Applications à Page unique (ZPS), jQuery ne fournit pas plusieurs fonctionnalités souhaitées qui offrent des angulaire et réagir.

### <a name="legacy-web-apps-with-jquery"></a>Applications Web héritées avec jQuery

Bien que les anciennes par les normes d’infrastructure JavaScript, jQuery continue à être une bibliothèque très fréquemment utilisée pour travailler avec HTML/CSS et génération d’applications qui effectuent des appels AJAX aux API web. Toutefois, jQuery fonctionne au niveau du modèle d’objet document (DOM) navigateur et par défaut offre uniquement un modèle impératif, plutôt que déclaratif.

Par exemple, imaginez que si la valeur d’une zone de texte est supérieur à 10, un élément sur la page doit être rendu visible. Dans jQuery, cela est généralement implémentée en écrivant un gestionnaire d’événements avec le code qui serait inspecter la valeur de la zone de texte et définir la visibilité de l’élément cible en fonction de cette valeur. Il s’agit d’une approche basée sur le code impérative. Une autre infrastructure peut utiliser à la place de la liaison de données pour lier la visibilité de l’élément à la valeur de la zone de texte de façon déclarative. Cela n’a pas besoin de l’écriture de code, mais au lieu de cela requiert uniquement décorer les éléments impliqués dans les attributs de liaison de données. À mesure que les comportements de côté client augmentent plus complexes, la liaison de données approches fréquemment résultat dans des solutions plus simples avec moins de code et complexité conditionnelle

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs une infrastructure SPA

| **Facteur** | **jQuery** | **Angulaire**|
|--------------------------|------------|-------------|
| Extrait le DOM | **Oui** | **Oui** |
| Prise en charge d’AJAX | **Oui** | **Oui** |
| Liaison de données déclarative | **Non** | **Oui** |
| Le routage MVC-style | **Non** | **Oui** |
| Création de modèles | **Non** | **Oui** |
| Routage de lien ciblé | **Non** | **Oui** |

La plupart des fonctionnalités qui ne dispose pas de jQuery intrinsèquement peut être ajoutée avec l’ajout d’autres bibliothèques. Toutefois, une infrastructure SPA comme angulaire fournit ces fonctionnalités de façon plus intégrée, étant donné que vise tous à l’esprit à partir du début. En outre, jQuery est une bibliothèque très impérative, c'est-à-dire que vous devez appeler les fonctions de jQuery afin de faire quelque chose avec jQuery. La plupart du travail et des fonctionnalités qui fournissent des infrastructures SPA est possible de façon déclarative, ne nécessitant aucun code réel à écrire.

Liaison de données est un bon exemple. Dans jQuery, il suffit habituellement une ligne de code pour obtenir la valeur d’un élément DOM ou d’un élément de valeur. Toutefois, vous devez écrire ce code chaque fois que vous devez modifier la valeur de l’élément, et parfois s’affiche dans plusieurs fonctions dans une page. Un autre exemple courant est la visibilité de l’élément. Dans jQuery, il peut exister des nombreux emplacements distincts et où écrire le code pour contrôler si certains éléments étaient visibles. Dans chacun de ce cas, lors de l’utilisation de la liaison de données, aucun code ne besoin d’être écrite. Vous liez simplement la valeur ou la visibilité des éléments en question pour une *viewmodel* sur la page et les modifications qui viewmodel automatiquement apparaîtraient dans l’élément lié.

### <a name="angular-spas"></a>SPAs angulaires

AngularJS est rapidement devenu une des infrastructures de JavaScript les plus populaires au monde. Avec 2 angulaire, l’équipe reconstruit le framework dès le départ des (à l’aide de [TypeScript](https://www.typescriptlang.org/)) et renommé à partir de AngularJS pour simplement angulaire. Actuellement sur la version 4, angulaire reste une infrastructure robuste pour la création d’Applications à Page unique.

Applications angulaires sont générées à partir des composants. Composants de combinent les modèles HTML avec des objets spéciaux et contrôlent une partie de la page. Un composant simple à partir de documents d’angulaire est illustré ici :

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Les composants sont définis à l’aide de la @Component fonction d’élément décoratif, qui prend dans les métadonnées relatives au composant. La propriété du sélecteur identifie l’id de l’élément sur la page où ce composant sera affiché. La propriété de modèle est un modèle HTML simple qui inclut un espace réservé qui correspond à la propriété nom du composant définie sur la dernière ligne.

En utilisant des composants et des modèles, au lieu des éléments DOM, les applications angulaires peuvent fonctionner à un niveau supérieur d’abstraction et avec moins de code globale à celui des applications écrites à l’aide de JavaScript simplement les (également appelé « vanille JS ») ou avec jQuery. Angulaire impose également un ordre sur la manière dont vous organisez vos fichiers de script côté client. Par convention, les applications angulaires utilisent une structure de dossiers commune, module et le composant fichiers de script que se trouvent dans un dossier d’application. Scripts angulaires soucieux de génération, déploiement et test de l’application sont généralement placés dans un dossier de niveau supérieur.

Angulaire rend également une grande utilité des outils de ligne de commande (CLI). Prise en main du développement angulaire localement (en supposant que vous avez déjà git et npm installé) se compose de simplement cloner un référentiel à partir de GitHub et en cours d’exécution \`npm installer\` et \`npm début\`. Au-delà de cela, angulaire fourni son propre outil CLI qui permettre créer des projets, ajouter des fichiers et des tâches de test, le regroupement et le déploiement. Cette interface pour les outils sa convivialité rend angulaire particulièrement compatible avec ASP.NET Core, qui propose aussi grande CLI prennent en charge.

Microsoft a développé une application de référence, [eShopOnContainers](http://aka.ms/MicroservicesArchitecture), qui inclut une implémentation SPA angulaire. Cette application inclut des modules Angular pour gérer le magasin en ligne les articles du panier d’achat, charge et l’affichage de son catalogue et de gestion de la création de la commande. Vous pouvez afficher et télécharger l’exemple d’application à partir de [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>réagir

Contrairement aux angulaire, qui offre un complet implémentation du modèle Model-View-Controller, réagissent ne concerne que les vues. Il n’est pas une infrastructure, simplement une bibliothèque, et pour générer un SPA, vous devrez donc tirer parti de bibliothèques supplémentaires.

Une des fonctionnalités les plus importantes de réaction est l’utilisation d’un modèle virtuel DOM. Le DOM virtuel fournit React avec plusieurs avantages, notamment de performances (DOM virtuel peut optimiser les parties du modèle DOM réel doivent être mis à jour) et testabilité (sans devoir disposer d’un navigateur pour tester React et ses interactions avec son modèle DOM virtuel).

React également est inhabituel dans son fonctionnement avec du code HTML. Au lieu d’avoir une séparation stricte entre le code et le balisage (avec des références à JavaScript qui apparaissent dans les attributs HTML par exemple), de réagir ajoute HTML directement dans le code JavaScript en tant que JSX. JSX est la syntaxe de type HTML qui peut compiler à JavaScript pure. Exemple :

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Si vous connaissez déjà JavaScript, la réaction d’apprentissage doit être facile. Il n’est pas autant courbe d’apprentissage ou une syntaxe spéciale impliqués en tant qu’avec angulaire ou d’autres bibliothèques populaires.

Étant donné que React n’est pas une infrastructure complète, vous souhaiterez généralement autres bibliothèques pour gérer des opérations telles que le routage, les appels d’API et la gestion des dépendances web. Est la chose intéressante, vous pouvez choisir la bibliothèque meilleures pour chacun d’eux, mais l’inconvénient est que vous devez effectuer toutes ces décisions et vérifiez que toutes vos bibliothèques choisis fonctionnent bien lorsque vous avez terminé. Si vous souhaitez un bon point de départ, vous pouvez utiliser un starter kit comme Slingshot réagir, lequel préemballages un ensemble de bibliothèques compatibles avec React.

### <a name="choosing-a-spa-framework"></a>Choix d’une infrastructure SPA

Lorsque vous envisagez de quelle infrastructure JavaScript convient le mieux pour prendre en charge votre SPA, gardez à l’esprit les points suivants :

-   Votre équipe s’est familiarisé avec l’infrastructure et de ses dépendances (y compris TypeScript dans certains cas) ?

-   Comment opinionated est l’infrastructure, et vous acceptez avec sa méthode par défaut de faire les choses ?

-   (Ou une bibliothèque d’accompagnement) comprend toutes les fonctionnalités requises par votre application ?

-   Il est bien documenté ?

-   Comment active est sa communauté ? Création de nouveaux projets sont générés avec celui-ci ?

-   Comment active est son équipe ? Problèmes étant résolues et les nouvelles versions sont livrés régulièrement ?

Infrastructures JavaScript continuent à faire évoluer avec une fréquence blindé. Utilisez les considérations répertoriées ci-dessus pour aider à atténuer le risque de choisir une infrastructure que vous allez plus loin regrettons dépend. Si vous êtes particulièrement réticents risque, envisagez une infrastructure qui offre une prise en charge commerciale et/ou est développée par une grande entreprise.

> ### <a name="references--client-web-technologies"></a>Références à des Technologies Web Client
> - **HTML et CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. MOINS**  
> <https://www.keycdn.com/blog/sass-VS-less/>
> - **Styles de police impressionnant, Sass et les applications ASP.NET Core avec moins**  
> <https://docs.Microsoft.com/ASPNET/Core/client-side/less-sass-FA>
> - **Développement côté client dans ASP.NET Core**  
> <https://docs.Microsoft.com/ASPNET/Core/client-side/>
> - **jQuery**  
> <https://jQuery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jQuery-angularjs-Comparison-migration-Walkthrough>
> - **Angulaire**  
> <https://Angular.IO/>
> - **Réagir**  
> <https://Facebook.github.IO/React/>
> - **Réagir Slingshot**  
> <https://github.com/coryhouse/React-Slingshot>
> - **Réagir vs angulaire 2 comparaison**  
> <https://www.codementor.IO/codementorteam/React-VS-Angular-2-Comparison-Beginners-Guide-lvz5710ha>
> - **Infrastructures JavaScript meilleures 5 de 2017**  
> <https://hackernoon.com/5-Best-JavaScript-Frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
[Précédente] (commun-web-application-architectures.md) [suivant] (develop-asp-net-core-mvc-apps.md)
