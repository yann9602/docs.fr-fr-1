---
title: "$ (référence C#) | Microsoft Docs"
ms.date: 2017-02-09
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
dev_langs:
- CSharp
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8b6afd7d9839f6d86f7fcfa3f097053ba4f418ff
ms.lasthandoff: 03/13/2017

---
# <a name="-c-reference"></a>$ (référence C#)

Identifie un littéral de chaîne comme une [chaîne interpolée](../keywords/interpolated-strings.md). Une chaîne interpolée est une chaîne de type modèle qui contient du texte littéral et des *expressions interpolées*. Lorsque la chaîne interpolée est résolue, par exemple dans une instruction d’assignation ou un appel de méthode, ses expressions interpolées sont remplacées par leur représentation sous forme de chaînes dans la chaîne de résultat. Les chaînes interpolées remplacent les [chaînes de format composite](../../../standard/base-types/composite-format.md) prises en charge par le .NET Framework.

L’exemple suivant utilise le caractère `$` pour définir une chaîne interpolée.

[!CODE-cs[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]

Pour plus d’informations sur les chaînes interpolées, consultez la rubrique [Chaînes interpolées](../keywords/interpolated-strings.md).

## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Caractères spéciaux C#](../../../csharp/language-reference/tokens/index.md)

