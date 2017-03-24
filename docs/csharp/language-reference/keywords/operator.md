---
title: "operator (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "operator_CSharpKeyword"
  - "operator"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "operator (mot clé C#)"
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# operator (r&#233;f&#233;rence C#)
Utilisez le mot clé `operator` pour surcharger un opérateur intégré ou fournir une conversion définie par l'utilisateur dans une déclaration de classe ou de structure.  
  
## Exemple  
 La formulation suivante est une classe extrêmement simplifiée pour les nombres fractionnels.  Elle surcharge les opérateurs \+ et \* pour effectuer des additions et des multiplications de fractions, et fournit également un opérateur qui convertit un type fraction en type double.  
  
 [!code-cs[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [implicites](../../../csharp/language-reference/keywords/implicit.md)   
 [explicites](../../../csharp/language-reference/keywords/explicit.md)   
 [Comment : implémenter des conversions définies par l'utilisateur entre des structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)