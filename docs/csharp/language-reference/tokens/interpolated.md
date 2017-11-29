---
title: "$ (référence C#)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d245bab063721abdb930aae113aab2094553b9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a>$ (référence C#)

Identifie un littéral de chaîne comme une [chaîne interpolée](../keywords/interpolated-strings.md). Une chaîne interpolée est une chaîne de type modèle qui contient du texte littéral et des *expressions interpolées*. Lorsque la chaîne interpolée est résolue, par exemple dans une instruction d’assignation ou un appel de méthode, ses expressions interpolées sont remplacées par leur représentation sous forme de chaînes dans la chaîne de résultat. Les chaînes interpolées remplacent les [chaînes de format composite](../../../standard/base-types/composite-format.md) prises en charge par le .NET Framework.

L’exemple suivant utilise le caractère `$` pour définir une chaîne interpolée.

[!code-csharp[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]

Pour plus d’informations sur les chaînes interpolées, consultez la rubrique [Chaînes interpolées](../keywords/interpolated-strings.md).

## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Caractères spéciaux C#](../../../csharp/language-reference/tokens/index.md)
