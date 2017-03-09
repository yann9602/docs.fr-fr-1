---
title: "||, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "||_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "|| (opérateur C#)"
  - "opérateur conditionnel OR (||) (C#)"
  - "opérateur OR logique (C#)"
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 25
---
# ||, op&#233;rateur (r&#233;f&#233;rence C#)
L'opérateur OR conditionnel \(`||`\) effectue une logique OR de ses opérandes d' `bool` .  Si le premier opérande a la `true`, le deuxième n'est pas évaluée.  Si le premier opérande a la `false`, le deuxième opérateur OR détermine si l'expression dans son ensemble à `true` ou à `false`.  
  
## Notes  
 L'opération  
  
```  
x || y  
```  
  
 correspond à l'opération  
  
```  
x | y  
```  
  
 sauf si `x` est `true`, `y` n'est pas évalué car l'opération OR est `true` indépendamment de la valeur d' `y`.  Ce concept est appelé l'évaluation de court\-circuit «  ».  
  
 L'opérateur OR conditionnel ne peut pas être surchargé, mais les surcharges des opérateurs logiques normaux et les opérateurs de [true](../../../csharp/language-reference/keywords/true.md) et de [false](../../../csharp/language-reference/keywords/false.md) , avec certaines restrictions, sont également prises en compte les surcharges des opérateurs logiques conditionnels.  
  
## Exemple  
 Dans les exemples suivants, l'expression qui utilise `||` a uniquement le premier opérande.  L'expression qui utilise `|`évalue les deux opérandes.  Dans le deuxième exemple, une exception runtime se produit si les deux opérandes sont évalués.  
  
 [!code-cs[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#52)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)