---
title: "&gt;, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
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
ms.openlocfilehash: 5b4eb1f6fcca311fc772e4dbe0ce0391201af3de
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a>&gt;, opérateur (référence C#)
Tous les types numériques et d’énumération définissent un opérateur relationnel « supérieur à » (`>`) qui retourne `true` si le premier opérande est supérieur au second, et `false` dans le cas contraire.  
  
## <a name="remarks"></a>Remarques  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `>` (voir [operator](../../../csharp/language-reference/keywords/operator.md)). Si `>` est surchargé, [<](../../../csharp/language-reference/operators/less-than-operator.md) doit l’être aussi. Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)

