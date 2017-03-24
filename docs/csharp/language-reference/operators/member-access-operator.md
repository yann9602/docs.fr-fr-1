---
title: ". Op&#233;rateur (r&#233;f&#233;rence&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "._CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ". opérateur (C#)"
  - "opérateur point (.) (C#)"
  - "opérateur d'accès aux membres (.) (C#)"
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# . Op&#233;rateur (r&#233;f&#233;rence&#160;C#)
L'opérateur point \(`.`\) est utilisé pour l'accès aux membres.  L'opérateur point spécifie un membre d'un type ou d'un espace de noms.  Par exemple, l'opérateur point est utilisé pour accéder aux méthodes spécifiques figurant dans les bibliothèques de classes .NET Framework :  
  
 [!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 Par exemple, considérons la classe suivante :  
  
 [!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 La variable `s` possède deux membres, `a` et `b`. Pour accéder à ces membres, utilisez l'opérateur point :  
  
 [!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 Le point est aussi utilisé pour former des noms qualifiés, c'est\-à\-dire des noms qui spécifient l'espace de noms ou l'interface, par exemple, auquel ils appartiennent.  
  
 [!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 La directive using rend facultative la qualification de certains noms :  
  
 [!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 En revanche, lorsqu'un identificateur est ambigu, il doit être qualifié :  
  
 [!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)