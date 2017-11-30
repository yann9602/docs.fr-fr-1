---
title: "Exceptions : fonction failwith (F#)"
description: "Découvrez comment la fonction 'failwith' génère une exception F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2e0c1f28-cc6c-4ecd-bb93-3816c4dd7cd3
ms.openlocfilehash: 295a4d754e0df015ba67daa9cf80d7df5b40199c
ms.sourcegitcommit: ffb9aa26cd5211dc6d96ebb42968d8357048880e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="exceptions-the-failwith-function"></a>Exceptions : fonction failwith

Le `failwith` fonction génère une exception F #.


## <a name="syntax"></a>Syntaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Remarques
Le *chaîne du message d’erreur* dans la syntaxe précédente est une chaîne littérale ou une valeur de type `string`. Il devient le `Message` propriété de l’exception.

L’exception qui est générée par `failwith` est un `System.Exception` exception, qui est une référence qui porte le nom `Failure` dans le code F #. Le code suivant illustre l’utilisation de `failwith` pour lever une exception.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a>Voir aussi
[Gestion des exceptions](index.md)

[Types d'exceptions](exception-types.md)

[Exceptions : expression `try...with`](the-try-with-expression.md)

[Exceptions : expression `try...finally`](the-try-finally-expression.md)

[Exceptions : fonction `raise`](the-raise-function.md)
