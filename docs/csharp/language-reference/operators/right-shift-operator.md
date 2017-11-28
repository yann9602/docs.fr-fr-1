---
title: "&gt;&gt;, opérateur (Informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7c2eddf06d7b8417c9fcb0fed395b2bf51e07144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;, opérateur (Informations de référence sur C#)
L’opérateur de décalage vers la droite (`>>`) décale son premier opérande vers la droite du nombre de bits spécifié par son deuxième opérande.  
  
## <a name="remarks"></a>Remarques  
 Si le premier opérande est de type [int](../../../csharp/language-reference/keywords/int.md) ou [uint](../../../csharp/language-reference/keywords/uint.md) (quantité 32 bits), la valeur du décalage est donnée par les cinq bits de poids faible du second opérande (second opérande & 0x1f).  
  
 Si le premier opérande est un [long](../../../csharp/language-reference/keywords/long.md) ou un [ulong](../../../csharp/language-reference/keywords/ulong.md) (quantité 64 bits), la valeur du décalage est donnée par les six bits de poids faible du second opérande (second opérande & 0x3f).  
  
 Si le premier opérande est un [int](../../../csharp/language-reference/keywords/int.md) ou un [long](../../../csharp/language-reference/keywords/long.md), le décalage vers la droite est un décalage arithmétique (les bits vierges d’ordre haut prennent la valeur du bit de signe). Si le premier opérande est de type [uint](../../../csharp/language-reference/keywords/uint.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md), le décalage vers la droite est un décalage logique (les bits de poids fort prennent la valeur zéro).  
  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `>>` ; le type du premier opérande doit être le type défini par l’utilisateur, et le type du second opérande doit être [int](../../../csharp/language-reference/keywords/int.md). Pour plus d’informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md). Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
