---
title: Type unit (F#)
description: "Découvrez comment le type 'unit' F # est souvent utilisé pour marquer l’emplacement où une valeur est requise par la syntaxe du langage lorsqu’aucune valeur n’est nécessaire ou souhaitée."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: eabbb6d7-80f3-4fa5-80b4-0f48982466a7
ms.openlocfilehash: 60ac08c0e3f8380a8f9dec7a083ede93c68bb0e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="unit-type"></a>Unit, type

Le `unit` type est un type qui indique l’absence d’une valeur spécifique ; la `unit` type a uniquement une valeur unique, qui agit comme un espace réservé lorsqu’aucune autre valeur n’existe ou n’est nécessaire.


## <a name="syntax"></a>Syntaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Remarques
Chaque expression F # doit correspondre à une valeur. Pour les expressions qui ne génèrent pas d’une valeur qui présente un intérêt, la valeur de type `unit` est utilisé. Le `unit` type ressemble à la `void` type dans les langages tels que c# et C++.

Le `unit` type a une valeur unique, et qui est indiquée par le jeton `()`.

La valeur de la `unit` type est souvent utilisé dans la programmation F # pour marquer l’emplacement où une valeur est requise par la syntaxe du langage, mais lorsqu’aucune valeur n’est nécessaire ou souhaitée. Un exemple peut être la valeur de retour d’un `printf` (fonction). Étant donné que les actions importantes de la `printf` opération se produit dans la fonction, la fonction n’a pas retourner une valeur réelle. Par conséquent, la valeur de retour est de type `unit`.

Certaines constructions attendent une `unit` valeur. Par exemple, un `do` liaison ou du code au niveau supérieur d’un module est censé prendre une `unit` valeur. Le compilateur émet un avertissement quand un `do` liaison ou du code au niveau supérieur d’un module produit un résultat autre que le `unit` valeur qui n’est pas utilisé, comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Cet avertissement est une caractéristique de la programmation fonctionnelle ; Il n’apparaît pas dans les autres langages de programmation .NET. Dans un programme purement fonctionnel, dans lequel les fonctions n’ont pas d’effets secondaires, la valeur de retournée finale est le seul résultat d’un appel de fonction. Par conséquent, lorsque le résultat est ignoré, il est une erreur de programmation possible. Bien que F # n’est pas un langage de programmation purement fonctionnel, il est conseillé de suivre le style de programmation fonctionnelle autant que possible.

## <a name="see-also"></a>Voir aussi
[Primitifs](primitive-types.md)

[Informations de référence du langage F#](index.md)
