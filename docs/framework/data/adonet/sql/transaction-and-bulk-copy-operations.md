---
title: "Transaction et op&#233;rations de copie en bloc | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Transaction et op&#233;rations de copie en bloc
Les opérations de copie en bloc peuvent être réalisées sous forme d'opérations isolées ou en tant qu'étape d'une transaction en comptant plusieurs.  Cette dernière option vous permet d'effectuer plus d'une opération de copie en bloc dans la même transaction et d'effectuer d'autres opérations de base de données \(telles que des insertions, des mises à jour et des suppressions\) tout en vous laissant la possibilité de valider ou de restaurer toute la transaction.  
  
 Par défaut, une opération de copie en bloc est exécutée sous forme d'opération isolée :  elle se produit de manière non traitée, sans possibilité de restauration.  Si vous devez restaurer tout ou partie de la copie en bloc en cas d'erreur, vous pouvez soit utiliser une transaction <xref:System.Data.SqlClient.SqlBulkCopy> managée, soit effectuer une opération de copie en bloc à l'intérieur d'une transaction existante, soit être inscrit dans un **System.Transactions** <xref:System.Transactions.Transaction>.  
  
## Exécution d'une opération de copie en bloc non traitée  
 L'application console suivante montre ce qui se passe lorsqu'une opération de copie en bloc non traitée rencontre une erreur dans l'opération.  
  
 Dans l'exemple, la table source et la table de destination incluent une colonne `Identity` nommée **ProductID**.  Le code commence par préparer la table de destination en supprimant toutes les lignes puis en insérant une simple ligne dont le **ProductID** est censé exister dans la table source.  Par défaut, une nouvelle valeur pour la colonne `Identity` est générée dans la table de destination pour chaque ligne ajoutée.  Dans cet exemple, une option est définie lorsque la connexion est ouverte qui oblige le processus de chargement en bloc à utiliser les valeurs `Identity` de la table source.  
  
 L'opération de copie en bloc est exécutée avec la propriété <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> ayant la valeur 10.  Lorsque l'opération rencontre la ligne non valide, une exception est levée.  Dans ce premier exemple, l'opération de copie en bloc n'est pas traitée.  Tous les lots copiés jusqu'au moment de l'erreur sont validés ; le lot contenant la clé dupliquée est annulé et l'opération de copie en bloc est suspendue avant la reprise du traitement des autres lots.  
  
> [!NOTE]
>  Cet exemple ne s'exécutera pas à moins que vous ayez créé les tables de travail comme décrit dans la rubrique [Configuration de l'exemple de copie en bloc](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).  Ce code est fourni uniquement pour illustrer la syntaxe de l'utilisation de **SqlBulkCopy**.  Si les tables sources et de destination se trouvent dans la même instance [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], il est plus facile et plus rapide d'utiliser une instruction [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## Exécution d'une opération de copie en bloc dédiée dans une transaction  
 Par défaut, une opération de copie en bloc est sa propre transaction.  Si vous voulez effectuer une opération de copie en bloc dédiée, créez une nouvelle instance de <xref:System.Data.SqlClient.SqlBulkCopy> avec une chaîne de connexion ou utilisez un objet <xref:System.Data.SqlClient.SqlConnection> existant sans transaction active.  Dans chaque scénario, l'opération de copie en bloc crée puis valide ou annule la transaction.  
  
 Vous pouvez spécifier explicitement l'option <xref:System.Data.SqlClient.SqlBulkCopyOptions> dans le constructeur de classe <xref:System.Data.SqlClient.SqlBulkCopy> pour exécuter explicitement une opération de copie en bloc dans sa propre transaction. Chaque lot de l'opération de copie en bloc s'exécute alors dans une transaction distincte.  
  
> [!NOTE]
>  Puisque des lots différents sont exécutés dans différentes transactions, si une erreur se produit durant l'opération de copie en bloc, toutes les lignes du lot en cours seront annulées mais les lignes des lots précédents resteront dans la base de données.  
  
 L'application console suivante est semblable à l'exemple précédent, avec une exception : dans cet exemple, l'opération de copie en bloc gère ses propres transactions.  Tous les lots copiés jusqu'au moment de l'erreur sont validés ; le lot contenant la clé dupliquée est annulé et l'opération de copie en bloc est suspendue avant la reprise du traitement des autres lots.  
  
> [!IMPORTANT]
>  Cet exemple ne s'exécutera pas à moins que vous ayez créé les tables de travail comme décrit dans la rubrique [Configuration de l'exemple de copie en bloc](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).  Ce code est fourni uniquement pour illustrer la syntaxe de l'utilisation de **SqlBulkCopy**.  Si les tables sources et de destination se trouvent dans la même instance [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], il est plus facile et plus rapide d'utiliser une instruction [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## Utilisation de transactions existantes  
 Vous pouvez spécifier un objet <xref:System.Data.SqlClient.SqlTransaction> existant comme paramètre dans un constructeur <xref:System.Data.SqlClient.SqlBulkCopy>.  Dans cette situation, l'opération de copie en bloc est effectuée dans une transaction existante et l'état de la transaction ne subit aucune modification \(c'est\-à\-dire qu'elle n'est ni validée ni abandonnée\).  Cela permet à une application d'inclure l'opération de copie en bloc dans une transaction avec d'autres opérations de base de données.  Cependant, si vous ne spécifiez pas un objet <xref:System.Data.SqlClient.SqlTransaction> et passez une référence null, et que la connexion a une transaction active, une exception est levée.  
  
 Si vous devez restaurer toute l'opération de copie en bloc en raison d'une d'erreur ou si la copie en bloc doit s'exécuter dans le cadre d'un plus grand processus pouvant être restauré, vous pouvez fournir un objet <xref:System.Data.SqlClient.SqlTransaction> au constructeur <xref:System.Data.SqlClient.SqlBulkCopy>.  
  
 L'application console suivante est semblable au premier exemple \(non accompli\), avec une exception : dans cet exemple, l'opération de copie en bloc est incluse dans une transaction externe plus large.  Si l'erreur de violation de clé primaire se produit, toute la transaction est annulée et aucune ligne n'est ajoutée à la table de destination.  
  
> [!IMPORTANT]
>  Cet exemple ne s'exécutera pas à moins que vous ayez créé les tables de travail comme décrit dans la rubrique [Configuration de l'exemple de copie en bloc](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).  Ce code est fourni uniquement pour illustrer la syntaxe de l'utilisation de **SqlBulkCopy**.  Si les tables sources et de destination se trouvent dans la même instance [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], il est plus facile et plus rapide d'utiliser une instruction [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` pour copier les données.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## Voir aussi  
 [Opérations de copie en bloc dans SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)