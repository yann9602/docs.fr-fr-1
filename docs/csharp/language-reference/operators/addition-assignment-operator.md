---
title: "+=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: 20
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
ms.openlocfilehash: 42567b2d8e7d9b694ce64ccb88e0fd4bfe05b020
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>+=, opérateur (référence C#)
Opérateur d’assignation d’addition.  
  
## <a name="remarks"></a>Remarques  
 Une expression qui utilise l’opérateur d’assignation `+=`, telle que  
  
```  
x += y  
```  
  
 est équivalent à  
  
```  
x = x + y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. La signification de l’[opérateur +](../../../csharp/language-reference/operators/addition-operator.md) dépend des types de `x` et `y` (addition pour les opérandes numériques, concaténation pour les opérandes de type chaîne, etc.).  
  
 L’opérateur `+=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur -](../../../csharp/language-reference/operators/addition-operator.md) (consultez [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
 L’opérateur `+=` est également utilisé pour spécifier une méthode qui sera appelée en réponse à un événement ; ces méthodes sont appelées « gestionnaires d’événements ». L’utilisation de l’opérateur `+=` dans ce contexte est appelée *abonnement à un événement*. Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) et [Délégués](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

