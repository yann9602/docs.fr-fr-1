---
title: "^, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 19
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
ms.openlocfilehash: f081dd2979930404639638179444adc05dd462e1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>^, opérateur (référence C#)
Les opérateurs `^` binaires sont prédéfinis pour les types intégraux et `bool`. Pour les types intégraux, `^` effectue l’opération de bits OR exclusif sur les opérandes. Pour les opérandes `bool`, `^` effectue l’opération OR exclusif logique sur ses opérandes. En conséquence, le résultat est `true` si et seulement si un seul des opérandes correspond à `true`.  
  
## <a name="remarks"></a>Remarques  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `^` (voir [operator](../../../csharp/language-reference/keywords/operator.md)). Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 Le calcul de `0xf8 ^ 0x3f` dans l’exemple précédent effectue une opération de bits OR exclusif des deux valeurs binaires suivantes, qui correspondent aux valeurs hexadécimales F8 et 3F :  
  
 `1111 1000`  
  
 `0011 1111`  
  
 Le résultat de l’opération OR exclusif est `1100 0111`, qui correspond à C7 en hexadécimal.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

