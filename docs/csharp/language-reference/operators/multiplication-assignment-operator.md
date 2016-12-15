---
title: "*=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "*=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "*= (opérateur C#)"
  - "opérateur d'assignation de multiplication binaire (*=) (C#)"
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# *=, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Opérateur binaire d'assignation de multiplication.  
  
## Notes  
 Expression utilisant l'opérateur d'assignation `*=`, comme  
  
```  
x *= y  
```  
  
 est équivalent à  
  
```  
x = x * y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  L'[opérateur \*](../../../csharp/language-reference/operators/multiplication-operator.md) est prédéfini pour les types numériques afin d'effectuer une multiplication.  
  
 L'opérateur `*=` ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'opérateur [\*](../../../csharp/language-reference/operators/multiplication-operator.md) \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  
  
## Exemple  
 [!code-cs[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)