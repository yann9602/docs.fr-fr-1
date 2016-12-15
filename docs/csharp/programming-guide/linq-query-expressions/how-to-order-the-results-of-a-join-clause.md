---
title: "Comment&#160;: classer les r&#233;sultats d&#39;une clause Join (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Join (clause C#)"
  - "jointures (C#), trier les résultats"
  - "requêtes (LINQ en C#), jointures"
  - "expressions de requête (LINQ en C#), jointures"
ms.assetid: 83f36f16-2ba3-453f-8b9f-7d02b415610e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: classer les r&#233;sultats d&#39;une clause Join (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cet exemple indique comment classer les résultats d'une opération de jointure.  Notez que le classement est exécuté après la jointure.  Bien que vous puissiez utiliser une clause `orderby` avec l'une ou plusieurs des séquences sources avant la jointure, nous ne le recommandons généralement pas.  Certains fournisseurs [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] ne peuvent pas conserver ce classement après la jointure.  
  
## Exemple  
 Cette requête crée une jointure de groupe, puis classe les groupes selon l'élément de catégorie, qui est encore dans la portée.  À l'intérieur de l'initialiseur de type anonyme, une sous\-requête classe tous les éléments correspondants à partir de la séquence de produits.  
  
 [!code-cs[csProgGuideLINQ#81](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-order-the-results-of-a-join-clause_1.cs)]  
  
## Compilation du code  
  
-   Créez un projet [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] qui cible la version 3.5 du .NET Framework.  Par défaut, le projet possède une référence à System.Core.dll et une directive `using` pour l'espace de noms System.Linq.  
  
-   Copiez le code dans votre projet.  
  
-   Appuyez sur F5 pour compiler et exécuter le programme.  
  
-   Appuyez sur une touche pour quitter la fenêtre de console.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [orderby, clause](../../../csharp/language-reference/keywords/orderby-clause.md)   
 [join, clause](../../../csharp/language-reference/keywords/join-clause.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)