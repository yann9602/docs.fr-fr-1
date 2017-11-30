---
title: "Visite guidée de F #"
description: "Examiner certaines des fonctionnalités clés de la programmation de langage dans cette visite guidée avec des exemples de code F #."
keywords: "Visual f #, f #, fonctionnelle programmation .NET, visite guidée"
author: cartermp
ms.author: phcart
ms.date: 01/24/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: c027e6b71f35fc3b58750eb164124de145244825
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="tour-of-f"></a>Visite guidée de F # #

La meilleure façon d’en savoir plus sur F # est en lecture et écriture de code F #.  Cet article agissent comme une visite guidée des fonctionnalités clées du langage F # et vous donner des extraits de code que vous pouvez exécuter sur votre ordinateur.  Pour en savoir plus sur la configuration d’un environnement de développement, consultez [mise en route](tutorials/getting-started/index.md).

Il existe deux concepts principaux en F #: types et les fonctions.  Cette visite guidée sera mettent l’accent sur les fonctionnalités du langage qui appartiennent à ces deux concepts.

## <a name="how-to-run-the-code-samples"></a>Comment exécuter les exemples de Code

>[!NOTE]
Deux options pour les exemples de code en cours d’exécution sont [F # essayez](http://www.tryfsharp.org/Create) (requiert Silverlight) et [F # pour les ordinateurs portables Azure](https://notebooks.azure.com/Microsoft/libraries/fsharp/html/FSharp%20for%20Azure%20Notebooks.ipynb) sur Microsoft Azure.

Pour exécuter ces exemples de code le plus rapide consiste à utiliser [F # Interactive](tutorials/fsharp-interactive/index.md).  Simplement copier/coller les exemples de code et il les exécuter.  Vous pouvez également configurer un projet pour compiler et exécuter le code en tant qu’une Application Console.  Consultez le [prise en main](./get-started/index.md) section pour en savoir plus.

## <a name="functions-and-modules"></a>Fonctions et des Modules

Les éléments essentiels de n’importe quel programme F # sont ***fonctions*** organisés en ***modules***.  [Fonctions](language-reference/functions/index.md) travailler sur des entrées pour produire des sorties, et ils sont organisés sous [Modules](language-reference/modules.md), qui sont la principale manière de regrouper des éléments en F #.  Ils sont définis à l’aide de la [ `let` liaison](language-reference/functions/let-bindings.md), donnez un nom à la fonction et définir ses arguments.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let`les liaisons sont également comment vous liez une valeur à un nom, semblable à une variable dans d’autres langages.  `let`les liaisons sont ***immuable*** par défaut, ce qui signifie qu’une fois qu’une valeur ou une fonction est liée à un nom, il ne peut pas être modifié sur place.  Ce comportement diffère variables dans d’autres langages qui sont ***mutable***, ce qui signifie que leurs valeurs peut être modifié à tout moment dans le temps.  Si vous avez besoin d’une liaison mutable, vous pouvez utiliser `let mutable ...` syntaxe.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Nombres, des valeurs booléennes et des chaînes

Un langage .NET, F # prend en charge les mêmes sous-jacent [les types primitifs](language-reference/primitive-types.md) qui existent dans .NET.

Voici comment les différents types numériques sont représentées en F #:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Voici les valeurs booléennes et exécution d’une logique conditionnelle base ressemble à :

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

Et Voici quelles basic [chaîne](language-reference/strings.md) manipulation ressemble à :

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Tuples

[Tuples](language-reference/tuples.md) sont très important en F #.  Il s’agit d’un regroupement de valeurs sans nom, mais ordonnées, qui peut être traitée en tant que valeurs elles-mêmes.  Considérer les sous forme de valeurs qui sont agrégées à partir d’autres valeurs.  Ils ont de nombreuses utilisations, telles que facilement retourner plusieurs valeurs à partir d’une fonction ou de regroupement pour des raisons de commodité ad-hoc.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

À compter de F # 4.1, vous pouvez également créer `struct` tuples.  Ces également interagissent entièrement avec des tuples C# 7/Visual Basic 15, qui sont également `struct` tuples :

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

Il est important de noter que, car `struct` tuples sont des types valeur, ils ne peuvent pas être convertis implicitement pour référencer les tuples, ou vice versa.  Vous devez convertir explicitement entre un tuple de référence et struct.

## <a name="pipelines-and-composition"></a>Pipelines et Composition

Diriger des opérateurs (`|>`, `<|`, `||>`, `<||`, `|||>`, `<|||`) et les opérateurs de composition (`>>` et `<<`) sont largement utilisés lors du traitement des données en F #.  Ces opérateurs sont des fonctions qui vous permettent d’établir un « pipelines » des fonctions de manière flexible.  L’exemple suivant décrit comment tirer parti de ces opérateurs pour créer un pipeline fonctionnels simple.

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

L’exemple ci-dessus effectuée utiliser de nombreuses fonctionnalités de F #, y compris les fonctions de traitement de liste, les fonctions de première classe, et [application partielle](language-reference/functions/index.md#partial-application-of-arguments).  Bien qu’une compréhension approfondie de chacun de ces concepts peut devenir un peu avancée, il doit être clair facilement les fonctions peuvent être utilisées pour traiter les données lors de la création de pipelines.

## <a name="lists-arrays-and-sequences"></a>Listes, tableaux et séquences

Listes, tableaux et séquences sont trois types de collection principale dans la bibliothèque principale F #.

[Répertorie les](language-reference/lists.md) sont des collections d’éléments du même type ordonnées et immuables.  Ils sont des listes liées uniques, ce qui signifie qu’ils sont destinés à énumération, mais un choix médiocre pour un accès aléatoire et la concaténation s’ils sont volumineux.  Ce comportement diffère de listes dans d’autres langages courants, ce qui est en général, n’utilisent pas une liste liée unique pour représenter les listes.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Tableaux](language-reference/arrays.md) sont de taille fixe, *mutable* collections d’éléments du même type.  Ils prennent en charge un accès aléatoire rapide d’éléments et sont plus rapides que F #, car ce sont des blocs de mémoire contigus simplement des listes.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Séquences](language-reference/sequences.md) sont une série logique d’éléments, tous du même type.  Il s’agit d’un type plus général que les listes et les tableaux, susceptibles d’être votre « vue » dans n’importe quelle série logique d’éléments.  Ils également ressortent, car ils peuvent être ***différée***, ce qui signifie que les éléments peuvent être calculées uniquement lorsqu’elles sont nécessaires.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Fonctions récursives

Traitement des collections ou des séquences d’éléments est généralement le cas avec [récursivité](language-reference/functions/index.md#recursive-functions) en F #.  Bien que F # prend en charge les boucles for et la programmation impérative, la récursivité est recommandée, car il est plus facile de garantir l’exactitude.

>[!NOTE]
L’exemple suivant utilise la correspondance de modèle le `match` expression.  Cette construction fondamentale est couvert plus loin dans cet article.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F # possède également une prise en charge complète pour l’optimisation d’appel Tail, qui consiste à optimiser les appels récursifs afin qu’ils soient aussi rapides que d’une construction de la boucle.

## <a name="record-and-discriminated-union-types"></a>Enregistrement et les Types Union discriminée

Enregistrement et les types Union sont deux types de données fondamentaux utilisés dans le code F # et sont généralement le meilleur moyen de représenter les données dans un programme F #.  Bien que cela les rend similaire aux classes dans d’autres langages, parmi les principales différences est qu’ils ont une sémantique d’égalité structurelle.  Cela signifie qu’ils sont comparables « en mode natif » et l’égalité est simple - simplement vérifier si une est égale à l’autre.

[Enregistrements](language-reference/records.md) sont un agrégat de valeurs nommées, avec des membres facultatives (tels que les méthodes).  Si vous êtes familiarisé avec c# ou en Java, puis ces devraient vous sentir semblables à POCOs ou POJO - uniquement avec l’égalité structurelle et moins de cérémonie.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

À compter de F # 4.1, vous pouvez également représenter des enregistrements sous la forme `struct`s.  Cette opération s’effectue avec la `[<Struct>]` attribut :

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[(DUs) d’Unions discriminées](language-reference/discriminated-unions.md) sont des valeurs qui peut être un nombre de formulaires nommés ou les cas.  Les données stockées dans le type peuvent être une de plusieurs valeurs distinctes.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Vous pouvez également utiliser DUs en tant que *Unions discriminées de casse simple*, à l’aide sur les types primitifs de modélisation de domaine.  Souvent, les chaînes et autres types primitifs sont utilisés pour représenter un élément et figurent donc une signification particulière.  Toutefois, en utilisant uniquement la représentation primitifs des données peut entraîner par inadvertance affectation d’une valeur incorrecte !  Représentant chaque type d’information sous la forme d’une union de casse simple distincte peut imposer l’exactitude dans ce scénario.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Comme indiqué dans l’exemple ci-dessus, pour obtenir la valeur sous-jacente dans un seul cas discriminée Union, vous devez le déballer explicitement.

En outre, DUs prennent également en charge les définitions récursives, ce qui vous permet de facilement représenter des arbres et, par nature, les données récursives.  Par exemple, voici comment vous pouvez représenter une arborescence de recherche binaire avec `exists` et `insert` fonctions.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Car DUs vous permettent de représenter la structure récursive de l’arborescence dans le type de données, d’utiliser cette structure récursive est simple et garantit l’exactitude.  Il est également pris en charge dans les critères spéciaux, comme indiqué ci-dessous.

En outre, vous pouvez représenter DUs en tant que `struct`s avec la `[<Struct>]` attribut :

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

Toutefois, il existe deux éléments clés à prendre en compte lorsque vous procédez ainsi :

1. Un struct DU ne peut pas être définie de manière récursive par.
2. Un struct DU doit avoir des noms uniques pour chacun de ses cas.

Le non-respect ci-dessus entraîne une erreur de compilation.

## <a name="pattern-matching"></a>Critères spéciaux

[Correspondance de modèle](language-reference/pattern-matching.md) est la fonctionnalité du langage F # qui est correct pour l’exploitation de types F #.  Dans les exemples ci-dessus, vous avez probablement remarqué un certain `match x with ...` syntaxe.  Cette construction permet au compilateur, ce qui permet de comprendre la « forme » de types de données, qui vous oblige pour prendre en compte tous les cas possibles lors de l’utilisation d’un type de données via ce que l'on appelle comme Exhaustive de correspondance.  Cela est extrêmement puissant est correcte et intelligemment permet « de courbes d’élévation » ce qui serait normalement un problème d’exécution dans la compilation.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

Vous pouvez également utiliser la syntaxe raccourcie `function` construction pour les critères spéciaux, ce qui est utile lorsque vous écrivez des fonctions qui utilisent des [Application partielle](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

Vous avez peut-être remarqué pose l’utilisation de la `_` modèle.  Il s’agit du [modèle de caractère générique](language-reference/pattern-matching.md#wildcard-pattern), qui est une façon de dire « Je ne se soucient pas qu’un élément est ».  Bien qu’adaptés, vous pouvez accidentellement contourner Exhaustive de correspondance et ne bénéficie plus des mises en conformité de la compilation si vous ne faites pas attention à l’aide de `_`.  Il est particulièrement adapté lorsque vous ne vous souciez certains éléments d’un type décomposé lorsque de modèle mise en correspondance ou la clause finale lorsque vous avez énuméré tous les cas significatifs dans une expression de critères spéciaux.

[Modèles actifs](language-reference/active-patterns.md) sont une autre construction puissante à utiliser avec les critères spéciaux.  Ils permettent de partitionner les données d’entrée dans les formulaires personnalisés, les décomposant au site d’appel de correspondance de modèle.  Ils peuvent également être paramétrés, ce qui permet de définir la partition en tant que fonction.  Développement de l’exemple précédent pour prendre en charge les modèles actifs ressemble à ceci :

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a>Types facultatif

Un cas spécial de types discriminée Union est le Type d’Option, qui est donc utile dont il fait partie de la bibliothèque principale F #.

[Le Type d’Option](language-reference/options.md) est un type qui représente un des deux cas : une valeur ou rien du tout.  Il est utilisé dans les scénarios où une valeur peut ou ne peut pas entraîner à partir d’une opération particulière.  Cela force ensuite pour prendre en compte les deux cas, en rendant un problème lors de la compilation plutôt qu’un problème d’exécution.  Ils sont souvent utilisés dans les API où `null` est utilisé pour représenter « nothing » au lieu de cela, évite ainsi d’avoir à vous soucier `NullReferenceException` dans de nombreux cas.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a>Unités de mesure

Une fonctionnalité du système de type F # est la possibilité de fournir un contexte pour les littéraux numériques via des unités de mesure.

[Unités de mesure](language-reference/units-of-measure.md) vous permettent d’associer un type numérique à une unité, telles que des compteurs, et ont les fonctions ne fonctionnent sur les unités au lieu de littéraux numériques.  Cela permet au compilateur de vérifier que les types de littéraux numériques passés dans un sens dans un contexte de certain, ce qui élimine les erreurs d’exécution associé à ce type de travail.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

La bibliothèque principale F # définit plusieurs types d’unités SI et conversions d’unité.  Pour plus d’informations, consultez la [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Classes et Interfaces

F # possède également une prise en charge complète pour les classes .NET, [Interfaces](language-reference/interfaces.md), [Classes abstraites](language-reference/abstract-classes.md), [héritage](language-reference/inheritance.md), et ainsi de suite.

[Classes](language-reference/classes.md) sont des types qui représentent des objets .NET, qui peut avoir des propriétés, méthodes et événements en tant que son [membres](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

Définition des classes génériques est également très simple.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

Pour implémenter une Interface, vous pouvez utiliser `interface ... with` syntaxe ou un [objet Expression](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a>Les Types à utiliser

La présence de Classes, les enregistrements, les Unions discriminées et Tuples conduit à une question importante : qui faut-il utiliser ?  Comme la plupart des tous les éléments de durée de vie, la réponse dépend de votre situation.

Tuples sont parfaites pour retourner plusieurs valeurs à partir d’une fonction et à l’aide d’un agrégat ad hoc de valeurs en tant que valeur lui-même.

Les enregistrements sont un « step up » à partir de Tuples, avoir nommé étiquettes et la prise en charge des membres facultatives.  Ils sont parfaites pour une représentation de cérémonie de faible des données en transit via votre programme.  Parce qu’ils ont l’égalité structurelle, ils sont faciles à utiliser avec la comparaison.

Les Unions discriminées ont de nombreuses applications, mais l’avantage principal est de pouvoir les utiliser conjointement avec les critères spéciaux pour prendre en compte toutes les possibles « formes » qui peuvent avoir des données.  

Les classes sont parfaites pour un très grand nombre de raisons, telles que lorsque vous devez représentent des informations et également lier ces informations à la fonctionnalité.  En règle générale, lorsque vous disposez de fonctionnalités qui sont sur le plan conceptuel liée à des données, à l’aide des Classes et les principes de programmation orientée objet est un avantage considérable.  Les classes sont également le type de données par défaut lors de l’interaction avec c# et Visual Basic, comme ces langues utilisent des classes pour quasiment tous les éléments.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez vu certaines des fonctionnalités du langage principales, vous devez être prêt à écrire votre première programmes F # !  Extraire [mise en route](tutorials/getting-started/index.md) pour savoir comment configurer votre environnement de développement et d’écrire du code.

Les étapes suivantes pour en savoir plus peuvent être comme vous le souhaitez, mais nous vous recommandons de [fonctionne comme valeurs de première classe](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)--> à obtenir à l’aise avec certains concepts de programmation fonctionnelle.  Il s’agit essentielles pour la création des programmes robustes en F #.

Consultez également le [référence du langage F #](language-reference/index.md) pour afficher une collection complète de contenu conceptuel sur F #.
