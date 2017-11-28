---
title: "/, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>/, opérateur (référence C#)
L’opérateur de division (`/`) divise son premier opérande par son deuxième opérande. Tous les types numériques ont des opérateurs de division prédéfinis.  
  
## <a name="remarks"></a>Remarques  
 Les types définis par l’utilisateur peuvent surcharger l’opérateur `/` (voir [operator](../../../csharp/language-reference/keywords/operator.md)). Une surcharge de l’opérateur `/` surcharge implicitement l’[opérateur /=](division-assignment-operator.md).  
  
 Quand vous divisez deux entiers, le résultat est toujours un entier. Par exemple, le résultat de 7 / 3 est 2. Pour déterminer le reste de 7 / 3, utilisez l’opérateur de reste ([%](../../../csharp/language-reference/operators/modulus-operator.md)). Pour obtenir un quotient comme nombre rationnel ou fraction, affectez au dividende ou au diviseur le type `float` ou `double`. Vous pouvez attribuer le type implicitement si vous exprimez le dividende ou le diviseur sous forme de nombre décimal en plaçant un chiffre à droite de la virgule décimale, comme le montre l’exemple suivant.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
