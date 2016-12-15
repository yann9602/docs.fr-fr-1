---
title: "false, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "false operator (mot clé C#)"
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# false, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Retourne la valeur [bool](../../../csharp/language-reference/keywords/bool.md) `true` pour indiquer qu'un opérande est `false` ; sinon, retourne la valeur `false`.  
  
 Avant C\# 2.0, les opérateurs `true` et `false` étaient utilisés pour créer des types valeur Nullable compatibles avec des types tels que `SqlBool`.  Le langage offre désormais une prise en charge intégrée des types valeur Nullable qu'il est préférable d'exploiter dès que possible pour ne pas surcharger les opérateurs `true` et `false` operators.  Pour plus d'informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Avec les valeurs booléennes Nullable, l'expression `a != b` n'équivaut pas nécessairement à `!(a == b)` puisque que l'une des valeurs ou les deux peuvent être Null.  Vous devez surcharger à la fois les opérateurs `true` et `false` séparément pour gérer comme il se doit les valeurs Null dans l'expression.  L'exemple suivant montre comment surcharger et utiliser les opérateurs `true` et `false`.  
  
 [!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 Vous pouvez utiliser un type qui surcharge les opérateurs `true` et `false` pour l'expression de contrôle dans les instructions [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md) et [for](../../../csharp/language-reference/keywords/for.md), ainsi que dans les [expressions conditionnelles](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Si un type définit l'opérateur `false`, il doit aussi définir l'opérateur [true](../../../csharp/language-reference/keywords/true.md).  
  
 Un type ne peut pas surcharger directement les opérateurs logiques conditionnels \([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)\), mais il est possible d'obtenir un résultat équivalent en surchargeant les opérateurs logiques réguliers et les opérateurs `true` et `false`.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)   
 [true](../../../csharp/language-reference/keywords/true.md)