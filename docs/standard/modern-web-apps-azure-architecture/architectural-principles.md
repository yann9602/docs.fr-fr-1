---
title: "Principes d’architecture"
description: "Architecture des Applications Web avec ASP.NET Core et Azure | Principes d’architecture"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 20524c8aa0e64fd40a1a4a6811063557f74074d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
#<a name="architectural-principles"></a>Principes d’architecture

> « Si générateurs générée bâtiments les programmeurs de façon écrit des programmes, puis le premier woodpecker fournie le long, cela va détruire civilisation. »  
> _\-Victor Weinberg_

## <a name="summary"></a>Résumé

Vous devez aussi créer et concevoir des solutions logicielles avec sa maintenabilité. Les principes présentées dans cette section peuvent vous aider à vous vers des décisions architecturales qui entraîne des applications propre et facile à gérer. En règle générale, ces principes vous guide vers les systèmes de messagerie ou de la création d’applications en dehors des composants individuels qui ne sont pas étroitement couplées à d’autres parties de votre application, mais plutôt de communiquer via des interfaces explicites.

## <a name="common-design-principles"></a>Principes de conception communs

### <a name="separation-of-concerns"></a>Séparation des problèmes

Un principe lors du développement est **séparation des intérêts**. Ce principe déclare que le logiciel doit être divisé selon les types de travail, qu'il effectue. Par exemple, considérez une application qui inclut une logique pour identifier les éléments dignes d’intérêt à afficher à l’utilisateur, et qui met en forme des éléments d’une manière particulière afin de les rendre plus visible. Le comportement est chargé de choisir les éléments à mettre en forme doivent être séparés du comportement responsable de la mise en forme les éléments, ceux-ci étant divisez les problèmes qui sont uniquement par coïncidence associés à un autre.

Point de vue architectural, les applications peuvent être créées logiquement pour suivre ce principe en séparant le comportement d’entreprise principal à partir de la logique de l’interface utilisateur et d’infrastructure. Dans l’idéal, la logique et les règles d’entreprise doivent résider dans un projet distinct, ce qui ne doit pas dépendre d’autres projets dans l’application. Cela permet de garantir que le modèle de gestion est facile à tester et peut évoluer sans être étroitement couplés aux détails d’implémentation de bas niveau. Séparation des problèmes est un aspect clé derrière l’utilisation des couches dans les architectures d’application.

### <a name="encapsulation"></a>Encapsulation

Différentes parties d’une application doivent utiliser **encapsulation** pour isoler les d’autres parties de l’application. Couches et les composants de l’application doivent pouvoir ajuster leur implémentation interne sans rompre leurs collaborateurs tant que contrats externes ne sont pas violées. Utilisation correcte de l’encapsulation permet d’atteindre un couplage faible et modularité dans des conceptions d’application, étant donné que les objets et les packages peuvent être remplacées par implémentations alternatives tant que la même interface est conservée.

Dans les classes, encapsulation est obtenue en limitant l’accès à l’état interne de la classe à l’extérieur. Si un intervenant externe souhaite manipuler l’état de l’objet, il doit le faire via une fonction bien définie (ou l’accesseur Set de propriété), au lieu d’avoir un accès direct à l’état privé de l’objet. De même, les composants d’application et les applications elles-mêmes doivent exposer des interfaces bien définies pour leurs collaborateurs à utiliser, au lieu d’autoriser leur état à modifier directement. Cela libère la conception interne de l’application d’évoluer au fil du temps sans craindre que cela rompt les collaborateurs, tant que les contrats publics sont conservées.

### <a name="dependency-inversion"></a>Inversion de dépendance

La direction de la dépendance au sein de l’application doit être dans la direction d’abstraction, pas les détails d’implémentation. La plupart des applications sont écrites de telle sorte que les dépendances de compilation circulent dans la direction de l’exécution du runtime. Cela génère un graphique de dépendance directe. Autrement dit, si les appels de module A une fonction dans le module B, qui appelle une fonction dans le module C, puis à volonté de fois qu’une compilation dépendent B qui dépend de C, comme indiqué dans la Figure 4-1.

![](./media/image4-1.png)

**Figure 4-1.** Graphique de dépendance directe.

