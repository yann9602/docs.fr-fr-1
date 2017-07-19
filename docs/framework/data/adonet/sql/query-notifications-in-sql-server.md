---
title: "Notifications de requ&#234;te dans SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Notifications de requ&#234;te dans SQL Server
Basées sur l'infrastructure Service Broker, les notifications de requête permettent de notifier des applications en cas de modification de données.  Cette fonction est particulièrement utile pour les applications qui génèrent un cache d'informations à partir d'une base de données, telles que les applications Web, et qui doivent être informées en cas de modification des données sources.  
  
 ADO.NET vous permet d'implémenter les notifications de requête de trois manières :  
  
1.  L'implémentation de bas niveau est assurée par la classe `SqlNotificationRequest` qui expose les fonctionnalités côté serveur, vous permettant d'exécuter une commande avec une demande de notification.  
  
2.  L'implémentation de haut niveau est assurée par la classe `SqlDependency` qui fournit une abstraction de haut niveau des fonctionnalités de notification entre l'application source et SQL Server, ce qui vous permet d'utiliser une dépendance pour détecter des modifications au niveau serveur.  Généralement, il s'agit de la manière la plus simple et la plus efficace, pour des applications clientes managées, d'exploiter la fonctionnalité de notification de SQL Server en utilisant le fournisseur de données .NET Framework pour SQL Server.  
  
3.  En outre, les applications Web créées à l'aide d'ASP.NET 2.0 ou version ultérieure peuvent utiliser les classes d'assistance `SqlCacheDependency`.  
  
 Les notifications de requête sont utilisées pour les applications qui doivent actualiser des affichages ou des caches suite à l'apport de modifications aux données sous\-jacentes.  Microsoft SQL Server permet aux applications .NET Framework d'envoyer une commande à SQL Server et de demander la génération d'une notification si l'exécution de cette commande produit des ensembles de résultats différents de ceux extraits initialement.  Les notifications générées au niveau du serveur sont envoyées via des files d'attente pour être traitées ultérieurement.  
  
 Vous pouvez configurer des notifications pour les instructions SELECT et EXECUTE.  Avec une instruction EXECUTE, SQL Server enregistre une notification pour la commande exécutée et non l'instruction EXECUTE elle\-même.  La commande doit répondre aux spécifications et aux limitations d'une instruction SELECT.  Lorsqu'une commande qui enregistre une notification contient plusieurs instructions, le moteur de base de données crée une notification pour chaque instruction du lot.  
  
 Si vous développez une application où vous avez besoin de notifications fiables à la fraction de seconde près quand des données sont modifiées, consultez les sections **Planification d'une stratégie efficace de notifications de requête** et **Alternatives aux notifications de requête** dans la rubrique [Planification des notifications](http://go.microsoft.com/fwlink/?LinkId=211984) de la documentation en ligne de SQL Server.  Pour plus d'informations sur les notifications de requête et Service Broker de SQL Server, voir les liens aux rubriques ci\-dessous dans la documentation en ligne de SQL Server.  
  
 **Documentation en ligne de SQL Server**  
  
-   [Utilisation des notifications de requête](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [Création d'une requête pour la notification](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Service Broker](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [Centre d'informations du développeur Service Broker](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Développement \(Service Broker\)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## Dans cette section  
 [Activation des notifications de requête](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 Explique comment utiliser des notifications de requête incluant les exigences relatives à leur utilisation et à leur activation.  
  
 [SqlDependency dans une application ASP.NET ](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 Montre comment utiliser les notifications de requête à partir d'une application ASP.NET.  
  
 [Détection des modifications à l'aide de SqlDependency](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 Montre comment détecter lorsque les résultats de la requête seront différents de ceux reçus à l'origine.  
  
 [Exécution de SqlCommand avec un SqlNotificationRequest](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Illustre la configuration d'un objet <xref:System.Data.SqlClient.SqlCommand> pour travailler avec une notification de requête.  
  
## Référence  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Décrit la classe <xref:System.Data.Sql.SqlNotificationRequest> et tous ses membres.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Décrit la classe <xref:System.Data.SqlClient.SqlDependency> et tous ses membres.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Décrit la classe <xref:System.Web.Caching.SqlCacheDependency> et tous ses membres.  
  
## Voir aussi  
 [SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)