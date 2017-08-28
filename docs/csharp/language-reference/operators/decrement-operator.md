---
title: "--, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 17
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
ms.openlocfilehash: 100e68f3b07164b0cfb398a32f47137f2726943f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="---operator-c-reference"></a>--, opérateur (référence C#)
L’opérateur de décrémentation (`--`) décrémente son opérande de 1. L’opérateur de décrémentation peut figurer avant ou après son opérande : `--variable` et `variable--`. La première forme est une opération de décrément préfixé. Le résultat de l’opération est la valeur de l’opérande « après » sa décrémentation. La deuxième forme est une opération de décrément suffixé. Le résultat de l’opération est la valeur de l’opérande « avant » sa décrémentation.  
  
## <a name="remarks"></a>Remarques  
 Les types numériques et d’énumération ont des opérateurs de décrémentation prédéfinis.  
  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `--` (voir [operator](../../../csharp/language-reference/keywords/operator.md)). Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

