---
title: "*=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
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
ms.openlocfilehash: 2969ba3ce303da591353fd0114dccf752e63f2c3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>*=, opérateur (référence C#)
Opérateur d’assignation de multiplication binaire.  
  
## <a name="remarks"></a>Remarques  
 Une expression qui utilise l’opérateur d’assignation `*=`, telle que  
  
```  
x *= y  
```  
  
 est équivalent à  
  
```  
x = x * y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. L’[opérateur *](../../../csharp/language-reference/operators/multiplication-operator.md) est prédéfini pour les types numériques de façon à effectuer une multiplication.  
  
 L’opérateur `*=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur *](../../../csharp/language-reference/operators/multiplication-operator.md) (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

