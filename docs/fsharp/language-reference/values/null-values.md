---
title: Valeurs Null (F#)
description: "Découvrez comment la valeur null est utilisée dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 68ebd261-51cf-4582-b2dc-44c84d1c2500
ms.openlocfilehash: 01c14de00eb5efd0952145ffc8aabe69d65a3a48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="null-values"></a>Valeurs Null

Cette rubrique décrit l’utilisation de la valeur null en F #.


## <a name="null-value"></a>Valeur null
La valeur null n’est pas normalement utilisée en F # pour des valeurs ou des variables. Toutefois, null apparaît comme une valeur anormale dans certaines situations. Si un type est défini en F #, valeur null n’est pas autorisée comme valeur normale, sauf si le [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) attribut est appliqué au type. Si un type est défini dans un autre langage .NET, null est une valeur possible, et lorsque vous interagissez avec de tels types, votre code F # peut rencontrer des valeurs null.

Pour un type défini en F # et utilisé strictement à partir de F #, la seule façon de créer une valeur null à l’aide de la bibliothèque F # directement consiste à utiliser [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) ou [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Toutefois, pour un type F #, qui est utilisé à partir d’autres langages .NET, ou si vous utilisez ce type avec une API qui n’est pas écrite en F #, telles que le .NET Framework, les valeurs null peuvent se produire.

Vous pouvez utiliser la `option` type en F # lorsque vous utilisez une variable de référence avec une valeur null possible dans un autre langage .NET. Au lieu de null, avec F # `option` type, vous utilisez la valeur de l’option `None` si aucun objet. Vous utilisez la valeur de l’option `Some(obj)` avec un objet `obj` lorsqu’il existe un objet. Pour plus d’informations, consultez [Options](../options.md).

Le `null` le mot clé est un mot clé valide dans le langage F #, et vous devez l’utiliser lorsque vous travaillez avec des API .NET Framework ou d’autres API qui est écrites dans un autre langage .NET. Les deux situations dans lesquelles vous devrez peut-être une valeur null sont lorsque vous appelez une API .NET et passez une valeur null en tant qu’argument, et lorsque vous interprétez la valeur de retour ou paramètre de sortie d’un appel de méthode .NET.

Pour passer une valeur null à une méthode .NET, utilisez simplement le `null` mot clé dans le code appelant. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Pour interpréter une valeur null est obtenue à partir d’une méthode .NET, utiliser les critères spéciaux si vous le pouvez. L’exemple de code suivant montre comment utiliser les critères spéciaux pour interpréter la valeur null est retournée à partir de `ReadLine` quand il tente de lire au-delà de la fin d’un flux d’entrée.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Valeurs NULL pour des types F # peuvent également être générées d’autres manières, par exemple, lorsque vous utilisez `Array.zeroCreate`, qui appelle `Unchecked.defaultof`. Vous devez être prudent avec ce code pour conserver les valeurs null encapsulées. Dans une bibliothèque prévue uniquement pour F #, vous n’avez pas à vérifier les valeurs null dans chaque fonction. Si vous écrivez une bibliothèque pour l’interopérabilité avec d’autres langages .NET, vous devrez peut-être ajouter des vérifications pour la valeur null de paramètres d’entrée et lever une `ArgumentNullException`, tout comme vous le feriez dans le code c# ou Visual Basic.

Vous pouvez utiliser le code suivant pour vérifier si une valeur arbitraire est null.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Voir aussi
[Valeurs](index.md)

[Expressions match](../match-expressions.md)
