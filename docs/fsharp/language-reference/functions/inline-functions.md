---
title: Fonctions inline (F#)
description: "Découvrez comment utiliser les fonctions F # inline intégrés directement dans le code appelant."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a>Fonctions inline

*Les fonctions inline* sont des fonctions intégrées directement dans le code appelant.


## <a name="using-inline-functions"></a>À l’aide de fonctions Inline
Lorsque vous utilisez des paramètres de type statique, toutes les fonctions qui sont paramétrables par des paramètres de type doivent être inline. Cela garantit que le compilateur peut résoudre ces paramètres de type. Lorsque vous utilisez des paramètres de type générique ordinaires, il n’existe aucune restriction de ce type.

Autre que l’activation de l’utilisation de contraintes de membre, les fonctions inline peuvent être utiles pour optimiser le code. Toutefois, les utilisation abusive des fonctions inline peut rendre votre code moins résistant aux modifications apportées aux optimisations du compilateur et l’implémentation des fonctions de bibliothèque. Pour cette raison, évitez d’utiliser des fonctions inline pour l’optimisation, sauf si vous avez tenté de tous les autres techniques d’optimisation. Rendre une fonction ou une méthode inline peut parfois améliorer les performances, mais qui n’est pas toujours le cas. Par conséquent, vous devez également utiliser les mesures de performances pour vérifier que la fabrication d’une fonction donnée inline n’a en fait un effet positif.

Le `inline` modificateur peut être appliqué à des fonctions au niveau supérieur, au niveau du module ou au niveau de la méthode dans une classe.

L’exemple de code suivant illustre une fonction inline au niveau supérieur, une méthode d’instance inline et une méthode statique inline.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a>Les fonctions inline et inférence de Type
La présence de `inline` affecte l’inférence de type. Il s’agit, car les fonctions inline peuvent avoir résolus statiquement des paramètres de type, alors que les fonctions non inline ne peut pas. L’exemple de code suivant illustre un cas où `inline` est utile parce que vous utilisez une fonction qui a un paramètre de type résolus statiquement, le `float` opérateur de conversion.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Sans le `inline` modificateur, l’inférence de type force la fonction à prendre un type spécifique, dans ce cas `int`. Mais avec la `inline` modificateur, la fonction est également déduite comme ayant un paramètre de type résolus statiquement. Avec la `inline` modificateur, le type est déduit que les éléments suivants :

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Cela signifie que la fonction accepte tout type qui prend en charge une conversion vers **float**.


## <a name="see-also"></a>Voir aussi
[Fonctions](index.md)

[Contraintes](../generics/constraints.md)

[Paramètres de type résolus statiquement](../generics/statically-resolved-type-parameters.md)
