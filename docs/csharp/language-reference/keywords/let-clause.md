---
title: "let, clause (R&#233;f&#233;rence&#160;C#) | Microsoft Docs"
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
  - "let_CSharpKeyword"
  - "let"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "let (clause C#)"
  - "let (mot clé C#)"
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# let, clause (R&#233;f&#233;rence&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Dans une expression de requête, il est parfois utile de stocker le résultat d'une sous\-expression pour l'utiliser dans les clauses suivantes.  Vous pouvez faire ceci avec le mot clé `let` qui crée une variable de portée et l'initialise avec le résultat de l'expression que vous fournissez.  Une fois initialisée avec une valeur, la variable de portée ne peut pas être utilisée pour stocker une autre valeur.  Toutefois, si la variable de portée contient un type requêtable, elle peut être interrogée.  
  
## Exemple  
 Dans l'exemple suivant, `let` est utilisé de deux façons :  
  
1.  Pour créer un type énumérable qui peut faire l'objet d'une requête.  
  
2.  Pour permettre à la requête d'appeler `ToLower` une seule fois sur la variable de portée `word`.  Si vous n'utilisez pas `let`, vous devez appeler `ToLower` dans chaque prédicat de la clause `where`.  
  
 [!code-cs[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Comment : gérer des exceptions dans des expressions de requête](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)