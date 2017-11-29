---
title: Types d'exceptions (F#)
description: "Découvrez comment définir et utiliser des types d’exception F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a>Types d'exceptions

Il existe deux catégories d’exceptions en F #: les types d’exceptions .NET et les types d’exception F #. Cette rubrique décrit comment définir et utiliser des types d’exception F #.


## <a name="syntax"></a>Syntaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Remarques
Dans la syntaxe précédente, *-type d’exception* est le nom d’un type d’exception F # nouveau, et *-type d’argument* représente le type d’un argument qui peut être fourni lorsque vous déclenchez une exception de ce type. Vous pouvez spécifier plusieurs arguments à l’aide d’un type de tuple pour *-type d’argument*.

Une définition classique pour une exception F # semblable au suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Vous pouvez générer une exception de ce type en utilisant la `raise` de fonction, comme suit.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Vous pouvez utiliser un type d’exception F # directement dans les filtres dans un `try...with` expression, comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Le type d’exception que vous définissez avec la `exception` mot-clé dans F # est un nouveau type qui hérite de `System.Exception`.


## <a name="see-also"></a>Voir aussi
[Gestion des exceptions](index.md)

[Exceptions : fonction `raise`](the-raise-function.md)

[Hiérarchie des exceptions](https://msdn.microsoft.com/library/z4c5tckx.aspx)
