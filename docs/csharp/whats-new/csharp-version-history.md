---
title: "L’historique de c# - Guide c#"
description: "Ce qui l’apparence de la langue, dans les versions antérieures, et comment a elle a évolué depuis ?"
keywords: "C#, .NET, .NET Core, quelles sont les nouveautés, l’historique de c#"
author: erikdietrich
ms.author: wiwagn
ms.date: 09/20/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 207c97c5dd7e04f815da61bff7f44393aea86222
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="the-history-of-c"></a>L’historique du langage c# #

Ce qui le langage ressemble dans ses premières incarnations ? Et comment a elle a évolué au fil des ans ?

## <a name="c-version-10"></a>C# version 1.0

Lorsque vous revenez en arrière et regardez, c# version 1.0 présentait un lot sur Java. En tant que [dans le cadre de ses objectifs énoncés pour ECMA](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), il a cherché à être une « objectif simple, moderne, général et orienté objet langue. »  À l’heure, recherche comme Java destinée il atteint ces objectifs de conception.

Mais si vous revenez sur c# 1.0 maintenant, vous vous-même un peu la liste. Il n’offraient pas les fonctionnalités intégrées async et certaines fonctionnalités efficace autour génériques qui ont pour reçoivent. En fait, il n’offraient pas de génériques complètement.  Et [LINQ](../linq/index.md)? Non disponible encore. Cela équivaudrait à des années à venir.

C# version 1.0 de recherche simplifié de fonctionnalités, par rapport à la date du jour. Vous trouverez vous-même écrire du code détaillé. Mais, encore, vous devez commencer quelque part. C# version 1.0 est une alternative viable à Java sur la plateforme Windows.

## <a name="c-version-20"></a>C# version 2.0

Maintenant les choses commencent à devenir intéressantes. Examinons des principales fonctionnalités de c# 2.0, publiée en 2005, ainsi que Visual Studio 2005 :

- [Génériques](../programming-guide/generics/index.md)
- [Types partiels](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Méthodes anonymes](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Types Nullable](../programming-guide/nullable-types/index.md)
- [Itérateurs](../programming-guide/concepts/iterators.md)
- [Covariance et contravariance](../programming-guide/concepts/covariance-contravariance/index.md)

Bien que peut avoir démarré c# comme langage orientée objet (OO) relativement générique, le langage c# version 2.0 changé qui pressé. Une fois qu’elles avaient pieds qu’ils contiennent, je les ai après certains points faibles de développeur grave. Et je les ai après leur considérablement.

Avec les génériques, vous disposez des types et méthodes qui peuvent opérer sur un type arbitraire tout en conservant la sécurité de type. Ainsi, par exemple, avoir un <xref:System.Collections.Generic.List%601> vous permet d’avoir `List<string>` ou `List<int>` et effectuer des opérations de-safe de type sur les chaînes ou des entiers lorsque vous itérez au sein de ces. Il est préférable que la création de `ListInt` l’attention des héritiers ou effectuer un cast de `Object` pour chaque opération.

Itérateurs c# version 2.0 mises. Pour résumer, cela vous permet de parcourir les éléments dans un `List` (ou d’autres types énumérables) avec un `foreach` boucle. En tant qu’une partie de première classe du langage ayant considérablement amélioré la lisibilité de la langue et possibilité de personnes raison sur le code.

Pourtant, C# continué et lire un peu de rattrapage avec Java. Java avait déjà publié des versions qui incluaient les génériques et les itérateurs. Mais qui pourrait être modifié dès que les langues continués à évoluer éloignés.

## <a name="c-version-30"></a>C# version 3.0

C# version 3.0 fournie dans fin 2007, ainsi que de Visual Studio 2008, bien que le bateau complète des fonctionnalités de langage se sont réellement avec c# version 3.5. Cette version marquée comme une modification majeure de la croissance de c#. Elle établie c# comme langage de programmation vraiment formidable. Examinons certaines fonctionnalités principales dans cette version :

