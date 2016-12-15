---
title: "&amp;&amp;, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "&&_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "&& (opérateur C#)"
  - "opérateur AND logique (C#)"
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &amp;&amp;, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'opérateur AND conditionnel \(`&&`\) effectue une opération AND logique sur les opérandes de type `bool`, mais évalue uniquement le second opérande, si nécessaire.  
  
## Notes  
 L'opération  
  
```  
x && y  
```  
  
 correspond à l'opération  
  
```  
x & y  
```  
  
 sauf si `x`est `false`, `y` n'est pas évaluée, car le résultat du AND de l'opération est `false` indépendamment de la valeur d' `y` est.  Ce concept porte le nom d'évaluation « de court\-circuit ».  
  
 L'opérateur AND conditionnel ne peut pas être surchargé, mais la surcharge des opérateurs logiques normaux et des opérateurs [true](../../../csharp/language-reference/keywords/true.md) et [false](../../../csharp/language-reference/keywords/false.md) est, dans une certaine mesure, considérée également comme une surcharge des opérateurs logiques conditionnels.  
  
## Exemple  
 Dans l'exemple suivant, l'expression conditionnelle dans la deuxième instruction d' `if` a uniquement le premier opérande parce que l'opérande retourne `false`.  
  
 [!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)