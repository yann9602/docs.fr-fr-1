---
title: "Inférence de type (F#)"
description: "Découvrez comment le compilateur F # déduit les types de valeurs, variables, paramètres et valeurs de retour."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2d5fa4b1-732a-4d71-a62d-07f7ee79fe06
ms.openlocfilehash: c23954c0a0828cc7d2aae0553d37d5ee1dfbe152
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-inference"></a>Inférence de type

Cette rubrique décrit comment le compilateur F # déduit les types de valeurs, variables, paramètres et valeurs de retour.

## <a name="type-inference-in-general"></a>En général l’inférence de type
L’idée de l’inférence de type est que vous n’avez pas à spécifier les types de constructions F #, sauf lorsque le compilateur ne peut pas déduire ait le type. Omettre les informations de type explicite ne signifie pas que F # est un langage typé dynamiquement ou que les valeurs en F # sont faiblement typée. F # est un langage typé statiquement, ce qui signifie que le compilateur déduit un type exact pour chaque construction lors de la compilation. S’il n’est pas suffisamment d’informations pour le compilateur déduire les types de chaque construction, vous devez fournir les informations de type supplémentaires, généralement en ajoutant des annotations de type explicite quelque part dans le code.


## <a name="inference-of-parameter-and-return-types"></a>Inférence de paramètre et Types de retour
Dans une liste de paramètres, il est inutile de spécifier le type de chaque paramètre. Pourtant, F # est un langage typé statiquement et par conséquent, chaque valeur et chaque expression ont un type défini au moment de la compilation. Pour les types que vous ne spécifiez pas explicitement, le compilateur déduit le type en fonction du contexte. Si le type n’est pas un spécifié dans le cas contraire, il est déduit générique. Si le code utilise une valeur de façon incohérente, de sorte qu’il n’existe pas d’une seule type inféré satisfaisant à toutes les utilisations d’une valeur, que le compilateur signale une erreur.

Le type de retour d’une fonction est déterminé par le type de la dernière expression dans la fonction.

Par exemple, dans le code suivant, les types de paramètres `a` et `b` et le type de retour sont déduits pour être `int` , car le littéral `100` est de type `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Vous pouvez influencer l’inférence de type en modifiant les littéraux. Si vous effectuez la `100` un `uint32` en ajoutant le suffixe `u`, les types de `a`, `b`, et la valeur de retour sont déduits pour être `uint32`.

Vous pouvez également influencer l’inférence de type à l’aide d’autres constructions qui impliquent des restrictions sur le type, telles que les fonctions et méthodes qui fonctionnent avec un type particulier.

En outre, vous pouvez appliquer des annotations de type explicite pour les paramètres de fonction ou une méthode ou à des variables dans les expressions, comme indiqué dans les exemples suivants. Erreurs survenir si les conflits se produisent entre des contraintes différentes.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Vous pouvez également spécifier explicitement la valeur de retour d’une fonction en fournissant une annotation de type une fois tous les paramètres.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Un cas courant où une annotation de type est utile sur un paramètre est lorsque le paramètre est un type d’objet et que vous souhaitez utiliser un membre.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a>Généralisation automatique
Si le code de fonction n’est pas dépendant du type d’un paramètre, le compilateur considère que le paramètre générique. Il s’agit *généralisation automatique*, et il peut être très utile pour écrire du code générique sans augmenter la complexité.

Par exemple, la fonction suivante combine deux paramètres de n’importe quel type dans un tuple.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Le type est déduit

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Informations supplémentaires
L’inférence de type est décrite plus en détail dans la spécification du langage F #.


## <a name="see-also"></a>Voir aussi
[Généralisation automatique](generics/automatic-generalization.md)
