---
title: "Publication de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e0cf48d429282c692557fd66bc6ef1295e6a531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="publishing-metadata"></a>Publication de métadonnées
Les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] publient les métadonnées à l'aide d'un ou de plusieurs points de terminaison. La publication de métadonnées de service permet d'accéder à celles-ci à l'aide de protocoles standardisés, tels que WS-MetadataExchange (MEX) et les requêtes HTTP/GET. Les points de terminaison de métadonnées sont semblables aux autres points de terminaison de service dans le sens où ils ont une adresse, une liaison et un contrat, et qu'ils peuvent être ajoutés à un hôte de service via la configuration ou du code impératif.  
  
## <a name="publishing-metadata-endpoints"></a>Publication de points de terminaison de métadonnées  
 Pour publier des points de terminaison de métadonnées pour un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous devez dans un premier temps ajouter le comportement de service <xref:System.ServiceModel.Description.ServiceMetadataBehavior> au service. L'ajout d'une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> permet à votre service d'exposer des points de terminaison de métadonnées. Après avoir ajouté le comportement de service <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, vous pouvez ensuite exposer les points de terminaison de métadonnées qui prennent en charge le protocole MEX ou qui répondent aux requêtes HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> utilise <xref:System.ServiceModel.Description.WsdlExporter> pour exporter les métadonnées de tous les points de terminaison de service de votre service. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]exportation de métadonnées à partir d’un service, consultez [exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> ajoute une instance <xref:System.ServiceModel.Description.ServiceMetadataExtension> comme extension à votre hôte de service. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> fournit l'implémentation pour les protocoles de publication de métadonnées. Vous pouvez également utiliser <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> pour obtenir les métadonnées de service au moment de l'exécution en accédant à la propriété <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType>.  
  
### <a name="mex-metadata-endpoints"></a>Points de terminaison de métadonnées MEX  
 Pour ajouter des points de terminaison de métadonnées qui utilisent le protocole MEX, ajoutez des points de terminaison de service à votre hôte de service qui utilisent le contrat de service nommé `IMetadataExchange`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclut une interface <xref:System.ServiceModel.Description.IMetadataExchange> avec ce nom de contrat de service que vous pouvez utiliser dans le cadre du modèle de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Les points de terminaison WS-MetadataExchange (ou points de terminaison MEX) peuvent utiliser l'une des quatre liaisons par défaut que les méthodes de fabrique statiques exposent sur la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings> afin d'établir une correspondance avec les liaisons par défaut utilisées par les outils [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tels que Svcutil.exe. Vous pouvez également configurer des points de terminaison de métadonnées MEX à l'aide de votre propre liaison personnalisée.  
  
### <a name="http-get-metadata-endpoints"></a>Points de terminaison de métadonnées HTTP GET  
 Pour ajouter un point de terminaison de métadonnées à votre service qui répond aux requêtes HTTP/GET, affectez <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> sur `true`. Vous pouvez également configurer un point de terminaison de métadonnées qui utilise HTTPS en affectant <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> sur `true`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment : publier des métadonnées pour un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Indique comment configurer un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] afin de publier les métadonnées et permettre ainsi aux clients de les récupérer à l'aide d'un échange WS-MetadataExchange ou d'une requête HTTP/GET en utilisant la chaîne de requête `?wsdl`.  
  
 [Comment : publier les métadonnées d’un Service à l’aide de Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Indique comment activer la publication de métadonnées pour un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans le code afin que les clients puissent les récupérer à l'aide d'un échange WS-MetadataExchange ou d'une requête HTTP/GET en utilisant la chaîne de requête `?wsdl`.  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
