---
title: "H&#233;bergement dans une application manag&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# H&#233;bergement dans une application manag&#233;e
Les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peuvent être hébergés dans toute application [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Les services auto\-hébergés constituent l'option d'hébergement la plus flexible parce qu'ils requièrent le déploiement de moins d'infrastructure. Toutefois, c'est également l'option d'hébergement la moins fiable, parce que les applications gérées ne fournissent pas les fonctionnalités d'hébergement et de gestion avancées offertes par d'autres solutions d'hébergement dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], comme les services IIS \(Internet Information Services\) et les services Windows.  
  
 Pour créer un service auto\-hébergé, créez et ouvrez une instance d'objet <xref:System.ServiceModel.ServiceHost>, qui démarre un service d'écoute des messages.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Comment : héberger un service WCF dans une application managée](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Pour obtenir un exemple complet sur la définition et l’implémentation d’un contrat ainsi que sur l’hébergement d’un service dans une application managée, consultez [Didacticiel de mise en route](../../../../docs/framework/wcf/getting-started-tutorial.md) et [Self\-Host](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Les sections suivantes décrivent des scénarios courants utilisant cette option d'hébergement.  
  
## Applications console  
 Les scénarios courants autorisés par l'auto\-hébergement sont les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent à l'intérieur d'applications console. L'hébergement d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'intérieur d'une application console est en général utile pendant la phase de développement du service. Cela simplifie son débogage, l'obtention des informations de suivi pour déterminer ce qui se passe à l'intérieur de l'application, et son déplacement en la copiant vers un nouvel emplacement.  
  
## Applications clientes complexes  
 Les autres scénarios courants autorisés par l'auto\-hébergement sont les applications clientes élaborées, comme [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] ou Windows Forms \(WinForms\). Cette option d'hébergement permet aux applications clientes complexes, comme [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] et WinForms, de communiquer facilement avec le monde extérieur. Il peut s'agit par exemple, d'un client de collaboration pair à pair qui utilise [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] pour son interface utilisateur et héberge également un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui permet à d'autres clients de se connecter à lui et de partager des informations.  
  
## Voir aussi  
 [Hébergement de services](../../../../docs/framework/wcf/hosting-services.md)   
 [Didacticiel de mise en route](../../../../docs/framework/wcf/getting-started-tutorial.md)