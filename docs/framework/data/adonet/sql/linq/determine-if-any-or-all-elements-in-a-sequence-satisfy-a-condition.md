---
title: "D&#233;terminer si certains ou tous les &#233;l&#233;ments d&#39;une s&#233;quence remplissent une condition | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# D&#233;terminer si certains ou tous les &#233;l&#233;ments d&#39;une s&#233;quence remplissent une condition
L'opérateur <xref:System.Linq.Enumerable.All%2A> retourne `true` si tous les éléments d'une séquence remplissent une condition.  
  
 L'opérateur <xref:System.Linq.Queryable.Any%2A> retourne `true` si un élément d'une séquence remplit une condition.  
  
## Exemple  
 L'exemple suivant retourne une séquence de clients possédant au moins une commande.  La clause `Where`\/`where` prend la valeur `true` si le `Customer` donné possède une `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## Exemple  
 Le code Visual Basic suivant détermine la liste des clients qui n'ont pas passé de commande et vérifie qu'un nom de contact est fourni pour chaque client de cette liste.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## Exemple  
 L'exemple C\# suivant retourne une séquence de clients dont la `ShipCity` des commandes commence par la lettre C.  Il retourne également les clients qui n'ont pas de commandes.  De par sa conception, l'opérateur <xref:System.Linq.Queryable.All%2A> retourne `true` pour une séquence vide. Les clients qui n'ont pas de commande sont supprimés de la sortie de la console à l'aide de l'opérateur `Count`.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)