---
title: "%=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>%=, opérateur (référence C#)
Opérateur d’assignation de reste.  
  
## <a name="remarks"></a>Remarques  
 Une expression qui utilise l’opérateur d’assignation `%=`, telle que  
  
```  
x %= y  
```  
  
 est équivalent à  
  
```  
x = x % y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. L’[opérateur %](../../../csharp/language-reference/operators/modulus-operator.md) est prédéfini pour les types numériques de façon à calculer le reste d’une division.  
  
 L’opérateur `%=` ne peut pas être surchargé directement, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur %](../../../csharp/language-reference/operators/modulus-operator.md) (consultez [operator (informations de référence sur C#)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
