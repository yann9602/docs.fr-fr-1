---
title: "^=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "^=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "^= (opérateur C#)"
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# ^=, op&#233;rateur (r&#233;f&#233;rence C#)
Opérateur d'assignation OR exclusif.  
  
## Notes  
 Une expression de la forme  
  
```  
x ^= y  
```  
  
 est évaluée comme  
  
```  
x = x ^ y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  L'[opérateur ^](../../../csharp/language-reference/operators/xor-operator.md) effectue une opération de bits OR exclusif sur les opérandes de type intégral et une opération logique OR exclusif sur les opérandes de type [bool](../../../csharp/language-reference/keywords/bool.md).  
  
 L'opérateur ^\= ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'opérateur [^ operator](../../../csharp/language-reference/operators/xor-operator.md) \(consultez [operator](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemple  
 [!code-cs[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)