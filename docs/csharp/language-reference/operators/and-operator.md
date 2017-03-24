---
title: "&amp;, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "&_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "opérateur de bits AND (C#)"
  - "& (opérateur C#)"
  - "& (opérateur C#)"
  - "AND (opérateur &) (C#)"
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# &amp;, op&#233;rateur (r&#233;f&#233;rence C#)
L'opérateur & peut fonctionner comme opérateur unaire ou binaire.  
  
## Notes  
 L'opérateur & unaire retourne l'adresse de son opérande \(requiert un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md)\).  
  
 Les opérateurs & binaires sont prédéfinis pour les types intégraux et `bool`.  Pour les types intégraux, & effectue l'opération logique de bits AND sur les opérandes.  Pour les opérandes `bool`, & effectue l'opération logique AND sur les opérandes. En conséquence, le résultat est `true` uniquement si les deux opérandes ont la valeur `true`.  
  
 L'opérateur `&` évalue les deux opérateurs indépendamment de la valeur du premier.  Par exemple :  
  
 [!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Les types définis par l'utilisateur peuvent surcharger l'opérateur `&` binaire \(consultez [operator](../../../csharp/language-reference/keywords/operator.md)\).  Les opérations sur les types intégraux sont en général autorisées sur énumération.  Lorsqu'un opérateur binaire est surchargé, l'opérateur d'assignation correspondant \(s'il y en a un\) est, lui aussi, implicitement surchargé.  
  
## Exemple  
 [!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)