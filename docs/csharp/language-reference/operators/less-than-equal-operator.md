---
title: "&lt;=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
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
ms.openlocfilehash: 931843783888a844d9f90f273b2362d327e8ccbc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="lt-operator-c-reference"></a>&lt;=, opérateur (référence C#)
Tous les types numériques et d’énumération définissent un opérateur relationnel « inférieur ou égal à » (`<=`) qui retourne `true` si le premier opérande est inférieur ou égal au deuxième et `false` dans le cas contraire.  
  
## <a name="remarks"></a>Remarques  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `<=`. Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md). Si `<=` est surchargé, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) doit aussi l’être. Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)

