---
title: "Expressions lambda : mot clé fun (F#)"
description: "Découvrez comment utiliser le mot clé F # 'fun' pour définir une expression lambda, qui est une fonction anonyme."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Expressions lambda : mot clé fun (F#)

Le `fun` est utilisé pour définir une expression lambda, autrement dit, une fonction anonyme.


## <a name="syntax"></a>Syntaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Remarques
Le *la liste des paramètres* se compose généralement de noms et, éventuellement, de types de paramètres. En règle générale, les *la liste des paramètres* peuvent être composées de n’importe quel modèle F #. Pour obtenir une liste complète des modèles possibles, consultez [recherche de correspondance](../pattern-matching.md). Les listes de paramètres valides incluent les exemples suivants.

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

Le *expression* est le corps de la fonction, la dernière expression qui génère une valeur de retour. Exemples d’expressions lambda valides sont les suivantes :

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a>Utilisation d’expressions lambda
Expressions lambda sont particulièrement utiles lorsque vous souhaitez effectuer des opérations sur une liste ou un autre regroupement et souhaitez éviter la définition d’une fonction. De nombreuses fonctions de bibliothèque F # prennent les valeurs de fonction en tant qu’arguments, et il peut être particulièrement pratique d’utiliser une expression lambda dans ces cas. Le code suivant applique une expression lambda aux éléments d’une liste. Dans ce cas, la fonction anonyme ajoute 1 à chaque élément d’une liste.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a>Voir aussi
[Fonctions](index.md)
