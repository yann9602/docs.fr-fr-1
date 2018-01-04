---
title: "Intégration à des applications COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 130a7cda170721f34a5b44f3361bd591d6375267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications"></a>Intégration à des applications COM
Les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peuvent être intégrés directement dans votre code existant à l'aide du moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Le moniker de service peut être utilisé à partir d'une large gamme d'environnements de développement COM, tels qu'Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de l’intégration à des applications COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 Fournit une vue d'ensemble des principales phases du processus d'intégration.  
  
 [Guide pratique pour inscrire et configurer un moniker de service](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 Pour utiliser le moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans une application COM, inscrivez les types attribués requis avec COM et configurez l'application COM et le moniker avec la configuration de liaison requise.  
  
 [Guide pratique pour utiliser le moniker de service Windows Communication Foundation sans inscription](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 Explique comment obtenir la définition du contrat sous la forme d'un document WSDL (Web Services Definition Language) ou à partir d'un point de terminaison WS-MetadataExchange.  
  
 [Guide pratique pour utiliser un moniker de service avec des contrats WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 Décrit comment appeler un exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'un moniker WSDL [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Guide pratique pour utiliser un moniker de service avec des contrats d’échange de métadonnées](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 Décrit comment appeler un exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'un moniker [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui spécifie un point de terminaison Mex.  
  
 [Guide pratique pour spécifier des informations d’identification pour la sécurité des canaux](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 Le moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge l'interface `IChannelCredentials` qui prévoit une plage de méthodes secondaires pour spécifier des informations d'identification de canal.  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration à des applications COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
