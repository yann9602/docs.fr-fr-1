---
title: "Guide pratique pour effectuer sans risque un cast à l'aide des opérateurs as et is (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
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
ms.openlocfilehash: c5daa8525f45c123dabb0f59dfd29385b9e50354
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Guide pratique pour effectuer sans risque un cast à l'aide des opérateurs as et is (Guide de programmation C#)
Les objets étant polymorphes, une variable d’un type de classe de base peut contenir un type dérivé. Pour accéder à la méthode du type dérivé, il est nécessaire de convertir à nouveau la valeur dans le type dérivé. Or, dans ce cas, toute tentative de conversion simple risque de lever une exception <xref:System.InvalidCastException>. C’est pourquoi C# propose les opérateurs [is](../../../csharp/language-reference/keywords/is.md) et [as](../../../csharp/language-reference/keywords/as.md). Vous pouvez utiliser ces opérateurs pour vérifier si une conversion de type (cast) aboutit sans lever d’exception. En règle générale, l’opérateur `as` est plus efficace, car de fait, il ne retourne la valeur de conversion que si cette opération peut aboutir. L’opérateur `is` retourne uniquement une valeur booléenne. Vous pouvez donc vous en servir pour déterminer simplement le type d’un objet sans avoir réellement besoin de le convertir.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent comment utiliser les opérateurs `is` et `as` pour effectuer une conversion d’un type de référence vers un autre sans risquer de lever une exception. L’exemple montre aussi comment utiliser l’opérateur `as` avec les types valeur Nullable.  
  
 [!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Types](../../../csharp/programming-guide/types/index.md)   
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)

