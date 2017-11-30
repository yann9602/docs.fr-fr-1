---
title: "Comment : déterminer si certains ou tous les éléments d'une séquence remplissent une condition"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0dda546c0d8cd073a5d11bdf22805310e3f4f40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Comment : déterminer si certains ou tous les éléments d'une séquence remplissent une condition
L'opérateur <xref:System.Linq.Enumerable.All%2A> retourne `true` si tous les éléments d'une séquence remplissent une condition.  
  
 L'opérateur <xref:System.Linq.Queryable.Any%2A> retourne `true` si un élément d'une séquence remplit une condition.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne une séquence de clients possédant au moins une commande. Le `Where` / `where` clause prend la valeur de `true` si la donnée `Customer` a des `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Exemple  
 Le code Visual Basic suivant détermine la liste des clients qui n'ont pas passé de commande et vérifie qu'un nom de contact est fourni pour chaque client de cette liste.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Exemple  
 L'exemple C# suivant retourne une séquence de clients dont la `ShipCity` des commandes commence par la lettre C. Il retourne également les clients qui n'ont pas de commandes. De par sa conception, l'opérateur <xref:System.Linq.Queryable.All%2A> retourne `true` pour une séquence vide. Les clients qui n'ont pas de commande sont supprimés de la sortie de la console à l'aide de l'opérateur `Count`.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
