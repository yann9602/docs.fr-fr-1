---
title: "Ex&#233;cution de SqlCommand avec un SqlNotificationRequest | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Ex&#233;cution de SqlCommand avec un SqlNotificationRequest
Un <xref:System.Data.SqlClient.SqlCommand> peut être configuré pour générer une notification lors de la modification de données, une fois qu'il a été extrait à partir du serveur et que le jeu de résultats est différent en cas de nouvelle exécution de la requête.  Cette fonction est utile dans les scénarios où vous voulez utiliser des files d'attente de notification personnalisées sur le serveur ou lorsque vous ne souhaitez pas conserver des objets actifs.  
  
## Création de la demande de notification  
 Vous pouvez utiliser un objet <xref:System.Data.Sql.SqlNotificationRequest> pour créer la demande de notification en le liant à un objet `SqlCommand`.  Une fois la demande créée, vous n'avez plus besoin de l'objet `SqlNotificationRequest`.  Vous pouvez interroger la file d'attente pour toute notification et réagir de façon appropriée.  Des notifications peuvent survenir même si l'application est arrêtée, puis redémarrée.  
  
 Lorsque la commande avec la notification associée est exécutée, toute modification du jeu de résultats d'origine déclenche l'envoi d'un message à la file d'attente SQL Server qui a été configurée dans la demande de notification.  
  
 La manière dont vous interrogez la file d'attente SQL Server et interprétez le message est spécifique à votre application.  L'application est chargée d'interroger la file d'attente et de réagir en fonction du contenu du message.  
  
> [!NOTE]
>  Lors de l'utilisation de demandes de notification SQL Server avec <xref:System.Data.SqlClient.SqlDependency>, créez votre propre nom de file d'attente au lieu d'utiliser le nom de service par défaut.  
  
 Il n'y a pas de nouveaux éléments de sécurité côté client pour <xref:System.Data.Sql.SqlNotificationRequest>.  Il s'agit principalement d'une fonctionnalité du serveur et le serveur a créé des privilèges spéciaux dont les utilisateurs doivent disposer pour demander une notification.  
  
### Exemple  
 Le fragment de code ci\-dessous montre comment créer un <xref:System.Data.Sql.SqlNotificationRequest> et l'associer à un <xref:System.Data.Sql.SqlCommand>.  
  
```vb  
' Assume connection is an open SqlConnection.  
' Create a new SqlCommand object.  
Dim command As New SqlCommand( _  
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)  
  
' Create a SqlNotificationRequest object.  
Dim notficationRequest As New SqlNotificationRequest()  
notficationRequest.id = "NotificationID"  
notficationRequest.Service = "mySSBQueue"  
  
' Associate the notification request with the command.  
command.Notification = notficationRequest  
' Execute the command.  
command.ExecuteReader()  
' Process the DataReader.  
' You can use Transact-SQL syntax to periodically poll the   
' SQL Server queue to see if you have a new message.  
```  
  
```csharp  
// Assume connection is an open SqlConnection.  
// Create a new SqlCommand object.  
SqlCommand command=new SqlCommand(  
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);  
  
// Create a SqlNotificationRequest object.  
SqlNotificationRequest notficationRequest=new SqlNotificationRequest();  
notficationRequest.id="NotificationID";  
notficationRequest.Service="mySSBQueue";  
  
// Associate the notification request with the command.  
command.Notification=notficationRequest;  
// Execute the command.  
command.ExecuteReader();  
// Process the DataReader.  
// You can use Transact-SQL syntax to periodically poll the   
// SQL Server queue to see if you have a new message.  
  
```  
  
## Voir aussi  
 [Notifications de requête dans SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)