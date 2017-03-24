---
title: "|=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "|=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "|= (opérateur) (OU assignation) (C#)"
  - "OU opérateur d'assignation (|=) (C#)"
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# |=, op&#233;rateur (r&#233;f&#233;rence C#)
Opérateur d'assignation OR.  
  
## Notes  
 Expression utilisant l'opérateur d'assignation `|=`, comme  
  
```  
x |= y  
```  
  
 est équivalent à  
  
```  
x = x | y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  L'[opérateur &#124;](../../../csharp/language-reference/operators/or-operator.md) effectue une opération logique de bits OR sur les opérandes de type intégral et une opération logique OR sur les opérandes de type bool.  
  
 L'opérateur `|=` ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'opérateur [&#124;](../../../csharp/language-reference/operators/or-operator.md) \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemple  
 [!code-cs[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)