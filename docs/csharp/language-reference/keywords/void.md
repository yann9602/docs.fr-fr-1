---
title: "void (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
dev_langs:
- CSharp
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d1bd7ece5ce3b558c616a4eb3a4668c3c13eb1cb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="void-c-reference"></a>void (Référence C#)
Quand le mot clé `void` est utilisé en tant que type de retour pour une méthode, il spécifie que cette méthode ne retourne aucune valeur.

`void` n’est pas autorisé dans la liste des paramètres d’une méthode. Une méthode sans paramètres qui ne retourne aucune valeur se déclare comme suit :

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` est également utilisé dans un contexte unsafe pour déclarer un pointeur vers un type inconnu. Pour plus d’informations, consultez [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void` est un alias du type <xref:System.Void?displayProperty=fullName> .NET Framework.

## <a name="c-language-specification"></a>Spécification du langage C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)   
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

