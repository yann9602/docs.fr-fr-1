---
title: "Comment&#160;: retourner une requ&#234;te &#224; partir d&#39;une m&#233;thode (Guide de programmation&#160;C#) | Microsoft Docs"
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
  - "requête de retours de méthode (C#)"
  - "requêtes (LINQ en C#), requête de retours de méthode"
  - "expressions de requête (LINQ en C#), requête de retours de méthode"
ms.assetid: 9d6f20a7-f085-44cf-9df3-71948255ec68
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: retourner une requ&#234;te &#224; partir d&#39;une m&#233;thode (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cet exemple indique comment retourner une requête à partir d'une méthode comme valeur de retour et en tant que paramètre `out`.  
  
 Toute requête doit avoir un type de <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, ou un type dérivé tel que <xref:System.Linq.IQueryable%601>.  Par conséquent, toute valeur de retour ou paramètre `out` d'une méthode qui retourne une requête doit également avoir ce type.  Si une méthode matérialise une requête dans un type <xref:System.Collections.Generic.List%601> concret ou un type <xref:System.Array>, il est considéré comme retournant les résultats de la requête au lieu de la requête elle\-même.  Une variable de requête retournée à partir d'une méthode peut néanmoins être composée ou modifiée.  
  
## Exemple  
 Dans l'exemple suivant, la première méthode retourne une requête comme valeur de retour et la seconde méthode retourne une requête comme paramètre `out` .  Notez que dans les deux cas, c'est une requête qui est retournée, et non des résultats de requête.  
  
 [!code-cs[csProgGuideLINQ#80](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-a-query-from-a-method_1.cs)]  
  
## Compilation du code  
  
-   Créez un projet [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] qui cible la version 3.5 ou une version ultérieure de .NET Framework.  Par défaut, le projet possède une référence à System.Core.dll et une directive `using` pour l'espace de noms System.Linq.  
  
-   Remplacez la classe par le code dans l'exemple.  
  
-   Appuyez sur F5 pour compiler et exécuter le programme.  
  
-   Appuyez sur une touche pour quitter la fenêtre de console.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)