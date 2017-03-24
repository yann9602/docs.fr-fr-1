---
title: "Présentation de .NET"
description: "Visite guidée de certaines fonctionnalités principales de la plateforme .NET."
keywords: ".NET, .NET Core, Présentation, Langages de programmation, Non sécurisé, Gestion de la mémoire, Cohérence des types, Asynchrone"
author: cartermp
manager: wpickett
ms.author: phcart
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: 2c57b5cebd63b1d94b127cd269e3b319fb24dd97
ms.openlocfilehash: 02e2fa22e36fd2f6618527ad3c89cbbd8587dfe2

---

# <a name="tour-of-net"></a>Présentation de .NET

.NET est une plateforme de développement généraliste.  Elle comporte plusieurs fonctionnalités clés, telles que plusieurs langages de programmation, des modèles de programmation asynchrone et simultanée et une interopérabilité native, qui permettent un large éventail de scénarios sur plusieurs plateformes.

Cet article propose une visite guidée de certaines fonctionnalités principales de la plateforme .NET.

Consultez [Composants architecturaux de .NET](components.md) pour en savoir plus sur chacune des « parties » architecturales de .NET et sur leur finalité.

## <a name="how-to-run-the-code-samples"></a>Guide pratique pour exécuter les exemples de code

Pour savoir comment configurer un environnement de développement pour exécuter les exemples de code, consultez [Bien démarrer](getting-started.md).  Vous pouvez copier et coller les exemples de code à partir de cette page dans votre environnement pour les exécuter. 

> [!NOTE]
À l’avenir, ce site de documentation pourra exécuter ces exemples de code dans votre navigateur.

## <a name="programming-languages"></a>Langages de programmation

.NET prend en charge plusieurs langages de programmation.  Les runtimes .NET implémentent le [Common Language Infrastructure (CLI)](https://www.visualstudio.com/en-us/mt639507), qui, entre autres, spécifie un runtime indépendant du langage et une interopérabilité des langages.  Cela signifie que vous pouvez choisir n’importe quel langage .NET pour générer des applications et services sur .NET.

Microsoft développe et prend en charge activement trois langages .NET : C#, F# et Visual Basic .NET. 

* C# est simple, puissant, de type sécurisé et orienté objet, tout en conservant l’expressivité et l’élégance des langages de style C. Les utilisateurs familiarisés avec le langage C et les langages similaires auront peu de difficultés à s’adapter à C#.  Consultez le [Guide C#](../csharp/index.md) pour en savoir plus sur C#.

* F# est un langage de programmation multiplateforme et fonctionnel qui prend également en charge la programmation orientée objet et impérative traditionnelle.  Consultez le [Guide F#](../fsharp/index.md) pour en savoir plus sur F#.

* Visual Basic est un langage facile à apprendre que vous pouvez utiliser pour créer une variété d’applications qui s’exécutent sur .NET.

## <a name="automatic-memory-management"></a>Gestion automatique de la mémoire

.NET utilise le [garbage collection](garbagecollection/index.md) pour fournir une gestion automatique de la mémoire pour les programmes.  Le récupérateur de mémoire opère avec une approche différée de la gestion de la mémoire, préférant le débit de l’application à la collecte immédiate de la mémoire.  Pour plus d’informations sur le garbage collector .NET, consultez [Notions de base du garbage collection (GC)](garbagecollection/fundamentals.md).

Les deux lignes suivantes allouent de la mémoire :

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Il n’existe aucun mot clé analogue pour libérer de la mémoire, car la libération de mémoire se produit automatiquement quand le récupérateur de mémoire réclame la mémoire dans son exécution planifiée.

Les types dans une portée donnée sont normalement hors de portée à la fin d’une méthode, point auquel ils peuvent être récupérés. Toutefois, vous pouvez indiquer au récupérateur de mémoire qu’un objet en particulier est hors de portée avant la fin de la méthode à l’aide de l’instruction `using` :

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

Une fois que le bloc `using` a terminé, le récupérateur de mémoire sait que l’objet `stream` dans l’exemple précédent peut être collecté et sa mémoire récupérée.

En F#, les règles concernant ce point ont une sémantique légèrement différente.  Pour en savoir plus sur la gestion des ressources en F#, consultez [Resource Management: The `use` Keyword](../fsharp/language-reference/resource-management-the-use-keyword.md) (Gestion des ressources : mot clé « use »).

Une des fonctionnalités les moins évidentes et pourtant assez importantes que le récupérateur de mémoire active est la sûreté de la mémoire. L’invariant de la sûreté de la mémoire est très simple : un programme a une mémoire sécurisée s’il accède uniquement à la mémoire qui a été allouée (et non libérée). Les pointeurs non résolus sont toujours des bogues et leur suivi est souvent très difficile.

Le runtime .NET fournit des services supplémentaires pour assurer la sûreté de la mémoire, qui ne sont pas naturellement offerts par un récupérateur de mémoire. Il garantit que les programmes n’indexent pas à la fin d’un tableau ou accèdent à un champ fantôme à la fin d’un objet.

L’exemple suivant lève une exception en raison de la sûreté de la mémoire.

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="type-safety"></a>Cohérence des types

Les objets sont alloués en termes de types. Les seules opérations autorisées pour un objet donné et la mémoire qu’il consomme sont celles de son type. Un type `Dog` peut avoir des méthodes `Jump` et `WagTail`, mais probablement pas une méthode `SumTotal`. Un programme peut appeler uniquement les méthodes déclarées d’un type donné. Tous les autres appels entraînent une erreur au moment de la compilation ou une exception au moment de l’exécution (en cas d’utilisation de fonctionnalités dynamiques ou du type `object`).

Les langages .NET sont orientés objet, avec des hiérarchies de classes de base et dérivées. Le runtime .NET autorise uniquement les casts et les appels d’objet qui s’alignent sur la hiérarchie d’objets. N’oubliez pas que chaque type défini dans un langage .NET dérive du type `object` de base.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L18-L23)]

