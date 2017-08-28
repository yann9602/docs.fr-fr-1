---
title: "&gt;=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
caps.latest.revision: 16
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
ms.openlocfilehash: 59b134ce1e1169b0a5f4583374148d39ceb8326a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a>&gt;=, opérateur (référence C#)
Tous les types numériques et d’énumération définissent un opérateur relationnel « supérieur ou égal à », `>=`, qui retourne `true` si le premier opérande est supérieur ou égal au second, et `false` dans le cas contraire.  
  
## <a name="remarks"></a>Remarques  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `>=`. Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md). Si `>=` est surchargé, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) doit l’être aussi. Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

