---
title: "Transactions locales | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Transactions locales
Dans [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], vous pouvez utiliser des transactions lorsque vous souhaitez lier plusieurs tâches entre elles afin qu'elles s'exécutent comme une seule unité de travail.  Par exemple, imaginez qu'une application effectue deux tâches.  Premièrement, elle met à jour une table avec des informations de commande.  Deuxièmement, elle met à jour une table qui contient des informations de stock, en débitant les articles commandés.  Si l'une des tâches échoue, les deux mises à jour sont annulées.  
  
## Détermination du type de transaction  
 Une transaction est considérée comme locale lorsqu'il s'agit d'une transaction en une seule phase et qu'elle est gérée directement par la base de données.  Les transactions sont considérées comme distribuées lorsqu'elles sont coordonnées par un moniteur de transaction et utilisent des mécanismes de prévention de défaillance \(tels qu'une validation en deux phases\) pour la résolution des transactions.  
  
 Chacun des fournisseurs de données [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] a son propre objet `Transaction` pour l'exécution des transactions locales.  Si vous avez besoin qu'une transaction soit effectuée dans une base de données SQL Server, sélectionnez une transaction <xref:System.Data.SqlClient>.  Pour une transaction Oracle, utilisez le fournisseur <xref:System.Data.OracleClient>.  En outre, il y a une nouvelle classe <xref:System.Data.Common.DbTransaction> disponible pour l'écriture de code indépendant du fournisseur qui requiert des transactions.  
  
> [!NOTE]
>  Les transactions ont une efficacité maximale lorsqu'elles sont exécutées sur le serveur.  Si vous utilisez une base de données SQL Server qui utilise beaucoup des transactions explicites, envisagez de les écrire sous la forme de procédures stockées à l'aide de l'instruction Transact\-SQL BEGIN TRANSACTION.  Pour plus d'informations sur l'exécution de transactions côté serveur, consultez la documentation en ligne de SQL Server.  
  
## Exécution d'une transaction à l'aide d'une connexion unique  
 Dans [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], vous contrôlez les transactions à l'aide de l'objet `Connection`.  Vous pouvez initier une transaction locale avec la méthode `BeginTransaction`.  Après avoir commencé une transaction, vous pouvez inscrire une commande dans cette transaction avec la propriété `Transaction` d'un objet `Command`.  Vous pouvez ensuite valider ou annuler les modifications apportées à la source de données en fonction de la réussite ou de l'échec des composants de la transaction.  
  
> [!NOTE]
>  La méthode `EnlistDistributedTransaction` ne doit pas être utilisée pour une transaction locale.  
  
 La portée de la transaction est limitée à la connexion.  L'exemple suivant exécute une transaction explicite consistant en deux commandes distinctes dans le bloc `try`.  Les commandes exécutent des instructions INSERT sur la table Production.ScrapReason dans l'exemple de base de données [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] AdventureWorks, qui sont validées si aucune exception n'est levée.  Le code dans le bloc `catch` annule la transaction si une exception est levée.  En cas d'annulation de la transaction ou de fermeture de la connexion avant que la transaction ne soit terminée, celle\-ci est automatiquement annulée.  
  
## Exemple  
 Procédez comme suit pour effectuer une transaction.  
  
1.  Appelez la méthode <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> de l'objet <xref:System.Data.SqlClient.SqlConnection> pour marquer le début de la transaction.  La méthode <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> retourne une référence à la transaction.  Cette référence est affectée aux objets <xref:System.Data.SqlClient.SqlCommand> inscrits dans la transaction.  
  
2.  Assignez l'objet `Transaction` à la propriété <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> de l'objet <xref:System.Data.SqlClient.SqlCommand> à exécuter.  Si une commande est exécutée sur une connexion sur laquelle une transaction est active et si l'objet `Transaction` n'a pas été affecté à la propriété `Transaction` de l'objet `Command`, une exception est levée.  
  
3.  Exécutez les commandes requises.  
  
4.  Appelez la méthode <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> de l'objet <xref:System.Data.SqlClient.SqlTransaction> pour effectuer la transaction ou la méthode <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> pour y mettre fin.  Si la connexion est fermée ou libérée avant que l'une des méthodes <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> ou <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> ait été exécutée, la transaction est annulée.  
  
 L'exemple de code suivant illustre la logique transactionnelle utilisant [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] avec Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## Voir aussi  
 [Transactions et concurrence](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)   
 [Transactions distribuées](../../../../docs/framework/data/adonet/distributed-transactions.md)   
 [Intégration de System.Transactions à SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)