La cohérence des types est également utilisée pour aider à appliquer l’encapsulation en garantissant la fidélité des mots clés d’accesseur. Les mots clés d’accesseur sont des artefacts qui contrôlent l’accès aux membres d’un type donné par un autre code. Ils servent généralement à différentes sortes de données dans un type utilisées pour gérer son comportement.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic et F# prennent en charge l’**inférence de type** locale. L’inférence de type signifie que le compilateur déduit le type de l’expression à gauche à partir de l’expression à droite. Cela ne signifie pas que la cohérence des types est interrompue ou évitée. Le type résultant **a** un type fort avec tout ce que cela implique. Réécrivons les deux premières lignes de l’exemple précédent pour introduire l’inférence de type. Notez que le reste de l’exemple est complètement identique.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F# offre des fonctionnalités d’inférence de type qui vont au-delà de l’inférence de type limitée aux méthodes disponible en C# et Visual Basic.  Pour plus d’informations, consultez [Type Inference](../fsharp/language-reference/type-inference.md) (Inférence de type).

## <a name="delegates-and-lambdas"></a>Délégués et expressions lambda

Les délégués sont comme des pointeurs de fonction C++, à la grande différence qu’ils sont de type sécurisé. Ils représentent une sorte de méthode déconnectée au sein du système de type CLR. Les méthodes régulières sont attachées à une classe et peuvent être appelées directement uniquement par des conventions d’appel statiques ou d’instance.

Les délégués sont utilisés dans diverses API et emplacements de l’environnement .NET, en particulier dans les expressions lambda, qui sont la pierre angulaire de LINQ.

Pour en savoir plus sur ce sujet, lisez le document [Délégués et expressions lambda](delegates-lambdas.md).

## <a name="generics"></a>Génériques

Les génériques sont une fonctionnalité qui a été ajoutée dans .NET Framework 2.0. En bref, les génériques permettent au programmeur d’introduire un « paramètre de type » quand il désigne leurs classes qui permet au code client (les utilisateurs du type) de spécifier le type exact à utiliser à la place du paramètre de type.

Les génériques ont été ajoutés pour aider les programmeurs à implémenter des structures de données génériques. Avant leur arrivée, pour qu’un type `List`, par exemple, soit générique, il fallait utiliser des éléments qui étaient de type `object`. Cela entraînait des variations de performances ainsi que des problèmes sémantiques, sans oublier les possibles erreurs d’exécution subtiles. Les erreurs les plus connues dans cette dernière catégorie interviennent quand une structure de données contient, par exemple, des entiers et des chaînes et qu’une exception `InvalidCastException` est levée pendant l’utilisation des membres de la liste.

