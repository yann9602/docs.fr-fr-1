---
title: "+ , opérateur (Informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
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
ms.openlocfilehash: 5455375148f1924c7fe1cdb10e7924abb83a1565
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>+, opérateur (référence C#)
L’opérateur `+` peut être utilisé comme opérateur unaire ou opérateur binaire.  
  
## <a name="remarks"></a>Notes  
 Les opérateurs `+` sont prédéfinis pour tous les types numériques. Le résultat d’une opération `+` unaire sur un type numérique correspond simplement à la valeur de l’opérande.  
  
 Les opérateurs `+` binaires sont prédéfinis pour les types numériques et chaîne. Pour les types numériques, + calcule la somme des deux opérandes. Quand les deux opérandes ou l’un d’entre eux sont de type chaîne, + concatène les représentations sous forme de chaîne des opérandes.  
  
 Les types délégués fournissent aussi un opérateur `+` binaire, qui effectue la concaténation de délégués.  
  
 Les types définis par l’utilisateur peuvent surcharger les opérateurs `+` unaires et `+` binaires. Les opérations sur les types intégraux sont en général autorisées sur l’énumération. Pour plus d’informations, consultez [operator (référence C#)](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [operator (référence C#)](../../../csharp/language-reference/keywords/operator.md)

