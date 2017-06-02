---
title: "Op&#233;rations asynchrones | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Op&#233;rations asynchrones
L'exécution de certaines opérations de base de données, telles que des exécutions de commande, peut prendre du temps.  Dans ce cas, les applications mono\-thread doivent bloquer d'autres opérations et attendre que l'exécution de la commande s'achève avant de pouvoir continuer leurs propres opérations.  En revanche, la possibilité d'assigner l'opération longue à un thread d'arrière\-plan permet au thread à l'avant\-plan de rester actif pendant toute l'opération.  Dans une application Windows, par exemple, vous pouvez déléguer l'opération de longue durée à un thread d'arrière\-plan tout en autorisant le thread d'interface utilisateur à rester réactif pendant l'exécution de l'opération.  
  
 .NET Framework comprend plusieurs modèles de design asynchrone standard que les développeurs peuvent utiliser pour tirer parti des threads d'arrière\-plan et libérer l'interface utilisateur ou des threads hautement prioritaires pour l'accomplissement d'autres opérations.  ADO.NET prend en charge ces mêmes modèles de design dans sa classe <xref:System.Data.SqlClient.SqlCommand>.  Plus spécifiquement, les méthodes <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> et <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>, associées aux méthodes <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A> et <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A>, assurent la prise en charge des opérations asynchrones.  
  
> [!NOTE]
>  La programmation asynchrone est une fonction clé de .NET Framework et ADO.NET exploite pleinement les modèles de design standard.  Pour plus d'informations sur les techniques asynchrones disponibles pour les développeurs, voir [Calling Synchronous Methods Asynchronously](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Bien que l'utilisation de techniques asynchrones avec les fonctions d'ADO.NET ne nécessite pas de commentaires particuliers, il est probable que les développeurs utiliseront les fonctions asynchrones davantage dans ADO.NET que dans d'autres domaines de .NET Framework.  Il est important d'être conscient des avantages et des pièges liés à la création d'application multithread.  Les exemples présentés dans cette section épinglent plusieurs problèmes importants dont les développeurs doivent tenir compte lors de la création d'applications qui incorporent une fonctionnalité multithread.  
  
## Dans cette section  
 [Applications Windows utilisant des rappels](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Fournit un exemple montrant comment exécuter une commande asynchrone en toute sécurité, en gérant correctement l'interaction avec un formulaire et son contenu depuis un thread distinct.  
  
 [Applications ASP.NET utilisant des handles d'attente](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Fournit un exemple montrant comment exécuter plusieurs commandes simultanées à partir d'une page ASP.NET, en utilisant des handles d'attente pour gérer l'opération lors de l'accomplissement de toutes les commandes.  
  
 [Interrogation dans des applications console](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Fournit un exemple montrant l'utilisation de l'interrogation pour attendre l'accomplissement de l'exécution d'une commande asynchrone à partir d'une application console.  Cette technique est également valable dans une bibliothèque de classes ou une autre application sans interface utilisateur.  
  
## Voir aussi  
 [SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)   
 [Calling Synchronous Methods Asynchronously](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)