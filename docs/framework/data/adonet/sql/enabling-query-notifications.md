---
title: "Activation de notifications de requête"
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
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 473f1ca54d54a1d852edaed424729778e5a7513d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-query-notifications"></a>Activation de notifications de requête
Les applications qui utilisent des notifications de requête ont un ensemble commun d’exigences. Votre source de données doit être correctement configurée pour prendre en charge les notifications de requête SQL et l'utilisateur doit disposer des autorisations appropriées côté client et côté serveur.  
  
 Pour utiliser des notifications de requête, vous devez :  
  
-   Activer les notifications de requête pour votre base de données.  
  
-   Veiller à ce que l'ID utilisateur utilisé pour se connecter à la base de données dispose des autorisations nécessaires.  
  
-   Utiliser un objet <xref:System.Data.SqlClient.SqlCommand> pour exécuter une instruction SELECT valide avec un objet notification associé — <xref:System.Data.SqlClient.SqlDependency> ou <xref:System.Data.Sql.SqlNotificationRequest>.  
  
-   Fournir le code permettant de traiter la notification en cas de modification des données surveillées.  
  
## <a name="query-notifications-requirements"></a>Spécifications des notifications de requête  
 Les notifications de requête ne sont prises en charge que pour les instructions SELECT qui répondent à une liste de spécifications précises. Le tableau suivant présente des liens vers la documentation consacrée à Service Broker et aux notifications de requête dans la documentation en ligne de SQL Server.  
  
 **Documentation en ligne de SQL Server**  
  
-   [Création d’une requête de Notification](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Considérations sur la sécurité pour Service Broker](http://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [Sécurité et Protection (Service Broker)](http://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [Considérations de sécurité pour les Services de Notifications](http://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [Autorisations associées aux notifications de requête](http://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [Considérations internationales pour Service Broker](http://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [Considérations de conception de solution (Service Broker)](http://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [Centre d’informations du développeur Service Broker](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Guide du développeur (Service Broker)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Activation des notifications de requête pour exécuter l'exemple de code  
 Pour activer Service Broker sur le **AdventureWorks** de la base de données à l’aide de SQL Server Management Studio, exécutez l’instruction Transact-SQL suivante :  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Pour que les exemples de notification de requête s'exécutent correctement, les instructions Transact-SQL suivantes doivent être exécutées sur le serveur de base de données.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Autorisations de notifications de requête  
 Les utilisateurs qui exécutent des commandes nécessitant une notification doivent disposer d'une autorisation de base de données SUBSCRIBE QUERY NOTIFICATIONS sur le serveur.  
  
 Le code côté client exécuté dans une situation de confiance partielle requiert le <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Le code suivant crée un objet <xref:System.Data.SqlClient.SqlClientPermission> en affectant la valeur <xref:System.Security.Permissions.PermissionState> à l'objet <xref:System.Security.Permissions.PermissionState.Unrestricted>. La méthode <xref:System.Security.CodeAccessPermission.Demand%2A> forcera un objet <xref:System.Security.SecurityException> au moment de l'exécution si l'autorisation n'a été accordée à aucun des appelants figurant plus haut dans la pile des appels.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Sélection d'un objet notification  
 L'API des notifications de requête fournit deux objets pour traiter les notifications :<xref:System.Data.SqlClient.SqlDependency> et <xref:System.Data.Sql.SqlNotificationRequest>. En règle générale, la plupart des applications non ASP.NET doivent utiliser l'objet <xref:System.Data.SqlClient.SqlDependency>. Les applications ASP.NET doivent utiliser le <xref:System.Web.Caching.SqlCacheDependency> de niveau supérieur, qui enveloppe <xref:System.Data.SqlClient.SqlDependency> et fournit un cadre pour l'administration des objets notification et cache.  
  
### <a name="using-sqldependency"></a>Utilisation de SqlDependency  
 Pour utiliser <xref:System.Data.SqlClient.SqlDependency>, Service Broker doit être activé pour la base de données SQL Server utilisée et les utilisateurs doivent disposer des autorisations nécessaires pour recevoir des notifications. Les objets Service Broker, tels que la file d'attente des notifications, sont prédéfinis.  
  
 De plus, l'objet <xref:System.Data.SqlClient.SqlDependency> lance automatiquement un thread de travail pour traiter les notifications à mesure qu'elles sont publiées dans la file d'attente ; il analyse également le message de Service Broker, en exposant les informations comme données d'argument d'événement. L'objet <xref:System.Data.SqlClient.SqlDependency> doit être initialisé par l'appel à la méthode `Start` afin d'établir une dépendance par rapport à la base de données. Il s'agit d'une méthode statique qui doit être appelée une fois durant l'initialisation de l'application pour chaque connexion requise à la base de données. La méthode `Stop` doit être appelée à la fin de l'application pour chaque connexion de dépendance établie.  
  
### <a name="using-sqlnotificationrequest"></a>Utilisation de SqlNotificationRequest  
 En revanche, <xref:System.Data.Sql.SqlNotificationRequest> requiert que vous implémentiez vous-même l'infrastructure d'écoute complète. En outre, tous les objets Service Broker tels que la file d'attente, le service et les types de message pris en charge par la file d'attente doivent être définis. Cette approche manuelle est utile si votre application requiert des messages ou des comportements de notification spéciaux, ou si votre application fait partie d'une application Service Broker plus large.  
  
## <a name="see-also"></a>Voir aussi  
 [Notifications de requête dans SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
