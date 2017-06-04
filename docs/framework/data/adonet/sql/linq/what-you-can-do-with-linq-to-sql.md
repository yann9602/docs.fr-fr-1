---
title: "Que faire avec LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Que faire avec LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge toutes les fonctions clés que recherchent les développeurs SQL. Vous pouvez demander des informations et insérer, mettre à jour et supprimer des informations dans des tables.  
  
## Sélection  
 Pour effectuer une sélection \(*projection*\) il vous suffit d'écrire une requête [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dans votre propre langage de programmation, puis d'exécuter cette requête pour récupérer les résultats.[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit lui\-même toutes les opérations requises dans les opérations SQL nécessaires que vous connaissez. Pour plus d'informations, consultez [LINQ à SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Dans l'exemple suivant, les noms de société des clients de Londres sont récupérés et affichés dans la fenêtre de console.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## Insertion  
 Pour exécuter une `Insert` SQL, il vous suffit d'ajouter des objets au modèle objet que vous avez créé et d'appeler <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext>.  
  
 Dans l'exemple suivant, un nouveau client et des informations le concernant sont ajoutés à la table `Customers` à l'aide de <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## Mise à jour  
 Pour `Update` une entrée d'une base de données, récupérez d'abord l'élément et modifiez\-le directement dans le modèle objet. Après avoir modifié l'objet, appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext> pour mettre la base de données à jour.  
  
 Dans l'exemple suivant, tous les clients de Londres sont récupérés. Le nom de ville "London" est ensuite remplacé par "London \- Metro". Enfin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelée pour envoyer les modifications à la base de données.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## Suppression  
 Pour `Delete` un élément, supprimez\-le de la collection à laquelle il appartient, puis appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext> pour valider la modification.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne reconnaît les opérations de suppression en cascade. Si vous voulez supprimer une ligne dans une table avec des contraintes sur cette suppression, consultez [Procédure : supprimer des lignes de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Dans l'exemple suivant, le client dont le `CustomerID` est `98128` est extrait de la base de données. Ensuite, après confirmation de la récupération de la ligne client, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> est appelé pour supprimer cet objet de la collection. Enfin, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé pour envoyer la suppression à la base de données.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## Voir aussi  
 [Guide de programmation](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)   
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [Prise en main](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)