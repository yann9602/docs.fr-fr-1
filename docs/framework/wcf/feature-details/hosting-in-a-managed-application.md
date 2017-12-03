---
title: "Hébergement dans une application managée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e6543f1faec5d3298c9a2b825b3a016eb5e7d09
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-in-a-managed-application"></a>Hébergement dans une application managée
Les services[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peuvent être hébergés dans toute application [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] . Les services auto-hébergés constituent l'option d'hébergement la plus flexible parce qu'ils requièrent le déploiement de moins d'infrastructure. Toutefois, c'est également l'option d'hébergement la moins fiable, parce que les applications gérées ne fournissent pas les fonctionnalités d'hébergement et de gestion avancées offertes par d'autres solutions d'hébergement dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], comme les services IIS (Internet Information Services) et les services Windows.  
  
 Pour créer un service auto-hébergé, créez et ouvrez une instance d'objet <xref:System.ServiceModel.ServiceHost>, qui démarre un service d'écoute des messages. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : héberger un Service WCF dans une Application managée](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Pour obtenir un exemple complet sur la façon de définir un contrat, implémentez le contrat et héberger un service à l’intérieur d’une application managée, consultez le [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md) et [auto-hébergement](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Les sections suivantes décrivent des scénarios courants utilisant cette option d'hébergement.  
  
## <a name="console-applications"></a>Applications console  
 Les scénarios courants autorisés par l'auto-hébergement sont les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent à l'intérieur d'applications console. L'hébergement d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'intérieur d'une application console est en général utile pendant la phase de développement du service. Cela simplifie son débogage, l'obtention des informations de suivi pour déterminer ce qui se passe à l'intérieur de l'application, et son déplacement en la copiant vers un nouvel emplacement.  
  
## <a name="rich-client-applications"></a>Applications clientes complexes  
 Les autres scénarios courants autorisés par l'auto-hébergement sont les applications clientes élaborées, comme [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] ou Windows Forms (WinForms). Cette option d'hébergement permet aux applications clientes complexes, comme [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] et WinForms, de communiquer facilement avec le monde extérieur. Il peut s'agit par exemple, d'un client de collaboration pair à pair qui utilise [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] pour son interface utilisateur et héberge également un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui permet à d'autres clients de se connecter à lui et de partager des informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de services](../../../../docs/framework/wcf/hosting-services.md)  
 [Didacticiel Bien démarrer](../../../../docs/framework/wcf/getting-started-tutorial.md)
