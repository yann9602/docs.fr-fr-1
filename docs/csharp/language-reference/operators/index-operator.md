---
title: "Op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "[]_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "opérateur d'indice (C#)"
  - "crochets [ ], opérateur C#"
  - "[], opérateur C#"
  - "opérateur d'indexation (C#)"
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# Op&#233;rateur (r&#233;f&#233;rence C#)
Les crochets \(`[]`\) sont utilisés pour les tableaux, les indexeurs et les attributs.  Ils peuvent aussi être utilisés avec des pointeurs.  
  
## Notes  
 Un type de tableau est un type suivi de `[]` :  
  
 [!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 Pour accéder à un élément d'un tableau, l'index de l'élément souhaité est placé entre crochets :  
  
 [!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 Une exception est levée si un index de tableau est hors limites.  
  
 L'opérateur d'indexation de tableau ne peut pas être surchargé. Toutefois, les types peuvent définir des indexeurs et des propriétés qui acceptent un ou plusieurs paramètres.  Les paramètres d'indexeur sont placés entre crochets, comme des index de tableau, mais ils peuvent être déclarés d'un type quelconque, contrairement aux index de tableau, qui doivent être intégraux.  
  
 Par exemple, le .NET Framework définit un type `Hashtable` qui associe des clés et des valeurs d'un type arbitraire :  
  
 [!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 Des crochets sont également utilisés pour spécifier des [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md) :  
  
 [!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 Vous pouvez utiliser des crochets pour ignorer un pointeur dans un index :  
  
 [!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 Aucune vérification des limites n'est effectuée.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)