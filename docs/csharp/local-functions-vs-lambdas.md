---
title: Fonctions locales et expressions lambda
description: "Découvrez pourquoi des fonctions locales peuvent être un meilleur choix que les expressions lambda."
keywords: "C#, .NET, .NET Core, dernières fonctionnalités, nouveautés, fonctions locales, expressions lambda"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 20312b58a24dc991791edad4bb92d3a8ca6d501a
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2017
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Fonctions locales par rapport aux expressions lambda

À première vue, les [fonctions locales](programming-guide/classes-and-structs/local-functions.md) et les [expressions lambda](lambda-expressions.md) sont très similaires. Dans de nombreux cas, le choix entre l’utilisation d’expressions lambda et les fonctions locales est une question de style et préférences personnelles. Toutefois, il existe des différences réels où vous pouvez utiliser un ou l’autre que vous devez être conscient de.

Examinons les différences entre l’implémentation de l’algorithme factoriel avec une fonction locale et une expression lambda. Voici tout d’abord la version utilisant une fonction locale :

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Comparez cette implémentation avec une version qui utilise des expressions lambda :

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Les fonctions locales ont des noms. Les expressions lambda sont des méthodes anonymes sont affectées aux variables qui sont `Func` ou `Action` types. Lorsque vous déclarez une fonction locale, les types d’arguments et le type de retour sont partie de la déclaration de fonction. Au lieu de faire partie du corps de l’expression lambda expression, les types d’arguments et le type de retour sont partie de déclaration de type de variable de l’expression lambda. Ces deux différences risque de code plus claire.

Fonctions locales ont des règles différentes pour l’assignation à des expressions lambda. Une déclaration de fonction locale peut être référencée à partir de n’importe quel emplacement de code où il est dans la portée. Une expression lambda doit être affectée à une variable de délégué avant de pouvoir être accessible (ou appelé par le biais du delgate faisant référence à l’expression lambda.) Notez que la version utilisant l’expression lambda doit déclarer et initialiser l’expression lambda `nthFactorial` avant de la définir. Si ce n’est pas le cas, cela entraîne une erreur de compilation due au fait que vous référencez `nthFactorial` avant de lui affecter une valeur.
Ces différences font que les algorithmes récursifs sont plus faciles à créer à l’aide des fonctions locales. Vous pouvez déclarer et définir une fonction locale qui s’appelle elle-même. Expressions lambda doivent être déclarées et une valeur par défaut assignées avant de pouvoir être réaffectés à un corps qui fait référence à la même expression lambda.

Règles d’assignation définie affectent également toutes les variables qui sont capturées par l’epression de fonction ou un objet lambda locale. Les fonctions locales et les règles d’expression lambda exigent que toutes les variables capturées sont définitivement assignés au point lorsque l’expression lambda ou de fonction locale est convertie en un délégué. La différence est que les expressions lambda sont converties en délégués lorsqu’ils sont déclarés. Fonctions locales sont converties en délégués uniquement lorsqu’elle sert d’un délégué. Si vous déclarez une fonction locale et à le référencez uniquement en l’appelant comme une méthode, il ne sera pas converti en un délégué. Cette règle permet de déclarer une fonction locale à n’importe quel emplacement pratique dans sa portée englobante. Il est courant de déclarer des fonctions locales à la fin de la méthode parente, après les instructions return.

Enfin, le compilateur peut effectuer une analyse statique qui active des fonctions locales sans aucun doute affecter les variables capturées dans la portée englobante. Considérez cet exemple :

```csharp
bool M()
{
    int y;
    Local();
    return y;

    void Local() => y = 0;
}
```

Le compilateur peut déterminer que `Local` définitivement assigne `y` lorsqu’elle est appelée. Étant donné que `Local` est appelée avant la `return` instruction, `y` definitiely affecté à la `return` instruction.

L’analyse qui permet cette analyse permet à la différence du quatrième.
En fonction de leur utilisation, fonctions locales peuvent éviter les allocations de tas sont toujours nécessaires pour les expressions lambda. Si une fonction locale n’est jamais convertie en un délégué, et qu’aucun des variables capturées par la fonction locale est capturé par d’autres expressions lambda ou les fonctions locales qui sont converties en délégués, le compilateur peut éviter les allocations de tas. 

Penchons-nous sur cet exemple asynchrone :

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

La fermeture de cette expression lambda contient les variables `address`, `index` et `name`. Dans le cas des fonctions locales, l’objet qui implémente la fermeture peut être un type `struct`. Ce type de structure peuvent être transmis par référence à la fonction locale. Cette différence de mise en œuvre serait enregistrer sur une allocation.

L’instanciation nécessaire pour les expressions lambda signifie que les allocations de mémoire supplémentaire, qui peuvent être un facteur de performances dans les chemins d’accès du code à durée critique.
Les fonctions locales n’entraînent pas cette charge supplémentaire. Dans l’exemple ci-dessus, la version à fonction locale a 2 allocations de moins que la version à expression lambda.

> [!NOTE]
> L’équivalent de cette méthode avec une fonction locale fait aussi appel à une classe pour la fermeture. Le fait que la fermeture d’une fonction locale soit implémentée en tant que `class` ou `struct` est un détail d’implémentation. Une fonction locale peut utiliser un type `struct` contrairement à une expression lambda qui utilise toujours un type `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

Ultime avantage non décrit dans cet exemple : les fonctions locales peuvent être implémentées en tant qu’itérateurs, en utilisant la syntaxe `yield return` pour produire une séquence de valeurs. La `yield return` instruction n’est pas autorisée dans les expressions lambda.

Alors que les fonctions locales peuvent sembler redondantes par rapport aux expressions lambda, elles ont en réalité des objectifs différents et des utilisations différentes.
Les fonctions locales sont plus efficaces dans le cas où vous voulez écrire une fonction qui est appelée seulement dans le contexte d’une autre méthode.