L’application du principe d’inversion de dépendance permet A pour appeler des méthodes sur une abstraction qui implémente de B, rendant possible pour un appel B lors de l’exécution, mais pour B dépendent d’une interface contrôlée par un au moment de la compilation (ainsi, *inversion* la dépendance compilation classique). Au moment de l’exécution, le flux d’exécution du programme reste inchangé, mais l’introduction des interfaces signifie que des implémentations différentes de ces interfaces peuvent facilement être branchées.

![](./media/image4-2.png)

**Figure 4-2.** Graphique de dépendance inversé.

**Inversion de dépendance** est un aspect essentiel de la création d’applications faiblement couplées, étant donné que les détails d’implémentation peuvent être écrite dans dépendent et implémenter des abstractions de niveau supérieur, plutôt que l’autre sens. Les applications qui en résulte sont plus faciles à tester, modulaire et en conséquence. La pratique de *injection de dépendance* est rendue possible en suivant le principe d’inversion de dépendance.

### <a name="explicit-dependencies"></a>Dépendances explicites

**Classes et méthodes doivent requérir explicitement tous les objets de collaboration que dont ils ont besoin pour fonctionner correctement.** Constructeurs de classe de fournissent une opportunité pour les classes identifier les éléments que dont ils ont besoin pour être dans un état valide et fonctionne correctement. Si vous définissez des classes qui peuvent être construits et appelé, mais qui fonctionnera correctement si certains composants globales ou d’infrastructure sont en place, ces classes sont en cours *malveillants* avec leurs clients. Le contrat de constructeur informe le client qu’il doit uniquement les éléments spécifiés (éventuellement nothing si la classe utilise uniquement un constructeur par défaut), mais ensuite lors de l’exécution, qu'il se trouve l’objet avait réellement besoin d’un autre élément.

En suivant le principe de dépendances explicites, vos classes et méthodes sont en cours objective avec leurs clients qu’ils ont besoin pour fonctionner. Cela rend votre code plus correctement documentés et votre codage contrats plus convivial, étant donné que les utilisateurs visualisent une confiance tant qu’ils fournissent ce qui est requis sous la forme d’une méthode ou comporteront des paramètres du constructeur, les objets qu’il utilise correctement lors de l’exécution.

### <a name="single-responsibility"></a>Responsabilité unique

Le principe de responsabilité unique s’applique à la conception orientée objet, mais peut également être considéré comme un principe architecture similaire à la séparation des problèmes. Elle indique que les objets doivent avoir qu’une seule responsabilité et qu’ils doivent avoir qu’une seule raison de modifier. Plus précisément, le seul cas dans lequel l’objet doit modifier est si le mode dans lequel il effectue sa un responsabilité doit être mis à jour. Selon ce principe vous aide à produire plus faiblement couplées et systèmes modulaires, depuis les nombreux types de nouveau comportement peuvent être implémentées en tant que de nouvelles classes, plutôt qu’en ajoutant la responsabilité pour les classes existantes. Ajout de nouvelles classes est toujours plus sûre que la modification des classes existantes, car aucun code encore varie selon les nouvelles classes.

Dans une application monolithique, nous pouvons appliquer le principe de responsabilité unique à un niveau élevé pour les couches de l’application. Responsabilité de présentation doit rester dans le projet d’interface utilisateur, alors que l’accès aux données responsabilité doit être conservée au sein d’un projet d’infrastructure. Logique métier doit être conservée dans le projet de base d’application, où il peut être facilement testé et peut évoluer indépendamment à partir d’autres tâches.

Lorsque ce principe est appliqué à l’architecture de l’application et dirigé vers son point de terminaison logique, vous obtenez microservices. Un microservice donné doit avoir une seule responsabilité. Si vous avez besoin étendre le comportement d’un système, il est généralement préférable de le faire en ajoutant des microservices supplémentaires, plutôt qu’en ajoutant la responsabilité à un autre existant.

