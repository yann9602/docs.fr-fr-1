---
title: "Procédure : déterminer la version de découverte d'une demande Probe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f51f48d6eefcc0f8ae5129526477d6e2a5b2385
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Procédure : déterminer la version de découverte d'une demande Probe
Un proxy de découverte peut exposer plusieurs points de terminaison de découverte à l'aide de différentes versions de découverte. Lorsqu'une demande UDP multicast Probe arrive au proxy, celui-ci doit répondre avec un message de suppression de multidiffusion. Pour cela, il doit connaître la version de découverte de la demande.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Pour déterminer la version de découverte d'une demande Probe  
  
1.  Dans la méthode qui répond à une demande Probe (par exemple <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) utilisez la propriété <xref:System.ServiceModel.OperationContext.Current%2A> statique pour rechercher un <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> comme indiqué dans le code suivant.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [Implémentation d’un proxy de découverte](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [Exemple de proxy de découverte](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
