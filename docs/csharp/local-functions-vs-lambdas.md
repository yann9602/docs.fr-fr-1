---
title: Fonctions locales et expressions lambda
description: "Découvrez pourquoi des fonctions locales peuvent être un meilleur choix que les expressions lambda."
keywords: "C#, .NET, .NET Core, dernières fonctionnalités, nouveautés, fonctions locales, expressions lambda"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: visual-studio-dev-15
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.translationtype: HT
ms.sourcegitcommit: 4582cb0ee091526423cce3fc1d8243029f34f59c
ms.openlocfilehash: 366d7465433f2786960e22418b8aa46ba10e1fd1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/16/2017

---

### <a name="local-functions-compared-to-lambda-expressions"></a>Fonctions locales comparées aux expressions lambda

À première vue, les [fonctions locales](programming-guide/classes-and-structs/local-functions.md) et les [expressions lambda](lambda-expressions.md) sont très similaires.
Or, selon vos besoins, les fonctions locales peuvent offrir une solution beaucoup plus efficace et simple.

Examinons les différences entre l’implémentation de l’algorithme factoriel avec une fonction locale et une expression lambda. Voici tout d’abord la version utilisant une fonction locale :

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Factorielle récursive utilisant une fonction locale")]

Comparez cette implémentation avec une version qui utilise des expressions lambda :

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Factorielle récursive utilisant des expressions lambda")]

En premier lieu, les expressions lambda sont implémentées en instanciant un délégué et en appelant ce même délégué. Les fonctions locales sont implémentées comme des appels de méthode.
L’instanciation nécessaire pour les expressions lambda signifie des allocations de mémoire supplémentaires, qui peuvent être un facteur influençant les performances dans les chemins de code critiques au niveau du temps.
Les fonctions locales n’entraînent pas cette charge supplémentaire. Dans l’exemple ci-dessus, la version à fonction locale a 2 allocations de moins que la version à expression lambda.

Cette méthode récursive est suffisamment simple pour que la fonction locale soit implémentée en tant que méthode privée avec un nom généré par le compilateur. Sa seule différence par rapport aux autres méthodes privées est qu’elle est sémantiquement étendue au sein de la fonction externe.

En second lieu, les fonctions locales peuvent être appelées avant d’être définies. Les expressions lambda doivent être déclarées avant d’être définies. Cela signifie que les fonctions locales sont plus faciles à utiliser dans des algorithmes récursifs, comme nous l’avons vu précédemment.

Notez que la version utilisant l’expression lambda doit déclarer et initialiser l’expression lambda `nthFactorial` avant de la définir. Si ce n’est pas le cas, cela entraîne une erreur de compilation due au fait que vous référencez `nthFactorial` avant de lui affecter une valeur.
Les algorithmes récursifs sont plus faciles à créer en utilisant des fonctions locales.

En troisième lieu, pour les expressions lambda, le compilateur doit toujours créer une classe anonyme et une instance de cette classe pour stocker les variables capturées par la fermeture. Penchons-nous sur cet exemple asynchrone :

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Méthode retournant une tâche avec une expression lambda")]

La fermeture de cette expression lambda contient les variables `address`, `index` et `name`. Dans le cas des fonctions locales, l’objet qui implémente la fermeture peut être un type `struct`. Cela permet d’économiser une allocation.

> [!NOTE]
> L’équivalent de cette méthode avec une fonction locale fait aussi appel à une classe pour la fermeture. Le fait que la fermeture d’une fonction locale soit implémentée en tant que `class` ou `struct` est un détail d’implémentation. Une fonction locale peut utiliser un type `struct` contrairement à une expression lambda qui utilise toujours un type `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Méthode retournant une tâche avec une fonction locale")]

Ultime avantage non décrit dans cet exemple : les fonctions locales peuvent être implémentées en tant qu’itérateurs, en utilisant la syntaxe `yield return` pour produire une séquence de valeurs.

Alors que les fonctions locales peuvent sembler redondantes par rapport aux expressions lambda, elles ont en réalité des objectifs différents et des utilisations différentes.
Les fonctions locales sont plus efficaces dans le cas où vous voulez écrire une fonction qui est appelée seulement dans le contexte d’une autre méthode.

