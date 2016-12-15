---
title: "/=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "/=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/= (opérateur d'assignation de division) (C#)"
  - "opérateur d'assignation de division (/=) (C#)"
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /=, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Opérateur d'assignation de division.  
  
## Notes  
 Expression utilisant l'opérateur d'assignation `/=`, comme  
  
```  
x /= y  
```  
  
 est équivalent à  
  
```  
x = x / y  
```  
  
 si ce n'est que `x` n'est évalué qu'une seule fois.  L'[opérateur \/](../../../csharp/language-reference/operators/division-operator.md) est prédéfini pour les types numériques afin d'effectuer une division.  
  
 L'opérateur `/=` ne peut pas être surchargé directement, mais les types définis par l'utilisateur peuvent surcharger l'opérateur [\/](../../../csharp/language-reference/operators/division-operator.md) \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  Sur tous les opérateurs d'assignation composée, surcharger l'opérateur binaire surcharge implicitement l'assignation composée équivalente.  
  
## Exemple  
 [!code-cs[csRefOperators#5](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)