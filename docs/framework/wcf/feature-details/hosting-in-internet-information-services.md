---
title: "Hébergement dans les services IIS (Internet Information Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc0a2692e105588d482156dfa870d8e587008b8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-in-internet-information-services"></a>Hébergement dans les services IIS (Internet Information Services)
L'une des solutions pour héberger les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] consiste à les inclure dans les services IIS (Internet Information Services). Ce modèle d'hébergement est semblable au modèle utilisé par [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et les services Web ASP.NET (ASMX).  
  
## <a name="versions-of-iis"></a>Versions d'IIS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être hébergé sur les versions suivantes d'IIS et sur les systèmes d'exploitation suivants :  
  
-   IIS 5.1 sur [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Cet environnement est utile pour la conception et développement d'applications hébergées par IIS et déployées ultérieurement sur un système d'exploitation de serveur tel que [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] sur [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] fournit un modèle de processus avancé qui offre une évolutivité, une fiabilité et une isolation d'application améliorées. Cet environnement est approprié pour le déploiement de la production des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui utilisent la communication HTTP exclusivement.  
  
-   IIS 7.0 sur [!INCLUDE[wv](../../../../includes/wv-md.md)] et [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. ISS 7.0 fournit le même modèle de processus avancé que [!INCLUDE[iis601](../../../../includes/iis601-md.md)], mais il utilise le service d'activation de processus de Windows (WAS) pour autoriser l'activation et la communication réseau sur des protocoles autres que HTTP. Cet environnement est adapté au développement de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui communiquent sur tous les protocoles réseau pris en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (y compris HTTP, net.tcp, net.pipe et net.msmq). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]A été, consultez [hébergement dans le Service d’Activation des processus Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) fonctionne avec [!INCLUDE[iisver](../../../../includes/iisver-md.md)] et le Service de l’Activation des processus Windows (WAS) pour fournir une environnement de services aux services NET4 WCF et WF d’hébergement d’application riche. Ces avantages incluent la gestion du cycle de vie de processus, le recyclage de processus, l'hébergement partagé, la protection rapide contre les incidents, les processus parallèles, l'activation à la demande et le contrôle d'état. Pour plus d’informations, consultez [fonctionnalités d’hébergement AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494) et [Concepts d’hébergement AppFabric](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Avantages de l'hébergement IIS  
 L'hébergement de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans IIS offre plusieurs avantages :  
  
-   Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS sont déployés et gérés comme tout autre type d'application IIS, y compris les applications [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et ASMX.  
  
-   IIS assure l'activation de processus, la gestion de l'intégrité et le recyclage des fonctions afin d'accroître la fiabilité des applications hébergées.  
  
-   À l'instar de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] peuvent tirer parti du modèle d'hébergement partagé de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] où plusieurs applications résident dans un processus de traitement commun afin d'optimiser l'évolutivité et la densité des serveurs.  
  
-   Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans IIS utilisent le même modèle de compilation dynamique qu'[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], ce qui simplifie le développement et le déploiement des services hébergés.  
  
 Lorsque vous décidez d'héberger des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans IIS, rappelez-vous que IIS 5.1 et [!INCLUDE[iis601](../../../../includes/iis601-md.md)] sont limités uniquement à la communication HTTP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]choix d’un environnement d’hébergement, consultez [Services d’hébergement](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Déploiement d'un service WCF hébergé par IIS  
 Le développement et le déploiement d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergé par IIS impliquent les tâches suivantes :  
  
-   Vérifier que IIS, ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ainsi que le composant d'activation HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont installés et inscrits correctement.  
  
-   Créer une application IIS ou réutiliser une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] existante.  
  
-   Créer un fichier .svc pour le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .  
  
-   Déployer l'implémentation de service vers l'application IIS.  
  
-   Configurer le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .  
  
 Pour en savoir plus sur chacune de ces tâches, consultez [déploiement d’un Service WCF de sujet](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Services WCF et ASP.NET  
 Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent être hébergés côte à côte avec [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou en mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dans lequel les services peuvent tirer parti des fonctionnalités fournies par la plateforme d'application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Pour une description de ces fonctionnalités, consultez [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de l’hébergement à l’aide de ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Déploiement d’un Service Internet Information Services hébergés de WCF](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Internet Information Services d’hébergement des meilleures pratiques](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Configuration d’Internet Information Services 7.0 pour Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Fonctionnalités d’hébergement de Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
