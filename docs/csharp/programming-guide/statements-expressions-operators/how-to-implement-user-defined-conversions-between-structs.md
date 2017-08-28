---
title: "Guide pratique pour implémenter des conversions définies par l'utilisateur entre des structs (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: 11
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
ms.openlocfilehash: cc8856bb3bf8943c1b6648f7d81447a3e59b9489
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Guide pratique pour implémenter des conversions définies par l'utilisateur entre des structs (Guide de programmation C#)
L’exemple suivant définit deux structs, `RomanNumeral` et `BinaryNumeral`, et décrit les conversions entre ces deux structs.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>Programmation fiable  
  
-   Dans l’exemple précédent, l’instruction :  
  
     [!code-cs[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     convertit un `RomanNumeral` en `BinaryNumeral`. Étant donné qu’il n’existe pas de conversion directe de `RomanNumeral` en `BinaryNumeral`, un cast est utilisé pour convertir un `RomanNumeral` en un `int`, et un autre cast est utilisé pour convertir un `int` en un `BinaryNumeral`.  
  
-   L’instruction  
  
     [!code-cs[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     convertit un `BinaryNumeral` en `RomanNumeral`. Étant donné que `RomanNumeral` définit une conversion implicite d’un `BinaryNumeral`, aucun cast n’est nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)

