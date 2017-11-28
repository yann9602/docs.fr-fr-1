---
title: "++, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>++, opérateur (référence C#)
L’opérateur d’incrément (`++`) incrémente son opérande de 1. L’opérateur d’incrément peut figurer avant ou après son opérande : `++variable` et `variable++`.  
  
## <a name="remarks"></a>Remarques  
 La première forme est une opération d’incrément préfixé. Le résultat de l’opération est la valeur de l’opérande après qu’il a été incrémenté.  
  
 La deuxième forme est une opération d’incrément suffixé. Le résultat de l’opération est la valeur de l’opérande avant qu’il ait été incrémenté.  
  
 Les types numériques et d’énumération ont des opérateurs d’incrément prédéfinis. Les types définis par l’utilisateur peuvent surcharger l’opérateur `++` . Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
