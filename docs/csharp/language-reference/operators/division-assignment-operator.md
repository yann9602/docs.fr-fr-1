---
title: "/=, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26096d9b5dfc565c9933f1ed8ffb241dc900d9ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>/=, opérateur (référence C#)
Opérateur d’assignation de division.  
  
## <a name="remarks"></a>Notes  
 Une expression qui utilise l’opérateur d’assignation `/=`, telle que  
  
```  
x /= y  
```  
  
 est équivalent à  
  
```  
x = x / y  
```  
  
 sauf que `x` n’est évalué qu’une seule fois. L’[opérateur /](../../../csharp/language-reference/operators/division-operator.md) est prédéfini pour les types numériques afin d’effectuer une division.  
  
 Vous ne pouvez pas surcharger directement l’opérateur `/=`, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur /](../../../csharp/language-reference/operators/division-operator.md) (voir [opérateur](../../../csharp/language-reference/keywords/operator.md)). Sur tous les opérateurs d’assignation composée, le fait de surcharger l’opérateur binaire surcharge implicitement l’assignation composée équivalente.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)
