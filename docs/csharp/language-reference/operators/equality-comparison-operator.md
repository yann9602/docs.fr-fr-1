---
title: "==, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>==, opérateur (référence C#)
Pour les types valeur prédéfinis, l’opérateur d’égalité (`==`) retourne true si les valeurs des opérandes sont égales et `false` dans le cas contraire. Pour les types référence autres que [string](../../../csharp/language-reference/keywords/string.md), `==` retourne `true` si ses deux opérandes font référence au même objet. Pour le type `string`, `==` compare les valeurs des chaînes.  
  
## <a name="remarks"></a>Remarques  
 Les types valeur définis par l’utilisateur peuvent surcharger l’opérateur `==` (consultez [operator](../../../csharp/language-reference/keywords/operator.md)). Il en va de même pour les types référence définis par l’utilisateur, même si par défaut `==` se comporte comme indiqué ci-dessus pour les types référence prédéfinis et définis par l’utilisateur. Si `==` est surchargé, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) doit l’être aussi. Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
