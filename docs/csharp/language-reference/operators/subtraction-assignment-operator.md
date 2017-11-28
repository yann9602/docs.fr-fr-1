---
title: "-=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 443f0d717288a491838d23eaa63218150bd346d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-c-reference"></a>-=, opérateur (référence C#)
Opérateur d’assignation de soustraction.  
  
## <a name="remarks"></a>Remarques  
 Une expression qui utilise l’opérateur d’assignation `-=`, telle que  
  
```  
x -= y  
```  
  
 est équivalent à  
  
```  
x = x - y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. La signification de l’[opérateur -](../../../csharp/language-reference/operators/subtraction-operator.md) dépend des types de `x` et `y` (soustraction pour les opérandes numériques, suppression de délégués pour les opérandes délégués, etc.).  
  
 L’opérateur `-=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur -](../../../csharp/language-reference/operators/subtraction-operator.md) (voir [opérateur](../../../csharp/language-reference/keywords/operator.md)).  
  
 L’opérateur -= est également utilisé en C# pour annuler l’abonnement à un événement. Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
