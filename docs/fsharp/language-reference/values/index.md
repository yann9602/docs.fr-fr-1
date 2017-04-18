---
title: Valeurs (F#)
description: Valeurs (F#)
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5e1e73c3-5adb-4bba-9976-d57f1ff6cd8d
translationtype: Human Translation
ms.sourcegitcommit: 0a01ec92a90d99fafaacbd3f71f5177e5cf94a68
ms.openlocfilehash: 31d28a5ff1bb7d9a88949bcaee895a405a5e7014
ms.lasthandoff: 04/05/2017

---

# <a name="values"></a>Valeurs

En F#, les valeurs sont des quantités qui ont un type spécifique ; les valeurs peuvent être des nombres intégraux ou à virgule flottante, des caractères ou du texte, des listes, des séquences, des tableaux, des tuples, des unions discriminées, des enregistrements, des types de classe ou des valeurs de fonction.


## <a name="binding-a-value"></a>Liaison d’une valeur
Le terme *liaison* signifie l’association d’un nom à une définition. Le mot clé `let` lie une valeur, comme dans les exemples suivants :

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Le type d’une valeur est déduit de la définition. Pour un type primitif, tel qu’un nombre intégral ou à virgule flottante, le type est déterminé à partir du type du littéral. Par conséquent, dans l’exemple précédent, le compilateur déduit que le type de `b` est `unsigned int`, alors qu’il déduit que le type de `a` est `int`. Le type d’une valeur de fonction est déterminé à partir de la valeur de retour dans le corps de la fonction. Pour plus d’informations sur les types de valeurs de fonction, consultez [Fonctions](../functions/index.md). Pour plus d’informations sur les types de littéraux, consultez [Littéraux](../literals.md).


## <a name="why-immutable"></a>Pourquoi immuables ?
Des valeurs immuables sont des valeurs qui ne peuvent pas être modifiées durant toute l’exécution d’un programme. Si vous travaillez d’habitude avec des langages tels que C++, Visual Basic ou C#, vous pourrez être surpris de constater que F# donne la primauté aux valeurs immuables, et non aux variables auxquelles de nouvelles valeurs peuvent être assignées pendant l’exécution d’un programme. Les données immuables sont un élément important de la programmation fonctionnelle. Dans un environnement multithread, des variables mutables partagées qui peuvent être modifiées par différents threads sont difficiles à gérer. Par ailleurs, avec des variables mutables, il peut parfois être difficile de savoir si une variable peut être modifiée quand elle est passée à une autre fonction.

Dans les langages fonctionnels purs, il n’y a pas de variables, les fonctions se comportent strictement comme des fonctions mathématiques. Là où le code dans un langage procédural utilise une assignation de variable pour modifier une valeur, le code équivalent dans un langage fonctionnel comprend une valeur immuable comme entrée, une fonction immuable et différentes valeurs immuables comme sortie. Cette rigueur mathématique donne lieu à un raisonnement plus carré sur le comportement du programme, ce qui permet aux compilateurs de vérifier le code plus rigoureusement et de l’optimiser plus efficacement. Pour les développeurs, il est plus facile de comprendre le code et de l’écrire correctement. Le code fonctionnel est donc probablement plus facile à déboguer que le code procédural ordinaire.

F# n’est pas un langage fonctionnel pur ; toutefois, il prend entièrement en charge la programmation fonctionnelle. L’utilisation de valeurs immuables est conseillée, car votre code bénéficie ainsi d’un aspect important de la programmation fonctionnelle.


## <a name="mutable-variables"></a>Variables mutables
Vous pouvez utiliser le mot clé `mutable` pour spécifier une variable pouvant être modifiée. En F#, les variables mutables doivent généralement avoir une portée limitée, soit comme champ d’un type, soit comme valeur locale. Des variables mutables avec une portée limitée sont plus faciles à contrôler et moins susceptibles d’être modifiées de manière incorrecte.

Vous pouvez assigner une valeur initiale à une variable mutable à l’aide du mot clé `let`, de la même façon que vous définissez une valeur. Toutefois, la différence est que vous pouvez assigner par la suite de nouvelles valeurs à des variables mutables à l’aide de l’opérateur `<-`, comme dans l’exemple suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]
    
## <a name="related-topics"></a>Rubriques connexes


|Titre|Description|
|-----|-----------|
|[Liaisons let](../functions/let-bindings.md)|Fournit des informations sur l’utilisation du mot clé `let` pour lier des noms à des valeurs et à des fonctions.|
|[Fonctions](../functions/index.md)|Fournit une vue d’ensemble des fonctions en F#.|

## <a name="see-also"></a>Voir aussi
[Valeurs Null](null-Values.md)

[Informations de référence du langage F#](../index.md)

