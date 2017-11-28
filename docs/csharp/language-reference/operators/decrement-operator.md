---
title: "--, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4eb68143103d44defeac7191e7c4ce7d1ee90e9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="---operator-c-reference"></a>--, opérateur (référence C#)
L’opérateur de décrémentation (`--`) décrémente son opérande de 1. L’opérateur de décrémentation peut figurer avant ou après son opérande : `--variable` et `variable--`. La première forme est une opération de décrément préfixé. Le résultat de l’opération est la valeur de l’opérande « après » sa décrémentation. La deuxième forme est une opération de décrément suffixé. Le résultat de l’opération est la valeur de l’opérande « avant » sa décrémentation.  
  
## <a name="remarks"></a>Remarques  
 Les types numériques et d’énumération ont des opérateurs de décrémentation prédéfinis.  
  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `--` (voir [operator](../../../csharp/language-reference/keywords/operator.md)). Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
