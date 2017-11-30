---
title: "Comment : demander des informations"
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
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0722f83c19c1eff43606afceeda484d72691eb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-information"></a>Comment : demander des informations
Les requêtes effectuées dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilisent la même syntaxe que les requêtes effectuées dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. La seule différence est que les objets référencés dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requêtes sont mappés aux éléments d’une base de données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement.  
  
 Certaines fonctionnalités de requêtes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] peuvent nécessiter une attention particulière dans les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Pour plus d’informations, consultez [concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).  
  
## <a name="example"></a>Exemple  
 La requête suivante demande une liste de clients de Londres. Dans cet exemple, `Customers` est une table de l'exemple de base de données Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Interrogation de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