[En savoir plus sur l’architecture de microservices](http://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Ne répétez pas vous-même (sec)

L’application doit éviter de spécifier le comportement lié à un concept spécifique à plusieurs endroits, car il s’agit d’une source fréquente des erreurs. À un moment donné, une modification de la configuration requise nécessite la modification de ce comportement et la probabilité qu’au moins une instance du comportement ne pourront pas être mis à jour entraîne un comportement incohérent du système.

Au lieu de dupliquer la logique, encapsuler dans une construction de programmation. Faire créer l’autorité unique sur ce comportement, et de toute autre partie de l’application qui requiert cette utilisation comportement la construction de nouveau.

> [!NOTE]
> Éviter la liaison ensemble le comportement qui est uniquement par coïncidence répétitive. Par exemple, le simple fait que deux constantes différentes les deux ont la même valeur, cela ne signifie pas qu'avoir qu’une seule constante, si le point de vue conceptuel, elle fait référence aux mêmes éléments.

### <a name="persistence-ignorance"></a>Ignorant la persistance

**Ignorant la persistance** (PI) fait référence aux types qui doivent être persistants, mais dont le code n’est pas affecté par le choix de la technologie de persistance. Ces types dans .NET sont parfois appelés Plain Old CLR Objects (POCOs), car ils n’avez pas besoin d’hériter d’une classe de base implémente une interface particulière. Ignorant la persistance est utile, car elle permet le même modèle d’entreprise à rendre persistantes de plusieurs façons, offre davantage de flexibilité pour l’application. Choix de persistance peut changer au fil du temps, à partir de la technologie d’une base de données vers un autre, ou d’autres formes de persistance peuvent être requises en plus quel que soit l’application a démarré avec (par exemple, à l’aide de cache Redis Azure DocumentDb à un base de données relationnelle).

Voici quelques exemples de violations de ce principe :

-   Une classe de base requise

-   Une implémentation d’interface requise

-   Classes responsables de l’enregistrement eux-mêmes (par exemple, le modèle d’enregistrement actif)

-   Constructeur par défaut obligatoire

-   Propriétés nécessitant le mot clé virtual

-   Spécifique à la persistance des attributs requis

Le fait que les classes ont toutes les fonctionnalités et les comportements ci-dessus ajoute un couplage entre les types devant être persistantes et le choix de la technologie de persistance, ce qui tend à adopter les nouvelles stratégies d’accès aux données à l’avenir.

### <a name="bounded-contexts"></a>Contextes de limitées

**Délimitée contextes** sont un modèle central dans la conception. Elles offrent un moyen de complexité de réalisation dans des applications de grande taille ou organisations en fractionnant en modules conceptuels distincts. Chaque module conceptuel alors représente un contexte qui est distincte des autres contextes (donc limités) et peut évoluer indépendamment. Chaque contexte délimitée doit idéalement être libre de choisir ses propres noms pour les concepts qu’il contient et doit avoir un accès exclusif à son propre magasin de persistance.

Au minimum, des applications web individuelles efforcez-vous être son propre contexte délimitée, avec leur propre magasin de persistance pour leur modèle d’entreprise, plutôt que d’une base de données de partage avec d’autres applications. Communication entre les contextes délimitées se produit via des interfaces de programmation, plutôt que via une base de données partagée, ce qui permet de logique métier et placer des événements à prendre en réponse aux modifications qui ont lieu. Délimité contextes carte étroitement à microservices, également dans l’idéal, implémentés sous forme de leurs propres contextes délimitées individuels.

> ### <a name="references--modern-web-applications"></a>Références à des Applications Web
> - **Séparation des problèmes**  
> <http://deviq.com/SEPARATION-of-Concerns/>
> - **Encapsulation** <http://deviq.com/encapsulation/>
> - **Principe d’Inversion de dépendance**  
> <http://deviq.com/Dependency-inversion-Principle/>
> - **Principe des dépendances explicites**  
> <http://deviq.com/Explicit-Dependencies-Principle/>
> - **Ne répétez pas vous-même**  
> <http://deviq.com/don-t-Repeat-Yourself/>
> - **Ignorant la persistance**  
> <http://deviq.com/Persistence-ignorance/>
> - **Limite de contexte**  
> <https://martinfowler.com/bliki/BoundedContext.HTML>

> [!div class="step-by-step"]
[Précédente] (choose-between-traditional-web-and-single-page-apps.md) [suivant] (commun-web-application-architectures.md)
