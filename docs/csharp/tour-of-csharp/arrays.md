---
title: "Tableaux C# - Visite guidée du langage C#"
description: Les tableaux sont le type de collection le plus simple dans le langage c#
keywords: .NET, csharp, tableau, collection
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: d7d5ae9f99ba1629a6f0aec57bebf74853cab27f
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="arrays"></a>Tableaux

Un ***tableau*** est une structure de données qui contient un certain nombre de variables qui sont accessibles par des indices calculés. Les variables contenues dans un tableau, également appelé ***éléments*** du tableau, sont tous du même type, et ce type est appelé ***type d’élément*** du tableau.

Les types tableau sont des types référence, et la déclaration d’une variable tableau réserve simplement un espace pour une référence à une instance de tableau. Les instances de tableau réelles sont créées dynamiquement lors de l’exécution à l’aide de l’opérateur new. La nouvelle opération spécifie la ***longueur*** de la nouvelle instance de tableau, qui est ensuite fixée pour la durée de vie de l’instance. Les indices des éléments d’un tableau vont de `0` à `Length - 1`. L’opérateur `new` initialise automatiquement les éléments d’un tableau à leur valeur par défaut, c'est-à-dire, par exemple, zéro pour tous les types numériques et `null` pour tous les types référence.

L’exemple suivant crée un tableau de `int` éléments, initialise le tableau et imprime le contenu du tableau.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Cet exemple crée et utilise un ***tableau unidimensionnel***. C# prend également en charge les ***tableaux multidimensionnels***. Le nombre de dimensions d’un type tableau, également appelé ***rang*** du type tableau, est de un plus le nombre de virgules entre les crochets du type tableau. L’exemple suivant alloue respectivement des tableaux à une seule, deux et trois dimensions, respectivement.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

Le tableau `a1` contient 10 éléments, le tableau `a2` en contient 50 (10 x 5) et le tableau `a3` en contient 100 (10 × 5 × 2).
Le type d’élément d’un tableau peut être de n’importe quel type, y compris un type tableau. Un tableau avec des éléments d’un type tableau est parfois appelé un ***tableau en escalier***, car les longueurs des tableaux d’éléments ne sont pas nécessairement pas les mêmes. L’exemple suivant alloue un tableau de tableaux de `int` :

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

La première ligne crée un tableau avec trois éléments, chacun de type `int[]` et chacun avec une valeur initiale de `null`. Les lignes suivantes initialisent ensuite les trois éléments avec des références aux instances individuelles de tableau de longueur variable.

L’opérateur new autorise la spécification des valeurs initiales des éléments du tableau en utilisant un ***initialiseur de tableau***, qui est une liste d’expressions écrites entre les délimiteurs `{` et `}`. L’exemple suivant alloue et initialise un `int[]` avec trois éléments.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Notez que la longueur du tableau est déduite à partir du nombre d’expressions entre { et }. Les déclarations locales des champs et variables peuvent être abrégées davantage afin de ne pas avoir à redéclarer le type tableau.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Les deux exemples précédents sont équivalents à ce qui suit :

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
[Précédent](structs.md)
[Suivant](interfaces.md)
