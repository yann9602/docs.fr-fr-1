---
title: "struct (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- struct_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: 23
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
ms.openlocfilehash: 309e68a57e1ee869850d960ffaac6cf35eb6e260
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="struct-c-reference"></a>struct (Référence C#)
Un type `struct` est un type valeur utilisé pour encapsuler de petits groupes de variables liées, par exemple les coordonnées d'un rectangle ou les caractéristiques d'un élément dans un inventaire. L'exemple suivant illustre une déclaration struct simple :  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a>Remarques  
 Les structs peuvent également contenir des [constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md), des [constantes](../../../csharp/programming-guide/classes-and-structs/constants.md), des [champs](../../../csharp/programming-guide/classes-and-structs/fields.md), des [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), des [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), des [indexeurs](../../../csharp/programming-guide/indexers/index.md), des [opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md), des [événements](../../../csharp/programming-guide/events/index.md) et des [types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md). Toutefois, si plusieurs membres sont nécessaires, il est conseillé de plutôt utiliser une classe.  
  
 Pour obtenir des exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Les structs peuvent implémenter une interface, mais ne peuvent pas hériter d'un autre struct. C'est pourquoi, les membres struct ne peuvent pas être déclarés en tant que `protected`.  
  
 Pour plus d’informations, consultez [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="examples"></a>Exemples  
 Pour obtenir des exemples et des informations supplémentaires, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 Pour obtenir des exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)   
 [class](../../../csharp/language-reference/keywords/class.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)

