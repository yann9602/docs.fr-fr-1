---
title: "Comment : migrer le code client des services Web ASP.NET vers Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b93460fd6d331b43b49f10cf78fc8863ca1d8d88
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>Comment : migrer le code client des services Web ASP.NET vers Windows Communication Foundation
La procédure suivante décrit la procédure générale de migration du code client des services Web ASP.NET vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>Pour migrer le code client des services Web ASP.NET vers WCF  
  
1.  Assurez-vous qu'un jeu complet de tests existe pour le client.  
  
2.  Utilisez Visual Studio 2005 pour mettre à niveau l'application cliente vers .NET 2.0. Exécutez l'ensemble des tests.  
  
3.  Supprimez le code client ASP.NET du projet client. Ce code se trouve dans les modules générés à l'aide de l'outil WSDL.exe.  
  
4.  Générer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] code client qui utilise le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Ajoutez ce code au projet client et fusionnez la sortie de la configuration dans le fichier de configuration existant du client.  
  
5.  Compilez l'application. Réparez les erreurs de compilation en remplaçant les références aux types de clients ASP.NET précédents par les références aux nouveaux types de clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
6.  Exécutez l'ensemble des tests.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : migrer du Code de Service Web ASP.NET vers Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