- [Propriétés automatiques implémentée](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Types anonymes](../programming-guide/classes-and-structs/anonymous-types.md)
- [Expressions de requête](../linq/query-expression-basics.md)
- [Expression lambda](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [Arborescences d’expressions](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [Méthodes d’extension](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)

Dans retrospect, bon nombre de celles-ci semblent inévitable et non séparables. Ils s’assemblent stratégique. Il est généralement considéré que fonctionnalité robuste de la version c# a l’expression de requête, également appelé Language-Integrated Query (LINQ).

Une vue plus subtils examine tress d’expression, les expressions lambda et les types anonymes fondation sur laquelle est construite LINQ. Toutefois, dans les deux cas, c# 3.0 a présenté un concept révolutionnaire. C# 3.0 ont commencé à jeter les bases de l’activation c# dans un hybride orienté objet / fonctionnel language.

Plus précisément, vous pouvez maintenant écrire SQL-style, des requêtes déclaratives pour effectuer des opérations sur des collections, entre autres choses. Au lieu d’écrire un `for` de boucle pour calculer la moyenne d’une liste d’entiers, vous pouvez le faire maintenant simplement comme `list.Average()`. La combinaison des expressions de requête et les méthodes d’extension a bien cette liste d’entiers avait eu beaucoup plus efficacement.

Nécessaire aux utilisateurs de comprendre et d’intégrer le concept de réellement le temps, mais ils le faisaient progressivement. Et maintenant, années plus tard, code est beaucoup plus concis, simple et fonctionnel.

## <a name="c-version-40"></a>C# version 4.0

C# version 4.0 aurait dû fois difficile montre à l’état révolutionnaire de version 3.0. Avec la version 3.0, c# a déplacé la langue bien déconnecter à partir de l’ombre de Java et importance. La langue a été de devenir élégante.

La prochaine version introduit de nouvelles fonctionnalités intéressantes :

- [Liaison dynamique](../language-reference/keywords/dynamic.md)
- [Arguments facultatifs/nommé](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Générique covariant et contravariant](../../standard/generics/covariance-and-contravariance.md)
- [Types interop incorporés](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

Les types interop incorporés soulagé un travail de déploiement. Générique covariance et contravariance vous donnent davantage de puissance pour utiliser des génériques, mais ils sont un peu éducation et probablement plus appréciée par les auteurs de bibliothèque et le framework. Les paramètres nommés et facultatifs vous permettent d’éliminer les nombreuses surcharges de méthode et fournir des raisons de commodité. Mais aucune de ces fonctionnalités est exactement paradigme de modification.

La fonctionnalité principale a été l’introduction de la `dynamic` (mot clé). Le `dynamic` mot clé introduits dans c# version 4.0, la possibilité de remplacer le compilateur sur la saisie de la compilation. En utilisant le mot clé dynamique, vous pouvez créer des constructions semblables aux langages dynamiquement typés tels que JavaScript. Vous pouvez créer un `dynamic x = "a string"` , puis ajouter six, laissant le runtime à ce qui doit se produire ensuite.

Cela vous donne la possibilité pour les erreurs, mais également d’énergie dans le langage.

## <a name="c-version-50"></a>C# version 5.0

C# version 5.0 était une version très ayant le focus de la langue. Presque tous les efforts de cette version a pris un autre concept de langage révolutionnaire.  Voici la liste des fonctionnalités principales :

- [Membres asynchrones](../async.md)
- [Attributs d’informations de l’appelant](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

L’attribut info appelant vous permet de récupérer facilement les informations sur le contexte dans lequel vous êtes en cours d’exécution sans avoir recours à une multitude de code de réflexion réutilisable. Il a de nombreuses utilisations dans le diagnostic et les tâches de journalisation.

Mais `async` et `await` sont les étoiles réelles de cette version. Lorsque ces fonctionnalités sont apparus dans 2012, C# modifier le jeu en intégrant le comportement asynchrone dans la langue que celle d’un participant de première classe. Si vous avez déjà traitées avec les opérations longues et l’implémentation de sites Web de rappels, vous aimé probablement cette fonctionnalité de langage.

## <a name="c-version-60"></a>C# version 6.0

Avec les versions 3.0 et 5.0, C# avait ajouté certaines des fonctionnalités dans un langage orienté objet. Avec la version 6.0, il éloigne d’une fonctionnalité qui tue dominante et libérer à la place de nombreuses fonctionnalités qui apprécient les utilisateurs parlant la langue. Voici certains d'entre eux :

- [Importations statiques](../language-reference/keywords/using-static.md)
- [Filtres d’exception](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [Initialiseurs de propriété](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [Membres de l’expression pulvérisée](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Propagateur null](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [Interpolation de chaîne](../language-reference/keywords/interpolated-strings.md)
- [opérateur nameof](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [Initialiseur de dictionnaire](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)

Chacune de ces fonctionnalités est intéressant à part entière. Mais si vous examinez les complètement, vous voyez un modèle intéressant. Dans cette version, C# éliminée réutilisable de langage pour rendre le code plus succincts et plus lisibles. Par conséquent, des ventilateurs de code propre et simple, cette version de langage a été un énorme avantage.

C’était le cas, une autre chose avec cette version, s’il n’est pas une fonctionnalité de langage traditionnel dans lui-même. Ils publié [Roslyn le compilateur en tant que service](https://github.com/dotnet/roslyn). Le compilateur c# est désormais écrits en c#, et vous pouvez utiliser le compilateur en tant que partie de vos efforts de programmation.

## <a name="c-version-70"></a>C# version 7.0

La dernière version majeure est le langage c# version 7.0. Cette version présente certaines choses évolutive et utile de la manière de c# 6.0, mais sans le compilateur en tant que service. Voici quelques-unes des nouvelles fonctionnalités :

- [Les variables](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [Déploiement et tuples](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [Critères spéciaux](./csharp-7.md#pattern-matching)
- [Fonctions locales](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [Membres de l’expression développée pulvérisée](./csharp-7.md#more-expression-bodied-members)
- [Retourne et les variables locales de ref](./csharp-7.md#ref-locals-and-returns)

Toutes ces fonctionnalités offrent de nouvelles fonctionnalités intéressantes pour les développeurs et la possibilité d’écrire du code de nettoyage de même que jamais. Une mise en surbrillance est condensation la déclaration de variables à utiliser avec le `out` (mot clé) et en permettant à plusieurs valeurs de retour via un tuple.

Mais c# est mis à utiliser jamais plus large. .NET core maintenant cibler n’importe quel système d’exploitation et a ses yeux bien sur le cloud et à la portabilité.  Il occupe certainement pensées concepteurs du langage et heure, en plus des prochaines évolutions avec les nouvelles fonctionnalités.

_Article_ [ _initialement publiée sur le blog NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, gracieusement Erik Dietrich et Patrick Smacchia._
