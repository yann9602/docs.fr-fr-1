---
title: "!=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b69d0b12734e690f0ba0209ccbbc7627ff92fe8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>!=, opérateur (référence C#)
L’opérateur d’inégalité (`!=`) retourne la valeur false si ses opérandes sont égaux et la valeur true dans le cas contraire. Les opérateurs d’inégalité sont prédéfinis pour tous les types, dont string et object. Les types définis par l’utilisateur peuvent surcharger l’opérateur `!=`.  
  
## <a name="remarks"></a>Remarques  
 Pour les types valeur prédéfinis, l’opérateur d’inégalité (`!=`) retourne la valeur true si les valeurs de ses opérandes sont différentes et la valeur false dans le cas contraire. Pour les types référence autres que `string`, `!=` retourne la valeur true si ses deux opérandes font référence à des objets différents. Pour le type `string`, `!=` compare les valeurs des chaînes.  
  
 Les types valeur définis par l’utilisateur peuvent surcharger l’opérateur `!=` (consultez [operator](../../../csharp/language-reference/keywords/operator.md)). Il en va de même pour les types référence définis par l’utilisateur, même si par défaut `!=` se comporte comme indiqué ci-dessus pour les types référence prédéfinis et définis par l’utilisateur. Si `!=` est surchargé, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) doit aussi l’être. Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
