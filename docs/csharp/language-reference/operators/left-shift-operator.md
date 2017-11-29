---
title: "&lt;&lt;, opérateur (Informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 400dbc799c68bb9e1bc00695954115f2eb6af7c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;, opérateur (Informations de référence sur C#)
L’opérateur de décalage vers la gauche (`<<`) décale son premier opérande vers la gauche du nombre de bits spécifié par son deuxième opérande. Le deuxième opérande doit être de type [int](../../../csharp/language-reference/keywords/int.md) ou d’un type pour lequel une conversion numérique implicite vers `int` est prédéfinie.  
  
## <a name="remarks"></a>Remarques  
 Si le premier opérande est de type [int](../../../csharp/language-reference/keywords/int.md) ou [uint](../../../csharp/language-reference/keywords/uint.md) (quantité de 32 bits), la valeur du décalage est donnée par les cinq bits de poids faible du second opérande. Autrement dit, la valeur réelle du décalage est comprise entre 0 et 31 bits.  
  
 Si le premier opérande est de type [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) (quantité de 64 bits), la valeur du décalage est donnée par les six bits de poids faible du second opérande. Autrement dit, la valeur réelle du décalage est comprise entre 0 et 63 bits.  
  
 Les bits de poids fort qui ne se trouvent pas dans la plage du type du premier opérande après le décalage sont ignorés, et les bits vides de poids faible sont remplis de zéros. Les opérations de décalage ne provoquent jamais de dépassements de capacité.  
  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `<<` (consultez [operator](../../../csharp/language-reference/keywords/operator.md)) ; le type du premier opérande doit être le type défini par l’utilisateur, et le type du second opérande doit être `int`. Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a>Commentaires  
 Notez que `i<<1` et `i<<33` donnent le même résultat, car 1 et 33 possèdent les cinq mêmes bits de poids faible.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