L’exemple suivant montre une exécution de programme de base utilisant une instance des types @System.Collections.Generic.List%601.

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Pour plus d’informations, consultez l’article [Vue d’ensemble des types génériques (Génériques)](generics.md).

## <a name="async-programming"></a>Programmation asynchrone

La programmation asynchrone est un concept de première classe dans .NET, avec prise en charge asynchrone dans le runtime, les bibliothèques de framework et les constructions de langage .NET. En interne, ils sont basés sur des objets (comme `Task`) qui tirent parti du système d’exploitation pour effectuer aussi efficacement que possible des tâches utilisant des E/S.

Pour en savoir plus sur la programmation asynchrone dans .NET, commencez par la [Vue d’ensemble d’Async](async.md).

## <a name="language-integrated-query-linq"></a>LINQ (Language-Integrated Query)

LINQ est un ensemble puissant de fonctionnalités pour C# et VB qui vous permettent d’écrire du code simple et déclaratif pour l’exploitation des données. Les données peuvent se présenter sous plusieurs formes (comme des objets en mémoire, dans une base de données SQL ou un document XML), mais le code LINQ que vous écrivez généralement n’est pas différent pour chaque source de données !

Pour en savoir plus et obtenir des exemples, consultez [LINQ (Language Integrated Query)](using-linq.md).

## <a name="native-interoperability"></a>Interopérabilité native

Chaque système d’exploitation en cours d’utilisation prend en charge un grand nombre de plateformes pour diverses tâches de programmation. .NET offre plusieurs moyens de tirer parti de ces API. Collectivement, cette prise en charge est appelée « interopérabilité native » et, dans cette section, nous allons voir comment accéder aux API natives à partir du code managé .NET.

Le principal moyen d’effectuer une interopérabilité native est via l’« appel de code non managé » ou P/Invoke, en forme abrégée. Cette prise en charge dans .NET Core est disponible sur les plateformes Linux et Windows. Un autre moyen de faire une interopérabilité native sur Windows uniquement est connu sous le nom de « COM Interop », utilisé pour travailler avec des [composants COM](https://msdn.microsoft.com/library/bwa2bx93.aspx) dans du code managé. Il est basé sur l’infrastructure de P/Invoke, mais fonctionne légèrement différemment.

Une grande partie de la prise en charge d’interopérabilité dans Mono (et donc dans Xamarin) pour Java et Objective-C est générée de la même façon, autrement dit, ils utilisent les mêmes principes.

Pour en savoir plus, lisez le document [Interopérabilité native](native-interop.md).

## <a name="unsafe-code"></a>Code unsafe

Le CLR permet d’accéder à la mémoire native et d’effectuer une opération arithmétique de pointeur via du code `unsafe`. Ces opérations sont nécessaires pour certains algorithmes et pour l’interopérabilité du système. L’utilisation de code unsafe, bien que puissante, est déconseillée, sauf si elle est nécessaire pour assurer l’interopérabilité avec les API système ou implémenter l’algorithme le plus efficace. Le code unsafe peut ne pas s’exécuter de la même façon dans différents environnements et perd les avantages d’un récupérateur de mémoire et de la cohérence des types. Il est recommandé de restreindre et centraliser le code unsafe autant que possible, et de tester ce code de manière approfondie.

L’exemple suivant est une version modifiée de la méthode `ToString()` à partir de la classe `StringBuilder`.  Il illustre comment l’utilisation de code `unsafe` peut implémenter efficacement un algorithme en déplaçant directement des segments de mémoire :

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Étapes suivantes

Si vous êtes intéressé par une présentation des fonctionnalités de C#, consultez [Tour of C#](../csharp/tour-of-csharp/index.md) (Présentation de C#).

Si vous êtes intéressé par une présentation des fonctionnalités de F#, consultez [Tour of F#](../fsharp/tour.md) (Présentation de F#).

Si vous voulez vous familiariser avec l’écriture de votre propre code, consultez [Getting Started](getting-started.md) (Bien démarrer).

Pour obtenir des informations sur les composants importants de .NET, consultez [Composants architecturaux de .NET](components.md).


<!--HONumber=Nov16_HO3-->


