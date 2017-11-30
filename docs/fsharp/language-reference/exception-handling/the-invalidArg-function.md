---
title: "Exceptions : fonction invalidArg (F#)"
description: "Découvrez comment la fonction 'invalidArg' F # génère une exception d’argument."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d375b704-6b27-493e-bd1d-ee217a53c4b5
ms.openlocfilehash: 107bef361a6bd034e3d6a2227e18cf64b1b04576
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-invalidarg-function"></a>Exceptions : fonction invalidArg

Le `invalidArg` fonction génère une exception d’argument.


## <a name="syntax"></a>Syntaxe

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Remarques
Le nom de paramètre dans la syntaxe précédente est une chaîne avec le nom du paramètre dont l’argument n’était pas valide. Le *chaîne du message d’erreur* est une chaîne littérale ou une valeur de type `string`. Il devient le `Message` propriété de l’objet exception.

L’exception générée par `invalidArg` est un `System.ArgumentException` exception. Le code suivant illustre l’utilisation de `invalidArg` pour lever une exception.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

La sortie est la suivante, suivie d’une trace de pile (non affichée).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Voir aussi
[Gestion des exceptions](index.md)

[Types d'exceptions](exception-types.md)

[Exceptions : expression `try...with`](the-try-with-expression.md)

[Exceptions : expression `try...finally`](the-try-finally-expression.md)

[Exceptions : fonction `raise`](the-raise-function.md)

[Exceptions : fonction `failwith`](the-failwith-function.md)
