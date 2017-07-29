---
title: "/, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
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
ms.openlocfilehash: 2972261996467f987fa457213b1bcb482d9f1519
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>/, opérateur (référence C#)
L’opérateur de division (`/`) divise son premier opérande par son deuxième opérande. Tous les types numériques ont des opérateurs de division prédéfinis.  
  
## <a name="remarks"></a>Remarques  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `/` (voir [operator](../../../csharp/language-reference/keywords/operator.md)). Une surcharge de l’opérateur `/` surcharge implicitement l’[opérateur /=](division-assignment-operator.md).  
  
 Quand vous divisez deux entiers, le résultat est toujours un entier. Par exemple, le résultat de 7 / 3 est 2. Pour déterminer le reste de 7 / 3, utilisez l’opérateur de reste ([%](../../../csharp/language-reference/operators/modulus-operator.md)). Pour obtenir un quotient comme nombre rationnel ou fraction, affectez au dividende ou au diviseur le type `float` ou `double`. Vous pouvez attribuer le type implicitement si vous exprimez le dividende ou le diviseur sous forme de nombre décimal en plaçant un chiffre à droite de la virgule décimale, comme le montre l’exemple suivant.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)

