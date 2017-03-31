---
title: Fonctions locales et expressions lambda
description: "Pourquoi des fonctions locales peuvent-elles être un meilleur choix que les expressions lambda ?"
keywords: "C#, .NET, .NET Core, dernières fonctionnalités, nouveautés, fonctions locales, expressions lambda"
author: BillWagner
ms.author: wiwagn
ms.date: 10/27/2016
ms.topic: article
ms.prod: visual-studio-dev-15
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bba2a8d183f928e298c452f6ec132f3eb9dffbd3
ms.lasthandoff: 03/13/2017

---

### <a name="local-functions-compared-to-lambda-expressions"></a>Fonctions locales comparées aux expressions lambda

Dans certains cas d’usage, vous pouvez créer une expression lambda et l’utiliser sans avoir à créer une fonction locale. Voici un exemple de méthode asynchrone qui fait exactement cela :

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Méthode retournant une tâche avec une expression lambda")]

Plusieurs raisons peuvent cependant amener à préférer l’utilisation de fonctions locales au lieu de définir et d’appeler des expressions lambda.

D’abord, pour les expressions lambda, le compilateur doit créer une classe anonyme et une instance de cette classe pour stocker les variables capturées par la fermeture. La fermeture de cette expression lambda contient les variables `address`, `index` et `name`. 

Deuxièmement, les expressions lambda sont implémentées en instanciant un délégué et en l’appelant. Les fonctions locales sont implémentées comme des appels de méthode.
L’instanciation nécessaire pour les expressions lambda signifie des allocations de mémoire supplémentaires, qui peuvent être un facteur influençant les performances dans les chemins de code critiques au niveau du temps.
Les fonctions locales n’entraînent pas cette charge supplémentaire.

Troisièmement, les fonctions locales peuvent être appelées avant d’être définies. Les expressions lambda doivent être déclarées avant d’être définies. Cela signifie que les fonctions locales sont plus faciles à utiliser dans des algorithmes récursifs :

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Factorielle récursive utilisant une fonction locale")]

Comparez cette implémentation avec une version qui utilise des expressions lambda :

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Factorielle récursive utilisant des expressions lambda")]

Notez que la version utilisant l’expression lambda doit déclarer et initialiser l’expression lambda `nthFactorial` avant de la définir. Si ce n’est pas le cas, cela entraîne une erreur de compilation due au fait que vous référencez `nthFactorial` avant de lui affecter une valeur.
Les algorithmes récursifs sont plus faciles à créer en utilisant des fonctions locales. 

Alors que les fonctions locales peuvent sembler redondantes par rapport aux expressions lambda, elles ont en réalité des objectifs différents et des utilisations différentes.
Les fonctions locales sont plus efficaces dans le cas où vous voulez écrire une fonction qui est appelée seulement dans le contexte d’une autre méthode.


