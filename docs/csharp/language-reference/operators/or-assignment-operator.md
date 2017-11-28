---
title: "|=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aac4fd6016b65daa15da4bd3a414f385edce7c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>|=, opérateur (référence C#)
Opérateur d’assignation OR.  
  
## <a name="remarks"></a>Remarques  
 Une expression qui utilise l’opérateur d’assignation `|=`, telle que  
  
```  
x |= y  
```  
  
 est équivalent à  
  
```  
x = x | y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. L’[opérateur &#124](../../../csharp/language-reference/operators/or-operator.md) effectue une opération OR logique au niveau du bit sur les opérandes intégraux et une opération OR logique sur les opérandes de type bool.  
  
 L’opérateur `|=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur &#124;](../../../csharp/language-reference/operators/or-operator.md) (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
