---
title: "(), op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "()_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "() (opérateur C#)"
  - "cast (opérateur C#)"
  - "conversion de type (C#), () (opérateur)"
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# (), op&#233;rateur (r&#233;f&#233;rence C#)
En plus d'être utilisé pour spécifier l'ordre des opérations dans une expression, les parenthèses sont utilisées pour effectuer les tâches suivantes :  
  
1.  Spécifiez des casts, ou conversions de type.  
  
     [!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  Appelez des méthodes ou des délégués.  
  
     [!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## Notes  
 Un cast appelle explicitement l'opérateur de conversion d'un type en un autre ; le cast échoue si aucun opérateur de conversion de ce genre n'est défini.  Pour définir un opérateur de conversion, consultez [explicit](../../../csharp/language-reference/keywords/explicit.md) et [implicit](../../../csharp/language-reference/keywords/implicit.md).  
  
 L'opérateur `()` ne peut pas être surchargé.  
  
 Pour plus d'informations, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Une expression de cast pourrait donner une syntaxe ambiguë.  L'expression `(x)–y`, par exemple, peut tout aussi bien être interprétée comme une expression de cast \(un cast de \-y en type x\) ou comme une expression additive combinée à une expression entre parenthèses \(qui calcule la valeur x \- y\).  
  
 Pour plus d'informations sur l'appel de méthode, consultez [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)