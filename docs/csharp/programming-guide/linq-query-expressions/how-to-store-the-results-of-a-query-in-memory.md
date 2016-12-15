---
title: "Comment&#160;: stocker les r&#233;sultats d’une requ&#234;te dans la m&#233;moire (Guide de programmation&#160;C#) | Microsoft Docs"
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
  - "stockage des résultats de requête LINQ [LINQ en C#]"
  - "expressions de requête [LINQ en C#], stocker les résultats"
ms.assetid: 7271597f-3523-4f7b-b088-1eeffe913b2d
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: stocker les r&#233;sultats d’une requ&#234;te dans la m&#233;moire (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fondamentalement, une requête est un jeu d'instructions sur la récupération et l'organisation de données.  L'exécution de la requête requiert un appel à sa méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.  Cet appel est effectué lorsque vous utilisez une boucle `foreach` pour itérer au sein des éléments.  Évaluer une requête et stocker ses résultats sans exécuter une boucle d' `foreach`, appelez simplement l'une des méthodes suivantes sur la variable de requête :  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 Lorsque vous stockez les résultats de la requête, nous vous recommandons d'assigner l'objet de collection retourné à une nouvelle variable comme indiqué dans l'exemple suivant :  
  
## Exemple  
 [!code-cs[csProgGuideLINQ#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  
## Compilation du code  
  
-   Créez un projet [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] qui cible la version 3.5 du .NET Framework.  Par défaut, le projet possède une référence à System.Core.dll et une directive `using` pour l'espace de noms System.Linq.  
  
-   Copiez le code dans votre projet.  
  
-   Appuyez sur F5 pour compiler et exécuter le programme.  
  
-   Appuyez sur une touche pour quitter la fenêtre de console.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)