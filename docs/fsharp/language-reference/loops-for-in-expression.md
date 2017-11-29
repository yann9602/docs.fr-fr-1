---
title: "Boucles : expression for...in (F#)"
description: "Voir comment la boucle for) (F #... dans l’expression de construction en boucle est utilisée pour itérer sur les correspondances d’un modèle dans une collection énumérable."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f54e3228-4aec-4d0a-ae37-bc3376508284
ms.openlocfilehash: d86aeb3bdd975261e59004d636354a740bd95c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forin-expression"></a>Boucles : expression for...in

Cette construction de bouclage est utilisée pour itérer sur les correspondances d’un modèle dans une collection énumérable comme une expression de plage, séquence, liste, tableau ou autre construction qui prend en charge d’énumération.


## <a name="syntax"></a>Syntaxe

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Remarques
Le `for...in` expression peut être comparée à la `for each` instruction dans d’autres langages .NET, car il est utilisé pour effectuer une boucle sur les valeurs d’une collection énumérable. Toutefois, `for...in` prend également en charge la mise en correspondance sur la collection au lieu de simplement itération sur la collection entière.

L’expression énumérable peut être spécifiée comme une collection énumérable ou, à l’aide de la `..` opérateur, comme une plage sur un type intégral. Les collections énumérables incluent les listes, séquences, tableaux, jeux, mappages et ainsi de suite. Tout type qui implémente `System.Collections.IEnumerable` peut être utilisé.

Lorsque vous exprimez une plage à l’aide de la `..` (opérateur), vous pouvez utiliser la syntaxe suivante.

*Démarrer* ... *Terminer*

Vous pouvez également utiliser une version qui inclut un incrément appelé le *ignorer*, comme dans le code suivant.

*Démarrer* ... *Ignorer* ... *Terminer*

Lorsque vous utilisez des plages intégrales et une variable de compteur simple comme modèle, le comportement par défaut est pour incrémenter la variable de compteur de 1 à chaque itération, mais si la plage comprend une valeur à ignorer, le compteur est incrémenté par la valeur skip à la place.

Les valeurs correspondantes dans le modèle peuvent également servir dans l’expression de corps.

Les exemples de code suivants illustrent l’utilisation de la `for...in` expression.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

La sortie est la suivante.

```
1
5
100
450
788
```

L’exemple suivant montre comment effectuer une boucle sur une séquence et comment utiliser un modèle de tuple au lieu d’une simple variable.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

La sortie est la suivante.

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

L’exemple suivant montre comment effectuer une boucle sur une plage d’entiers simple.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

La sortie de function1 est la suivante.

```
1 2 3 4 5 6 7 8 9 10
```

L’exemple suivant montre comment effectuer une boucle sur une plage avec un saut de 2, qui inclut tous les autres éléments de la plage.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

La sortie de `function2` est comme suit.

```
1 3 5 7 9
```

L’exemple suivant montre comment utiliser une plage de caractères.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

La sortie de `function3` est comme suit.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

L’exemple suivant montre comment utiliser une valeur de saut négative pour effectuer une itération inverse.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

La sortie de `function4` est comme suit.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Le début et la fin de la plage peuvent également être des expressions, telles que des fonctions, comme dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

La sortie de `function5` avec cette entrée est la suivante.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

L’exemple suivant illustre l’utilisation d’un caractère générique (_) lorsque l’élément n’est pas nécessaire dans la boucle.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

La sortie est la suivante.

```
Number of elements in list1: 5
```

`Note`Vous pouvez utiliser `for...in` dans les expressions de séquence et autres expressions de calcul, auquel cas une version personnalisée de la `for...in` expression est utilisée. Pour plus d’informations, consultez [séquences](sequences.md), [Workflows asynchrones](asynchronous-workflows.md), et [Expressions de calcul](computation-expressions.md).


## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Boucles : expression `for...to`](loops-for-to-expression.md)

[Boucles : expression `while...do`](loops-while-do-expression.md)
