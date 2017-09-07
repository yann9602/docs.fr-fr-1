---
title: "&amp;, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d92a860df6fcc9acf14aab4ec558556735ac8aac
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="amp-operator-c-reference"></a>&amp;, opérateur (référence C#)
L’opérateur & peut être utilisé comme opérateur unaire ou comme opérateur binaire.  
  
## <a name="remarks"></a>Remarques  
 L’opérateur & unaire retourne l’adresse de son opérande (requiert un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md)).  
  
 Les opérateurs & binaires sont prédéfinis pour les types intégraux et `bool`. Pour les types intégraux, & calcule l’opération logique AND au niveau du bit de ses opérandes. Pour les opérandes `bool`, & calcule l’opération logique AND de ses opérandes ; autrement dit, le résultat est `true` uniquement si ses deux opérandes ont la valeur `true`.  
  
 L’opérateur `&` évalue les deux opérateurs indépendamment de la valeur du premier. Exemple :  
  
 [!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `&` binaire (voir [operator](../../../csharp/language-reference/keywords/operator.md)). Les opérations sur les types intégraux sont en général autorisées sur l’énumération. Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

