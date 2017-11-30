---
title: "Exceptions : fonction raise (F#)"
description: "Découvrez comment la fonction F # 'raise' est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: dc524a06d075b982a6aa1fd266769bfc7d883517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-raise-function"></a>Exceptions : fonction raise

Le `raise` fonction est utilisée pour indiquer qu’une erreur ou une condition exceptionnelle s’est produite. Informations sur l’erreur sont capturées dans un objet exception.


## <a name="syntax"></a>Syntaxe

```fsharp
raise (expression)
```

## <a name="remarks"></a>Remarques
Le `raise` fonction génère un objet exception et lance une pile de processus de déroulement. Le processus de déroulement de pile est géré par le common language runtime (CLR), par conséquent, le comportement de ce processus est le même, comme dans tout autre langage .NET. Le processus de déroulement de pile est une recherche pour un gestionnaire d’exceptions qui correspond à l’exception générée. La recherche commence dans le courant `try...with` expression, le cas échéant. Chaque modèle dans le `with` bloc est activé, dans l’ordre. Lorsqu’un gestionnaire d’exceptions correspondant est trouvé, l’exception est considérée comme gérée ; Sinon, la pile est déroulée et `with` blocs de la chaîne d’appel sont vérifiées jusqu'à ce qu’un gestionnaire correspondant est trouvé. N’importe quel `finally` blocs qui sont rencontrées dans la chaîne d’appel sont également exécutées en séquence comme la pile se déroule.

Le `raise` fonction est l’équivalent de `throw` en c# ou C++. Utilisez `reraise` dans un gestionnaire catch pour propager la même exception en haut de la chaîne d’appel.

Les exemples de code suivants illustrent l’utilisation de la `raise` fonction génère une exception.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

Le `raise` fonction peut également être utilisée pour lever des exceptions .NET, comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a>Voir aussi
[Gestion des exceptions](index.md)

[Types d'exceptions](exception-types.md)

[Exceptions : expression `try...with`](the-try-with-expression.md)

[Exceptions : expression `try...finally`](the-try-finally-expression.md)

[Exceptions : fonction `failwith`](the-failwith-function.md)

[Exceptions : fonction `invalidArg`](the-invalidArg-function.md)
