---
title: "Comment&#160;: migrer le code client des services Web ASP.NET vers Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Comment&#160;: migrer le code client des services Web ASP.NET vers Windows Communication Foundation
La procédure suivante décrit la procédure générale de migration du code client des services Web ASP.NET vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Procédure  
  
#### Pour migrer le code client des services Web ASP.NET vers WCF  
  
1.  Assurez\-vous qu'un jeu complet de tests existe pour le client.  
  
2.  Utilisez Visual Studio 2005 pour mettre à niveau l'application cliente vers .NET 2.0.Exécutez le jeu de tests.  
  
3.  Supprimez le code client ASP.NET du projet client.Ce code se trouve dans les modules générés à l'aide de l'outil WSDL.exe.  
  
4.  Générez le code client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide de [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).Ajoutez ce code au projet client et fusionnez la sortie de la configuration dans le fichier de configuration existant du client.  
  
5.  Compilez l'application.Réparez les erreurs de compilation en remplaçant les références aux types de clients ASP.NET précédents par les références aux nouveaux types de clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
6.  Exécutez l'ensemble des tests.  
  
## Voir aussi  
 [Comment : migrer le code d'un service Web ASP.NET vers Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)