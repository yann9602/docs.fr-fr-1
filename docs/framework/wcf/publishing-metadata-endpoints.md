---
title: "Publication de points de terminaison de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f4d7d99304df1622f482a827d67d389760bf76d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="publishing-metadata-endpoints"></a>Publication de points de terminaison de métadonnées
Les services [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] publient les métadonnées à l'aide d'un ou de plusieurs points de terminaison. La publication de métadonnées de service permet d'accéder à celles-ci à l'aide de protocoles standardisés, tels que WS-MetadataExchange (MEX) et les requêtes HTTP/GET. Les points de terminaison de métadonnées sont semblables aux autres points de terminaison de service dans le sens où ils ont une adresse, une liaison et un contrat, et qu'ils peuvent être ajoutés à un hôte de service via la configuration ou dans du code. Pour activer la publication de points de terminaison de métadonnées, vous devez ajouter le comportement de service <xref:System.ServiceModel.Description.ServiceMetadataBehavior> au service.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour publier les métadonnées d’un service à l’aide d’un fichier de configuration](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Indique comment configurer un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] afin de publier les métadonnées et permettre ainsi aux clients de les récupérer à l'aide d'un échange WS-MetadataExchange ou d'une requête HTTP/GET en utilisant la chaîne de requête `?wsdl`.  
  
 [Guide pratique pour publier les métadonnées d’un service à l’aide de code](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Indique comment activer la publication de métadonnées pour un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dans le code afin que les clients puissent les récupérer à l'aide d'un échange WS-MetadataExchange ou d'une requête HTTP/GET en utilisant la chaîne de requête `?wsdl`.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de métadonnées](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
