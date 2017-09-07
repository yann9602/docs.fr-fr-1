---
title: "++, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
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
ms.openlocfilehash: 9f481dbe2437495b109d6d41cd24c8b4bb5b6a5b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>++, opérateur (référence C#)
L’opérateur d’incrément (`++`) incrémente son opérande de 1. L’opérateur d’incrément peut figurer avant ou après son opérande : `++variable` et `variable++`.  
  
## <a name="remarks"></a>Remarques  
 La première forme est une opération d’incrément préfixé. Le résultat de l’opération est la valeur de l’opérande après qu’il a été incrémenté.  
  
 La deuxième forme est une opération d’incrément suffixé. Le résultat de l’opération est la valeur de l’opérande avant qu’il ait été incrémenté.  
  
 Les types numériques et d’énumération ont des opérateurs d’incrément prédéfinis. Les types définis par l’utilisateur peuvent surcharger l’opérateur `++` . Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

